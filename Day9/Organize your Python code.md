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
The former one refers to the variable used to define a function, like `name` in the `MySecondFunction(name)`; the latter refers to the variable inputted to operate the function, like `'Alice'` in `MySecondFunction('Alice')`.\
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
Let us look at some special types of arguments.
##### Keyword argument关键字参数
Python will recognize your inputs by their order, by default, in order to make correspondence between the inputs (arguments) and the parameters. Alternatively, you can sepcify their correspondence by keyword arguments, and in this case the order of inputs does not matter.
```Python
>>> def SaySome(name, words):
	print(name + '->' + words)

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
##### Default argument默认参数
You can set a default argument for a parameter when defining a function. If there is no input for a parameter with a default argument, Python will automatically adopt this default one. 
```Python
>>> def SaySome(name='Alice', words='Hi~'):
	print(name + '->' + words)

	
>>> SaySome()
Alice->Hi~
>>> SaySome('Ben')  #the input 'Ben' is recognized as the name, by its order (1st parameter = 1st input)
Ben->Hi~
>>> SaySome('Ben', 'Goodbye!') 
Ben->Goodbye!
```
In the case that no default argument is set, the lack of input will lead to an error; thus it is recommended to set default arguments, to avoid unnecessary inputs while ensuring the operation of a function.

##### Variable argument收集参数，可选/可变参数
Sometimes you may be not sure how many arguments will be inputted for a parameter. To solve this problem, you can use a variable argument `*params` to define the parameter; all the inputs which correspond to this parameter are collected in one tuple. In some cases, we use the variable argument `**params`, and all its inputs are collected in one dictionary. This will be talked about in the future courses.
```Python
>>> def test(*params):
	print('the length of the argument: ', len(params))
	print('the second argument is: ', params[1])

>>> test(1, 'Alice', 3.14, 5, 6, 7, 8) #All the inputs here are in one tuple 'params'
the length of the argument:  7
the second argument is:  Alice
```
We can also mix the variable argument with other types of arguments. Note that we must specify which parameter the inputs correspond to. Also, when there is a deault argument set for a parameter, its input is not required; when there is no default for it, its input is required.
```Python
>>> def test(*params, exp):
	print('the length of the argument: ', len(params))
	print('the second argument is: ', params[1])

#although the exp is not printed eventually in the output, the function requires its input since there is no default argument set for it	
>>> test(1, 'Alice', 3.14, 5, 6, 7, 8)   #exp has no input or default, so an error is reported
Traceback (most recent call last):
  File "<pyshell#73>", line 1, in <module>
    test(1, 'Alice', 3.14, 5, 6, 7, 8)
TypeError: test() missing 1 required keyword-only argument: 'exp'
>>> test(1, 'Alice', 3.14, 5, 6, 7, exp=8) #8 is specified as the input of exp
the length of the argument:  6
the second argument is:  Alice

#now the exp does appear in the output; like the case above, as no default argument is set for it, its input is required
>>> def test(*params, exp):
	print('the length of the argument: ', len(params), exp)
	print('the second argument is: ', params[1])

	
>>> test(1, 'Alice', 3.14, 5, 6, 7, exp=8)
the length of the argument:  6 8
the second argument is:  Alice
```


You can see keyword arguments, default arguments and variable arguments in the explanation of the BIFs in Python, such as `print`.
```Python
>>> help(print)
Help on built-in function print in module builtins:

print(...)
    print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False) #'value, ...' actually means a variable argument; by default, sep is ' ', end is a newline, file is sys.stdout and flush is False, so it is fine not to input anything for them
    
    Prints the values to a stream, or to sys.stdout by default.
    Optional keyword arguments:
    file:  a file-like object (stream); defaults to the current sys.stdout.
    sep:   string inserted between values, default a space.
    end:   string appended after the last value, default a newline.
    flush: whether to forcibly flush the stream. 
```

## Keys
- Three key factors in Python code: 1. Function, 2. Module, and 3. Item
   1.1 Define a funciton: use `def` to define new functions, with/without inputted item(s)
   1.2 Parameter and arguemnt
       - Keyword argument
       - Default argument
       - Variable argument
  
