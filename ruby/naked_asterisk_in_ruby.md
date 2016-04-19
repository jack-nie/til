###Naked asterisk parameters in Ruby

  '''
  class Bar
    def save(*args)
      puts "Args passed to superclass Bar#save: #{args.inspect}"
    end
  end

  class Foo < Bar
    def save(*)
      puts "Entered Foo#save"
      super
    end
  end

  Foo.new.save("one", "two")
  '''

which will print out the following:

  '''
  Entered Foo#save
  Args passed to superclass Bar#save: ["one", "two"]
  '''

The globbed arguments are automatically passed up to the superclass method. Some might be of the opinion that it's better to be explicit and define methods with def method(*args), but in any case it's a neat trick worth knowing!
