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

### Application of lambda expression to two BIFs
We shall introduce two moew BIFs and apply lambda expression to their examples. 

The first one is `filter()`. See the explanation, note that `filter(None, iterable)` means we pick anything which is `True` or 1 from the iterable; `filter(function, iterable)` means we pick anything which is inputted to the specified function and results in `True` or 1 from the iterable.
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
Take an example for `filter(None, iterable)`.
```Python
>>> filter(None,[1, 0, False, True])
<filter object at 0x7fef4d7637c0>
>>> list(filter(None,[1, 0, False, True]))
[1, True]
```
Another example is for `filter(function, iterable)`.
```Python
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

The second one is `map()`.This operates a function (mapping) by inputting each item from the given iterable(s).
```Python
#apply a single-variable function to one iterable
>>> list(map(lambda x :x * 2, range(10))) #plug 0, 1, 2, ..., 8, 9 into x |-> x * 2 
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

#apply a two-variable function to two iterables; plug range(10) into x, and plug range(20, 30) into y, with 0 corresponding to 20, 1 to 21, ..., 10 to 30, though the function actually does not use the second variable y
>>> list(map(lambda x, y, :x * 2, range(10), range(20, 30)))
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

#apply a three-variable function to three iterables; the result has only 0 = 0 * 2, since the shortest iterable has only one item, even though it is not used by this function
>>> list(map(lambda x, y, z :x * 2, range(10), [19, 2], [-3]))
[0]
```

## Recursion


## Keys
- Lambda expression
  - simpler function expression
  - `filter(function or None, iterable)`
  - `map(function, *iterables)`
