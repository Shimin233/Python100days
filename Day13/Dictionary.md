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

Instead, such a correspondence can be built using __dictionaty__ in Python. A 
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

```Python
dict3 = dict((('F', 70), ('i', 105), ('s', 115), ('h', 104)))
>>> dict3
{'F': 70, 'i': 105, 's': 115, 'h': 104}
>>> dict4 = dict([('F', 70), ('i', 105), ('s', 115), ('h', 104)])
>>> dict4
{'F': 70, 'i': 105, 's': 115, 'h': 104}
>>> dict5 = dict(you='right', me='left') #will read the keyword as a string automatically; cannot use 'you'=..., since keyword cannot be an expression
>>> dict5
{'you': 'right', 'me': 'left'}
```
