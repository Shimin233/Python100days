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
#### 1.4 Global and local variables
We are going to introduce the variables with different domains: the local variables局部变量 and the global variables全局变量. A local variable is defined only inside a function and does not exist outside (if not defined elsewhere). A global variable makes sense in the whole file, can be viewed in the interior of functions but cannot be altered there (if trying to do so, Python will automatically create a new local variable with the same name inside the function).
```Python
#final_price is local inside discounts(price, rate); old_price, rate and new_price are global
def discounts(price, rate):
    final_price=price * rate
    return final_price

old_price=float(input('Insert the original price: '))
rate=float(input('Insert the rate of discount: '))
new_price=discounts(old_price, rate)
print('The price with discount is: ', new_price)
```
An example to see that the local variable `final_price` is not defined outside the function.
```Python
def discounts(price, rate):
    final_price=price * rate
    return final_price

old_price=float(input('Insert the original price: '))
rate=float(input('Insert the rate of discount: '))
new_price=discounts(old_price, rate)
print('The price with discount is: ', new_price)
print('Try to print the value of the local variable, final_price: ', final_price)
```
```Python
Insert the original price: 100
Insert the rate of discount: 0.8
The price with discount is:  80.0
Traceback (most recent call last):
  File "/Users/shiminfu/Desktop/Python100days/Day10/Global and local variables .py", line 9, in <module>
    print('Try to print the value of the local variable, final_price: ', final_price)
NameError: name 'final_price' is not defined
```
Also, another exmaple to see that the global variable `old_price` can be viewed/printed inside a function.
```Python
def discounts(price, rate):
    final_price=price * rate
    print('Try to print the value of the global variable, old_price: ', old_price)
    return final_price

old_price=float(input('Insert the original price: '))
rate=float(input('Insert the rate of discount: '))
new_price=discounts(old_price, rate)
print('The price with discount is: ', new_price)
```
```Python
Insert the original price: 100
Insert the rate of discount: 0.8
Try to print the value of the global variable, old_price:  100.0
The price with discount is:  80.0
```
One more example to see Python creates a local variable inside the function, with the same name as the global variable `old_price`.
```Python
#local variables incl: final_price, old_price=50; global variables incl: old_price (inserted), rate, new_price
def discounts(price, rate):
    final_price=price * rate
    #print('Try to print the value of the global variable, old_price: ', old_price)
    old_price=50
    print('Try to print the updated value of the global variable: ', old_price)
    return final_price

old_price=float(input('Insert the original price: '))
rate=float(input('Insert the rate of discount: '))
new_price=discounts(old_price, rate)
print('The orignal global variable is not updated: ', old_price)
print('The price with discount is: ', new_price)
```
```Python
Insert the original price: 100
Insert the rate of discount: 0.8
Try to print the updated value of the global variable:  50
The orignal global variable is not updated:  100.0
The price with discount is:  80.0
```

## Keys
- Three key factors in Python code: 1. Function, 2. Module, and 3. Item
  - 1.3 Function VS. procedure
  - 1.4 Global and local variables
