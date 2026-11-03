In the last week of CS50P, we are covering some extra things.

# Sets

A _set_ is something that holds data, but it doesn't allow for replicated forms of values. It is useful if you want to automatically filter out duplicates. To run it, we call the function set(), and we can append (in this case, add) using the method .add into the variable that we contained the set function on.

```
#we run the set function, assigning it to the houses variable
houses = set()

#we make a loop, where we iterate in the keys for a particular
#dictionary called students, and we add the unique house values
#to the houses variable. 
for student in students:
	houses.add(student["house"])
```

# Global Variable

If we declare a variable outside of some functions, it may be accessed but it may not be edited properly across my functions. In order to so, I must declare it as a global variable within the functions I want to use it in.

```
balance = 0

def main():
	print("Balance", balance)
	Deposit(50)
	Withdraw(20)
	print("Balance", balance)

def deposit(n):
	#make the variable global, or accessible here
	global balance
	balance += n
	
def withdraw(n):
	global balance
	balance -= n

if __name__ == "__main__":
	main()

```

The idea is to use global variables sparingly, as they can create issues. Using OOP is preferred if necessary. 

# Constants

Values that we do not want edited/changed at any time are constants. They should be at the top of the scripts so it is clear that they are not meant to be changed. Since Python is basically utilizing an honor system, it isn't really possible to make constants that can't be modified. They are though, meant to be all uppercase and again, at the top of the code in question. Another option is to just shove it into a Class, and reference the attribute its stored in.

# Type Hints

Python type hints are a formal syntax introduced in Python 3.5 that allows you to explicitly declare the expected data types of variables, function arguments, and return values. We can use the package _mypy_ to use them.

Install via, _pip install mypy_

To use a type hint, we use a colon, then the type that the data type should be. 

E.g.: def meow(n: int)

Doing so would not really do anything, since Python itself would not enforce this. But running mypy on your python file with this type hint will return a declarative tool in the terminal telling the user (me) what is wrong. You can actually connect type hints and running mypy will be explicit that the data types need to match a certain way.

If you expect a return value of a function to be a certain type (e.g., None), you should use _->_ None: when defining the function, and running mypy will tell you what is wrong. 

# Docstrings

Within a function, if you use triple quotes """, you can actually extract the notes of your code. When doing so, it is a convention to be explicit as to what the intended types/uses are for certain data values like parameters, types, etc.

To do so, you wrap them in colons. Parameters are 'param', and type is 'type'.

For instance, if our function:

```
#this function has a parameter n with a type hint of being an int
#and the final output should eventually be a str.
def meow(n: int) -> str
	"""
	Meow n times.
	
	:param n: number of times to meow
	:type n: int
	:raise TypeError: If n is not an int
	:return: A string of n meows, one per line
	:rtype: str
	"""
```

The docstring formatting is not Python per se, its known as restructured text. 

# argparse 

When using sys.argv, we know that we can provide inputs immediatlely from the terminal or command-line. 

When using sys.argv, we can actually use _-n_ to specify, for instance what the amount of times things can be printed. Obviously -n takes up a space in an element list so -n in something like "python myprogram.py -n 3" would be sys.argv[1]. 

If we wanted in the command line to specify a word, which typically uses two dashes, it would be --word or something. But note that sys.argv can be confusing if we have a bunch of elements that need to be in particular places.

The package _argprase_ , short for an argument parser, helps us analyze the command-line inputs for us. 

argparse comes with a bunch of functions or methods that allow us to store values as arguments and parse them. 

.ArgumentParser passes in the function to something we can store, into something like Parser.

.add_argument() actually adds the arguments, as if we were doing sys.argv, but we type it in explicity there. We can provide the argument, say "-n". We can attach to it a default value, a help message in case someone wants to run -h or --help (which is standard on a function for help) and the type it should be.

.parse_args() parses the arguments, so that this is our final step and we can store .parse_args() into a variable which we then use for a method. 

```
parser = argparse.ArgumentParser(description="Meow like a cat")

parser.add_argument("-n", default-1, help="number of times to meow", type=int)

args = parser.parse_args()

for _ in range(args.n):
	print("meow")

```

args.n contains the number that the user types after -n in the command line. 

# unpacking

When indexing into something like lists, (e.g.):
```
def main(first, second, third):
	return first, second, third


list = [dogs, cats, horses, fish]

#I want to print horses.

print(list[2])

```
this can get vulnerable or messy/complicated over time. Rather than doing this, we can _unpack_. 

Using an asterisk at the beginning of your variable will unpack it. 

```
def main(first, second, third):
	return first, second, third

list = [dogs, cats, horses, fish]

#I want to print horses.

print(main(*list))

```

If the values are stored in a dictionary, you can't just pass the dictionary as an argument into main, or you would get a TypeError. 

To unpack dictionaries, you use _two_ asterisks. It passes in all the keys and their respective values. 

##  ***_*args and _**kwargs

```
*args
```

indicates that there is a variable number of positional arguments. 

applied, this looks like:

```
def f(*args)
```

For keyword arguments, we use:

```
**kwargs
```

This collects named keyword arguments into a dictionary.

A good example used is the built-in _print_() function that we used commonly in Python. It is actually built of:

```
print(*objects, ...)
```
So we have been able to print whatever amount of contents we wanted.

# map

`map()` applies a function to every item in an iterable and gives you back the results, without you writing a loop.

nums = [1, 2, 3, 4]

def square(x):
    return x ** 2

result = list(map(square, nums))
print(result)  # [1, 4, 9, 16]

# list comprehensions

The ability to construct lists on the fly. A list comprehension builds a new list from an iterable in a single expression, replacing the usual “create empty list, loop, append” pattern.

[expression for item in iterable]

nums = [1, 2, 3, 4]
squares = [x ** 2 for x in nums]
print(squares)  # [1, 4, 9, 16]

# filter 

Similar in spirit to the map() function, you pass in a function that is going to be applied to each of the elements in a sequence. However, map returns *one* value for each element in the sequence, but filter() is a bit more dynamic, getting a boolean and leaving out what is a False value.

# dictionary comprehensions

The ability to create a dictionary on the fly. To do this, we structure a list comprehension, with a defined dictionary in it, then we do the list comprehension syntax afterwards:


```
students = ["Harry", "Hermione", "Ron"]

gryffindors = {student: "Gryffindor"} for student in students}

print(gryffindors)

```

# enumerate

Allows you to iterate and get BOTH the value and an index at one time. 

```
students = ["Harry", "Hermione", "Ron"]

for i, student in enumerate(students):
	print(i + 1, student`)
```

# generators

Sometimes, processing lots of data can cause memory issues. Using generators, you can parse returned data that is too large into chunks. So far, we have been getting our data back from functions with with the *return* keyword. But by using the keyword *yield*, we basically get one iteration at a time. Essentially, it returns an iterator rather than doing the whole loop in process.

# Recursion

Recursion refers to the solution of a problem in itself in terms of a slightly smaller problem but it is the solution. 

```
def factorial(n):
	return n * factorial(n - 1)

result = factorial(3)
```

Here, the example given is using factorials, which is basically how many ways a number can be ordered from its parts.

3! = 3 * 2 * 1, which can also be written as n! = n * (n -1). 

When running a recursive function, we should use a _base case_, a scenario in which we know the answer off the bat. 

If n == 1, you can just return 1, no need to go deeper into the function.