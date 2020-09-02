## Dictionary

In real life, we can look for some item among many others by looking for its corresponding tag, like 29 has its tag as 'age', 20200701 has its tag as 'date' in our collection of data. The tag is called a __key键__, and its corresponding content is called the __value值__; in one word, a key indexes its value.

The relation between keys and values can be shown by mapping映射 in Mathematics.

To look at the corresponding relation between keys and values, we may manually type two lists and obtain the correspondence from their order by default.
```Python
>>> name = ['Alice', 'Bob', 'Celine', 'Debbie', 'Who?']
>>> like = ['fish', 'sleeping', 'nothing', 'Alice', 'What']
>>> print('What is it: ', like[name.index('Bob')])  #'Bob' indexes 'sleeping' by default, since they are the 2nd item in their lists resp.
What is it:  sleeping
```

Instead, such a correspondence can be built using __dictionaty__ in Python.
