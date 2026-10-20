

# Lists, Dicts, and Tuples

Apparently OOP is good for problems as our code necessitates larger/more complicated.

We can return two variables at once in one function (I've done this before), called a *tuple*. Just make sure if you call it to be associated, it needs to be stored also as a tuple. (Unlike lists, tuples are immutable.) A tuple is one value, in a tuple is two (ore more?) values. You can return the tuple using parentheses () to make it more clear its a tuple. Tuples can be indexed. 

If you want something to be mutable with multiple values, it is better to use a list, explicitly called using []. 

A dictionary is most appropriate when we want better semantics, as we won't have to make new associates for keywords when we have one. Remember that we use a dictionary with {}. We identify a 'key' in a dictionary using an index with a string, e.g., if our dict is student = {}, we make a key with student["name"]. 

# Classes, Objects, and Attributes

So far, we have used general-purpose kinds of tools to make the data we want so it fits correctly.. .so rather than use lists, tuples, and dictionaries, we can make our own type of data type to fit a blueprint that we can invent and name called _classes_. 

Classes are created in OOP, made to represent entities that are either real or fictional, within code. 

To make a class, we use Classes *class* then we can make *attributes* to associate the class object. 

```
class Dog:


	#we can assign the class to variable, say my_dog, creating an Object/Instance:
	
	my_dog = Dog
	
	#we can make the object with attributes:
	my_dog.furry_level = input("Furry level: ")
	my_dog.bark_level = input("Bark level: ")
	
	print(f"My dog's furry and bark level is {my_dog.furry_level} and {my_dog.bark_level})
	```

So when we assign the my_dog to the class of Dog, what we are doing is creating an _object_. The class is the blueprint and objects are using the blueprint to create a specific house, so to speak.

The attributes I made, where a user dictates into my_dog, is an attribute, which is also known as an instance variable. In our example, we made it string, but the attributes or instance variables can be of any data type.

Classes and Methods -> Objects (Instance) --> Attributes (Instance Variables)

Another way you can make objects is to call the class, which is really calling a function since the class comes with a function of its own name once you define it:

```

```
#create a class, named Dog
class Dog:

#make variables defining furry and bark levels prompting user input.
furry_level = input("Furry level: ")
bark_level = input("Bark level : ")

#here, we do something MORE powerful, inserting those variables immmediatly as an object with attributes while calling the class function. 

my_dog = Dog(furry_level, bark_level)
```

Be sure to RETURN the object back! If it is contained in a seperate function then intended to be put in main(), such as create_dog():, then you need to return the created object so its used somewhere else. E.g.,:
```
def main():
	dog = create_dog():
	print(f"My dog has furry {dog.furry_level} and bark {dog.bark_level})
	
	
def create_dog():
	furry_level = input("Furry level: ")
	bark_level = input("Bark level : ")
	
	return Dog(furry_level, bark_level)
```

So above, even though the class Dog is returned as an object with attributes, it does NOT mean we have to specify the class itself again, we just associate the general function its in main where we did dog = create_dog():.

# Methods
Methods are basically built-in functions in a class.
## The init method

If we want to initialize the contents of an object in a class, we can do so using dunder (double underscores) _ _ _init_ _ _  method, whose purpose is just to initialize the object that is otherwise empty:

```
#We are adding instance variables 
def __init__(self, attributes):
	self.furry_level = furry_level
	self.bark_level = bark_level
	#attempting a raise
	if not name:
		raise ValueError("Missing a name!")
```

The dunder init is actually already called when we normally call the function of our class, Dog(), but we are modifying it specifically here.

The self parameter can be whatever we want, but this gives us access to the current object we created.

When we initialize the class in the beginning with dunder init, we can make raises too, in case the parameters involved (or attributes) aren't right. Then, when you go to create the object in the specified function later, you can make a try/except block that associates that object with the raise created.

## The str method

If we want our class to be able to handle its objects as strings, we need to define the dunder str method: _ _ str _ _ . Otherwise, for instance, if I wanted to use a print function on an object that is just a string but I didn't specify such in the class creation, I would just print the object, i.e., <main__.dog object .....>. 

```
def __str__(self):
	return f"My dog has {self.furrylevel} and {self.barklevel}"
```


## Custom methods 

We can make our own functions in our class, using def. It needs to have one parameter that is called self. 

# Properties

A property is like an attribute, but it allows us to have a little more control over it. To call it, we can use @property, and we can use _decorators_ that allows us to have more control over other functions. 

It is possible to pass the return value from one defined method that we have into another one and make it clear that we don't want certain things.

For instance, lets say that in my method of defining the attribute of a dog's furry level:

```
#when setting up class Dog:

#This is our GETTER. It helps us retrieve the value that we eventually get.
@property
def dogfurriness(self):
	return self.dogfurriness

#the above function is all well and fine. But we want to protect this attribute
#from being modified in a main function, for whatever reason:

#This is our SETTER. It helps us establish that the value must be a certain way.
#we make the decorator:
@dogfurriness.setter
def dogfurriness(self, dogfurriness):
	if dogfurriness not in ["1", "2", "3"]:
		raise ValueError("The furry level needs to be a number 1 - 3.")
	self.dogfurriness = dogfurriness
	
#All features of the class with the attribute of dogfurriness should call the 
#setter now, any time you access self.dogfurriness. 
```

If the instance variable ever collides with a function name, you can use the convention of using an underscore in the beginning of its name, e.g., def dogfurriness vs self. _ dogfurriness. The init method doesn't have an underscore, though, it needs to be distinct. 

So one other thing to note is that this works mostly on the convention of the honor system, so that instance variables (e.g., starting with an underscore, shouldn't be touched.).

# Previous Classes We Worked on Before

We have worked on OOP before, using classes such as int, str, list, dict. We've used methods, too, in such that whatever follows a period is a method in that class, like list.append(x). These built-in classes are lowercase, but the convention is that if we decide to create our own classes, we should uppercase the first letter in its name (e.g., Dog).

# Class Methods
## Class Methods in General
It's not always typical to associate variables/methods with objects of a class, but we can do so with the class itself.  

@classmethod is a decorator, so we would need to implement this to make the class method. 

We can make _class variables_ that aren't bound to other objects, but the class itself, and these do not require the self term. 

e.g., 
```
class Dog

	Furriness = [0, 1, 2, 3]
	#We can use this class function in ANY function in the class now.
	#If we want a class method, we use @classmethod.
	@classmethod
	#we use 'cls' as the parameter instead of 'self'.
	def sort(cls, name):
		print(name, "is of furry level" random.choice(cls.furriness))
		
	#Before we used dog = Dog, but we don't need to do that here, we just can
	#use Dog as a function.
	
```

When defining a function in a class (not an instance), we can simply return the value in the function back to the class using cls, like we did before instead of self. 

```
def get(cls):
	name = input("Name of dog: ")
	bark = input("How much does your dog bark a day? ")
	return cls(name, bark)
```

Now, instead of the function being inside an object, it is in the class of Dog. To call it, we just the method of the period ".". In this case, it would be Dog.get()

## Static Methods

Won't focus on here, but it exists with @staticmethod.

# Inheritance

You can actually borrow/retrieve attributes from class to class if they have it in common. To do so, when we first define a class that is a subgroup of another, e..g, a dog is a group of Canines, which is a group of Mammals, etc., we put the group in the parameter when defining the class:

And we also need to use _super()_._ _init_ _ _(method)  in the init method of the class that uses the methods from the superclass (i.e., the Canine).

Here we are having inheritance of the name method from Canine into Dog:

```
class Canine(Mammal):
	def __init__(self, name)
		...
	
class Dog(Canine):
	def __init__(self, bark, fur)
		self.bark = bark
		self.fur = fur
		super().__init__(name)
	
```

The hierarchy of classes is demonstrated in exceptions:

![[Pasted image 20261015153306.png]]

So ImportError is the superclass of ModuleNotFoundError and the superclass of ImportError is Exception Class, etc. 

# Operator Overloading

We can take common symbols/syntax and implement our own interpretation. + doesn't have to mean addition, - doesn't have to mean minus. 

We need to teach python what to do when using custom classes with operands. To do this, we define something, like overloading addition between classes using an add method:
```
Class Vault(dimes, nickels)
def __add__(self, other)
	firstitem = self.firstitem
	seconditem = self.other
	return Vault(firstitem, seconditem)
```

