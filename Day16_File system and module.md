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

Generally, the methods to visit file systems vary among various operation systems (macOS, Windows, Linux, UNIX, etc.). So we have to choose the modules of file systems according to operation systems, and have to rewrite large amounts of codes to deal with such a change. However, as an inter-system programming language, Python has the module 'OS', which automatically chooses and uses the correct module for us. Let us go through the functions contained in the OS module.

The functions in the os module
|Function|    How to use it    |
|--------|------------------|
|getcwd()|return the current working directory当前工作目录|
|chdir(path)|change the working directory|
|listdir(path='.')|list the file names in the specified directory/path, where '.' is the current directory, '..' is the upper-level directory|
|mkdir(path)|create a single-layer directory单层目录（？）, report an error if it exists|
|makedirs(path)| create iterably a multi-layer directory多层目录（？）, report an error if it exists, note that no conflicts between `'E:\\a\\b'` and `'E:\\a\\c'`|
|remove(path)|remove the file|
|rmdir(path)|remove a single-layer directory, report an error if it is nonempty|
|removedirs(path)|remove iterably a directory, from sub-directories to super-directories, report an error if some directory is nonempty|
|rename(old, new)|rename the file from old to new|
|system(command)|operate the 'shell' command of the system|
|os.curdir|refer to the current directory ('.')|
|os.pardir|refer to the previous(last) directory ('..')|
|os.sep|output the separator路径分隔符（？）specific to the operation system ('\\' for Windows, '\' for Linux)|
|os.linesep|the ?行终止符 use by current operation system ('\r\n' for Windows, '\n' for Linux)|
|os.name|refer to the operation system currently used (incl. 'posix', 'nt', 'mac', 'os2', 'ce', 'java')|

The functions in the os.path module
|Function|     How to use it        |
|--------|------------------|
|basename(path)|remove the file path, only return the file name|
|dirname(path)|remove the file name, only return the directory path|
|join(path1\[, path2\[, ...]])|combine the path1, path2, ... into one path name|



