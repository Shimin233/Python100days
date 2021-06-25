## Dictionary

In real life, we can look for some item among many others by looking for its corresponding tag, like 29 has its tag as 'age', 20200701 has its tag as 'date' in our collection of data. The tag is called a __key键__ (also called keyword), and its corresponding content is called the __value值__; in one word, a key indexes its value. 

The relation between keys and values can be shown by mapping映射 in Mathematics.

To look at the corresponding relation between keys and values, we may manually type two lists and obtain the correspondence from their order by default.
```Python
>>> name = ['Alice', 'Bob', 'Celine', 'Debbie', 'Who?']
>>> like = ['fish', 'sleeping', 'nothing', 'Alice', 'What']
>>> print('What is it: ', like[name.index('Bob')])  #'Bob' indexes 'sleeping' by default, since they are the 2nd item in their lists resp.
What is it:  sleeping
```

Instead, such a correspondence can be built using __dictionaty__ in Python. 
```Python
>>> dict1 = {'Alice':'fish', 'Bob':'sleeping', 'Celine':'nothing', 'Debbie':'Alice', 'Who?':'What'}
>>> print('What is it: ', dict1['Bob']) #the key 'Bob' indexes its value 'sleeping', like a position number indexes its value in tuples and lists
What is it:  sleeping
```
```Python
#the keywords can be numbers as well as strings
>>> dict2 = {1:'one', 2:'two', 3:'three'}
>>> dict2
{1: 'one', 2: 'two', 3: 'three'}
>>> dict2[2]
'two'
#an empty discitonary
>>> dict3 = {}
>>> dict3
{}
```
Note that lists and tuples are of the sequence type, while dictionaries are of the mapping type.

### Dict()
Use `dict(mapping)` to create a dictionary.
```Python
dict3 = dict((('F', 70), ('i', 105), ('s', 115), ('h', 104))) #input a tuple (consisting of smaller tuples) into dict(), where this tuple of tuples acts as a mapping
>>> dict3
{'F': 70, 'i': 105, 's': 115, 'h': 104}
>>> dict4 = dict([('F', 70), ('i', 105), ('s', 115), ('h', 104)]) #input a list (consisting of small tuples) into dict()
>>> dict4
{'F': 70, 'i': 105, 's': 115, 'h': 104}
>>> dict5 = dict(you='right', me='left') #will read the keyword as a string automatically; cannot use 'you'=..., since keyword cannot be an expression #use assignments to create a dictionary
>>> dict5
{'you': 'right', 'me': 'left'}
```
We can update the value of some key by re-assigning a new value to it. We can also create a new pair of key and value by '(re-)assigning' it. This is different from sequence-type items; re-assigning a non-existing item will lead to an error.
```Python
>>> dict5
{'you': 'right', 'me': 'left'}
#update by re-assigning
>>> dict5['me']='down'
>>> dict5
{'you': 'right', 'me': 'down'}
#create by assigning
>>> dict5['they']='up'
>>> dict5
{'you': 'right', 'me': 'left', 'they': 'up'}
```
### Fromkeys()
You can find the `fromkeys(iterable, value=None, /)` from `help(dict)`. It creates a_new_ dictionary with keys from iterable and values set (optional) to value. And the value set can only be one argument, thus the values of all the keys in the newly-created dictionary must be the same (To be confirmed).
```Python
>>> dict1={}
>>> dict1.fromkeys((1, 2, 3))
{1: None, 2: None, 3: None}
>>> dict1.fromkeys((1, 2, 3), 'Number')
{1: 'Number', 2: 'Number', 3: 'Number'}
>>> dict1.fromkeys((1, 2, 3), ('one', 'two', 'three')) 
{1: ('one', 'two', 'three'), 2: ('one', 'two', 'three'), 3: ('one', 'two', 'three')}
>>> dict1.fromkeys((1, 3), 'number') #it cannot update part of the keys, but only create a new dictionary
{1: 'number', 3: 'number'}
>>> dict1  #when new dictionaries are created, the original dict1 remains intact
{}
```
### Key(), values() and items()
We can visit the contents of a dictionary in three ways: `keys()` returns all of its keys, `values()` returns all of its values, and `items()` returns all the pairs of `(key, value)` in the form of tuples.

```Python
>>> dict1=dict1.fromkeys(range(12), 'miu')
>>> dict1
{0: 'miu', 1: 'miu', 2: 'miu', 3: 'miu', 4: 'miu', 5: 'miu', 6: 'miu', 7: 'miu', 8: 'miu', 9: 'miu', 10: 'miu', 11: 'miu'}
>>> for eachkey in dict1.keys():
	print(eachkey)

	
0
1
2
3
4
5
6
7
8
9
10
11
>>> for eachvalue in dict1.values():
	print(eachvalue)

	
miu
miu
miu
miu
miu
miu
miu
miu
miu
miu
miu
miu
>>> for eachitem in dict1.items():
	print(eachitem)

	
(0, 'miu')
(1, 'miu')
(2, 'miu')
(3, 'miu')
(4, 'miu')
(5, 'miu')
(6, 'miu')
(7, 'miu')
(8, 'miu')
(9, 'miu')
(10, 'miu')
(11, 'miu')
```
### Get(), in and not in
Note that we use `in` and `not in` to check values in sequences(lists and tuples) but keys in dictionaries. We can also use `dict.get(self, key, default=None, /)` to do this; it returns the value for key if key is in the dictionary, else default (None) or some expression set by us.
```Python
#nothing will be printed since dict1.get(12) does not exist
>>> dict1.get(12)
>>> print(dict1.get(12))
None
#set an expression for the case that dict1.get(sth) does not exist
>>> dict1.get(12, 'No such thing!')
'No such thing!'
>>> dict1.get(9, 'No such thing!') #for the item that exists, the value itself will be printed
'miu'
```
```Python
#use in, not in to check whether some key exists in a dictionary
>>> 11 in dict1
True
>>> 12 in dict1
False
>>> 44 in dict1
False
```
### Clear()
We use `dict1.clear()` to remove all the contents in a dictionary. 
```Python
>>> dict1.clear()
>>> dict1
{}
>>> dict1 = {}
```
Although we can clean a dictionary likewise by re-assigning am empty dictionary to it, the previously elsewhere-assigned copy will remain intact. However, `clear()` will clean all of the copies.
```Python
>>> a={'je':'I'}
>>> b = a
>>> a = {}
>>> a
{}
>>> b
{'je': 'I'}
>>> a = b #or a={'je':'I'}, put it back to test clear()
>>> a.clear()
>>> a
{}
>>> b
{}
```
Note, there is an issue when typeing the codes above: the semicolon ';' may be mistaken to be a comma, so the result will be `set()`. 
```Python
>>> a = {'you', 'me'}
>>> b = a
>>> b
{'you', 'me'}
>>> a = {}
>>> a
{}
>>> b
{'you', 'me'}
>>> a.clear()
>>> a
{}
>>> b
{'you', 'me'}
>>> b
{'you', 'me'}
>>> a = b
>>> a.clear()
>>> a
set()
>>> b
set()
```

## Copy() 浅拷贝
We may create a copy of some dictionary using `copy()`. Note the differences between `copy()` (a new item) and assigninment (the same thing with the same id, alternations updated together).
```Python
>>> a = {1:'one', 2:'two', 3:'three'}
>>> b = a.copy()
>>> c = a
>>> c
{1: 'one', 2: 'two', 3: 'three'}
>>> b
{1: 'one', 2: 'two', 3: 'three'}
>>> a
{1: 'one', 2: 'two', 3: 'three'}
>>> id(a)
140333840575104
>>> id(b)
140333845157824
>>> id(c)
140333840575104 #same as id(a)
>>> c[4]='four'
>>> c
{1: 'one', 2: 'two', 3: 'three', 4: 'four'}
>>> a
{1: 'one', 2: 'two', 3: 'three', 4: 'four'} #a and c have alternations updated together
>>> b
{1: 'one', 2: 'two', 3: 'three'} #b is independent from a
```
##### (Deep)copy and assignment
Campare copy浅拷贝, deepcopy()深拷贝 and assignment ([source](https://www.cnblogs.com/xiaodi914/p/5888052.html)).
First for assignment, we test the following codes.
```Python
>>> will = ["Will", 28, ["Python", "C#", "JavaScript"]]
>>> wilber = will

>>> id(will)
140333844956160
>>> will
['Will', 28, ['Python', 'C#', 'JavaScript']]
>>> [id(item) for item in will]
[140333845121776, 4462730784, 140333845131584]

>>> id(wilber)
140333844956160
>>> wilber
['Will', 28, ['Python', 'C#', 'JavaScript']]
>>> [id(item) for item in wilber]
[140333845121776, 4462730784, 140333845131584]
#the id's of will and wilber are exactly the same, implying that 'wilber is will' and 'wilber[i] is will[i]'


>>> will[0] = "Wilber"  #update will
>>> will[2].append('CSS')  #update will; note this is to append an item to the list, which is the 2-th item in the whole list, will

>>> id(will)
140333844956160  #id(will) remains the same 
>>> will
['Wilber', 28, ['Python', 'C#', 'JavaScript', 'CSS']]
>>> [id(item) for item in will]
[140333840570992, 4462730784, 140333845131584] #the id of 0th item changes because string is an 'un-alterable' item, so updation creates a new id #other id's remain the same 

>>> id(wilber)
140333844956160  #id(wilber) remains the same, like id(will)
>>> wilber
['Wilber', 28, ['Python', 'C#', 'JavaScript', 'CSS']]  #wilber alters in the same way as will
>>> [id(item) for item in wilber]
[140333840570992, 4462730784, 140333845131584] #the items' id's change in wilber in the same way as those in will

>>> wilber.pop()
['Python', 'C#', 'JavaScript', 'CSS']
>>> wilber
['Wilber', 28]
>>> will
['Wilber', 28] #the items' id's change in the same way in will as those in wilber
```
We can summarize from the example above that
- As will is assigned to wilber, they use exactly the same objects, 'wilber is will' and 'wilber\[i\] is will\[i]';
- Thus any change to will happens in wilber in the same way, also in the other direction: changes happen to will like to wilber;
- Note a string is 'un-alterrable', so updation of it will create a new string with a new id; but for the lists (and some other?), they are 'alterable' and so the id's remain the same after updation.

Secondly, we look at _copy浅拷贝_ by testing the following.
```Python
>>> import copy #引入copy模块

>>> will = ["Will", 28, ["Python", "C#", "JavaScript"]]
>>> wilber = copy.copy(will)

>>> id(will)
140333845132544
>>> will
['Will', 28, ['Python', 'C#', 'JavaScript']]
>>> [id(item) for item in will]
[140333845135728, 4462730784, 140333844931200]

>>> id(wilber)
140333845121216   #id(wilber) is distinct from id(will), 'wilber is not will'
>>> wilber
['Will', 28, ['Python', 'C#', 'JavaScript']]  #wilber appears like will
>>> [id(item) for item in wilber]
[140333845135728, 4462730784, 140333844931200]  #same id for each item, 'wilber\[i] is wll\[i]'

>>> will[0] = "Wilber"  #update will
>>> will[2].append("CSS")  #update will

>>> id(will)
140333845132544 #same id as the old will, despite updation
>>> will
['Wilber', 28, ['Python', 'C#', 'JavaScript', 'CSS']]
>>> [id(item) for item in will]
[140333845138160, 4462730784, 140333844931200] #string's id updated, others remain the same, like before

>>> id(wilber)
140333845121216 
>>> wilber
['Will', 28, ['Python', 'C#', 'JavaScript', 'CSS']] #wilber appears different from updated will; only 'alterable' (2-th, a list) items in wilber is updated, the 'un-alterable' (string) is not
>>> [id(item) for item in wilber]
[140333845135728, 4462730784, 140333844931200] #same id for each item of wilber, as in old will
# updation of will changes the 'alterable' (e.g. list) items but does not change 'un-alterable' items (e.g. string) in wilber, the copy of will
```
Summarize the codes above
- Copying creates a new object wilber distinct from will, 'wilber is not will'; but each item in wilber uses the original id's as in will, 'wilber\[i] is wll\[i]';
- Updation of will changes the 'alterable' (e.g. list) items but does not change 'un-alterable' items (e.g. string) in wilber;
- same as before, string's id changes after updation while that for list does not;
- The cases leading to copying include
  - slicing切片`[:]`
  - facory functions工厂函数, like list()/dir()/set()
  - `copy()` in the `copy` module模块 (like we did above)

Fianlly for _deepcopying_, test the below
```Python
>>> import copy

>>> will = ["Will", 28, ["Python", "C#", "JavaScript"]]
>>> wilber = copy.deepcopy(will)

>>> id(will)
140333844956160
>>> will
['Will', 28, ['Python', 'C#', 'JavaScript']]
>>> [id(item) for item in will]
[140333845135728, 4462730784, 140333845138240]

>>> id(wilber)
140333845138944  #id(wilber) is distinct from id(will), 'wilber is not will'
>>> wilber
['Will', 28, ['Python', 'C#', 'JavaScript']]
>>> [id(item) for item in wilber]
[140333845135728, 4462730784, 140333845131584] #deepcopy creates a new portion of each item (with exceptions), like 2-th item here (see the different id's in will and wilber), 'will[2] is not wilber[2]'


>>> will[0] = "Wilber" #update will
>>> will[2].append("CSS")  #update will

>>> id(will)
140333844956160 #same id as the old will
>>> will
['Wilber', 28, ['Python', 'C#', 'JavaScript', 'CSS']]
>>> [id(item) for item in will]
[140333845143280, 4462730784, 140333845138240] #string's id updated, others remain the same, like before

>>> id(wilber)
140333845138944
>>> wilber
['Will', 28, ['Python', 'C#', 'JavaScript']] #wilber appears not changed by updation of will
>>> [id(item) for item in wilber]
[140333845135728, 4462730784, 140333845131584] #the id's of wilber are not changed by updation of will
```
Summarize the codes above
- 'wilber is not will', 'will\[2] is not wilber\[2]' with some exceptions
- same as before, string's id changes after updation while that for list does not

See more examples [here](https://www.cnblogs.com/sxzwj/p/7967418.html).

### Pop(), popitem(), setdefault() and update()
Use `pop(key)` to remove and return a pair of key and value from a dictionary, while `popitem()` removes and returns the last pair.
```Python
>>> a
{1: 'one', 2: 'two', 3: 'three', 4: 'four'}
>>> a.pop(2)
'two'
>>> a
{1: 'one', 3: 'three', 4: 'four'}
>>> a.popitem()
(4, 'four')
```
The use of `setdefault(key)` is similar to `get(key)`, but when such a key does not exist, a pair of this key and value (None) will be created. Also, `setdefault(key, value)` will create and return a pair of key and value. \
We update a dictionary by adding another to it using `update(dict2)`.
```Python
>>> a.setdefault('ME')
>>> a
{1: 'one', 3: 'three', 'ME': None}
>>> a.setdefault(5,'five')
'five'
>>> a
{1: 'one', 3: 'three', 'ME': None, 5: 'five'}
>>> a.setdefault(3)
'three'
>>> b = {'ME': 'moi'}
>>> a.update(b)
>>> a
{1: 'one', 3: 'three', 'ME': 'moi', 5: 'five'} #the contents in the old dictionary can be updated by update(), (I guess )at some certain position
>>> c = {1: 'one', 2: 'two', 3: 'three', 4: 'four'}
>>> a.update(c)
>>> a
{1: 'one', 3: 'three', 'ME': 'moi', 2: 'two', 4: 'four'} #the duplicated pairs are not updated, the new pairs are added 
```

## Keys
- Dictionary
  - Key and value
  - Use `dict(mapping)` to create a dictionary
  - Use `fromkeys(iterable, value=None)` to create a dictionary
  - Use `key()`, `values()` and `items()` to visit contents of a dictionary
  - Use `get()`, `in` and `not in` to check wthether an item is in a dictionary
  - Use `clear()` to clean a dictionary, compared with assignment
  - Use `copy()` to create a new copy, compared with assignment
    - Campare copy浅拷贝, deepcopy()深拷贝 and assignment
  - Use `pop()`, `popitem()`, `setdefault()` and `update()` to remove, add and update items
