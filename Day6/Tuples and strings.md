## Tuple元组
A tuple is similar to a list, but the elements of a tuple cannot be altered once it is defined. We shall study tuples through comparing it with lists.

In terms of their forms, a tuple is typed with parentheses, while a list with brackets.
```
tuple1=

tuple1[1]

tuple1[5:]

tuple1[:5]

tuple2=tuple1[:]
tuple2

tuple1[1]=3  #cannot be altered

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

#islower() #if a string contains at least one case-sensitive element and they are all lowercase, then True, else False

#isupper() #if a string has at least one case-sensitive element and all of them are uppercase, then True, else False

#isnumeric() #if a string has only numerics, then True, else False

#isspace() #if a string has only spaces, then True, else False

#istitle() #if a string is titled (starts with an uppercase letter with all the rest lowercase), then True, else False


```



