###What's the difference between Ruby's dup and clone methods?
Subclasses may override these methods to provide different semantics. In Object itself, there are two key differences.

First, clone copies the singleton class, while dup does not.

o = Object.new
def o.foo
  42
end

o.dup.foo   # raises NoMethodError
o.clone.foo # returns 42
Second, clone preserves the frozen state, while dup does not.

class Foo
  attr_accessor :bar
end
o = Foo.new
o.freeze

o.dup.bar = 10   # succeeds
o.clone.bar = 10 # raises RuntimeError
The Rubinius implementation for these methods is often my source for answers to these questions, since it is quite clear, and a fairly compliant Ruby implementation.

When dealing with ActiveRecord there's a significant difference too:

dup creates a new object without its id being set, so you can save a new object to the database by hitting .save

category2 = category.dup
#=> #<Category id: nil, name: "Favorites">
clone creates a new object with the same id, so all the changes made to that new object will overwrite the original record if hitting .save

category2 = category.clone
#=> #<Category id: 1, name: "Favorites">

Both DUP & CLONE can be used to create shallow copy of an object. Both copies the instance variables of obj. But we need to be selective in their usage.

Few difference between these are

1) CLONE copies both FROZEN and TAINTED state of an object, where as DUP only copies TAINTED state of an object.

2) With CLONE you can copy any singleton methods of an object but DUP does not support this.

CLONE is used to duplicate an object, including its internal state, DUP typically uses the class of the descendent object to create the new instance.

I had some bitter experience while using DUP for duplicating an ActiveRecord row, this ended up in losing the original one the same worked fine with CLONE.
