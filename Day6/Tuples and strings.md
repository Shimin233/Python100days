## Tuple元组
A tuple is similar to a list, but the elements of a tuple cannot be altered once it is defined. We shall study tuples through comparing it with lists.

In terms of their forms, a tuple is typed with parentheses, while a list with brackets.
```Python
>>> tuple1=(1, 2, 3, 4, 5, 6, 7, 8)
>>> tuple1
(1, 2, 3, 4, 5, 6, 7, 8)
```
We can also use index to visit an element of a tuple. But tuples do not support item (re)assignment, i.e. cannot be altered, in a general sense.
```Python
>>> tuple1[1]
2
>>> tuple1[5:]
(6, 7, 8)
>>> tuple1[:5]
(1, 2, 3, 4, 5)
>>> tuple2=tuple1[:]
>>> tuple2
(1, 2, 3, 4, 5, 6, 7, 8)
tuple1[1]=3  #cannot be altered
Traceback (most recent call last):
  File "<pyshell#115>", line 1, in <module>
    tuple1[1]=3
TypeError: 'tuple' object does not support item assignment
```
In general, the comma is necessary for Python to recognize a tuple, but not the parentheses. The parentheses matter only for an empty tuple. But lists require both brackets and commas.
```Python
>>> temp=(1)
>>> temp
1
>>> type(temp) #parentheses not nece for a tuple
<class 'int'>
>>> temp2=1,2,3
>>> type(temp2)
<class 'tuple'>
```

```Python
>>> temp=()  # only to empty tuples, parentheses matter
>>> type(temp)
<class 'tuple'>
>>> temp=[]   #empty list
>>> type(temp)
<class 'list'>
```
So there are two ways to type a non-empty tuple.
```Python
>>> type(temp)
<class 'tuple'>
>>> temp=1,
>>> type(temp)
<class 'tuple'>
```
Also, note that commas matter when making copies of tuples.
```Python
>>> 8*(8)  #(8) is an integer
64
>>> 8*8,  #(8*8), = (64,) a tuple
(64,)
>>> 8*(8,)
(8, 8, 8, 8, 8, 8, 8, 8)  #here * acts as repeating the tuple (8, ) 8 times; , matters to a tuple
```

### Slice and update a tuple
We can slice a tuple in order to (indirectly) insert, remove elements of a tuple. We can delete a whole tuple using `del`; but it is rare to use `del` manually, as Python recognizes the (un)availability of a variable.

```Python
>>> temp=('me', 'you', 'she', 'he')
>>> temp=temp[:2]+('they',)+temp[2:] #note the addition + can only apply to items of the same type, here comma necessary to make ('they',) be a tuple
>>> temp
('me', 'you', 'they', 'she', 'he') #update by assigning a new item to temp, thus update temp; here () and, both matter, due to one element here
```
```Python
>>> del temp
>>> temp
Traceback (most recent call last):
  File "<pyshell#28>", line 1, in <module>
    temp
NameError: name 'temp' is not defined 
```
### Operators for tuples
The following operators apply to tuples.
`+` (for items of the same type), `*`
`in` `not in`
`>, <, <=, >=`
`and, or, not`

## Strings字符串
### Slice and update a string
Slicing applies to strings, as it does to lists and tuples.
```Python
>>> str1='Hello world'
>>> str1[:6]
'Hello '
```
Also, picking element by index is applicable to strings. You may notice the similarity between index and slicing in terms of forms (brackets).
```Python
>>> str1
'Hello world'
>>> str1[5]
' '
>>> str1[6]
'w'
```

We cannot directly alter a string, like a tuple. However, we can slice a string to indirectly update it, which is actually creating a new copy of string and then re-assigning this new copy to the old variable.
```Python
>>> str1[:6]+'string inserted'+str1[6:]
'Hello string insertedworld'
>>> str1
'Hello world'  #without reassignment, the originl str1 remains the same
>>> str1=str1[:6]+'string inserted'+str1[6:]
>>> str1
'Hello string insertedworld'
```
### Operators for strings
The operators `in` and `not in` apply to string like they do to lists and tuples.

Let's introduce more operators applicable to strings. 
- Lower/uppercase
  - `capitalize()` returns a new string by changing the first letter in a string to uppercase
```Python
>>> str2='miao'
>>> str2.capitalize() 
'Miao'
```
  - `casefold()` returns a new string by changing all the letters in a string to lowercase
```Python
>>> str2='MiAomIaO'
>>> str2.casefold()
'miaomiao'
```
  - `swapcase()` swaps upper/lowercase of the whole string
  
  - `islower()` if a string contains at least one case-sensitive element and they are all lowercase, then True, else False; for non-Latin letters, like Chinese, it returns False since they have nothing to do with lower/uppercase
  
  - `isupper()` if a string has at least one case-sensitive element and all of them are uppercase, then True, else False

- Position of the whole string
  - `center(width)` creates a new string via putting the string in the middle and using spaces to fill with the specified width
 ```Python
>>> str2
'MiAomIaO'
>>> str2.center(40)
'                MiAomIaO                '

>>> str2.center(19)
'      MiAomIaO     '
 ```
  - `count(sub[,start[,end]])` returns the number of appearences of sub (substring), in the range between start and end (optional)
```Python
>>> str2
'MiAomIaO'
>>> str2.count('mi')
0
>>> str2.count('mI')
1
```

- Contents, their formats and their positions
  - `encode(encoding='utf-8',errors='strict')` uses the method set by 'encoding=' to encode the specified strings (to be explained later)

  - `isalnum()` if a string has at least one element and all of them are numerics or letters, then True, else False; isalnum() = isalpha() + isnumeric()

  - `isalpha()` if a string has at least one element and all of them are letters, then True, else False

  - `isdecimal()` if a string has only decimal (system) numbers then True, else False

  - `isdigit()` if a string has only numbers then True, else False

  - `isnumeric()` if a string has only numerics, then True, else False

  - `isspace()` if a string has only spaces, then True, else False
  
  - `istitle()` if a string is titled (starts with an uppercase letter with the first letter behind each space is capital), then True, else False
```Python
>>> str5='Hello World'
>>> str5.istitle()
True
>>> str5='Hello world'
>>> str5.istitle()
False
>>> str5='If The First Letter Behind Each Space Is Capital, Then It Is Titled?'
>>> str5.istitle()
True
```

  - `endswith(sub[,start[,end]])` tells whether a string ends with sub, in the range btw start and end (optional); if yes then True, else False
```Python
>>> str2
'MiAomIaO'
>>> str2.endswith('io')
False
>>> str2.endswith('ao')
False
>>> str2.endswith('aO')
True
```
  - `startswith(prefix[,start[,end]])` tells whether the string starts with prefix(substring) in the range btw start and end (optional), if yes then True, else False

  - `expandtabs([tabsize=8])` replaces the tabs(\t) with spaces; if the item is not specified, the number of spaces is 8 by default
```Python
>>> str3='hello\tworld'
>>> str3
'hello\tworld'
>>> print(str3)
hello	world
>>> str3.expandtabs()
'hello   world'
#there are 7 (mine is 3) spaces between hello and world, since 8 spaces include the position of o
```
  - `find(sub[,start[,end]])` tells whether sub is in a string, in the range btw start and end (optional); if yes return its index (the index of the first letter of sub by default), else return -1
```Python
>>> str3
'hello\tworld'
>>> str3.find('ere')
-1
>>> str3.find('two')
-1    #obviously \t is recognized as one item and the 't' is not a letter
>>> str3.find('rld')
8     #begin with h as the 0-th, \t as one (5-th) item, r is the 8-th
```
  - `rfind(sub[,start[,end]])` is like find(), but from the right

  - `index(sub[,start[,end]])` is almost the same as find(sub), but if sub is not in the string then return an error
```Python
>>> str3.index('ere')
Traceback (most recent call last):
  File "<pyshell#67>", line 1, in <module>
    str3.index('ere')
ValueError: substring not found
```
  - `rindex(sub[,start[,end]])` is like index(), but from the right


- Alter the string
  - `join(sub)` inserts the string as separators between the elements of sub
```Python
>>> str5.join('12345')
'1A title in general2A title in general3A title in general4A title in general5'
```

  - `ljust(width)` returns a new string via left-aligning the string and fill spaces with width specified

  - `rjust(width)` returns a new string via right-aligning the string and filling spaces with width specified

  - `lower()` lowercases all the letters in a string

  - `upper()` uppercases all the letters in a string

  - `istrip()` removes all the spaces on the left of the string

  - `rstip()` deletes the spaces at the end of the string

  - `strip([chars])` deletes all the spaces in front of and behind the string, chars can be set to specify the strings to be deleted (optional)
```Python
>>> str7='    ssssslllll    '
>>> str7.strip()
'ssssslllll'
>>> str7=str7.strip()
>>> str7
'ssssslllll'
>>> str7.strip('s')
'lllll'
```
  - `replace(old,new[,count])` replaces old in a string with new; if specified using count, then replacement is made no more than count times
  
  - `partition(sub)` finds the sub, separate the string into a 3-element tuple (pre_sub, sub, fol_sub); if sub cannot be found, return ('originlstring', '', '')

  - `rpartition(sub)` is like partition(), but from the right

  - `split(sep=None, maxsplit=-1)` returns a list consisting the substrings splitted with respect to spaces, by default; if the maxsplit is set, returns a list consisting the substrings splitted into the number of maxsplit

  - `splitlines(([keepends))]` returns a list consisting of the substrings splitted with respect to \n; if the keepends is set, returns a list consisting of the first keepends(number) lines

  - `title()` returns a titled string

  - `translate(table)` translates the string according to the rules of table (can be specified by str.maketrans('a', 'b'))
```Python
>>> str7.translate(str.maketrans('s', 'a'))
'aaaaalllll'
>>> str.maketrans('s', 'a')
{115: 97}    #the ASCLL codes of s and a
```
  - `zfill(width)` returns a string of length=width, right-align the original string and fill the left with 0


## Keys
- Tuple
  - Slice and update a tuple
  - Operators for tuples
- String
  - Slice and update a string
  - Operators for strings, 3 categories: 
  1. Lower/uppercase, Contents, their formats and their positions, andAlter the string
