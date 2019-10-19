# Chapter 4 - Exercise

### Implement the lazy version of Enumerable#select() and Enumerable#drop()

```ruby
module Enumerable
  def lax
    Lax.new(self)
  end
end

class Lax < Enumerator
  def initialize(receiver)
    super() do |yielder|
      begin
        receiver.each do |val|
          if block_given?
            yield(yielder, val)
          else
            yielder << val
          end
        end
      rescue StopIteration
      end
    end
  end

  def map(&block)
    Lax.new(self) do |yielder, val|
      yielder << block.call(val)
    end
  end

  def take(n)
    taken = 0
    Lax.new(self) do |yielder, val|
      if taken < n
        yielder << val
        taken += 1
      else
        raise StopIteration
      end
    end
  end

  def select(&block)
    Lax.new(self) do |yielder, val|
      if block.call(val)
        yielder << val
      end
    end
  end

  def drop(n)
    dropped = 0
    Lax.new(self) do |yielder, val|
      if dropped < n
        dropped += 1
      else
        yielder << val
      end
    end
  end
end

# Test
1.upto(Float::INFINITY).lax.map { |x| x*x }.map { |x| x+1 }.take(5).to_a
1.upto(Float::INFINITY).lax.select { |x| x % 2 == 0 }.take(5).to_a
1.upto(Float::INFINITY).lax.drop(3).take(5).to_a
```