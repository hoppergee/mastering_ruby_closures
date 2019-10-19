# Chapter 2 - Exercise

### 1. Implement Array#map() using Array#each()

```ruby
class Array
  def map
    i = 0
    arr = []
    while i < self.size
      arr << yield self[i]
      i += 0
    end
    arr
  end
end


# Test
%w[look ma n for loops].map do |x|
  x.upcase
end
```

### 2. Implement String#each_word()

```ruby
class String
  def each_word
    split(' ').each do |x|
      yield(x)
    end
  end
end

# Test
"Nothing lasts forever but cold November Rain".each_word do |x|
  puts x
end
```

### 3. Implement File.open

```ruby
class File
  def self.open(file_path, mode)
    file = new(file_path, mode)
    return file unless block_given?
    yield(file)
  ensure
    file.close
  end
end
```

### 4. redis sample codes

1. Does run() requre a block to be passed in? Yes.
2. How is the return result of the block used? symbol or something else
3. How could this code be called? `Redis::Server::new.run { :exit }`

### 5. Implement ActiveRecord DSL

```ruby
module ActiveRecord
  class Schema
    def self.define(version, &block)
      @version = version
      instance_eval &block
    end

    def self.create_table(table_name, options = {}, &block)
      t = Table.new(table_name, options)
      yield t
    end
  end

  class Table
    def initialize(name, options)
      @name = name
      @options = options
    end

    def string(value)
      puts "Creating column of type string name #{value}"
    end

    def integer(value)
      puts "Creating column of type integer name #{value}"
    end

    def datetime(value)
      puts "Creating column of type datetime name #{value}"
    end
  end
end

# Test
ActiveRecord::Schema.define(version: 20130315230445) do
  create_table "microposts", force: true do |t|
    t.string "content"
    t.integer "user_id"
    t.datetime "created_at"
    t.datetime "updated_at"
  end
end
```
