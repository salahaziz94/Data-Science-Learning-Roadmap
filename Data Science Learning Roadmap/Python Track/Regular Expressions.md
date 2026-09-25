Regular expressions, or RegEx, is a pattern in code to more easily manipulate data. 

Rather than endlessly using a bunch of conditional statements to get more precise onto a kind of data, we can use regular expressions.

The library _re_ allows us to define patterns, like an e-mail address. 

# Re.search
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

# Re. match

Similar to re.search, but matches content and you don't need to specify a ^ for the start of a string.

Re.fullmatch does the same, but matches also at the end of the string for $ so you don't need to specify the end eitehr.




