## Three key factors
### Factor 1: Function
#### 1.3 Function VS. procedure
In most programming languages, we make difference between the function, which returns a result, and the procedure, which has no return.
But in Python, there is no procedure but only function, since no return will be shown by returning `None`.
 ```Python
 >>> def hello():
	print('Hello world!')

	
>>> temp=hello()
Hello world!
>>> hello()  #the last line is basically this
Hello world!
>>> temp   #it has no return, theoretically
>>> print(temp)
None
>>> type(temp)
<class 'NoneType'>
```
Python can return multiple items simultaneously using lists and tuples. Between them, tuples requires commas between items only.
```Python
>>> def back():
	return[1, 'Alice', 3.14]

>>> back()
[1, 'Alice', 3.14]
>>> temp=back()
>>> temp
[1, 'Alice', 3.14]
>>> print(temp)
[1, 'Alice', 3.14]
>>> def back():
	return 1, 'Alice', 3.14 

>>> back()
(1, 'Alice', 3.14) 
```


## Keys
- Three key factors in Python code: 1. Function, 2. Module, and 3. Item
  - 1.3 Function VS. procedure
