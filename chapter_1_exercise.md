# Chapter 1 - Exercise

### 1. What is the definition of a closure?

  Closure is a function that references a variable which is hold from parent scope.

### 2. Identify the free variable in the following

  "amount"

### 3. Implement database with lambda

```ruby
# Implement

new_db = lambda do
  database = {}
  insert = lambda { |k, v| database[k] = v }
  dump = lambda { database }
  delete = lambda { |k| database.delete(k) }
  { insert: insert, dump: dump, delete: delete }
end

# Test

db = new_db.call
db[:insert].call('A', 'a')
# => a

db[:insert].call('B', 'b')
# => b

db[:dump].call
# => { 'A' => 'a', 'B' => 'b' }

db[:delete].call('B')
# => 'b'

db[:dump].call
# => {'A' => 'a'}
```

### 4. Refactor complement()

```ruby
# Implement
complement = lambda do |predicate|
  lambda do |value|
    not predicate.call(value)
  end
end

# Test
is_even = lambda { |x| x % 2 == 0 }

complement.call(is_even).call(4)
# => false

complement.call(is_even).call(5)
# => true
```
   
### 5. Use #reduce like a #map

```ruby
[1,2,3,4,5].reduce([]) do |arr, x|
  arr << x * 2
end

# => [2,4,6,8,10]
```