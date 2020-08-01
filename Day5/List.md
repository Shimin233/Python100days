## List
A list is a collection of integers, floats, strings and/or other items (like the planes in our second game); even lists can be the elements of another list. A list can be empty, too.

See the examples of a list.
```Python
>>> member=['Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je']
>>> mix=[1, 'me', 2.18, [1, 2, 3], 'right'] 
>>> empty=[]
```
### Add elements to a list
To add one element to a list, we use `append()`, which acts on one item; to add multiple elements to a list, we use `extend`, though `extend` itself is a function acting on one item.
```Python
>>> member.append('il')
>>> member
['Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je', 'il']
>>> len(member)
9
>>> member.extend(['ils', 'elle'])
>>> member
['Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je', 'il', 'ils', 'elle']
```

To add one element and specify its position, we use `insert`, which acts on two items: the first is its position counted from left to right (0, 1, 2, ...) and the second is the new element.
```Python
>>> member,insert(0, 'elles')
>>> member
['elles', 'Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je', 'il', 'ils', 'elle']
>>> member.insert(1, 'tu')
>>> member
['elles', 'tu', 'Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je', 'il', 'ils', 'elle']
```
### Obtain an element from a list
We use index to obtain an elements from a list.
```Python
>>> member[0]
'elles'
>>> member[1]
'tu'
```
Use a temporary variable to swap the positions of two elements.
```
>>> temp=member[0]  #store 'elles' in temp
>>> member[0]=member[1] #assign 'tu' to the original position of 'elles'
>>> member
['tu', 'tu', 'Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je', 'il', 'ils', 'elle']
>>> member[1]=temp #put 'elles back to the list
>>> member
['tu', 'elles', 'Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je', 'il', 'ils', 'elle']
```
 
### Delete an element in a list
To remove an element, we use `remove()` by specifying the contents of that element; `del` by specifying the position of it; and `pop()` returning its value while simultaneously removing the last element (by default) in the list.

```Python
>>> member.remove('ils')
>>> member
['elles', 'tu', 'Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je', 'il', 'elle']
>>> del member[1]
>>> member
['elles', 'Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je', 'il', 'elle']
```
```Python
>>> mix=[1, 'me', 2.18, [1,2,3], 'right']
>> mix.pop()
'right'

>>> mix
[1, 'me', 2.18, [1, 2, 3]]
>> mix2=[2, 'you', 'hi']
>>> mix2.pop()
'hi'
>>> mix2
[2, 'you']
```
We can also specify the position to remove a certain element.
```Python
>> mix.pop(3)
[1, 2, 3]
>>> mix
[1, 'me', 2.18]
```

### Slice to obtain multiple elements
We can create a copy which is a slice of the list by inputting the starting (by default 0; included in the slice) and the ending psoition (by default, after the ending element; excl.).
```Python
>>> member

>>> member[1:3]

>>> member #the original list remains intact

>>> member[:3]

>>> member[1:]

>>> member[:]

>>> member2=member[:] 
>>> member2  #can create a copy of list using the slice

```

### Operators for lists
We can compare two lists.
```Python
>>> list1=[123]
>>> list2=[234]
>>> list1 > list2
False
>>> list1=[123, 456]
>>> list2=[234, 123]
>>> list1 > list2  #by default, camparison is between the number 0 element of the two lists
False
>>> list3=[123, 456]
>>> (list1 < list2) and (list1 == list3)  #True and True
True
>>> 

```
Lists' comparison compares strings via ASCLL codes.


## Keys
- Add elements to a list
- Obtain elements from a list
- Delete elements in a list
- Slice
