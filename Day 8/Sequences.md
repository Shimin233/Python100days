## Sequences
Recall that in Python100days/Day1/First lines of codes.md, we have introduced the data of _sequence type_: a sequence is an ordered collection of same or different data types; includes lists, tuples and ranges. Alternatively, we may also summarize the lists, tuples and strings as __sequences__, as all these three have the following properties in common:
- we can use index to pick each element
- the index starts with 0 by default
- we can slice them to obtain a set of some of its elements
- many operators apply to them, including `*` for repetition, `+` for combination, `in`, `not in`
Let's introduce more functions related to them.

### Sequences-related functions
As we have seen before, we can type `help(list)` to check what functions are related to `list` (See another file in the folder Day8 for them). Some examples are shown below.\

First, `list()` transforms an iterable item to a list
   - if no argument is given in the parentheses, this creats a new empty list
   - otherwise, the given argument is transformed to a list
```Python
>>> a=list()
>>> a
[]
>>> b='Hello this~crazy .world!'
>>> b=list(b)
>>> b
['H', 'e', 'l', 'l', 'o', ' ', 't', 'h', 'i', 's', '~', 'c', 'r', 'a', 'z', 'y', ' ', '.', 'w', 'o', 'r', 'l', 'd', '!']
>>> c=(1, 1, 2, 3, 5, 8, 13, 21, 34)
>>> c=list(c)
>>> c
[1, 1, 2, 3, 5, 8, 13, 21, 34]
```

Second, `tuple(iterable)` transforms an iterable item to a tuple. Likewise, see the related functions via `help(tuple)` (see another file in the folder Day8).

Third, `str(object)` transforms the object to a string.

Next, `len(sub)` measures the length of the sub.
```Python
>>> a
[]
>>> len(a)
0
>>> b
['H', 'e', 'l', 'l', 'o', ' ', 't', 'h', 'i', 's', '~', 'c', 'r', 'a', 'z', 'y', ' ', '.', 'w', 'o', 'r', 'l', 'd', '!']
>>> len(b)
24
```
The operators `max()`, `min()` output the maximum, minimum reps. in the given argument.
```Python
#compare the numbers
>>> max(1, 2, 3, 4, 5 )  
5

#compare the strings by their ASCII codes
>>> b
['H', 'e', 'l', 'l', 'o', ' ', 't', 'h', 'i', 's', '~', 'c', 'r', 'a', 'z', 'y', ' ', '.', 'w', 'o', 'r', 'l', 'd', '!']
>>> max(b)
'~'

#max(), min() apply to negative numbers
>>> numbers=[-1, 29, 333, -112, 0, 34]
>>> max(numbers)
333
>>> min(numbers)
-112

#max(), min() apply to the numbers in a string
>>> chars='1234567890'
>>> min(chars)
'0'
>>> max(chars)
'9'

#max(), min() do not apply to a mix of strings and numbers
>>> tuple1=(1, 2, 3, 4, 5, 6, 7, 8, 9, 0)
>>> max(tuple1)
9
>>> numbers.append('m')
>>> numbers
[-1, 29, 333, -112, 0, 34, 'm']
>>> max(numbers)
Traceback (most recent call last):
  File "<pyshell#33>", line 1, in <module>
    max(numbers)
TypeError: '>' not supported between instances of 'str' and 'int'
>>> min(numbers)
Traceback (most recent call last):
  File "<pyshell#34>", line 1, in <module>
    min(numbers)
TypeError: '<' not supported between instances of 'str' and 'int'
```
The logic for `max()` to work is as follows; similarly for `min()`.
```
#begin with the leading element in tuple1
max=tuple1[0]
#then repeat comparisons, re-assign max if necessary
for each in tuple1:
    if each > max:
        max=each
return max
```

The operator `sum(iterable[, start=0])` returns the sum of iterable (a sequence) and start (optional). It only applies to the data of the same type.
```Python
>>> tuple2=(3.1, 2.3, 3.4)
>>> sum(tuple2)
8.8
>>> sum(tuple2, 1)  #3.1 + 2.3 + 3.4 + 1
9.799999999999999 

# sum() does not apply to a mix of string and numbers
>>> numbers
[-1, 29, 333, -112, 0, 34, 'm']
>>> sum(numbers)
Traceback (most recent call last):
  File "<pyshell#39>", line 1, in <module>
    sum(numbers)
TypeError: unsupported operand type(s) for +: 'int' and 'str'
>>> numbers.pop()
'm'
>>> numbers
[-1, 29, 333, -112, 0, 34]
>>> sum(numbers)
283
>>> sum(numbers, 15) #-1 + 29 + 333 + -112 + 0 + 34 + 15
298

#distinct from max() and min(), sum() cannot add a string up, even there are numbers inside
>>> chars
'1234567890'
>>> sum(chars)
Traceback (most recent call last):
  File "<pyshell#46>", line 1, in <module>
    sum(chars)
TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

The operator `sorted(iterable, reverse=False)` creates a new list containing all items from iterable, in ascending order by default
It works similarly to `list.sort()`.
```Python
>>> sorted(numbers)
[-112, -1, 0, 29, 34, 333]
>>> sorted(numbers, reverse=True)
[333, 34, 29, 0, -1, -112]
```
The operator `reversed(sequence)` creates a new list which is a reverse iterator over the values of the given sequence; requires `list()` to transform its result to a list. It works similarly to `list.reverse`.
```Python
>>> reversed(numbers)
<list_reverseiterator object at 0x7f9820f93f10>
>>> list(reversed(numbers))
[34, 0, -112, 333, 29, -1]
```
The operator `enumerate(iterable, start=0)` creates a new list which is an enumerate object; requires `list()` to transform its result to a list.
```Python
>>> enumerate(numbers)
<enumerate object at 0x7f982201f180>
>>> list(enumerate(numbers))
[(0, -1), (1, 29), (2, 333), (3, -112), (4, 0), (5, 34)]
```
The operator `zip(iterable, iterable, ..., iterable)` creates a new list which consists of tuples consisting of given iterables until one of them is exhausted; requires `list()` to transform its result to a list.
```Python
# zip() combines two items
>>> p=[1, 2, 3, 4, 5, 6, 7, 8]
>>> q=[4, 5, 6, 7, 8]
>>> zip(p,q)
<zip object at 0x7f9820fb3340>
>>> list(zip(p,q))
[(1, 4), (2, 5), (3, 6), (4, 7), (5, 8)]

## zip() combines three items
>>> r=[0, 9, 8, 7, 6, 5, 4]
>>> list(zip(p, q, r))
[(1, 4, 0), (2, 5, 9), (3, 6, 8), (4, 7, 7), (5, 8, 6)]
```

## Keys
- Sequences (two definitons)
  - the common properties of lists, tuples and strings
  - related functions
    - `list(iterable), tuple(iterable), str(object)`
    - `len(sub)`
    - `max(), min()`
    - `sum(iterable[, start=0])`
    - `sorted(iterable, reverse=False)`
    - `reversed(sequence)`
    - `enumerate(iterable, start=0)`
    - `zip(iterable, iterable, ..., iterable)`
