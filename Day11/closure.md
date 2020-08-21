## Global keyword
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


## Keys
