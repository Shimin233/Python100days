## The Pickle module
The module of Pickle can store almost everything in the form of binary numbers and permanently(?).

Storing is called 'pickling' and reading 'unpickling'.

```Python
>>> import pickle
>>> my_list = [123, 2.33, 'me', ['another list']]
>>> pickle_file = open('my_list.pklanyext', 'wb') #the extension of the newly created file can be any text: pkl, pklanyext, whateverext, etc; 'wb' means 'writing binary'
>>> pickle.dump(my_list, pickle_file)  #dump the contents into the new file, like making pickle :)
>>> pickle_file.close()
>>> pickle_file = open('my_list.pklanyext', 'rb') #'rb' means 'reading binary'
>>> my_list2 = pickle.load(pickle_file)
>>> print(my_list2)
[123, 2.33, 'me', ['another list']]
```
I can see the file with its path /Users/shiminfu/Documents/my_list.pklanyext.
Pickle can be used to store a large amount of file and read it in one line.
