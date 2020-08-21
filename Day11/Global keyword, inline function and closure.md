## Global keyword
We can claim that a variable is global rather than local inside some function, simply using the __global keyword__ `global`, so that we can alter a global variable inside a function.
```Python
>>> count=5  #conut is a global variable
>>> def MyFun():
	count=10  #Python automatically treats this count=10 as local inside Myfun()
	print(10)

	
>>> MyFun()
10
>>> count
5  #global variable not altered by MyFun()
>>> def MyFun():
	global count   #claim this 'count' is the local one defined before
	count=10
	print(10)

>>> MyFun()
10
>>> count
10
```

## Inline function 内嵌函数/内部函数
Python allows us to define a function inside another function. The interior funciton is called an __inline funciton__.
```Python
>>> def fun1():
	print('fun1() is operating')
	def fun2():
		print('fun2() is operating')
	fun2()

	
>>> fun1()
fun1() is operating
fun2() is operating
>>> fun2()
Traceback (most recent call last):
  File "<pyshell#17>", line 1, in <module>
    fun2()
NameError: name 'fun2' is not defined
```

## Closure
If an interior function quotes some variable which is external to this function but not global, then this interior funcitn is called a __closure__.
For example, the interior function `Fun2()` quotes the variable `x`, which is external to `Fun2()` but not global (it is in the domain of `Fun1()`), thus `Fun2()` is a closure.

inside a function, not global but external, 
```Python
>>> def Fun1():
	x = 5
	def Fun2():
		x *= x
		return x
	return Fun2()

>>> Fun1()
Traceback (most recent call last):
  File "<pyshell#40>", line 1, in <module>
    Fun1()
  File "<pyshell#39>", line 6, in Fun1
    return Fun2()
  File "<pyshell#39>", line 4, in Fun2
    x *= x
UnboundLocalError: local variable 'x' referenced before assignment
>>> def Fun1():
	x = [5]
	def Fun2():
		x[0] *= x[0]
		return x[0]
	return Fun2()

>>> Fun1()
25
>>> def Fun1():
	x = 5
	def Fun2():
		nonlocal x
		x *= x
		return x
	return Fun2()

>>> Fun1()
25

>>> def funX(x):
	def FunY(y):
		return x * y
	return FunY

>>> i = FunX(8)
Traceback (most recent call last):
  File "<pyshell#23>", line 1, in <module>
    i = FunX(8)
NameError: name 'FunX' is not defined
>>> def FunX(x):
	def FunY(y):
		return x * y
	return FunY

>>> i = FunX(8)
>>> type(i)
<class 'function'>
>>> i
<function FunX.<locals>.FunY at 0x7f80e1f7a8b0>
>>> i(5)
40
>>> FunX(8)(5)
40
>>> FunY(5)
Traceback (most recent call last):
  File "<pyshell#31>", line 1, in <module>
    FunY(5)
NameError: name 'FunY' is not defined
>>> def Fun1():
	x = 5
	def Fun2():
		x* = x
		
SyntaxError: invalid syntax
>>> def Fun1():
	x = 5
	def Fun2():
		x *= x
		return x
	return Fun2()

>>> Fun1()
Traceback (most recent call last):
  File "<pyshell#40>", line 1, in <module>
    Fun1()
  File "<pyshell#39>", line 6, in Fun1
    return Fun2()
  File "<pyshell#39>", line 4, in Fun2
    x *= x
UnboundLocalError: local variable 'x' referenced before assignment
>>> def Fun1():
	x = [5]
	def Fun2():
		x[0] *= x[0]
		return x[0]
	return Fun2()

>>> Fun1()
25
>>> def Fun1():
	x = 5
	def Fun2():
		nonlocal x
		x *= x
		return x
	return Fun2()

>>> Fun1()
25
>>> 
```

##### Extension
The lisp processing (lisp) language, see definition [here](https://baike.baidu.com/item/lisp语言/2840299?fr=aladdin).
## Keys
- Factor 1: Function
  - 1.5 Global keyword
  - 1.6 Inline function
  - 1.7 Closure
    - Nonlocal keyword
