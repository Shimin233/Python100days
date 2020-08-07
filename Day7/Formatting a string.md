## Formatting a string
In order to output strings in compatible ways, we need to format them. This is done by a function `string{0}string{1}string.format('contents0', 'cont1')`. The correspondence between typed string and printed string is made by numbering, or letter-indexing.
```Python
#numbering to make correspondence
>>> '{0} say {1}.{2}'.format('I', 'Hello', 'com') 
'I say Hello.com'

#letter-index to make correspondence, requires additional labels in format()
>>> '{a} say {b}.{c}'.format(a='I', b='Hello', c='com')
'I say Hello.com'

#can mix numbering and letter-indexing; but require numbering first and then letters, other orders not allowed
>>> '{0} say {b}.{c}'.format('I', b='Hello', c='com')
'I say Hello.com'
>>> '{a} say {1}.{c}'.format(a='I', 'Hello', c='com')
SyntaxError: positional argument follows keyword argument
```
Recall that we can add a `\` to print some codes which may act as commands. Similarly for braces `{}` above, we can add another pair of braces to print the pair of braces inside. 
```Python
>>> '\ta'
'\ta'
>>> print('\ta')  #\t means a tab=8 spaces
	a
>>> print('\\')
\
>>> '{{0}}'.format('双重打括号将内容转义所以不打印')
'{0}'
```
We may talk about fixpoint定点数 a liitle bit here, using an example of formatting. `{0:.1f}` corresponds to the first item `27.658`, and alters it to print one decimal place (`.1`) and to print fixpoint (`f`). The fixpoint is quite similar to float, but expressed differently. Generally speaking, fixpoint means the position of the decimal point remains the same (e.g. integers, pure decimals like 0.125), while float means that position can vary (like 3.125). The definitions of the two matter to computer basics, so we can omit the differences between floats and fixpoints in the beginner Python courses.
```Python
>>> '{0:.1f}{1}'.format(27.658,'08')  #{1} corresponds to '08'
'27.708'
>>> '{0:.1f}{1}'.format(27.658,'GB')  #{1} corresponds to 'GB'
'27.7GB'
```
### More formatting commands
The following commands act like different translators, who interpret a same sentences in their own ways.
- `%c` formats strings and their ASCII codes
```Python
#%c interprets 97 by its corresponding letter a
>>> '%c' % 97  
'a'

#interpret multiple items, use a tuple to type them; otherwise hard for Python to understand
>>> '%c %c %c love' % (97,98,99)
'a b c love'
>>> '%c %c %c love' % 97,98,99
Traceback (most recent call last):
  File "<pyshell#107>", line 1, in <module>
    '%c %c %c love' % 97,98,99
TypeError: not enough arguments for format string
```
- `%s` formats strings
```Python
>>> '%s' % 'What' #%s thinks it ok to print this string directly
'What'
```
- `%d` formats integers
```Python
>>> '%d + %d = %d' % (4, 5, 4+5)  #when printing as interpreted by %d, also compute 4+5 as 9 automtically
'4 + 5 = 9'
```
- `%o` formats octal numbers （无符号八进制数）
```Python
>>> '%o' % 10  #since 10= 1*2 + 8*1 + 8^2 * 0 + 0 
'12'
>>> '%o' % 7
'7'
>>> '%o' % 8
'10'
```
- `%x` formats hexadecimal numbers（无符号十六进制数）　
- `%X` formats capital hexadecimal numbers（无符号大写十六进制数）
```Python
>>> '%x' % 10
'a'
>>> '%X' % 10
'A'
>>> '%X' % 160
'A0'
>>> '%X' % 11
'B'
```
- `%f` formats fixpoints, the number of decimal places can be specified
```Python
>>> '%f' % 27.658   #the fixpoint has 6 decimal places by default
'27.658000'
```
- `%e` formats fixpoints using scientific notation
- `%E` same as `%e` but uses capital E instead of e
```Python
>>> '%e' % 27.658
'2.765800e+01'
>>> '%E' % 27.658
'2.765800E+01'
```
- `%g` uses `%f` or `%e` according to the value
- `%G` uses `%f` or `%E` according to the value
```Python
>>> '%g' % 27.658  #%g thinks it better to interpret 27.658 as a fixpoint=27.658
'27.658'
```

There are also some __supplemantary commands of formatting__, added to the commands above like `'%+m.ne' % 27.658`.
- `m.n` m means the printed minimal total width of the string, n means the number of decimal places
```Python
>>> '%5.1f' % 27.658   #the output has one space in front since the minimal width is set as 5; 1 decimal place
' 27.7'
>>> '%.2e' % 27.658    #the minimal width is not set; 2 decimal places
'2.77e+01'
>>> '%10d' % 5         #the minimal width is set as 10; no decimal place
'         5'
```
- `-` left-align
```Python
>>> '%-10d' % 5    #-=left-align, 10 = minimal width, d = integer
'5         '
```
- `+` add a positive sign in front of the positive number(s)
```Python
>>> '%+d' % 5  
'+5'
>>> '%+d' % -5  #no change to negative number
'-5'
```
- `#` print `0o` in front of the octal numbers, and `0x` or `0X` in front of the hex numbers
```Python
 >>> '%#o' % 10  #0o = octal, 12 = the octal 12
'0o12'
>>> '%#x' % 108  #0x = hex, 6c = the hex 6c
'0x6c'
```
- `0` fill 0's _in front of_ the printed numbers to replace spaces
```Python
>>> '%010d' % 5   #0 = fill 0's in front, 10 = minimal width, d = format integers
'0000000005'
>>> '%-010d' % 5  #- = left-align, 0 = fill 0's in front, 10 = minimal width, d = format integers; 0's are only filled in front so as to avoid changing 5 to 5000000000
'5         '
```
Moreover, we have some __escape characters__ 转义字符.
- `\'` a single quotation mark
- `\"` a double quotation mark
- `\a` bell sound
- `\b` backspace
- `\n` a newline
- `\t` a tab 横向制表符
- `\v` a vertical tab 纵向制表符
- `\r` return
- `\f` form feed 换页符
- `\o` octal system
- `\x` hexadecimal system
- `\0` a space
- `\\` an escape character itself

## Keys
- Formatting a string
  - Double braces to print a pair of braces without further interpretation `{{0}}.format('no further interpretation')`
  - More formatting commands, 3 categories
  1. Basic ones acting like translators
  2. Supplementary commands
  3. Escape characters
