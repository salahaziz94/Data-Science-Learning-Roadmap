# Basics of Libaries
If I want to use a module in python, I can use the import _keyword_ to do that. From there, _all_ the associated functions with the particular module will work. 

E.g., import random means that if i do random.choice(), the function will always need to associate with the random module.

But I can use from random import choice, which allows my codespace to just borrow that function and I can call choice() without using the random keyword. This has drawbacks if my code needs more functions, or if I want to associate those functions with the module for memory.

# Command Line Arguments
The function of sys.argv, from the sys module? is used for _command line arguments_, where the advantage here is we don't need a human to sit at the computer to input something. 

E.g., print("hello, my name is ", sys.argv[1]). 
We can _proactively_ tell the IDE to work on what I want before it is even in the editor. 

Here, the 'argv' returns a list of the commands in the terminal window, so if I were to, in the terminal, run python name.py Salah, it would print "hello, my name is Salah". The [0] is only used for the first thing, so that would have been 'name.py'.

If we don't use [1], when there isn't something in that index, we would get an _IndexError_. 

Using sys.argv potentially allows us to not even deal with exception handling, as we can use conditional statements with sys.argv to specify arguments in the command-line interface. 

We can also use _sys.exit_ to just exit out of the code execution, almost similar to an exception. 

# Slices
If I wanted to get a portion of something, say a list, this is considered a _slice_. For example, if wanted to iterate over the list in sys.argv to return everything BUT the first thing on the index, which is [0], or name.py, I would use [1:], where the : specifies 'to the end' of what we are using. 

# Packages
Third-party modules, based in folders, called _packages_ are available for us to use. Seems similar to packages in R. We can get them at [pypi.org](http://www.pypi.org) 

_pip_ is a package manager that allows us to install packages in python.

we use 'pip install X', where we can then import after installation.

# APIs
Third-party services that we use code to talk to. The requests package allows us to make web requests as if I was a browser itself, and get URLS, etc. 
A _JSON_, short for Javascript Object Notation, is Javascript text that basically is used as a language-agnostic way to exchange information across computers. Python can read or write it. 

Using the requests package, we can use _requests.get()_ to specify a URL to get information. 

We can use the JSON library to read/manipulate JSON data if it is requested from the internet. In the tutorial video, the json.dumps() function grabbed all the string data from the JSON on the requests URL, if we wanted it. 

One of the shorts I watched documents that we can pass an input function to a parameter that does a search query in an API, which shows that we can try to be creative as to how a user can interact with it.
# Making Our Own Libraries 
We can import our own functions via the same import _library_ that we made, and import the exact function we created somewhere else. 

However, if we import a function from another file, it will call _everything_, which we may not even want or need. 

"_ _name_ _ "  allows us to ignore the main() function that is in another file. 

To make our own _packages_, we create our own folder, with our own py files that can act as modules, and they should be stored in that respective folder. We would need to also make a _ _init_ _ _.py_ file in the same folder. So, we would do:  _from package.module_import function_, where doing so consolidates functions and modules under one umbrella.

# PEP 8 
The agreed-upon standards of Python. These do function as guidelines, rather than hard and fast rules. Readability is king.
	There needs to be indentation.
	Tabs or spaces? Spaces of four! Although hitting the 'tab' key should provide four spaces.
	Limit all lines to a maximum of 79 characters. For flowing long blocks of text with fewer structural restrictions (docstrings or comments), the line length should be limited to 72 characters.
	Adding blank lines adds for more readability.
_Pylint_ is a package that allows for helping with this, but it may be too overwhelming with criticisms.
_Pycodestyle_ is the defacto standard package for formatting.
_Black_ is an 'opinionated', uncompromising package for formatting.