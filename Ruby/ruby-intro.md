# Intro To Ruby
Comments in Ruby start with #
Use snake case in ruby to name variables
##### let's get some practice
```
mkdir 05-ruby
cd 05-ruby
touch intro.rb
atom .


#type code inside atom and the in order to run the code:
#come back to command line and type
ruby intro.rb

# it executes the code
```
##### Practice on Command Line
```
# Way 1 ------------------------------------------------
# Type:
ruby
# it goes in ruby mode and waits for you to type a code so that it can execute it

3.times {puts "hello world"}
puts "Goodbye"
end

# will print all the code

# to EXIT press ctlr d


# Way 2 ------------------------------------------------
# Type:

irb #interactive ruby #aka ruby repl
# shows the version
> #type code and will execute your code straight away


# Way 3 ------------------------------------------------
# Type: (assuming pry has already been installed, if not then type "gem install pry")

pry
# it acts like ruby console

> where am i
=> At the top level

> exit
# will exit or can type ctlr d
```
#### More Pry
```
# WORKING WITH BACKTIKS (saves it in a variable)
> username = `whoami`
> puts username
=> inceptor

# even if you quit, pry remmeber previous commands
# so you can view by arrow up key

# INTERPOLATION
> " 2 + 2 = #{2+2} "
=> 2 + 2 = 4
#YOU MUST USE DOUBLE QUOTES FOR INTERPOLATION

> "a double quoted string can include 'single quotes'"

> 'a single quoted string can include \'single quotes\''
# condition: slash

> `ls`
=> #lists all files folders
Data Types - Strings and Numbers
Strings
Again, delimited by quotes.
"string" 'string'
Numbers
There are multiple types:
FixNum
Float
BigNum
# Ruby can deal with big numbers
> (99 ** 99) ** 99
=> # huge number

> x = 4.5
> x.class
=> float

# always use object first and then the method as Ruby is object oriented

> x = 4
> x.class
=> integer

> x = 3
> x.to_s # converts into string
=> "3"

> x.to_i # converts into string
> x.to_f # converts into float

> greeting = "hello"
> greeting.downcase # makes all letters small cases
> greeting.upcase # makes all letters capital
> greetings.capitalize # makes the first letter capital only

> 20/5
=> 4

> 21/5
=> 4 # beacuse it ignores the remainder

#if u do
> 21.0/5
# it will give floating number

# this will do the same
> 21.to_f / 5
Operators
Arithmetic Operators
Lots of them, but the basic ones are:
+     # Addition
-     # Subtraction
*     # Multiplication
/     # Division
**    # Exponent (to the power of)
%     # Modulus
Assignment Operators
=     # Assignment
+=    # Add then assign
-=    # Subtract then assign
*=    # Multiply then assign
/=    # Divide then assign
%=    # Modulus then assign - assigns the remainder of the modules to the left
      #operand
Logical Operators
&&    # And
and   # And (alternative to &&)
||    # Or
or    # Or (alternative to ||)
!     # Not
not   # Not (alternative to !)
Comparison Operators
All the usual suspects, plus a few new ones:
>       # Greater than
>=      # Greater than or equal to
<       # Less than
<=      # Less than or equal to
==      # Equality (generally just use the double equals in Ruby)
!=      # Inequality
<=>     # Combined comparison - returns -1 if less than, 0 if equal, and 1 if greater
        #than
.eql?   # True if the receiver and argument have the same type and equal values
.equal? # True if the receiver and the argument have the same object ID
> 2 ** 10 # to the pwer
> 2 % 10 # modulus

# no x-- available in ruby but the following are
x += 1
x -= 1
x *= 3
Ruby - Operators - Recommended Readings
​Tutorials Point - Ruby Operators​
Ruby Fundamentals - Pt I
Basic naming conventions
snake_case_everywhere - it's very rare to see camelCase!
Variable interpolation in strings
String interpolation is where we put Ruby code to be evaluated inside a string - the code to be evaluated is inserted within #{}. This is most often used when interpolating variables, but we can put any expression within the curly brackets (eg #{5 + 4} will interpolate 9 into the string).
name  = "gilberto"
drink = "scotch"

"My name is #{ name } and I drink #{ drink }!"
# A lot nicer than "my name is " + name + " and I drink " + drink
# Which is the way you would do it in JS
IMPORTANT: Interpolation only works with double quotes!! Single quotes mean 'leave this string alone, this is mine'.
Comments in Ruby
# This is is a single line comment

# This is
# a multiline
# comment

# OR (don't do this)

=begin
This is also a multi line comment
You can't have any an empty line between the =begin and the start of the comment
=end
Getting user input
In JavaScript, we have alert and prompt, in Ruby we have puts and gets.
# Initial greeting
puts "What is your first name?"

# first_name = gets
# This will wait for user input, and include the new line in the variable

first_name = gets.chomp
# This will wait for user input, and strip the new line from the variable
# For more documentation on chomp - http://ruby-doc.org/core-2.2.0/String.html#method-i-chomp

puts "Your first name is #{ first_name }."

p "What is your surname? " # using `p` will allow you to put the input on the same line.
surname = gets.chomp # Chaining and letting it stay in the same line
puts "Your surname is #{ surname }."

puts "Your full name is #{ first_name } #{ surname }"
# fullname = "#{ first_name } #{ surname }"
# Sames as ... puts "Your full name is #{ fullname }"

puts "What is your address?"
address = gets.chomp #chomp lets you stay on the same line
puts "Your name is #{ fullname } and you live at #{ address }"

# INTERPOLATION ONLY WORKS IN DOUBLE QUOTES!
# print stays on the same line
# puts goes to the second line

age = gets.to_i
# no need of chomp here as the number doesnt get printed on second line
Conditionals
If statements
if 13 > 10
    p "Yep, it is a bigger number"
end

grade = "A"

if grade == 'A'
    puts "You are killing it"
elsif grade == 'B'
    puts "You are coasting fine"
elsif grade == 'C'
    puts "Acceptable"
else
    puts "Please see me after class"
end

p "Yep, it is a bigger number" if 13 > 10 # This only works in single line statements

# It's called a modifier (if modifier)
Unless statements
# unless is the opposite of if, it executes if the condition is false
x = 1
unless x > 2
    puts "x is less than 2"
else
    puts "x is greater than 2"
end

# Modifier or backwards form
code_to_perform unless conditional
case statements
Think of these as shorter if statements, but don't overuse them (particularly in JS)
grade = 'B'
case grade
when 'A'
    p 'You are killing it'
when 'B'
    p 'You are coasting fine'
when 'C'
    p 'Acceptable'
else
    p 'Please see me after class'
end

case expression_one
when expression_two, expression_three
    statement_one
when expression_four, expression_five
    statement_two
else
    statement_three
end

# Very similar to the switch statement in JavaScript!
The case statement will compare the case expression with whatever a particular when expression evaluates to. This is fine when testing direct equality between the case expression and the when expressions. Example:
score = 1
case score
when 1
  print "You got one"
when 2
  print "You got two"
end
# => "You got one"
The first when expression - 1 - evaluates to 1, and since 1 == 1 evaluates to true, the first when expression is satisfied, and "You got one" is printed
But this is a problem when our when expression contain is more complex. Consider the following:
score = 1
case score
when score <= 1
  print "You got one or less"
when score > 1
  print "You got two or more"
end
# => nil
The first when expression - score <= 1 - evaluates to true, and since 1 != true, so none of the when expressions will be satisfied.
For complex expressions, the case expression should be left blank.
score = 1
case
when score <= 1
  print "You got one or less"
when score > 1
  print "You got two or more"
end
# => "You got two or more"
Control Structures
While Loops
while conditonal
    statement
end

while true
    p "OMG"
end # BAD IDEA

i = 0
while i < 5
    puts "i: #{ i }"
    i += 1
end
Until Loops
until conditional
    statement
end

i = 0
until i == 5
    puts "i: #{ i }"
    i += 1
end
Iterators
So, so common in Ruby.
5.times do
    puts "OMG"
end
# => "OMG
# => "OMG
# => "OMG
# => "OMG
# => "OMG

5.times do |i|
    puts "i: #{ i }"
end
# => I: 0
# => I: 1
# => I: 2
# => I: 3
# => I: 4
# => I: 5

# Here, | | is called pipe character

5.downto(0) do |i|
    puts "i: #{ i }"
end
# => I: 5
# => I: 4
# => I: 3
# => I: 2
# => I: 1
# => I: 0
for loops
For loops are very rarely used in Ruby.
# Don't ever use them
for i in 0..5
   puts "i: #{ i }"
end
# => I: 0
# => I: 1
# => I: 2
# => I: 3
# => I: 4
# => I: 5
Generating random numbers
Random.rand # Generates a number between 0 and 1
Random.rand(10) # Generates a random number up to 10 (including zero and 10)
Random.rand(5..10) # Generates a number between 5 and 10 (also includes them)
Random.rand(5...10) # Does not include 5 and 10
Variables
Unlike JavaScript, we don't need to use the let or const (or any other) keyword when declaring a variable in Ruby.
putting a $ sign in the beginning of a variable makes it a global variable. For example, $word. Here, the variable named "word" has a global scope.
ruby = "is nice"
It's much harder to accidentally make global variables in Ruby.
$ruby = "is nice"
To make a const variable you must define the variable name ALL in caps.
RUBY = "is nice"
Ruby will allow you to change this constant variable but will notify you if you change it.
Methods (Functions in JS)
puts "this is like console.log
print "this is also like console.log
 p "this is a bit more complex
Parentheses in method calls are mostly optional in Ruby, but they are occasionally necessary (eg, in method or function chaining)
puts("this")
puts "is the same as this"
Methods in Ruby have an implicit return, meaning that you don't need to use the return keyword in your methods - Ruby returns the last statement in a method on its own.
Methods
Methods are declared using the def keyword and called using the method's name.
Methods with no arguments
# Method definition
def hello
    puts "Hello"
end

# Method call
hello
# => "Hello"
Methods with arguments
For methods with defined parameters, arguments can be passed in with or without parentheses.
def hello( name )
    puts "Hello, #{name}"
end

hello("Josh")
# => "Hello, Josh"

hello "Josh"
# => "Hello, Josh"
If a method is defined with one or more parameters but is called without passing in the right number of arguments, an error will be thrown (Argument Error: wrong number of arguments).
Methods with default arguments
To avoid Argument Errors thrown by calling an argument without the requisite number of arguments, we can set default parameters in the method definition.
def hello( name = "World" )
  puts "Hello, #{name}"
end

hello
# => "Hello, World"

hello("Josh")
# => "Hello, Josh"

3.times { hello("Josh") }
# => "Hello, Josh"
# => "Hello, Josh"
# => "Hello, Josh"

def add(a, b)
  return a + b
end

add 4, 11
# => 15

new_total = add 4, 11
new_total
# => 15
