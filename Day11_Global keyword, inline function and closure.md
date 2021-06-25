## Global keyword
When Python sees some variable in a function, it will by default treat this variable as a local one, which is valid only in this function, even though it may have a name same as a global variable. We can claim that a variable is global rather than local inside some function, simply using the __global keyword__ `global`, so that we can alter a global variable inside a function.
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
	global count   #claim this 'count' is a variable defined previously and globally 
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

Recall that a function sends an independent variabl to a dependent variable; when some value is assigned to the independent variable, the function outputs a corresponding value of the dependent variable (called result for convernience). Note that here `FunX(x)` is a function sending a number (`x=8`)  to a function ( `FunX(8)`, also `FunY` in the case of `x=8`); and its result is a function sending a number (5) to another (40, i.e. `FunX(8)(5)`). In another words, what does `FunY(y)` look like depends on the value of `x`. With `x=8` given here, `FunX(x)` knows that its corresponding `FunY(y)` is "y |-> 8 * y", and then `y=5` is given, we can obtain the final result `FunX(8)(5)= 8 * 5 = 40`. Remark, it is `FunY(y)` that quotes `x` which is local to `FunX(x)` (which makes `FunY(y)` a closure) and acts as the result of `FunX(x)`; it is generally the closure that acts as the result of an external function.

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
		x *= x  #Python thinks this x is a local one in Fun2(), thus feel confused because it was not assigned in Fun2() yet
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
		nonlocal x  #tell Python that x is nonlocal to Fun2(), but a variable defined previously outside Fun2() (and inside Fun1(), i.e. not global)
		x *= x
		return x
	return Fun2()

>>> Fun1()
25
```

#### Factory function
The factory function is an application of closure. 见知乎上此问题中[张雨萌的回答](https://www.zhihu.com/question/20670869); I rewrite this explanation in my own words here, to improve understanding (to be confirmed and revised).\
A __factory function__ (called F for convenience) is generally a function which reuturns a closure (called f). 
It was mentioned above in the section of closure f that a function acting as a result of some other function (F here). Because f is a result of F, f=F(x) is a function for each given x; because f is a function, it has its own independent variable (y), thus we write z=f(y)=F(x)(y).  \
Now we talk about a property of the closure, which relates it to the factory function: f remembers the variable x that it quoted from an exterior domain (the domain of F), though F itself is not operating explicitly. Inside F, the closure is defined and then returned, but is not operated, so the result of operating F is still a function, i.e. F(x)=f.\
I express 'F itself is not operating' in the paragraph above in a different way from [张雨萌](https://www.zhihu.com/question/20670869). He said f remembers x when the operation of F has ended; but I would say F is still operating implicitly, since the operation of f relies on the definition and returning in the definition of F. Indeed, `F()` implies that we already get the result of operation of F, the rest operation seems to belong to f (`action()` ), but this relies on the definition of f, which quotes x from F. F has not ended, just the rest happens inside the 'scale' of its result.
```Python
>>> def F():
	x=88
	def f():
		return x
	return f

>>> action = F()
>>> type(action)
<class 'function'>
>>> action()
88
```
There is a detail: f remembers all the variables given in F, including the independent variable x of F, and the assignments made in the body of F. In one word, f know everything that F told it. See the examples below
```Python
>>> def F(x):
    n=18
    def f(y):
        return x*y+n
    return f
 
 >>> F(3) #this is exactly f, 
<function F.<locals>.f at 0x7fca6779e670>
>>> F(3)(2)
24
```
Remark that the `nonlocal` keyword allows us to alter the variable (`in_num`) in the closure which was originally quoted from exterior funcition. With different `num` 's are given, the results of a factory function (`test(num)` here) are indepdent form each other, like `F` and `G`. But inside one result (such that of `F`), the renewal of `in_num` by `nonlocal` will be recorded in the sacle of `F` and thus remembered by the closure.
```Python
>>> def test(num):
	in_num=num
	def nested(label):
		nonlocal in_num
		in_num += 1
		return(label, in_num)
	return nested

>>> F = test(0)
>>> F('a')
('a', 1) #from now on, in_num is updated to be 1 and so F = test(1)
>>> F('b')
('b', 2) #from now on, in_num is updated to be 2 and so F = test(2)
>>> F('c')
('c', 3) #likewise, in_num = 3...

>>> G=test(100)
>>> G('b')
('b', 101)
```
There are also factory functions in the BIFs, like `list()`, `dir()`, etc.

##### Extension
The lisp processing (lisp) language, see definition [here](https://baike.baidu.com/item/lisp语言/2840299?fr=aladdin).


## Keys
- Factor 1: Function
  - 1.5 Global keyword
  - 1.6 Inline function
  - 1.7 Closure
    - Error for running a closure without its external function(s) (and external domains)
    - Nonlocal keyword
    - Factory function
