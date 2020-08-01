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
['tu', 'elles', 'Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je', 'il', 'ils', 'elle']
>>> member[1:3]
['elles', 'Me']
>>> member #the original list remains intact; slicing creates new copies as required
['tu', 'elles', 'Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je', 'il', 'ils', 'elle']
>>> member[:3]
['tu', 'elles', 'Me']
>>> member[1:]
['elles', 'Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je', 'il', 'ils', 'elle']
>>> member[:]
['tu', 'elles', 'Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je', 'il', 'ils', 'elle']
>>> member2=member[:] 
>>> member2  #can create a copy of list using the slice
['tu', 'elles', 'Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je', 'il', 'ils', 'elle']
```

### Operators for lists
We can compare two lists. By default, camparison is made between the number 0 (leading) element of the two lists. Lists' comparison compares strings via ASCLL codes.
```Python
>>> list1=[123]
>>> list2=[234]
>>> list1 > list2
False
>>> list1=[123, 456]
>>> list2=[234, 123]
>>> list1 > list2  
False
>>> list3=[123, 456]
>>> (list1 < list2) and (list1 == list3)  #True and True
True
```
We can also combine two lists by 'addition'. 
```Python
>>> list4= list1 + list2
>>> list4
[123, 456, 234, 123]
```
It seems similar to combination of strings, but closer to extending lists. This means 'addition' can only be between two items of the same type. For example, `list1 + 'Me'` is not allowed; and they both allow the duplication of elements while preserving the order of elements. 

The operators `+=`, `*=` and others simplify updates of the lists as they do to numerial calculations.
```Python
>>> list3*3
[123, 456, 123, 456, 123, 456]
>>> list3
[123, 456]   #list3 itself remains intact after multiplicaton
>>> list3 *= 3
>>> list3
[123, 456, 123, 456, 123, 456]  #three copies of list3 is assigned to itself
```
Use `in`, `not in` to see whether an element is inside a list. 
```Python
>>> list3
[123, 456, 123, 456, 123, 456]
>>> 123 in list3
True
>>> 456 not in list 3
False
```
Also, we should note the statement structure in terms of specifying some element's position.
```Python
>>> list5=[23, ['me', 'il'], 72]
>>> 'me' in list5
False    
>>> 'me' in list5[1]
True            #'me' is in the list which is the number 1 element in the whole list, but not an element of the whole list itself
>>> list5[1][1]
'il'    #we can specify the number 1 element of the list which is the number 1 element in the whole list, by writing positons twice
```
### BIFs for lists
You can check the BIFs applicable to lists like below.
```Python
>>> dir(list)
['__add__', '__class__', '__contains__', '__delattr__', '__delitem__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__gt__', '__hash__', '__iadd__', '__imul__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__rmul__', '__setattr__', '__setitem__', '__sizeof__', '__str__', '__subclasshook__', 'append', 'clear', 'copy', 'count', 'extend', 'index', 'insert', 'pop', 'remove', 'reverse', 'sort']
```
For exmaple, `count()` is used to count the number of appearances of some element in a list; `index()` is used to find the exact position (like, number 9 position) of some element in a list.
```Python
>>> list3
[123, 456, 123, 456, 123, 456]
>>> list3.count(123)
3
>>> list3.index(123)
0           #by default, only the first position to appear
>>> list3.index(123, 3, 6) #specify the range of positions to be from 3 to 6 (6 can be replace by arbitrary large number, even more than the actual length of this list      
4
>>> list3.index(123, 1, 6) #specify the range of positions to be from 1 to 6   
2   # by default, output the first appearance in the specified range
```
Moreover, `reverse()` is used to reverse the order of elements of the whole list; `sort()` is used to reorder the elements of a list (by default, from smallest to largest, i.e. ascendingly). The default form is `sort(func, key=None, reverse=False)`.
```Python
>>> list6=[4, 2, 5, 1, 9, 23, 32, 0]
>>> list6.reverse()
>>> list6
[0, 32, 23, 9, 1, 5, 2, 4]
>>> list6.sort()  #sort(func, key, reverse) is the structure of sort function; sort() reorders elements from smallest to largest, by default
>>> list6
[0, 1, 2, 4, 5, 9, 23, 32]
>>> list6.reverse() #reverse after sorting = reorder elements descendingly; or via the following method
>>> list6
[32, 23, 9, 5, 4, 2, 1, 0]
>>> list6.sort(reverse=True) #another method to reorder descendingly; here 'reverse' is a variable in sort()
>>> list6
[32, 23, 9, 5, 4, 2, 1, 0]
```
Remark, the difference between two methods can be revealed by making changes. The assignment of list6 to list8, leads to that list6 and list8 actually mean the same list, and thus results in the simultaneous changes of them two. But the list7 is created by slices, which makes a copy independent of the original list6. So, to avoid the changes to be copied in other lists, it is recommended to use slices to create a copy of a list.
```Python
>>> list7=list6[:]
>>> list7
[32, 23, 9, 5, 4, 2, 1, 0]
>>> list8=list6
>>> list8
[32, 23, 9, 5, 4, 2, 1, 0]
>>> list6.sort()
>>> list6
[0, 1, 2, 4, 5, 9, 23, 32]
>>> list7 #remains the same, not vary with list6
[32, 23, 9, 5, 4, 2, 1, 0]
>>> list8 #varies together with list6, since list8 comes from assignment of value of list6
[0, 1, 2, 4, 5, 9, 23, 32]
```



## Keys
- Add elements to a list
- Obtain elements from a list
- Delete elements in a list
- Slice
- Operators for lists
  - `+`, `*`, and `+=`, `*=`, etc.
  - `in`, `not in`
- BIFs 
  - `count()`, `index()`, `reverse()` and `sort()`
  - differences between two methods to copying a list: slicing and assignment 
