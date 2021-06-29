## Else stataments
### 1 If-else: Either A or B
```Python
if True:
    A
else: 
    B
```
### 2 try-except-else: If done then A; if undone then not B 
```Python
if True:
    A
    break #this will pop out of the if-else process right away and thus the else part B will not be executed
    A'
else: 
    B
```
For example,
```Python
#In module: 
def showMaxFactor(num):
    counter = num // 2  #taking the integer part of num/2, that is either 0 or 1
    while count > 1:
        if num % count == 0:  #if the remainder of num/count is zero
            print('The largest divisor of %d is %d' %(num, count))
            break #i.e. pop out in the middle way, so that the else part will not be executed
        count -= 1
    else: 
        print('%d is prime' % num)
        
num = int(input('Insert one number: '))
showMaxFactor(num)

```

### 3 No error then A
```Python
try: 
    range to check
except SomeError as reason: 
    B
else: 
    A
```

For example, 
```Python
# In module
try: 
    int('abc')
except ValueError as reason: 
    print('Error:' + str(reason))
else:
    print('Everything works well!')  
```


## With statements
```Python
try:
    f = open('NonExisting.txt', 'w') 
    for each_line in f: 
        print(each_line)
except OSError as reason:
    print('Error:' + str(reason))
finally:
    f.close()
#there will be an error since the file opened does not exist
 
#With statement, will execute f.close() automatically if it finds that the file does not exist 
try:
    with open('NonExisting.txt', 'w') as f: 
        for each_line in f: 
            print(each_line)
except OSError as reason:
    print('Error:' + str(reason))

```
## Summary
- else
  - 1 if-else
  - 2 if-(break)-else
  - 3 try-except-else
- with: automatically close (stop introducing) a non-existing file
