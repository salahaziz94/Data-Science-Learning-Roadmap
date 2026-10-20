# Opening, writing, and reading files
The _open_ function allows us to open a file and return a corresponding object.

We would use it, to write information:

```
open("name.txt", "w")
```

Doing this allows us to OPEN the file, and it just gives us the means to write something in it. 

If we wish to do so, we can assign it to a variable, like _file_, and use some other functions associated with open:

```
file.write() #where, in write() we can put in some value or a variable.
file.close() #we close this
```

Note: using "w" can be dangerous since it essentially just recreates contents in a file. 
We can use "a" to append, so new contents are added each time we subsequently run the program. Be sure to add \n if wanting to append new content.

We do not need to use .close() if we start using _with_, which automatically opens and closes, but we add _as_ {file}:

```
with open("names.txt", "a") as file:
	file.write(f"{name}\n")
# as file is the new variable assigned.
```

Rather than using "w", to write, or "a", to append, we can use "r", to read the content in the files only. If we do that, then using the method file.readlines() reads all the lines in a file and we can store that in a list variable.

```
with open("names.txt", "r") as file:
	lines = file.readlines()
	#we could iterate in lines as a for loop if we wish.
```

There is a much better, cleaner way to do this. Rather than making a readlines method, which gathers all the lines, then we make an eventual for loop that goes in lines, we can just do:

```
with open("names.txt, "r") as file:
	for line in file:
		print("hello", line.rstrip())
```

What this does is it goes through every line live in names.txt.  Note that "r" is actually default if you don't assign a second argument in open function. 
# Comma Separated Values (CSV)
If we have a bunch of information, we can store it, perhaps not in a .txt file, but a comma separated value file, otherwise known as CSV file. Commas can represent a column where we can have multi-dimensional data, where they are stored in students.csv:
```
code students.csv
```
	(e.g., Harry,Gryffindor
	Herminone,Gryffindor
	Ron,Gryffindor
	Draco,Slytherin)
If we wanted to iterate on these lines and get particular data within each line, we can use the .split(",") method, which would effectively split up the values before and after each "," in each line. **It is good to know that each line of data in a CSV is also referred to as a row.**

Another thing to note is that when we parse data in a CSV file by splitting data, we can actually assign two variables at once, which can allow us to call those particular kinds of data from the CSV file, e.g.:
```
name, house = line.rstrip().split(",")
```

We can also make a dictionary following this to store the values of name and house if we wished, using curly braces:
```
#we first make an empty dictionary.
students{}
#then, we associate the indexed values in the dictionary of name and houses to the previously established variables using student (NOT PLURAL!).
student["name"] = name
student["house"] = house

#then we store all of the independent student values using the .append method:
students.append(student)
```

A much faster way of doing this, rather than three lines:

```
#defining a new dictionary and specifying its values in one line
student = {"name": name, "house": house}
#since each student is its own dictionary here, we can put them in a list:

students = []
students.append(student)
```

What is interesting is that we can pass functions into other functions by way of arguments.

So, for example, if we have a function that grabs the name of the student in the dictionary of students:
```

def get_name(student):
	return student["name"]
```

We can put the function _get_name_ as an argument into another function:
_example_function(key = get_name)

Where, the key is the defined names now. It is good to know that a key is used to look up a value, if we wanted names, then we would have to define the key as names, if we wanted to look up the value of houses, we would need to define the key as houses, etc. Putting the argument function automatically calls the defined function that established its value. Put in other words, calling example_function automatically calls get_name if it is in the argument of it.

BUT we don't even need to define a function explicity, we can do whats called a _lambda_ function, which is a kind of anonymous function:

_key = lambda_ _*rest of function here*_

If the data in a csv is complicated, we can use the CSV module within python to handle edge cases without reinventing the wheel so to speak.

The function _reader()_ from CSV helps us to do this. A reader returns list. We could be more flexible if we are gathering dictionary values by just using _DictReader()_ instead, but this requires editing the CSV file itself on line 1 and specifying the column values first. This allows us to bypass using indexing particular locations, in case values are in different places or switched later. 

The function _writer_ from CSV allows us to input new data into the CSV. Like DictReader, we can likewise use _DictWriter()_ which allows us to input new dictionaries instead of lists. CSV writer we have to pass them in a particular order, but the DictWriter just needs a argument called _FieldSpaces_[] that tells DictWriter() which column each value is. 

# Pillow

We can use a library called _PIL_, or _pillow_ which allows us to perform file I/O on images.  

