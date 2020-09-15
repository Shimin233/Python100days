## Module
A __module__ is a file containing a bunch of functions and variables, named as '.py'. A module can be imported by other programs 
so that we can use the contents inside.

```Python
#importing the module 'random' is necessary to use its contents
>>> secret = random.randint(1, 10)
Traceback (most recent call last):
  File "<pyshell#1>", line 1, in <module>
    secret = random.randint(1, 10)
NameError: name 'random' is not defined
>>> import random
>>> secret = random.randint(1, 10)
>>> secret
1
```
