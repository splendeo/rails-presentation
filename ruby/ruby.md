!SLIDE subsection

# Ruby #

!SLIDE bullets

# Several environments #

* 1.8.7 - legacy
* 1.9.2 - standard
* jRuby - jvm
* rubinious
* ...

!SLIDE bullets commandline

# Interactive Ruby

* \*nix  : `irb`
* windows: `fxri`

!SLIDE commandline incremental

    $irb(main):001:0> "Hello World"
    => "Hello World"

    $irb(main):001:0> 1+1
    => 2

    $irb(main):001:0> puts("Hello World")
    "Hello World"
    => nil

!SLIDE bullets

# Ruby has __conventions__ #

* Programmer-enforced Rules
* *Not* compiler-enforced

!SLIDE bullets

# Convention: Indentation #

* Always two spaces
* No tabs
* No discussion

!SLIDE bullets

# Convention: Names #

* Class names are `CamelCased`
* Constants are `ALL_CAPS_WITH_UNDERSCORES`\*
* Everything else is `under_scored`

\* Not entirely true

!SLIDE

# Object Oriented #

    @@@ ruby
    class Person

      def initialize(name)
        @name = name
      end

      def speak()
        puts("Hi, I am #{@name}")
      end

    end

    peter = Person.new("Peter")
    peter.speak() # Hi, I am Peter

!SLIDE

# Inheritance #

    @@@ ruby
    class Employee < Person

      def initialize(name, salary)
        super(name)
        @salary = salary
      end

    end

    michael = Employee.new("Michael", 10000)
    michael.speak() # Hi, I am Michael

!SLIDE

# Optional parenthesis #

## (most of the time) ##

    @@@ ruby
    sam = Employee.new("Sam", 30000)
    sam.speak()

    # same result:
    sam = Employee.new "Sam", 30000
    sam.speak

!SLIDE

# Convention: Question mark #

## On methods returning only `true` or `false` ##

    @@@ ruby
    17.even?   # false
    "".empty?  # true

!SLIDE

# Convention: Excl. mark #

## On _state-modifying __versions__ of methods_ ##

    @@@ ruby
    str = "Hello"
    other = str.upcase # doesn't modify str

    puts(str)   # Hello
    puts(other) # HELLO

    str.upcase! # modifies str
    puts(str)   # HELLO

!SLIDE

# _Everything_ is an object #

    @@@ ruby
    1.next         # 2
    -15.abs        # 15
    "hello".length # 5

    # Lots of stuff built-in:

    1.methods.count  # 130
    "".methods.count # 160

!SLIDE bullets

# `nil` and `false` #

* The only "falsy" values
* They are also objects
* Everything else is "truthy"
* `obj.nil?` method


!SLIDE

# Arrays #

    @@@ ruby

    array = [ 1, 2, 3, "catorce" ]

    array[4] # returns "catorce"
    array[4] = 4
    array[4] # returns 4

!SLIDE

# Parsing an array with `each` #

    @@@ ruby

    [ 1, 2, 3, 4 ].each do |n|
      puts(n)
    end

    # or

    [ 1, 2, 3, 4 ].each{ |n| puts(n) }

!SLIDE

# `String` vs `Symbol` #

    @@@ ruby
    string = "hello"
    symbol = :hello

    string != symbol      # not equal
    string == symbol.to_s # unless converted

!SLIDE bullets

# `String` vs `Symbol` (II) #

* `String`: _text that changes_, ex. db text fields.
* `Symbol`: _text that identifes_, ex. "enums"

!SLIDE bullets

# Hashes #

*  Can use anything as keys/values
*  Frequently use symbols for keys

!SLIDE

    @@@ ruby

    properties = {
      :name => "number_of_dwarves",
      :value => 7
    }

    properties[:name]      # "number_of_dwarves"
    properties[:value]     # 7
    properties[:value] = 6 # a dwarf died
    properties[:value]     # returns 6

!SLIDE code

# Hash.each #

    @@@ ruby

    hash = { :a => 1, :b => 2 }

    hash.each do |k, val|
      puts("#{k} => #{val}")
    end

    # or

    hash.each{ |k, val| puts("#{k} => #{val}") }

!SLIDE bullets

# gems #

* Gems are Ruby's "Libraries"
* Manageable through the `gem` command

!SLIDE commandline

    $ gem install gem_name











