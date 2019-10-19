# Chapter 3 - Exercise

### 1. Reimplement Symbol#to_proc()

```ruby
class Symbol
  def to_proc
    proc { |obj, args| obj.send(self, *args); }
  end
end

# Test
[1,2,3].map(&:to_s)
[1,2,3].inject(&:+)
```

### 2. use #to_proc() to instantiate classes

```ruby
class SpiceGirl
  def self.to_proc
    lambda { |args| new(*args) }
  end

  def initialize(name, nick)
    @name = name
    @nick = nick
  end

  def inspect
    "#{@name} (#{@nick}) Spice"
  end
end

# Test
spice_girls = [['Mel B', 'Scary'], ['Mel C', 'Sporty'],['Emma B', 'Baby']]
p spice_girls.map(&SpiceGirl)
```

### 3. difference between Proc and lambda in Ruby

* lambda has a more strict arguments number check than Proc.
  * If arguments number is not right lambda will raise an error.
* Proc always return from the context it was created
  * This different only exist when using `return`

### 4. What is the class of proc {}? What about lambda {}?

Their classes both are Proc.
