## Exception and error: some of them

- AssertionError: a fact (assertion) believed by the programmer (you, the one writing the codes) is actually impossible
  - Example (a claim that is actually wrong)
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
  - Example (undefined property)
```Python
>>> list1.great
Traceback (most recent call last):
  File "<pyshell#8>", line 1, in <module>
    list1.great
AttributeError: 'list' object has no attribute 'great'
```

- EOFError: Input() reads EOF (end-of-file, a condition in a computer operating system where no more data can be read from a data source, where the data source is usually called a file or stream) but not receive any data 

- FloatingPointError: error in floating computation

- GeneratorExit: generator.close()

- ImportError

- IndexError: the index specified is out of the available range ("out of range")
  - Example (index not available)
```Python
>>> list1[5]
Traceback (most recent call last):
  File "<pyshell#9>", line 1, in <module>
    list1[5]
IndexError: list index out of range
```

- KeyError: similarly to IndexError, but particularly for keys out of range for a dictionary
  - Example (key not available)
```Python
>>> dict1={1:10, 'key': ' content'}
>>> dict1[2]
Traceback (most recent call last):
  File "<pyshell#11>", line 1, in <module>
    dict1[2]
KeyError: 2
```
- KeyboardInterrupt: when the programmer (you) manually stops the process by Command + C, or Ctrl + C

- MemoryError

- NameError: when visiting a non-existing variable
```Python
>>> undefinedName
Traceback (most recent call last):
  File "<pyshell#12>", line 1, in <module>
    undefinedName
NameError: name 'undefinedName' is not defined
```
- NotImplementedError

- OSError: the error happening to the operation system, e.g. opening a non-existing file
  - Almost the same as IOError, so it suffices to stick with OSError, as suggested in [the top answer here](https://stackoverflow.com/questions/29347790/difference-between-ioerror-and-oserror)
  - FileNotFoundError
    - Example (opening a file without extension)

```Python
file_name = input('Please insert the file you want to open: ')
f=open(file_name)
print('The contents of this file are: ')
for each_line in f:
    print(each_line)
```
Assume we are going to open the file of `ReadMe.rtf`. If only inserting `ReadMe`, then it reuturns a `FileNotFoundError`; to avoid such error, an extension is necessay, so type `ReadMe.rtf`. 
- OverflowError

- ReferenceError: weak reference is trying to visit an item that has been put in rubbish bin

- SyntaxError
  - Example (wrong writing style)
```Python
>>> print 'syntax' #the old-version Python2 writing syntax
SyntaxError: Missing parentheses in call to 'print'. Did you mean print('syntac')?
>>> print('syntax')
syntax

```

- TypeError: improper mixing use of different types of data
  - Example (mixing numbers and strings)
```Python
>>> 2+'5'
Traceback (most recent call last):
  File "<pyshell#15>", line 1, in <module>
    2+'5'
    TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

- ZeroDivisionError: when zero occurs improperly as the denominator, like inputting `5/0`


Another source of exceptions and errors:[docs.python](https://docs.python.org/3/library/exceptions.html#exception-hierarchy)

## Deal with exceptions: 3 ways

### Try-except
You may type in the module the 'try-except' of the following format, to specify what to do when an exception occurs:
```Python
try:
  range to check
except Exception [as reason]: 
  what to do if finding an Exception
```
Let us see an example of OSError. Type the following in the module,
```Python
try: 
  f= open('Non-existingFile.txt')
  print(f.read())
  f.close() #these three lines from above make a scenario of OSError, since the file does not exist
except OSError: 
  print('This file does not exist') #whe detecting an OSError, we want to print this word
```  
Run it and you will see the 'This file does not exist' printed in the shell.
This shows one of the aims to use try-except: providing a straightforward expression of error. We can improve it by adding the exact reason of error.
```Python  
try:
  f= open('Non-existingFile.txt')
  print(f.read())
  f.close()
except OSError as reason: #note this is necessary to type 'as reason', in order to quoted below by str(reason)
  print('This file does not exist\nThe reason of error is:' + str(reason))
```  
Run it and you will see: 	
```Python
This file does not exist
The reason of error is:[Errno 2] No such file or directory: 'Non-existingFile.txt'
```

Furthermore, we can deal with _multiple exceptions_ in one single 'try-except', but an exception with dealing measures unspecified will still 
cause the default form of error reporting. Again type in the module: 
```Python
try:
   int('abc') #ValueError; with no dealing measure specified
   sum=1 +'1' #TypeError; with a dealing measure specified below
   f= open('Non-existingFile.txt')
   print(f.read())
   f.close()
except OSError as reason:
  print('This file does not exist\nThe reason of error is:' + str(reason))
except TypeError as reason:  
  print('The types do not work\nThe reason of error is:' + str(reason))
```
Alternatively, we can combine exceptions with the same dealing meausres:
```Python
try:
   int('abc') #ValueError; with no dealing measure specified
   sum=1 +'1' #TypeError; with a dealing measure specified below
   f= open('Non-existingFile.txt')
   print(f.read())
   f.close()
except (OSError, TypeError) as reason:
  print('This does not work\nThe reason of error is:' + str(reason))
```

Also, we may not make differences between different exception types at all, and define the dealing measure all togethor, like the following:
```Python
try:
   int('abc') #ValueError
   sum=1 +'1'
   f= open('Non-existingFile.txt')
   print(f.read())
   f.close()
except: #regardless of which exception occurring, the following measure is conducted
  print('This file does not exist\nThe reason of error is:' + str(reason))
```
But it is _not recommended_; e.g. Command+C will also result in this but not, as desired, stopping the process.   


### Try-except-finally
Sometimes we want to conduct something no matter we deal with an exception or not, like closing a file so as to save the contents back in it after retrieving its contents to read and write. The codes we use is called try-except-finally, or try-finally, of this format:
```Python
try: 
  range to check
except Exception [as reason]:
  what to do if finding an exception
finally:
  the codes that will be conducted regardless of the situation
```  
For example, maybe f.close() is not conducted yet when an error occurs; we want the file closed so as to save the contents back in it.
```Python  
try:
  f=open('File', 'w')
  print(f.write('here i am'))
  sum=1 + '1' #the file is not closed yet, when detecting this TypeError and conducting its dealing measure
  f.close()
except (OSError, TypeError):
  print('This does not work')
finally:
  f.close() #we want to close the file anyway
```  
so that the file will be saved finally.
  

### Raise
We may induce an exception via raising one. The following codes can be typed directly in the shell.

First, the simple `raise` can induce an error like below.
```Python
>>> raise
Traceback (most recent call last):
  File "<pyshell#33>", line 1, in <module>
    raise
RuntimeError: No active exception to reraise
```

We can raise a ZeroDivisionError using raise: 
```Python
#the common scenario for this error to occur is this
>>> 4/0
Traceback (most recent call last):
  File "<pyshell#34>", line 1, in <module>
    4/0
ZeroDivisionError: division by zero

#now raise this error manually
>>> raise ZeroDivisionError
Traceback (most recent call last):
  File "<pyshell#35>", line 1, in <module>
    raise ZeroDivisionError
ZeroDivisionError

#can also raise other types of error
>>> raise TypeError
Traceback (most recent call last):
  File "<pyshell#36>", line 1, in <module>
    raise TypeError
TypeError
```
Furthermore, we can manually add words to explain the reason of error here, like we did in try-except and try-finally codes above.
```Python
>>> raise ZeroDivisionError('The denominator is zero')
Traceback (most recent call last):
  File "<pyshell#37>", line 1, in <module>
    raise ZeroDivisionError('The denominator is zero')
ZeroDivisionError: The denominator is zero #the explanation is added here
```

## Summary
- Exceptions and errors
  - AttributeError, AssertionError
  - TypeError, OSError, ZeroDivisionError
  - IndexError, KeyError
- Dealing with exceptions in 3 ways
  - try-except
  - try-except-finally
  - raise
