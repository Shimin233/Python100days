## Set
In Python 3, a __set__ is denoted by some items which have no mapping relation and are enclosed in braces '{}'. 

```Python
>>> num = {}
>>> type(num)
<class 'dict'>
>>> num2 = {1, 2, 3, 4, 5}
>>> type(num2)
<class 'set'>
```

The items (called elements) in a set are not duplicated; and not ordered, and thus have no index defined for them.
```Python
>>> num2[2]
Traceback (most recent call last):
  File "<pyshell#4>", line 1, in <module>
    num2[2]
TypeError: 'set' object is not subscriptable
```

There are two methods to create a set:
1. enclose some items in a pair of braces
2. `set()` (a factory function), it turns a list, a tuple or a string to a set, removing any duplication of elements and outputting elements with no well-defined order.
```Python
>>> set1 = set([1, 2, 3, 3])
>>> set1
{1, 2, 3}
>>> set2 = set('hello')
>>> set2
{'l', 'h', 'e', 'o'}
>>> set3 = set(('hello', 'mine', 23))
>>> set3
{'mine', 'hello', 23}
```
Again, the items in the result of `set()`, i.e. the items in a set, are not ordered, and do not have index. In the following example, though `list()` re-orders the elements, the original order was lost in `set()`.
```Python
>>> num1=list(set(num1))
>>> num1
[0, 1, 2, 3, 4, 5]
```

We can build a list with no duplication of items in a similar logic to a set, as below.
```Python
>>> num1=[1, 2, 3, 4,5, 5, 3, 1, 0]
>>> temp=[]
>>> for each in num1:
	if each not in temp:
		temp.append(each)

		
>>> temp
[1, 2, 3, 4, 5, 0]
```

### Visit elements in a set
We can visit each element of a set using the cycle of `for`.

We check whether some element is in a set using`in` and `not in`like we did for lists, tuples and dictionaries. We can also add or remove elements using `add()` and `remove()` respectively.

```Python
>>> num2
{1, 2, 3, 4, 5}
>>> 1 in num2
True
>>> '1' in num2
False

#add() and remove()
>>> num2
{1, 2, 3, 4, 5}
>>> num2.add(6)
>>> num2
{1, 2, 3, 4, 5, 6}
>>> num2.remove(5)
>>> num2
{1, 2, 3, 4, 6}

#if trying to remove a non-existing element from a set, an error will be reported
>>> num2.remove('1')
Traceback (most recent call last):
  File "<pyshell#33>", line 1, in <module>
    num2.remove('1')
KeyError: '1'
```

### Frozenset
A __frozenset__ is a 'non-alterable' set. Build it using `frozenset()`.
```Python
>>> num3 = frozenset([1,2, 3, 4, 5])
>>> num3.add(0)
Traceback (most recent call last):
  File "<pyshell#35>", line 1, in <module>
    num3.add(0)
AttributeError: 'frozenset' object has no attribute 'add'
```

## Keys
