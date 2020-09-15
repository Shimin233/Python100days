## Deal with files 
We shall go through the methods to go through a file (calle f in the table below): opening, writing, closing, etc.
| Code | Operation |
|------|------------------------|
|f.read(\[size=-1])| Read the strings of the 'size' from the file, if size not given, read all the remaining and return as string|
|f.readline(\[size=-1])|Read from the file and return a line (ending string incl.), of the size if given|
|f.write(str)|Write str into the file|
|f.writelines(seq)|Write seq, the sequence of strings into the file, where seq is an iterable that returns strings|
|f.seek(offset, from)|Move the pointer指针 in the file, from 'from'(0 the beginning, 1 the current position, 2 the end) and by 'offset' bytes|
|f.tell()|Return the current position in the file|
|f.close()|Close the file|

Let us apply some of these to an exercise.

## A task (exercise)
We are going to complete a task in this class. We want to divide and save the contents of the file _record.txt_ as required below:
- remove the 'A:' in the words of A and save them as the file _A\_*.txt_;
- remove the 'B:' in the words of B and save them as the file _B\_*.txt_;
- split the three dialogues, which are lablled by '==========' between them and save them into six files: _A_1.txt_, _B_1.txt_, _A_2.txt_, _B_2.txt_, _A_3.txt_, and _B_3.txt_.

Begin with the codes following our intuition. Type in the module.
```Python
f = open('record.txt')

A = []
B = []
count = 1

for each_line in f:
    if each_line[:6] != '======': #split the string
        (role, line_spoken)=eachline.split(':', 1) #recall split(sep=None, maxsplit=-1), splitting by sep into substrings of maxsplit(number)
        if role == 'A':
            A.append(line_spoken)
        if role == 'B':
            B.append(line_spoken)
    else:
        file_name_A = 'A_'+str(count)+'.txt'#split and save
        file_name_B = 'B_'+str(count)+'.txt'

        A_file = open(file_name_A, 'w')
        B_file = open(file_name_B, 'w')

        A_file.writelines(A)
        B_file.writelines(B)

        A_file.close()
        B_file.close()

        A=[]
        B=[]
        count += 1
# since there are only two sets of '=========', we split and save the third part manually
file_name_A = 'A_'+str(count)+'.txt'#split and save
file_name_B = 'B_'+str(count)+'.txt'

A_file = open(file_name_A, 'w')
B_file = open(file_name_B, 'w')

A_file.writelines(A)
B_file.writelines(B)

A_file.close()
```
Simplify the codes by defining two functions `save_file(A, B, count)` and `split_file(file_name)`.
```Python
def save_file(A, B, count):
    file_name_A = 'A_'+str(count)+'.txt'#split and save
    file_name_B = 'B_'+str(count)+'.txt'

    A_file = open(file_name_A, 'w')
    B_file = open(file_name_B, 'w')

    A_file.writelines(A)
    B_file.writelines(B)

    A_file.close()
    B_file.close()

def split_file(file_name):
    f = open('record.txt')

    A = []
    B = []
    count = 1

    for each_line in f:
        if each_line[:6] != '======': #split the string
            (role, line_spoken)=each_line.split(':', 1)
            if role == 'A':
                A.append(line_spoken)
            if role == 'B':
                B.append(line_spoken)
        else: #split and save
            save_file(A, B, count)

            A=[]
            B=[]
            count += 1

    save_file(A, B, count)

    f.close()

split_file('record.txt')
```
PS. it should be the same as typed in the course, but it turns out an error (see below), to be fixed.
```Python
= RESTART: /Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day15/A_task.py
Traceback (most recent call last):
  File "/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day15/A_task.py", line 39, in <module>
    split_file('record.txt')
  File "/Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day15/A_task.py", line 21, in split_file
    for each_line in f:
  File "/Library/Frameworks/Python.framework/Versions/3.8/lib/python3.8/codecs.py", line 322, in decode
    (result, consumed) = self._buffer_decode(data, self.errors, final)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8e in position 16: invalid start byte
>>> 
```
