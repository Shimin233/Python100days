## Create a game
Create a new file in IDLE (command + N) and enter the following codes
```Python
print('---------My first game---------')
temp=input('Guess one number:') #assign anything we type to the variable temp
guess=int(temp) #transform the thing we type to an integer
if guess==8: 
    print('Right!')
    print('Happy guessing!')
else:
    print('Unfortunately... I prefer 8')
print('The End')
```
Save this file (command + S) in a new folder called Day2 in the folder Python100days; name this file as First _game.py_

Click the "Run" menu and then Run module (F5, = fn -> F5). You will see the shell is running your program. Now enter(guess) a number right after the `Guess one number:`, press return button, see what you get.

Note that the sign `:` will create indents in the follwoing lines automatically.
Remark, the cycles in Python are recognized by proper indents. For example, the `if ... else` cycle in the codes above, requires indents 
in front of the operations corresponding to `if` and `else` (printing two items for `if` and one for `else` here).

## Operators运算符
In the game above, the sign `==` means "equating", while `=` means value assingnment.
There are other operators similar to `==`, shown as below
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

## Built-in functions
We have used some of the __built-in functions(BIFs)__, such as `print()`, `input()`, `int()`. To see how many BIFs existing in Python,
```Python
>>> dir(__builtins__)
```
To see help on some specific BIF, such as `input`,
```Python
>>> help(input)
```

## More about variables in Python
In most of other programming languages, assignment of a value to a variable is called "storing a value in a variable". However, Python differs from other languages; it is closer to "sticking a value to a variable". Thus, we may say that there is no variables but "names" in Python. (Do not need to understand this in beginner Python courses)

Let's play with variables with more examples.
- Update the value assigned to a variable.
  ```Python
  >>> a=6 #print(a) gives 6
  >>> b=7
  >>> a=0 #print(a) gives 0 instead of 6
  ```
- Assign value of one variable to another.
  ```Python
  >>> a=6 #print(a) gives 6
  >>> b=7
  >>> c=a #print(c) gives
  ```
  Note the order of codes: `c=a` means assigning value of `a` to `c`; if replaced by `a=c`, which is assigning value of `c` to `a`, Python will wonder what is the value of `c`, and will report an error since `c` is not defined yet.
- Use variables with values assigned to do calculations.
  ```Python
  >>> a=6 
  >>> b=7
  >>> s= a + b  #print(s) or equivalently, print(a+b) gives 6+7=13
  
  >>> a='hello'
  >>> b='world'
  >>> s= a + b  #print(s) or equivalently, print(a+b) gives 'helloworld'; while print(a+' '+b) gives 'hello world'; 字符串拼接
  ```
Note the difference between numerics' calculations and strings' combination (more rigorous term to be search)
```Python
>>> 2+3.33 #numerics
5.33
>>> '2'+'3.33' #strings
'23.33'
```
## Use \ in a string
To include quotes in your string, you can add a `\` before each of them
```Python
>>> 'Let\'s go! I\'m coming.'
"Let's go! I'm coming."
```
and there is an alternative method to do this (tbc).

More codes containing `\` are as below
```Python
# \ is used to let special symbol appear in a string
>>> 'C:\now'  #every item is a part of this string
'C:\now'
>>> print('C:\now')  #here \n is recognized to start a new line
C:
ow
>>> 'C:\\now'  #again every item is a part of this string
'C:\\now'
>>> print('C:\\now')  #here the first \ is to let the second \ appear 
C:\now
>>> r'C:\now\Applications\Python3'   #原始字符串，add r before a string to let multiple \'s appear in this string; but cannot have a \ at the end of this string using this method
'C:\\now\\Applications\\Python3'    #all the \'s are doubled??
#to have a \ at the end while letting multiple \'s in a string, you may add a space after the ending \
>>> r'C:\now\Applications\Python3\ '
'C:\\now\\Applications\\Python3\\ '
#So, how to avoid this space? Have tested combining with '\', failed; TBC

# \n is used to start a new line
>>> '''this is
to test
multiple lines
'''
'this is\nto test\nmultiple lines\n'   #Python rewrites multiple-line string using \n

>>> print('this is\nto test\nmultiple lines\n')  
this is
to test
multiple lines
                    #note the automatically added last \n creates a new (empty) line here
                    
>>> print('''this is
to test
multiple lines
''')                #alternative method to print a multiple-line string, equivalent to the last one
this is
to test
multiple lines
                    #again, the last \n is automatically added, creating a new (empty) line here
>>> 
```
From the codes above, we can see two equivalent expressions of one multiple-line string in Python: 
```Python
'''this is
to test
multiple lines
'''
```
and `'this is\nto test\nmultiple lines\n'`; both are printed as 
```Python
this is
to test
multiple lines
                
```
### Keys
- Create a .py file and run it using the shell IDLE
  - `==` means "equating", while `=` means value assingnment
  - Some operators
- Built-in functions
- More about variables in Python
- Use \ in a string
  - let some special symbol appear in a string
  - \n to start a new line

### Appendix
I created a flow chart of this game using LaTeX, saved in the folder "Python100days/Day2". (how to save/sync local files on github? to be continued)
