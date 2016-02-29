###Block, lambda, proc, return, next, break

Ruby has three constructs:

. A block is not an object and is created by { ... } or do ... end.
. A proc is a Proc object created by Proc.new or proc.
. A lambda is a Proc created by lambda (or proc in Ruby 1.8).

Ruby has three keywords that return from something:

. return terminates the method or lambda it is in.
. next terminates the block, proc, or lambda it is in.
. break terminates the method that yielded to the block or invoked the proc or lambda it is in.

In lambdas, return behaves like next, for whatever reason. next and break are named the way they are because they are most commonly used with methods like each, where terminating the block will cause the iteration to resume with the next element of the collection, and terminating each will cause you to break out of the loop.

If you use return inside the definition of foo, you will return from foo, even if it is inside a block or a proc. To return from a block, you can use the next keyword instead.

```
def foo
  f = Proc.new { next "return from foo from inside proc" }
  f.call # control leaves foo here
  return "return from foo"
end
puts foo # prints "return from foo"
```
