## List
A list is a collection of integers, floats, strings and/or other items (like the planes in our second game); even lists can be the elements of another list. A list can be empty, too.

See the examples of a list.
```Python
>>> member=[

>>> mix=[1, 'me', 2.18, [1, 2, 3], 'right'] 
>>> empty=[]
```

To add one element to a list, we use `append()`, which acts on one item; to add multiple elements to a list, we use `extend`, though `extend` itself is a function acting on one item.
```
>>> member.append('il')
>>> member

>>> len(member)
9
>>> member.extend(['ils', 'elle'])
>>> member
```

To add one element and specify its position, we use `insert`, which acts on two items: the first is its position counted from left to right (0, 1, 2, ...) and the second is the new element.
```Python
>>> member,insert(0, 'elles')
>>> member

>>> member.insert(1, 'tu')
>>> member
```
