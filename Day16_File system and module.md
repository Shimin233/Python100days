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

### The functions in the os module
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

First we test some of the codes in the os module.
```Python
>> import os
>>> os.getcwd()
'/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day15'
>>> os.chdir('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16')
>>> os.getcwd()
'/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16'
>>> os.listdir('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days')
['Day4', 'Day3', '.DS_Store', 'PythonCheatSheets', 'Day2', 'Day12', 'Day15', 'Day13', 'hello', 'Day16', 'Day10']
>>> os.mkdir('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test') #create a new folder Test in Day16
>>> os.mkdir('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test/Test2') #create a new folder Test2 in Test
>>> os.mkdir('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test3/Test2')
Traceback (most recent call last):
  File "<pyshell#20>", line 1, in <module>
    os.mkdir('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test3/Test2')
FileNotFoundError: [Errno 2] No such file or directory: '/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test3/Test2'
#the folder Test3 does not exist, thus an error
```
Create a file, testtesttest.txt (note on mac it may appear without '.txt') in the folder Test2. We can see it is necessary to delete the file before deleting the folder Test2.
```Python
>>> os.rmdir('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test/Test2')
Traceback (most recent call last):
  File "<pyshell#21>", line 1, in <module>
    os.rmdir('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test/Test2')
OSError: [Errno 66] Directory not empty: '/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test/Test2'
>>> os.remove('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test/Test2/testtesttest.txt') 
>>> os.rmdir('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test/Test2')
```
Test some of them on my mac:
```Python
>>> os.curdir
'.'
>>> os.listdir('.')
['.DS_Store', 'Test']
>>> os.listdir(os.curdir)
['.DS_Store', 'Test']
>>> os.sep
'/'
>>> os.linesep
'\n'
>>> os.name
'posix'
>>> 
```
TBC:need exmaples for makedirs(path) and rmdirs(path)

TBC: need shell commands on mac to give examples of os.system(command), I have tried:
```Python
>>> os.system('cmd')
32512 #only number outputted but nothing else (no new windows)
>>> os.system('command')
0
>>> os.system('terminal')
32512
```

### The functions in the os.path module
|Function|     How to use it        |
|--------|------------------|
|basename(path)|remove the file path, only return the file name|
|dirname(path)|remove the file name, only return the directory path|
|join(path1\[, path2\[, ...]])|combine the path1, path2, ... into one path name|
|split(path)|split the file name from the path, return a tuple (f_path, f_name); even inputting a directory (i.e.the last part is a folder not file) or the file doesn't exist, it returns the last part as if it's file name|
|splitext(path)|split the file name and the extension扩展名, return a tuple (f_name, f_extension)|
|getsize(file)|return the size of the file, in bytes|
|getatime(file)|return the time of the most recent visit in a float in seconds, can convert it further by `gmtime()`(Greenwich mean time) or `localtime()`(local time zone) in the `time` module|
|getctime(file)|return the time of creation in a float in seconds, can convert it further by `gmtime()` or `localtime()` in the `time` module|
|getmtime(file)|return the time of the most recent modification in a float in seconds, cn convert it further by `gmtime()` or `localtime()` in the `time` module|
|exists(path)|tell whether the path (directory or file) exists or not|
|isabs(path)|tell whether the path is absolute or not|
|isdir(path)|tell whether the path exists as a directory|
|isfile(path)|tell whether the path exists as a file|
|islink(path)|tell whether the path exists as a link|
|ismount(path)|tell whether the path exists as a (?) 挂载点（what is this)|
|samefile(path1, path2)|tell whether the two paths refer to one same file|

To glance at the absolute/relative path, see an example: in the computer there is a drive `E:`. For a file we can write its absolute path as `E:/A/B/text.txt`. Relatively inside the drive `E:`, it can be referred to by `A/B/text.txt` or `./A/B/text.txt`. And relatively in the folder B, its path can be `../text.txt`.


We test some codes in the os.path module.
```Python
>>> import os.path

#basename and dirname
>>> os.path.basename('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test')
'Test'
>>> os.path.basename('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test/test1.txt')
'test1.txt'
>>> os.path.dirname('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test')
'/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16'

#join, split and splitext
>>> os.path.join('Test', 'Test2', 'Test3')
'Test/Test2/Test3'
>>> os.path.split('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test')
('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16', 'Test')
>>> os.path.splitext('E:/A/B.txt') #even this path does not exist
('E:/A/B', '.txt')

#getatime, getctime, getmtime and gmtime(), localtime()
>>> os.path.getatime('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test')
1600138718.5986953
>>> import time
>>> time.gmtime(os.path.getatime('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test'))
time.struct_time(tm_year=2020, tm_mon=9, tm_mday=15, tm_hour=2, tm_min=58, tm_sec=38, tm_wday=1, tm_yday=259, tm_isdst=0)
>>> time.localtime(os.path.getatime('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test'))
time.struct_time(tm_year=2020, tm_mon=9, tm_mday=15, tm_hour=10, tm_min=58, tm_sec=38, tm_wday=1, tm_yday=259, tm_isdst=0)

#check all the three times of the folder Test
>>> time.localtime(os.path.getmtime('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test'))
time.struct_time(tm_year=2020, tm_mon=9, tm_mday=15, tm_hour=10, tm_min=58, tm_sec=35, tm_wday=1, tm_yday=259, tm_isdst=0)
>>> time.localtime(os.path.getctime('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test'))
time.struct_time(tm_year=2020, tm_mon=9, tm_mday=15, tm_hour=10, tm_min=58, tm_sec=35, tm_wday=1, tm_yday=259, tm_isdst=0)
>>> time.localtime(os.path.getatime('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test'))
time.struct_time(tm_year=2020, tm_mon=9, tm_mday=15, tm_hour=10, tm_min=58, tm_sec=38, tm_wday=1, tm_yday=259, tm_isdst=0)

#modify the folder Test by deleting Test2 folder inside it, all three times changed (because Test is a folder?)
>>> time.localtime(os.path.getmtime('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test'))
time.struct_time(tm_year=2020, tm_mon=9, tm_mday=28, tm_hour=14, tm_min=28, tm_sec=52, tm_wday=0, tm_yday=272, tm_isdst=0)
>>> time.localtime(os.path.getctime('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test'))
time.struct_time(tm_year=2020, tm_mon=9, tm_mday=28, tm_hour=14, tm_min=28, tm_sec=52, tm_wday=0, tm_yday=272, tm_isdst=0)
>>> time.localtime(os.path.getatime('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test'))
time.struct_time(tm_year=2020, tm_mon=9, tm_mday=28, tm_hour=14, tm_min=28, tm_sec=57, tm_wday=0, tm_yday=272, tm_isdst=0)

#ismount, not sure what it means but I tried some
>>> os.path.ismount('/Users')
False
>>> os.path.ismount('/Users/shiminfu/')
False
>>> os.path.ismount('/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day16/Test')
False
```

## Keys
- module
  - os 
  - os.path module
