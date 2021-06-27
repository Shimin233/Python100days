## Exception and error

- AssertionError: a fact (assertion) believed by the programmer (you, the one writing the codes) is actually impossible
#### Example (a claim that is actually wrong)
```Python
>>> list1=[5, 4, 'hi']
>>> list1
[5, 4, 'hi']
>>> assert len(list1)>2 #this assertion is indeed true
>>> list1.pop()
'hi'
>>> list1
[5, 4]
>>> assert len(list1)>2 #now this assertion is false
Traceback (most recent call last):
  File "<pyshell#6>", line 1, in <module>
    assert len(list1)>2
AssertionError
```

- AttributeError: there exists a non-existing or undefined attribute, i.e. property/function/command
#### Example (undefined property)
```Python
>>> list1.great
Traceback (most recent call last):
  File "<pyshell#8>", line 1, in <module>
    list1.great
AttributeError: 'list' object has no attribute 'great'
```

- EOFError: Input() reads EOF (end-of-file, a condition in a computer operating system where no more data can be read from a data source, where the data source is usually called a file or stream) but not receive any data 
- 
- FileNotFoundError
#### Example (opening a file without extension)

```Python
file_name = input('Please insert the file you want to open: ')
f=open(file_name)
print('The contents of this file are: ')
for each_line in f:
    print(each_line)
```
Assume we are going to open the file of `ReadMe.rtf`. If only inserting `ReadMe`, then it reuturns a `FileNotFoundError`; to avoid such error, an extension is necessay, so type `ReadMe.rtf`. 

- FloatingPointError: error in floating computation

- GeneratorExit: generator.close()

- ImportError

- IndexError: the index specified is out of the available range ("out of range")

- KeyError: similarly to IndexError, but particularly for keys out of range for a dictionary

- KeyboardInterrupt: when the programmer (you) manually stops the process by Command + C, or Ctrl + C

- MemoryError

- NameError: when visiting a non-existing variable

- NotImplementedError

- OSError: the error happening to the operation system, e.g. opening a non-existing file

- OverflowError

- ReferenceError: weak reference is trying to visit an item that has been put in rubbish bin

- SyntaxError

- TypeError: improper mixing use of different types of data

- ZeroDivisionError: when zero occurs improperly as the denominator, like inputting `5/0`


Another source of exceptions and errors:[docs.python](https://docs.python.org/3/library/exceptions.html#exception-hierarchy)


