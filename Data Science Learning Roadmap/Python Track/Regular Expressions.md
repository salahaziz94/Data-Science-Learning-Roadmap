Regular expressions, or RegEx, is a pattern in code to more easily manipulate data. 

Rather than endlessly using a bunch of conditional statements to get more precise onto a kind of data, we can use regular expressions.

# Re.search basics

The library _re_ allows us to define patterns, like an e-mail address. 

The function _.search_ allows us to get at finding particular kinds of data, where re.search(pattern, string, flags = 0)

We may just use raw text for the pattern, but we can actually implement various patterns that are helpful:
	. any character except a newline
	* 0 or more repetitions
	+ 1 or more repetitions (one or more things to the left)
	? 0 or 1 repetition, effectively means something is optional. Put something to the left of this to essentially make it so.
	{m} m repetitions
	{m,n} m-n repetitions
	^ text must be at the beginning of the search
	$ text must be at the end of the search
	[] set of characters (can do a-zA-Z for letters, 0-9 for numbers and an _ at the end for underscores)
	[^] complementing the set (NOT to be included)
		more characters....
		\d decimal digit
		\D not a decimal digit
		\s whitespace characters
		\S not a whitespace character
		\w alphanumeric and underscores
		\W not alphanumeric and underscores
For example, if we wanted an email address, the pattern could be ".@", where the "." means _anything_ before an @ symbol, which represents a username. We do want to add a * so that it is more than just one possible character, and also to the right of the @ for the domain:
	pattern: _".*@.*"_  
Using a + is necessary if we want at least one repetition, so nothing is accepted if we used a *.
	".+@.+"
	(.+ is equal to ..*  * if we wanted) 
	__

Using a backslash allows us to be more literal in case there is an overlap of text in these patterns:
	".+@.+BACKSLASH.edu" , so that the ".edu" isn't confused with the . that means any character in re.search.
To do this, we need to use an _r string_, or raw string almost like an f string, which tells Python to literally treat backslashes differently:
	(r".+@.+BACKSLASH.edu")
The . character can possibly be too open for us. If so, we can use the [] to specify what characters we want, or the [^] which is everything EXCEPT a particular sign, e.g., [^@], when we want a pattern of a email address and don't want the beginning to include a @ symbol since we already have one in the search pattern.

We can literally use a BACKSLASH w to indicate "word character", in such that we are basically doing the [a-zA-Z0-9_] but in shorter form.

We can use inclusive or conditions using the | symbol, which stands for "or". So if we wanted to use more than just .edu, for instance, we can use .com, .net using parantheses and the or symbols, e.g., (edu|com|net)

Certain flags can be helpful, such as re.IGNORECASE which allows us to be case insensitive. 

Remember that we can group items logically using parenthesis, and even then apply a ? operator to the right of the grouping to make that group optional.

If a search pattern is too cryptic, we can always resort to using libraries for an official/nonofficial version for something we need.

# Other functions 
Re. match:

Similar to re.search, but matches content and you don't need to specify a ^ for the start of a string.

Re.fullmatch does the same, but matches also at the end of the string for $ so you don't need to specify the end either.

# Grouping and Returning Values in Re.search
Back on re .search:

By grouping elements together in the pattern argument, we essentially tell the program to return to us those values. For instance, if I wrote a pattern to capture last name, first name:

```
re.search(^.+,.+$) #before grouping
re.search(^(.+),(.+)$) 
#now I have grouped what I think should be returned as the last, first names.

#we can store these in a variable:

matches = re.search(^(.+),(.+)$)

#and then write a conditional on the new variable assigned to parse out the last and first names, giving it to the .groups() method:

if matches: #which WILL return true, clearly if it is non-none
	last, first = matches.groups() #this will correspond to our previous groups!
	name = f"{first}{last}"
print(f"hello, {name})
	
```

Another option, to be more explicit, is to assign matches.groups like this:

```
if matches:
	last = matches.groups(1)
	first = mastches.groups(2)
	name = f"{first}{last}}
print(f"hello, {name})

#I think the assumption is that if the user typed a commma, the order is last, first
```

OR:

```
if matches:
	name = matches.group(2) + " " + matches.group(1)
print(f"hello, {name})
```
Note that here something else is in 0, so this function starts with 1, unlike other python counting conventions.

If you want to assign something on the same line ...while IF and ONLY IF making a conditional you can do:

```
if matches := re.search(^(.+),(.+)$): 
#so we shoved the conditional into the top, but we needed the ":=" in order to #do that.
	name = matches.group(2) + " " + matches.group(1)
```
This is the WALRUS operator, and is new in recent years.

If we want to subsitute information using regular expression, we can use:

# Re.sub

_re.sub_ is useful for cleaning up data, where we have:

re.sub(pattern, repl, string, count=0, flags=0)

For example, if we wanted to replace the twitter handle https://www.twitter.com/davidjmalan where we just wanted the username 'davidjmalan', we use regular expression using r.sub:

```
#we get the user input for the URL
url = input("URL: ").strip()

#then we assign the sub function of regex into username
username = r.sub(r"^(https?://)?(www\.)?twitter\.com/", "", url)
#prints it
print(f"Username: {username}")
```



# Optional capturing

If I were to use regex, and I wanted to get back the group return of a username using r.search:
```
matches = r.search(r"^(https?://)?(www\.)?twitter\.com/",(.+) "", url)

```

Essentially, the username variable is getting returned various groups: the 1st group is the 'http?://', the 2nd group is the (www\.) and the 3rd group is what we intend to return, which is the (.+). 

Now, we can totally specify group(3) if we wanted to, using matches.group(3), or I can use the non-capturing version of paranthesis with a question-mark colon first inside it: (?:)
```
matches = r.search(r"^(?:https?://)?(?:www\.)?twitter\.com/",(.+) "", url)
```

Note that you can specify a group beyond just calling it by its index (1), or (2), etc.

if you do: (?P<_str_>) where str is where you put a value, you can call it by that instead.

