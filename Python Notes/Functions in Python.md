# Function
## Essentials
- Parameter is a slot in a function that defines the data to be accepted into the function. For example `param` is a parameter that defines a data to be inserted in the `func1` 
```python
def func1(param):
	 x = param 
```
- Argument is the data passed to the parameter in when the function is to be called. For example `arg` is the date pass into `func1` in which `'arg'` is assigned to the `param` of `func1` 
```python
def func1(param):
	x = param 
	return x

func1('arg') # func1 is called and 'arg' is pass as an agurment
```
## Recursion 
Recursion is when a function calls itself. For example
```python
def func1(param):
	# stop conditon for recursion 
	return func1(param-1)
```
The effective recursion depth is 997. If a recursion depth goes deeper than that limit python raises an error `RecursionError`; that is why it is important to have a stop condition for any recursive functions. 
The recursive depth can be overridden 
```python
import sys
sys.setrecursionlimit(2000)
```
The `sys.setrecursionlimit()` function allows you to set a new maximum depth for recursion depth 
## Argument
### Default Argument Values
A parameter can have a default value to be pass into the function 
```python
def func1(param=value):
	pass 
```
When a parameter is assigned a default value the parameter is an ***optional parameter***  and when the parameter had no default value it is a ***required parameter***. It is important to *never use a mutable value for a default argument* ; `None` should be used as default value
### Keyword Argument
Keyword argument help in the readability of a code by attaching labels to argument in function call. If a function call does not have a label to attach the argument, it can cause the reader to guess which goes against the on of the Zen of python 
>In the face of ambiguity, refuse the temptation to guess. 

Keyword argument removes ambiguity in a code, so it is good to use it often 
For example 
```python
def func1(param1, param2):
	pass

func_call = func1(para1='x', param2='y')
```
### Variadic Argument
There are situations where a function could potentially have many arguments pass into it. In this cases it *variadic argument* are used, using *arbitrary arguments list*. In which automatically pack multiple arguments into a single *variadic positional parameter*. For example 
```python
def fuction(*param):
	pass
```
Using the `*` on `params` parameter this turns `params` in to a variadic parameter in which all argument pass into `function` will be packed into a tuple. 
#### Keyword Variadic Arguments
To capture an unknown number of keyword argument, `**` is used to precede the parameter name, making the parameter a ***keyword parameter*** . The keyword argument is passed to the function and packed into a single dictionary object so as to preserve the association between keyword and value. For example
```python
def function(param, *args, **kwargs):
	pass
```



# Related Notes 
[[Zen of Python]]
[[Error and Exceptions]]