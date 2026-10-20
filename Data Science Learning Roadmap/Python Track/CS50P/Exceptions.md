When handling cases where a user in a python script may encounter an error, you can actually set up conditions where if a user prompts such an error, or an exception, a particular script does *x*. In the CS50p tutorial, the keywords try, except, and *else* were used to implement a scenario in which a user was prompted.

To _raise_, from my understanding, is to artificially induce an exception when the runtime doesn't actually encounter a genuine error. 

What I learned from the problem sets, really, is that the try and except blocks don't leave you any room for mistakes, because the triggering of an exception accidentally exits a while True loop, which many of those problems required. 

