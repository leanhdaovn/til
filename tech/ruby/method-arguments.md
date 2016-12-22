_12/22/2016_

# Ruby method arguments

#### Basic method arguments
```ruby
def calculate(a, b, c)
  a + b - c
end

calculate(3,2,1) #=> 4
```
-----

#### Arguments with default value (optional arguments)
```ruby
def calculate(a, b = 1, c = 2)
  a + b - c
end

calculate(3,2,1) #=> 4
calculate(3,2) #=> 3
calculate(3) #=> 2
```
-----

#### Keyword arguments (Ruby 2.0)
```ruby
def foo(bar: 'default', boo: 'aha')
  puts "#{bar}-#{boo}"
end

foo #=> 'default-aha'
foo(bar: 'baz') #=> 'baz-aha'
foo(bar: 'baz', boo: 'beer') #=> 'baz-beer'
foo(other_key: "other_value") #=> ArgumentError: unknown keywords: other_key
data = {bar: 'baz', boo: 'beer'}
foo(data) #=> 'baz-beer'
```

Ruby 2.0 blocks can also be defined with keyword arguments
```ruby
define_method(:foo) do |bar: 'default'|
  puts bar
end

foo #=> 'default'
foo(bar: 'baz') #=> 'baz'
```

Positions of keyword arguments can be flexible
```ruby
def calculate(a = 3, b = 1, c = 2)
  a + b - c
end

calculate(3,2,1) #=> 4
calculate(1,2,3) #=> 0

def calculate_keyword(a: 3, b: 1, c: 2)
  a + b - c
end

calculate_keyword(a: 3, b: 2, c: 1) #=> 4
calculate_keyword(c: 1, b: 2, a: 3) #=> 4
```

-----

#### Required keyword arguments
```ruby
def foo(bar:)
  puts bar
end

foo #=> ArgumentError: missing keyword: bar
foo(bar: 'baz') #=> 'baz'
```
-----

#### Splat arguments
```ruby

```
-----

#### Double splat arguments
```ruby

```
-----
