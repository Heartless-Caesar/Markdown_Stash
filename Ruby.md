# Ruby Programming Language


## Data types

- String,
- Numbers(Integers & Floats),
- Booleans,
- Nil(Acts as NULL in Ruby).


## Printing to the console

- "print": Will print to the console without breaking to the next line,

- "puts": Will print to the console and break to the next line. 

**OBS:** When printing strings with variables you have to put the statement in parenthesis.

```Ruby
my_name_var = "Cesar"
print ("My name is " + my_name_var)
``` 
### Getting user input

In Ruby you utilize the keyword ```gets``` to get input from the user.
The input is automatically set to string, to alter that behavior on the line you're printing change the type with the use of other methods.

**Working with strings**

```Ruby
print "Enter your name:"
name_var = gets.chomp()
print ("Your name is " + name_var)

print "Enter your age:"
age_var = gets.chomp()

print ("Your name is " + age_var)
```

**Working with numbers**
```Ruby
print "Enter a number:"
num1_var = gets.chomp().to_i

print "Enter another number:"
num2_var = gets.chomp().to_i

print ("The sum is " +  num1_var + num2_var)
```

The ```chomp()``` method is utilized to cut the line break that happens when the user types enter.

The ```to_i``` method converts the string to an integer. 

The ```to_f``` method converts the string to a float. 

### Arrays

In Ruby Arrays can store multiple data type variables simultaneously.

Example:
```Ruby
my_arr = ["String",0,1.0,true,nil]

puts my_arr

# Output

String
0
1.0
true
nil

```
You can utilize methods to perform certain tasks, such as verifying if an Array contains a specific element.

Example:
```Ruby
my_arr = ["String",0,1.0,true,nil]

# Check if element exists in the array
puts my_arr.include? "String"

# Output

true

## Inverting array order
puts my_arr.reverse()

# Output

nil
true
1.0
0
String

## Sorting
puts my_arr.sort()

# Output

ERROR
```
To sort elements the values should either be strings or numbers.

### Hashes
These data structures function like Javascript objects, with keys and values.

```Ruby
my_hash_DS = {
    "key_1" => 1,
    "key_2" => 2,
    "key_3" => 3,
    :key_4 => "Key four"
    
    puts my_hash_DS["key_1"]
    puts my_hash_DS[:key_4]
    
    # Output
    1
    Key four
}
```
Each key in Ruby Hashes necessarily have to be unique.
The double quotes and colon before the key are both valid syntaxes.

## Methods

Ruby at it's advanced level utilizes OOP to get results.
As such **methods** are present.

```Ruby
def sayHi
  print "Hello user"  
end

# Calling the method, no need for parenthesis when no arguments are required
puts "One"
sayHi
puts "Two"

# Output
One
Hello user
Two

# Utilizing parameters, the "=" determines the the following data is set to default if not provided when the method is called
def sayHi(name, age=18)

  # Convert integer to string so no errors occur 
  print ("Hello " + name + " you are " + age.to_s)  
  
end

sayHi(Caesar,21)

# Output
Hello Caesar you are 21
```

### Return types

The **return** keyword is necessary in methods so that a specific output is given in a method. If a **return** keyword is not utilized only the last line in the method will be returned.

```Ruby
def cubeNum_1(num)
   num * num * num
   5
end

def cubeNum_2(num)
   return num * num * num
   5
end

cubeNum_1(2)
cubeNum_2(2)

# Cube_1 output => Wrong
5

#Cube_2 output => Correct
8
```

In Ruby you can also return multiple data from a **return** statement as it will be returned as an array.

```Ruby
def cube(num)
 return num * num * num, 70
end

puts cube(2)

# Output
8
70
```

### If statements

Functions like in other programming languages but with some minor differences in the syntax.

```Ruby
ismale = true
istall = false

if ismale or istall
 puts "You are a guy"
elsif ismale and istall
 puts "You are a guy and tall"
elsif ismale and !istall
 puts "You are a guy but you are not tall"
else
 puts "You are not a guy and you are not tall"
end 
```

## Calculator with all operators

```Ruby
puts "Enter a number:"
num1 = gets.chomp().to_f

puts "Select an operator: 1 -> + \n 2 -> - \n 3 -> * \n 4 -> \ \n"
op = gets.chomp().to_f

puts "Enter another number:"
num2 = gets.chomp().to_f

if(op == 1){
    return (num1 + num2)
}
 elsif(op == 2){
     return (num1 - num2)
 }
 elsif(op == 3){
     return (num1 * num2)
 }
 elsif(op == 4){
     return (num1 / num2)
 }
 else{
     puts "Inavlid operator"
 }
end
```

### Case expressions

This expression is the substitute for the switch-case statements in other programming languages, and instead of the **default** keyword an **else** is utilized.ç

The following example will output the day of the week based on the provided shorthand term.

```Ruby
def getDay(exp)
 dayName= ""
 
 case exp
  when "mon"
   dayName = "Monday"
  when "tue"
    dayName = "Tuesday"
  when "wed"
     dayName = "Wednesday"
  when "thu"
    dayName = "Thursday"
  when "fri"
    dayName = "Friday"
  else
    dayName = "Invalid term"
  return dayName    
end

puts "Enter a shorthand term"

input = gets.chomp()

puts getDay(input)
```

## While loops

This functionality works the same way as in other programming languages.
Below is a basic example in Ruby syntax.
```Ruby
index = 1

while index <= 5
  puts index
  index += 1
end

# Output
1
2
3
4
5
```

### Begin and Rescue statement

In Ruby you utilize ```begin...rescue``` statements instead of  ```try...catch``` blocks to output error handling. 

```Ruby
  my_num = 0
  
begin
   result = my_num/0
rescue
    puts "Division by zero attempted"
end    

# Output

Division by zero attempted
```
However you need to input a rescue output for every error type,as shown below.

```Ruby
  my_num = 0
  my_arr = ["Teddy","Dinosaur","Dragon"]
begin
   result = my_num/0
   my_arr["Salamander"]
rescue DivisionByZeroAttempt
    puts "Division by zero attempted"
rescue TypeError
   puts "No such index/element in the given array"
end    

# Output

Division by zero attempted

No such index/element in the given array
```

## Classes in Ruby

### Class properties and initialize method
In Ruby classes have a syntax that differs mostly from languages like Java or Javascript. There will be code shown below exemplifying this syntax.

```Ruby
# Class
class Book
    #Attribute accessor functions as the skeleton attributes
    attr_accessor :title, :author, :pages
    
    #Initialize method sets the attribute to the input parameters of the object
    def initialize(title, author, pages)
      @title = title
      @author = author
      @pages = pages
    end
end    

# Book Object
book1 = Book.new("Crime and Punishment","Fyodor Dostoevsky", 492)
book2 = Book.new("Harry Potter", "JK Rowling", 400)
```

### Object methods

These methods are defined in the class element and are utilized when working with objects much like Angular.


```Ruby
class Student

    attr_accessor :name, :major, :gpa
    
    def initialize(name, major, gpa)
      @name = name
      @major = major
      @gpa = gpa
    end
    
    def has_honors
       if @gpa >= 3.5
        return true 
       end
        return false
    end 
end    

student1 = Student.new("Caesar","Software Engineering", 4.0)

# Calling method
student1.has_honors

# Output

true
```

### Class Inheritance

The inheritance property of class elements is also applied in Ruby, overrides are also present, example below.

```Ruby
class Chef
   attr_accessors :name
   
   def initialize(name)
    @name = name
   end
   
   def make_chicken
     puts ("Chef " + @name + " made chicken")
   end
   
   def make_special_dish
     puts ("Chef " + @name + " made special dish")
   end
end

# Class that inherits attributes and methods
# The "less than" symbol serves as the "extends" keyword
class ItalianChef < Chef
   def make_special_dish
     puts ("Chef " + @name + " made lasagna")
   end
 
   def make_salad
     puts ("Italian Chef " + @name + " made salad")
   end
end

```

### Modules in Ruby

Modules are blocks of code that store methods.

```Ruby
# Defining the module and it's methods
module Tools
   def sayHi(name)
    puts "Hello #{name}"
   end
   
   def sayBye(name)
    puts "Bye #{name}"
   end
end

# Importing modules from other files

# Relative as in the same relative directory
require_relative "file_in_same_directory.rb"
include Tools

# Using the module's methods
Tools.sayHi("Caesar") 


```






