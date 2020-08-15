## Three key factors
There are three key factors in Python code: funciton, module模块, item对象.

### Factor 1: Fucntion
#### 1.1 Define a function
We can define a function using `def`.
```Python
>>> def MyFirstFunction():
	print('This is the first function created by me~')
	print('Dokidoki')
	print('Blahblah')

#try to run it	
>>> MyFirstFunction()
This is the first function created by me~
Dokidoki
Blahblah
```
Basically, Python looks for the `def` typed before, and operates as defined there.

If Python cannot find the corresponding `def` typed before, it will report an error.
```Python
>>> MySecondFunction()
Traceback (most recent call last):
  File "<pyshell#6>", line 1, in <module>
    MySecondFunction()
NameError: name 'MySecondFunction' is not defined
```
We can also define a function which requires inputted item(s).
```Python
>>> def MySecondFunction(name):
	print(name + ' is here')

	
>>> MySecondFunction('Alice')
Alice is here
```
```Python
>>> def add(num1, num2):
	result=num1+num2
	print(result)

	
>>> add(1, 2)
3
``` 
We can set an arbitrary (finite?) number of items in a funciton.

```Python
>>> def add(num1, num2):
	return (num1 + num2)

>>> print(add(5, 6))
11
>>> print(11)   #the last line is exactly equivalent to this
11
```

#### 1.2 Parameter and argument
There are two types of variables involved in the definition and use of a function: __parameter__ （形式参数，形参）and __argument__ （实际参数，实参）.
The former one refers to the variable used to define a function, like `name` in the `MySecondFunction(name)`; the latter refers to the variable inputted to operate the function, like `Alice` in `MySecondFunction('Alice')`.\
Moreover, we can include some words of explanation when defining a function.
```Python
>>> def MyFirstFunction(name):
	'the item used to define a function is parameter'
	print('the inputted ' + name + ' is argument, since it is the actual item given eventually')

>>> MyFirstFunction('Blahblah')
the inputted Blahblah is argument, since it is the actual item given eventually
```
There are two ways to see the words of explanation: `help(MyFirstFunction)` and `MyFirstFunction.__doc__` (note there are two unerlines on each side of 'doc'). Usually `help()` gives a more tidy explanation, see that for `print` for example.
```Python
>>> help(MyFirstFunction)
Help on function MyFirstFunction in module __main__:

MyFirstFunction(name)
    the item used to define a function is parameter

>>> MyFirstFunction.__doc__
'the item used to define a function is parameter'
```
```Python
>>> print.__doc__
"print(value, ..., sep=' ', end='\\n', file=sys.stdout, flush=False)\n\nPrints the values to a stream, or to sys.stdout by default.\nOptional keyword arguments:\nfile:  a file-like object (stream); defaults to the current sys.stdout.\nsep:   string inserted between values, default a space.\nend:   string appended after the last value, default a newline.\nflush: whether to forcibly flush the stream."

>>> help(print)
Help on built-in function print in module builtins:

print(...)
    print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
    
    Prints the values to a stream, or to sys.stdout by default.
    Optional keyword arguments:
    file:  a file-like object (stream); defaults to the current sys.stdout.
    sep:   string inserted between values, default a space.
    end:   string appended after the last value, default a newline.
    flush: whether to forcibly flush the stream.

```
#### Keyword argument关键字参数
Python will recognize your inputs by their order, by default, in order to make correspondence between the inputs (arguments) and the parameters. Alternatively, you can sepcify their correspondence by keyword arguments, and in this case the order of inputs does not matter.
```Python
>>> SaySome('Alice', 'Hi~')
Alice->Hi~
>>> SaySome('Hi~', 'Alice')
Hi~->Alice
>>> SaySome(words='Hi~', name='Alice')
Alice->Hi~

#must specify all the keywords simultaneously
>>> SaySome('Hi~', name='Alice')
Traceback (most recent call last):
  File "<pyshell#56>", line 1, in <module>
    SaySome('Hi~', name='Alice')
TypeError: SaySome() got multiple values for argument 'name'
```
#### Default argument默认参数

#### Variable argument收集参数，可选/可变参数

It is recommended to set default arguments for a function, to avoid unnecessary inputs.
## Keys
- Three key factors in Python code: 1. Function, 2. Module, and 3. Item
   1.1 Define a funciton: use `def` to define new functions, with/without inputted item(s)
   1.2 Parameter and arguemnt
  
