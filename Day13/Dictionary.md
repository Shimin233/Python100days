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

## Keys
- Dictionary
  - Key and value
  - Use `dict(mapping)` to create a dictionary
  - Use `fromkeys(iterable, value=None)` to create a dictionary
