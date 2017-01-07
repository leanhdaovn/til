_07/01/2017_

## Block `return`, `break`, `next`

Ruby has three constructs:

1. A block is not an object and is created by `{ ... }` or `do ... end`.
2. A proc is a `Proc` object created by `Proc.new` or `proc`.
3. A lambda is a `Proc` created by `lambda`.

Ruby has three keywords that return from something:

1. `return` terminates the method or lambda it is in.
2. `next` terminates the block, proc, or lambda it is in.
3. `break` terminates the method that yielded to the block or invoked the proc or lambda it is in.

In lambdas, `return` behaves like `next`, for whatever reason.

```ruby
def foo
  f = Proc.new { return "inner proc" }
  f.call
  return "foo"
end

def bar
  b = Proc.new { "inner proc" }
  b.call
  return "bar"
end

def foo2
  b = lambda { return "inner lambda" }
  b.call
  return "foo2"
end

puts foo #=> "inner proc"
puts bar #=> "bar"
puts foo2 #=> "foo2"
```

`next` inside a block returns from the block. `break` inside a block returns from the function that yielded to the block. For `each` this means that `break` exits the loop and `next` jumps to the next iteration of the loop (thus the names). You can return values with `next value` and `break value`.

```ruby
foo = [1, 2, 3].map do |x|
  next false unless x.even?
  true
end

bar = [1, 2, 3].map do |x|
  break false unless x.even?
  true
end

p foo #=> [false, true, false]
p bar #=> false
```

http://stackoverflow.com/questions/2518075/how-can-i-return-something-early-from-a-block
http://stackoverflow.com/questions/1435743/why-does-explicit-return-make-a-difference-in-a-proc
