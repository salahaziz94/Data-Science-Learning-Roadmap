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

_pytest_, a third-party library, automates code as long as you run the tests. It helps so you don't have to manually write code to test. You don't have to put a bunch of conditionals and try/except blocks, just assertions. 

You use pytest in the command-line:

```
pytest example.py 
```

It is beneficial to not have a bunch of asserts in one function, as, like 'if' statements, the others may not even run. You should break down tests via the type of problem or situation so you can get more clues or handle as to what is going wrong. 

It doesn't seem that you need to call the defined functions when running pytest. 

We can actually use a built-in exception handler. For example, if we may expect or want to test for a TypeError when using the square function, if the user uses a string of, say cat, (the function itself isn't broken necessarily) we can do:

```
with pytest.raises(TypeError)
	square("cat")
	
```

Be careful when testing things, say strings, that use a print function only, as that doesn't actually mean the value is returned for us to test it! This is because asserts and tests are really meant to test the core arguments and return values, not side effects of them. 

Running _ _ init_ _ .py tells python to treat the folder its in as a package. You can then run, with "test" being the name of the folder/package:

```
pytest test 
```

By convention, pytest needs files that contains test to at least begin with "test_". 

When testing float conversions, its difficult since floats can be almost any infinite range of values. We can use _pytest.approx_ to make it approximately equal to that value, and it will pass the test. The second argument in the function is to fiddle with the _tolerance_ value, e.g., abs = 0.1 allows that value difference.

```
pytest.approx(149597870.691, abs = 1e-2)
```
