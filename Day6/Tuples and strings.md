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
In general, the comma is necessary for Python to recognize a tuple, but not the parentheses. The parentheses matter only for an empty tuple.
```Python
temp=(1)
temp
type(temp) #parentheses not nece for a tuple

temp2=

type(temp2)  #, matters

temp=()
type(temp)# only when empty, parentheses matter

temp=(1,)
type(temp)

temp=1,
type(temp)

8*(8)
64
8*(8,)  #here * acts as repeating the tuple (8, ) 8 times; , matters to a tuple


```

### Update a tuple indirectly
We can slice a tuple in order to (indirectly) insert, remove elements of a tuple. We can delete a whole tuple using `del`; but it is rare to use `del`, as Python recognizes the (un)availability of a variable.
```
temp=('me', 'you', 'she', 'he')
temp=temp[:2]+('they',)+temp[2:] #update by assigning a new item to temp, thus update temp; here () and, both matter, due to one element here
temp

del temp
temp #not defined

```
The following operators apply to tuples.
+ (same type), *
`in` `not in`
`>, <, <=, >=`
`and, or, not`

## Strings字符串
### Slicing strings
Slicing applies to strings, as it does to lists and tuples.
```
str1='Hello world'
str1[:6]

```

```
str1
str1[5]

str1[6]
```

It is usually hard to alter a string, like a tuple. However, we can slice a string to indirectly update it, which is actually creating a new copy of string and then re-assigning this new copy to the old variable.

```
str1[:6]+'string inserted'+str1[6:]

str1

str1=str1[:6]+'string inserted'+str1[6:]
str1

```
### Operators for strings
The operators `in` and `not in` apply to string like they do to lists and tuples.

```
str2='miao'
str2.capitalize() #capitalize() #return a new string by changing the first letter in a string to uppercase
'Miao'
```

```
str2='MiAomIaO'
str2.casefold() #casefold() #return a new string by changing all the letters in a string to lowercase
'miaomiao'
```

```
str2
str2.center(40) #center(width)#create a new string via putting the string in the middle and using spaces to fill with the specified width

str2.count(mi) #count(sub[,start[,end]]) #return the number of appearences of sub (substring), in the range between start and end (optional)

#encode(encoding='utf-8',errors='strict') #use the method set by 'encoding=' to encode the specified strings

str2.endswith('ao')#endswith(sub[,start[,end]]) #tell whether a string ends with sub, in the range btw start and end (optional); if yes then True, else False
str2.endswith('io')

str3='hello\tworld'
str3.expandtabs()#expandtabs([tabsize=8]) #replace the tabs(\t) with spaces; if the item is not specified, the number of spaces is 8 by default
hello       world #there are 7 spaces between hello and world, since 8 spaces include the position of o

str3.find('ere') #find(sub[,start[,end]]) #tell whether sub is in a string, in the range btw start and end (optional); if yes return its index (the index of the first letter of sub by default), else return -1
str3.find('iao')

str3.index('ere') #index(sub[,start[,end]]) #same as find(sub), but if sub is not in the string then return an error

#isalnum() #if a string has at least one element and all of them are numerics or letters, then True, else False; isalnum() = isalpha() + isnumeric()

#isalpha() #if a string has at least one element and all of them are letters, then True, else False

#isdecimal() #if a string has only decimal (system) numbers then True, else False

#isdigit() #if a string has only numbers then True, else False

#islower() #if a string contains at least one case-sensitive element and they are all lowercase, then True, else False; for non-Latin letters, like Chinese, it returns False since they have nothing to do with lower/uppercase

#isupper() #if a string has at least one case-sensitive element and all of them are uppercase, then True, else False

#isnumeric() #if a string has only numerics, then True, else False

#isspace() #if a string has only spaces, then True, else False

#istitle() #if a string is titled (starts with an uppercase letter with all the rest lowercase), then True, else False
str5='Hello World'
str5.istitle()
False
str5='Hello world'
str5.istitle()
False

#join(sub) #insert the string as separators between the elements of sub
str5.join('12345')

#ljust(width) #return a new string via left-aligning the string and fill spaces with width specified

#lower() #lowercase all the letters in a string

#upper() #uppercase all the letters in a string

#istrip() #remove all the spaces on the left of the string

#partition(sub) #find the sub, separate the string into a 3-element tuple (pre_sub, sub, fol_sub); if sub cannot be found, return ('originlstring', '', '')

#replace(old,new[,count]) #replace old in a string with new; if specified using count, then replacement is made no more than count times.

#rfind(sub[,start[,end]]) #like find(), but from the right

#rindex(sub[,start[,end]]) #like index(), but from the right

#rjust(width) #return a new string via right-aligning the string and filling spaces with width specified

#rpartition(sub) #like partition(), but from the right

#rstip() #delete the spaces at the end of the string

#split(sep=None, maxsplit=-1) #

#splitlines(([keepends))]

#startswith(prefic[,start[,end]])

#strip([chars])
str7='    ssssslllll    '
str7.strip()

str7=str7.strip
str7

str7.strip('s')


#swapcase() #swap upper/lowercase of the whole string

#title() #return a titled string

#translate(table) #translate the string according to the rules of table (can be specified by str.maketrans('a', 'b'))
str7
str7.translate(str.maketrans('s', 'a'))

str.maketrans('s', 'a')
#the ASCLL codes of s and a

#zfill(width) #return a string of length=width, right-align the original string and fill the left with 0

```


## Keys
- Tuple
  - Operators for tuples
- String
  - Operators for strings
