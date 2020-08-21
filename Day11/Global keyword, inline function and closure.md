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
Python allows us to define a function inside another function. The interior funciton is called an __inline funciton__. In the following example, as `fun1()` is operating, `fun2()`, which is inline, is operating as a part of `fun1()`.
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
If an interior function quotes some variable which is external to this function but not global, then this interior funcitn is called a __closure__. For instance, `FunY(y)` is a closure defined inside `FunX(x)`, and quotes the variable `x`, which is external to `FunY(y)` but local in `FunX(x)`. \
Note that `FunX(x)` is actually a function sending a number (like `x=8`, an independent variable of `FunX(x)`) to a function (like `FunX(8)`, a dependent variable of `FunX(x)`); and any of its dependent variables is a function sending a number (like 5) to another (40, i.e. `FunX(8)(5)`). In another words, with `x` given (8 here), `FunX(x)` knows what its `FunY(y)` looks like (y |-> 8 * y here), and then `y` is given, we know the final result. Remark, it is `FunY(y)` that quotes `x` which is local to `FunX(x)` (closure) and acts as the dependent variable of `FunX(x)`; probably it is generally the closure that acts as the dependent variable of an external function.\
Note that a closure cannot operate without its external function, since it quotes some variable which is local to another function (in the local domains of these external functions).
```Python
>>> def FunX(x):
	def FunY(y):
		return x * y
	return FunY

>>> i = FunX(8)   #FunX() sends 8 to a function FunX(8) = i
>>> type(i)
<class 'function'>
>>> i
<function FunX.<locals>.FunY at 0x7f80e1f7a8b0>
>>> i(5)   #the function i = FunX(8) sends 5 to 40
40
>>> FunX(8)(5)  #i(5) is exactly the same as this 
40
>>> FunY(5)  #FunY(), the closure cannot operate without FunX(), since x is local to FunX()
Traceback (most recent call last):
  File "<pyshell#31>", line 1, in <module>
    FunY(5)
NameError: name 'FunY' is not defined
```
Take another example, the interior function `Fun2()` quotes the variable `x`, which is external to `Fun2()` but not global (it is in the domain of `Fun1()`), thus `Fun2()` is a closure. An error will be caused by quoting a variable external to a closure, though this variable might be not global (local to a function which contains the closure). There are two solutions to this error: one is using lists, and the other is using __nonlocal keyword__.
```Python
#x is local (non-global) in Fun1(), but external to Fun2()
#thus when x is quoted inside Fun2() (the closure), the part 'return Fun2()' of Fun1() gives an error
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
#Soln1: in Python2, the error above can be solved by using a list rather than a single number
>>> def Fun1():
	x = [5]
	def Fun2():
		x[0] *= x[0]
		return x[0]
	return Fun2()

>>> Fun1()
25
#Soln2: in Python3, the error above can be solved by claiming 'nonlocal' keyword
>>> def Fun1():
	x = 5
	def Fun2():
		nonlocal x
		x *= x
		return x
	return Fun2()

>>> Fun1()
25
```


##### Extension
The lisp processing (lisp) language, see definition [here](https://baike.baidu.com/item/lisp语言/2840299?fr=aladdin).
## Keys
- Factor 1: Function
  - 1.5 Global keyword
  - 1.6 Inline function
  - 1.7 Closure
    - Error for running a closure without its external function(s) (and external domains)
    - Nonlocal keyword
