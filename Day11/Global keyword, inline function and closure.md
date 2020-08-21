## Global keyword
claim that a variable is global rather than local
```Python
>>> count=5
>>> def MyFun():
	count=10
	print(10)

	
>>> MyFun()
10
>>> count
5
>>> def MyFun():
	global count
	count=10
	print(10)

>>> MyFun()
10
>>> count
10
```

## Inline function 内嵌函数/内部函数
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
lisp

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
```

## Keys
- Factor 1: function
  - Global keyword
  - Inline function
  - Closure
    - Nonlocal keyword
