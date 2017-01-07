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

`next` inside a block returns from the block. `break` inside a block returns from the function that yielded to the block. For `each` this means that `break` exits the loop and `next` jumps to the next iteration of the loop (thus the names). You can return values with `next value` and `break value`.

```ruby
def foo
  f = Proc.new { return "return from foo from inside proc" }
  f.call
  return "return from foo"
end

def bar
  b = Proc.new { "return from bar from inside proc" }
  b.call
  return "return from bar"
end

puts foo #=> "return from foo from inside proc"
puts bar #=> "return from bar"
```

```ruby
[1,2,3].map do |x|
  next false unless x.even?
  2*x
end
#=> [false, nil, false]

[1,2,3].map do |x|
  break false unless x.even?
  2*x
end
#=> false
```

http://stackoverflow.com/questions/2518075/how-can-i-return-something-early-from-a-block
http://stackoverflow.com/questions/1435743/why-does-explicit-return-make-a-difference-in-a-proc
