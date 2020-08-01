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
### Obtain elements from a list
We use index to obtain an elements from a list.
```Python
>>> member[0]
'elles'
>>> member[1]
'tu'
```
Use a temporary variable to swap the positions of two elements.
```
>>> temp=member[0]
>>> member[0]=member[1]
>>> member

>>> member[1]=temp

>>> member

```
 
### Delete elements in a list
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


## Keys
- Add elements to a list
- Obtain elements from a list
