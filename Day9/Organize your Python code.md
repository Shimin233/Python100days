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
The former one refers to the variable used to define a function, like `name` in the `MySecondFunction(name)`; the latter refers to the variable inputted to operate the function, like `Alice` in `MySecondFunction('Alice')`.


## Keys
- Three key factors in Python code: 1. Function, 2. Module, and 3. Item
   1.1 Define a funciton: use `def` to define new functions, with/without inputted item(s)
   1.2 Parameter and arguemnt
  
