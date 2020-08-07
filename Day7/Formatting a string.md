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
- `%c`

- `%s`

- `%d`

- `%o`

- `%x`

- `%X`

- `%f`

- `%e`
## Keys
- Formatting a string
