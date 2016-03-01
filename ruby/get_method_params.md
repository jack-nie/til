###Get method params

in Ruby 1.9.2 you can use the parameters method on a method to get the list of parameters for that method. This will return a list of pairs indicating the name of the parameter and whether it is required.

e.g.

If you do

```
def foo(x, y)
end
```

then

```
method(:foo).parameters # => [[:req, :x], [:req, :y]]
```

You can use the special variable __method__ to get the name of the current method. So within a method the names of its parameters can be obtained via

```
args = method(__method__).parameters.map { |arg| arg[1] }

```
You could then display the name and value of each parameter with

```
logger.error "Method failed with " + args.map { |arg| "#{arg} = #{eval arg}" }.join(', ')

```

