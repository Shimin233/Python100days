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

## Update a tuple
We can slice a tuple in order to insert, remove elements of a tuple. We can delete a whole tuple using `del`; but it is rare to use `del`, as Python recognizes the (un)availability of a variable.
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

## Strings



