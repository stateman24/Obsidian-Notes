# Exceptions 
Exception is an interruption in normal processing, typically caused by an error condition, that can be handled by another part of the program.
> **It is important to read a traceback from bottom to top**

There two to ways of catching exceptions in a code 
1. LBYL (**Look Before You Leap**)
2. EAFP (**Easier to Ask Forgiveness than Permission**) (*pythonic way*)
An example of a LBYL approach of catching error
```python
# a guessing game
def make_guess(target):
	guess = None
	while guess in None:
		guess = input()
		if guess.isdigit(): # LBYL approach 
			guess = int(guess)
		else:
			print("Enter an Interger")
			guess = None
			
	# rest of the code .... 
```
The LBYL approach is not efficient due to fact that is requires more processing and error checking 
While the EAFP approach of catching error
```python
# a guessing game
def make_guess(target):
	guess = None
	while guess == None:
		try:
			guess = input()
		except ValueError:
			print('Enter an integer')
			
	# rest of the code .... 
```
## Multiple Exceptions
The `try` statement is not limited to a single error type. It can actually handle multiple error scenarios in one compound statement
For example
```python
--snip--
average = AverageCalcualtor()
values = input('Enter scores, seperated by spaces:\n ').split()
try:
	print(f"Average is {average(*values)}")
except ZeroDivisionError:
	print('ERROR: No values provided.")
except (ValueError, UnicodeError):
	print(f"Error: All inputs should be numeric.")
```
Note: Don't use exceptions like this 
```python
try:
	some_function()
except:
	print("An error occured. Moving on!)
```
This is a bare `except` in which catches all exceptions at once in a code. This can cause the code to misbehave
