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
`filter()`

```Python
>>> filter(None,[1, 0, False, True])
<filter object at 0x7fef4d7637c0>
>>> list(filter(None,[1, 0, False, True]))
[1, True]
>>> def odd(x):
	return x % 2

>>> temp = range(3, 21)
>>> show = filter(odd, temp)
>>> list(show)
[3, 5, 7, 9, 11, 13, 15, 17, 19]
>>> list(filter(lambda x: x % 2, range(3, 21)))
[3, 5, 7, 9, 11, 13, 15, 17, 19] 
```


## Keys
- Lambda expression
- Another two BIFs
