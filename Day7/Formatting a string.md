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

## Keys
- Formatting a string
