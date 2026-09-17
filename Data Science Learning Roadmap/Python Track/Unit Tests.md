Here we are focusing on content in which we want to test our code, but doing so using our own code to do so.

We can switch to another py file we make to make a test, import the function we want to test, and see how it works. 

Note that using the condition:
```
if __name__ == "__main":
	main()
```
allows us to borrow functions we import from another py file without running everything from that py file. It essentially ignores main if the current script doesn't match the one where the main command is running from. 

We can use the _assert_ keyword to basically mandate what should be the case in our code, rather than using a bunch of conditional statements. E.g.:, if we imported and wanted to test the _square_ function from another file, we would write:
```
assert square(2) == 4
```

We can also nest assertions in try and except blocks via coding _AssertionError_ to be more informative to the user as to what went wrong:
```
try:
	assert square(2) == 4
except AssertionError:
	print(f"2 squared was not 4")
```
