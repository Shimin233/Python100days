## Lambda expression
Using the lambda expression, we can express a function more concisely; lambda expression also makes it unnecessary to name a function, unless you want to. 
```Python
#replace ds(x) using lambda expression
>>> def ds(x):
	return 2 * x +3

>>> ds(6)
15
>>> lambda x : 2 * x + 3  #equivalent to ds(x)
<function <lambda> at 0x7fef4d7841f0>
>>> f = lambda x : 2 * x + 3
>>> f(6)
15

#replace add(x, y), a multiple-variable function using lambda expression
>>> def add(x, y):
	return x + y

>>> add(5, 6)
11
>>> lambda x, y: x + y
<function <lambda> at 0x7fef4d784280>
>>> f = lambda x, y: x + y
>>> f(5, 6)
11
```
The lambda expression allows us to save time by simpler, more efficient and more readable codes.

## Another two BIFs
We shall introduce two moew BIFs and apply lambda expression to their examples. 

The first one is `filter()`. See the explanation, note that `filter(None, iterable)` means we pick anything which is `True` or 1 from the iterable; `filter(function or None, iterable)` means we pick anything which is inputted to the specified function any results in `True` or 1 from the iterable.
```Python
>>> help(filter)
Help on class filter in module builtins:

class filter(object)
 |  filter(function or None, iterable) --> filter object
 |  
 |  Return an iterator yielding those items of iterable for which function(item)
 |  is true. If function is None, return the items that are true.
 |  
 |  Methods defined here:
 |  
 |  __getattribute__(self, name, /)
 |      Return getattr(self, name).
 |  
 |  __iter__(self, /)
 |      Implement iter(self).
 |  
 |  __next__(self, /)
 |      Implement next(self).
 |  
 |  __reduce__(...)
 |      Return state information for pickling.
 |  
 |  ----------------------------------------------------------------------
 |  Static methods defined here:
 |  
 |  __new__(*args, **kwargs) from builtins.type
 |      Create and return a new object.  See help(type) for accurate signature.
```
Take an example.
```Python
>>> filter(None,[1, 0, False, True])
<filter object at 0x7fef4d7637c0>
>>> list(filter(None,[1, 0, False, True]))
[1, True]
>>> def odd(x):
	return x % 2

>>> temp = range(3, 21)  #this is 3, 4, ..., 19, 20
>>> show = filter(odd, temp)
>>> list(show)
[3, 5, 7, 9, 11, 13, 15, 17, 19]
```
We can simplify this by lambda expresson.
```Python
>>> list(filter(lambda x: x % 2, range(3, 21)))
[3, 5, 7, 9, 11, 13, 15, 17, 19] 
```

The second one is `map`.This operates a function by inputting each item from the given iterable.

## Keys
- Lambda expression
- Another two BIFs
