## Lambda expression
Using the lambda expression, we can express a function in a way; lambda expression also makes it unnecessary to name a function, unless you want to.
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
