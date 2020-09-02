I have added the flow charts for each improvement and exercise2 in the folder Python100days/Day3/Flow chart. 

## More about operators
Recall the operators
| 运算符                                                       | 描述                           |
| ------------------------------------------------------------ | ------------------------------ |
| `[]` `[:]`                                                   | 下标，切片                     |
| `**`                                                         | 指数                           |
| `~` `+` `-`                                                  | 按位取反, 正负号               |
| `*` `/` `%` `//`                                             | 乘，除，模，整除               |
| `+` `-`                                                      | 加，减                         |
| `>>` `<<`                                                    | 右移，左移                     |
| `&`                                                          | 按位与                         |
| `^` `\|`                                                      | 按位异或，按位或               |
| `<=` `<` `>` `>=`                                            | 小于等于，小于，大于，大于等于 |
| `==` `!=`                                                    | 等于，不等于                   |
| `is`  `is not`                                               | 身份运算符                     |
| `in` `not in`                                                | 成员运算符                     |
| `not` `or` `and`                                             | 逻辑运算符                     |
| `=` `+=` `-=` `*=` `/=` `%=` `//=` `**=` `&=` `|=` `^=` `>>=` `<<=` | （复合）赋值运算符             |

>**说明：** 在实际开发中，如果搞不清楚运算符的优先级，可以使用括号来确保运算的执行顺序。
(Source: Jackfraud's notes https://github.com/Shimin233/Python-100-Days/blob/master/Day01-15/02.语言元素.md)

See more categories of operators [here](https://www.cnblogs.com/augustone/p/11320826.html).

We look at some of these operators in detail. 
#### Basic calculations, floor division and modulo
Those listed in the last row of the table, `+=`, `-=`, `*=`, `/=`, `%=` etc. simplify the update of value.
```Python
>>> a = 5
>>> a += 3 #is equivalent to a = a + 3
>>> a
8
>>> b = 3
>>> b -= 1 #is equivalent to b = b - 1
>>> b
2
```
A trick to simplify the assignment of one value to multiple variables.
```Python
>>> a = b = c = d = 10 #assign a=10, b=10, ..., d=10
```
Note that for the division `/`, Python 3 has the 'real' division instead of the floor division, which are used in older versions of Python and many other languages. That is, we will get a float/integer which equals exactly the ratio of two integers, while the floor division only gives the largest integer which are smaller than the real ratio (its 'floor' value), approximating the ratio.

If you prefer the floor division, you may use `//` to do the floor division.
```Python
>>> 10 // 8
1
>>> 3.0 // 2
1.0
```
To take the modulo, we use the form `dividend % divisor` (using these terms informally). 
```Python
>>> 5 % 2
1     #5=2*1+1
>>> -21 % 4
3
``` 
Note that -21 mod 4 = 3, calculated as -21 - 4 * (-6) = 3; while -21 = 4 * (-5) + (-1), the remainder of -21 divided by 4 is -1. But the modulus calculation and the remainder calculation behave the same for positive integers. For example, 21 - 4 * 5 = 1 so 21 mod 4 = 1 and 21 = 4 * 5 + 1.

My guess: does modulus calculation means the dstance from a number when getting close to it (like -21 in the last paragraph) from below, while remainder calculation means the distance to a number when getting the cloest to it.

```Python
3 ** 2   #3^2
9
2 ** 10  #2^10
1024
```
#### Comparison operators
As we have seen before, this includes `<, <=, >, >=, ==, !=`.

#### 逻辑操作符
This category includes `and`, `or` and `not`.
```Python
>>> True or True
True
>>> True or False
True
>>> False or False
False

>>> not False
True
>>> not 0
True
>>> not 5 #any non-zero number is interpreted as True
False
>>> 3<4<5 #interpreted as (3<4) and (4<5)
True
```

### 运算的优先级
Actually the order of operators in the table given in the beginning of this file reveals the order of operation, except specified by parentheses `()`, brackets `[]`, etc.

Let's go through some of their examples. First, `**`, `*, /, %, //`, and then `+, -`.
```Python
>>> -3 * 2 +5 / -2 - 4  #[(-3)*2] + [5/(-2)] - 4
-12.5
>>> 2 * 3 ** 2    #2*(3^2)
18
```
Comparison operators, and then 逻辑操作符
```Python
>>> 3 < 4 and 4 < 5  #more clearly (3 < 4) and (4 < 5)
True
```

When `-` acts on one item, meaning 'negative' instead of 'minus, subtraction', it operates before the operators on its left; but after those on its right.
```Python
>>> -3 ** 2  #-(3^2); - operats after **
-9
>>> 3 ** -2  #3^(-2)=1/9; - operats before **, -2 as a whole
0.1111111111
```

To summarize for the beginners, it suffices to remember the following: (first to last)\
`+, -` used as positive, negative (when thay are on the right of `**`)\
`**`\
`+, -` used as positive, negative\
`*, /, %, //`\
`+, -` used as addition, subtraction\
`<, <=, >, >=, ==, !=` comparison operators\
`and, or, not`

Tip: to start a new line in .md file, you may type two spaces at the end of the previous line or use a '\' in the same position; but we do not need this when leaving one line empty to start a new paragraph. See more advice/methods see this question on [StackOverflow](https://stackoverflow.com/questions/33191744/how-to-add-new-line-in-markdown-presentation).


## Branchings and cycles
We have seen `if...else` and `while` before. To learn more branchings and cycles, we create a second game.

We shall describe it in words:
```
load background music
replay the same music 
create our plane
interval=0

while True:
  if click 'Close':
     exit
     
  interval+ += 1
  if interval== 50:
      interval = 0
      create enemy's plane
   
  enemy's planes move to the next unit in position
  refresh the screen
   
  if mouse moved:
      our plane->mouse position
      refresh screen
      
  if conflict:
      bomb and its sound
      the image of our plane changed
      print('Game Over')
      Stop the background music, gradually if possible
 ```
Let's introduce more techniques in coding before creating the exact codes for this game.
### Elif
Let's create a program, such that it outputs A, B, C, and D resp. when inputting 100-90, 80-90, 60-80 and 0-60, and the full mark is 100.
Soln1 TBC
Note, you can use `if True:......` without `else`. 
Soln2 TBC
Soln3 TBC
We can combine `else: if True:` by typeing `elif True:`. 

Note that in the following cycles,
```Python
if True:   #the first cycle, only has 'if' but no 'else'
  print('The first if condition is True')
if True:   #the second cycle, this is its 'if'
  print('The second if condition is True') #Both if cycles may have printed
else:      #the second cycle, this is its 'else'
  print('One or two of the if conditions are False')
```
the two `if`'s will operate respectively in their order; the second `if` operates no matter whether the first one is True; and whether the `else` operates depends only on whether the second `if` condition is False. In another word, there are two independent cycles, operating respectively in order: the first one has only `if` but does not specify any operation for `else`, the second one specifies the operations for both `if` and `else`.

It is different from the case with `elif` replacing the second `if`:
```Python
if True:
  print('The first if condition is True') 
elif True:
  print('The second if condition is True') #if the last sentence prints, this will not print; this may print only when the last sentence did not
else:
  print('Both of the if conditions are False')
```
Only when the first `if` condition is False, `elif`'s condition is checked. Like the previosu case, only when neither of the two `if` conditions is True (i.e. both False), the `else` will operate. See the flowcharts of these two cases in Python100days/Day4/Elif_IfIfElse.

See an example for the case that for `if...if...else`, there is only one if condition is False. Saved as Python100days/Day4/IfIfElse.py. In the module,
```Python
a = int(input('Insert a positive integer: '))

if a > 2:
    print('The number %d is larger than 2' % a)
if a < 4:
    print('The number %d is smaller than 4' % a)
else:
    print('The number %d is not in the interval (2, 4)' % a)
```
Run it,
```Python
Insert a positive integer: 5
The number 5 is larger than 2
The number 5 is not in the interval (2, 4)
```
In contrast, replacing the second `if` with `elif`,
```Python
a = int(input('Insert a positive integer: '))

if a > 2:
    print('The number %d is larger than 2' % a)
elif a < 4:
    print('The number %d is smaller than 4' % a)
else:
    print('The number %d is not in the interval (2, 4)' % a)
```
```Python
Insert a positive integer: 5
The number 5 is larger than 2
```
### 避免'悬挂else'
Such a problem means the undesired correspondence of `if` and `else`. However, Python requires you to use indents to type tidy and correct codes, su that this type of problems can rarely occur in Python.

### Operators acting on three items
You can use one line of such operator to replace those multiple lines. For instance, rewrite
```Python
x, y = 4, 5
if x < y:
    small = x
else:
    small = y
```
as
```Python
small = x if x < y else y
```

### Assert断言
When the condition following `assert` is False, the program will automatically crush and report 'AssertionError'.
For example,
```
assert 3 > 4 #, which is False in normal definitions
```
This will lead to an error immediately. Instead, `assert 4 > 3` does not cause any error.

You can use `assert` to check some condition at certain points in a program. If you want to make sure some condition is always True throughout your program, `assert` can play a key role.

### For cycle
This cycle takes the following form.
```Python
for goal in expression:
  body of this cycle
```
Take an example,
```
>>> favourite = 'Hello'
>>> for i in favourite:
        print(i, end=' ') #i, refers to the single items in the variable called favoutie; can name items using anything, like 'each'
        
H e l l o
>>> member = ['Me', 'You', 'They', 'She', 'He', 'Nous', 'Vous', 'Je']  #create a list
>>> for each in member:
        print(each, len(member))   
        
Me 8
You 8
They 8
She 8
He 8
Nous 8
Vous 8
Je 8
>>> for each in member:
        print(each, len(each))
        
Me 2
You 3
They 4
She 3
He 2
Nous 4
Vous 4
Je 2
```
The main difference between  `while` cycle and `for` cycle is that the former keeps running the body of the cycle when some condition is True, while the latter keeps applying the body to the items specified in the cycle condition. Generally, the `while` cycle condition does not necessarily quote any item, while the `for` cycle condition specifies some items which later join in its cycle body.

### Range()
The grammar of this built-in function(BIF) is `range([start,] stop[, step])`. It acts on three items: start, stop and step. Those in the brackets are not required to specify; for example, `range(0, 5, 1)` can be simply typed as `range(5)`. This function will generate a sequence of numbers from the 'start' number (included; default 0) to 'stop' number (excluded), with a certain step (default 1).

```Python
>>> range(5)
range(0, 5)
>>> list(range(5))
[0, 1, 2, 3, 4]
```
Often used together with `for` cycle.
```
>>> for i in range(5):
        print(i)
        
0
1
2
3
4              
>>> for i in range(2, 9):
        print(i)
        
2
3
4
5
6
7
8        
>>> for i in range(1, 10, 2):
        print(i)
   
1
3
5
7
9   
```
### Break and continue
The code `break` is used to stop the current cycle. Try the following example in the module and run it.
```Python
bingo = 'Goodbye'
answer = input('Please type something to end this game:')

while True:   #True makes this while cycle operate infinitely
    if answer == bingo;
        break
    answer = input(Sorry, it is not the right word to end this game (only when correct, you can exit it):')
    
print('Right!')
print('The End')
```

The code `continue` is used to stop the current cycle and, if the condition of the next cycle is True, start the next cycle. Try th following example in the module and run it.
```Python
for i in range(10):
    if i%2 != 0:
        print(i)
        continue  
    i += 2
    print(i)
```
You will get
```Python
2
1
4
3
6
5
8
7
10
```
This is because, for each value of `i`:
i=0, 0%2=0, so go to 0 + 2 = 2, print 2;
1, 1%2=1 as 1 - 2 * 0 = 1, so print 1 and continue to the next turn of `if` cycle, without operating `i += 2   print(i)` afterwards;
2, 2%2=0, so go to 2 + 2 =4, print 4;
3, 3%2=1, so print 3 and continue to the next turn of `if` cycle, without operating the codes other than this `if` cycle;
4, 4%2=0, so go to 4 + 2 = 6, print 6;
...
9, 9%2=1, so print 9 and since the last turn of `if` has been finished, the whole `for` cycle ends.
In brief, all the odd numbers in \{0,1, 2, ..., 9\} are printed directly and all the even numbers in this set are added by 2 and then printed. The code `continue` avoids the (redundant) operations of the codes other than the `if` cycle.

We shall continue learning techniques on the next day.   

## Keys
- More about operators
  - Basic calculations, `%, //` and `**`; comparison; 逻辑
  - Two uses of each of`+, -`
  - Order of operation
- Branchings and cycles: 2nd game and more techniques
  - `elif`
  - 避免'悬挂else'
  - operators acting on three items
  - assert
  - `for`, `range()`
  - break and continue
