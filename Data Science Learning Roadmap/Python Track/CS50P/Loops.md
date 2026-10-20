
For loops always have the syntax of *for var in iterable*, where the var is a variable and iterable is the iterable object. You should always use for loops to basically go over a list, string, or something that you can know where the loop will end.

A while loop, in contrast, works best when you don't know when it should end. This includes user input, some kind of condition that needs to be fulfilled, etc. In such a way, you induce an infinite loop of *While True*, and it will only stop when the condition becomes false, or you intentionally make it end with *break*. 

Looping typically works best (or so I understand) on actual strings. i * as an integer doesn't work on integers or floating point values. 