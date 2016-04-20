### CLass Instance Variables

You can use this technique in any OO language. Ruby, however, actually has class instance variables.
    ```
    #ruby
    class Employee
      class << self; attr_accessor :instances; end
      def store
        self.class.instances ||= []
        self.class.instances << self
      end
      def initialize name
        @name = name
      end
    end

    class Overhead < Employee; end
    class Programmer < Employee; end

    Overhead.new('Martin').store
    Overhead.new('Roy').store
    Programmer.new('Erik').store
    puts Overhead.instances.size
    puts Programmer.instances.size
    ```
The definition of the class instance variable is the fragment class << self; attr_accessor :instances; end. For reasons that I don't really want to go into, this defines an instance variable (and getters and setters) on the class employee that's inherited by its descendents. Unlike class variables these class instance variables will take different values for each class object.

Class instance variables are pretty rare, but useful when you do need them.
