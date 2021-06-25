- I use #comments in the codes to add my comments which are not codes run by Python.
- By the rules of markdown, the codes can be quoted using two pairs of triple backticks (two pairs of \`\`\`); furthermore, adding `Python` just after the first set of triple quotes
backticks will quote codes as if they are in Python. Likewise for other programming languages.
  - Note that the contents (codes) between two pairs of triple quotes must be in different lines from the triple quotes; otherwise a blank field of code quoting will be outputted. Because the codes themselves are mistaken as a language, which does not exist in most cases (except when you codes begin with, for example "Java", by coincidence).
  - Letting the codes look like Python ones by adding `Python` after the first set of triple quotes does not mean it must appear the same in actual programs; you can type incomplete codes here.

## First code: print()
Open the _IDLE_, the shell of Python. You can see the first few lines are like
```Python
Python 3.8.4 (v3.8.4:dfa645a65e, Jul 13 2020, 10:45:06) 
[Clang 6.0 (clang-600.0.57)] on darwin
Type "help", "copyright", "credits" or "license()" for more information.
>>>
```
The set of signs ">>>" means Python has been prepared for you to type more codes.
 
Now type `print('hello world')` or `print("hello world")` right after `>>>`, so you will have
```Python
>>> print('hello world')
```
Press "Return"/"Enter" button, and you will get a response from Python, which is printing a line of text and a new ">>>" is provided. 
```Python
>>> print('hello world')
hello world
>>>
```
You can type more codes right after the newly prvided ">>>". I will omit ">>>" in the following texts, except for complete presentation of my codes.

Now try `print(5+3)` or `5+3`, you will get `8`. 
Try other codes and see their outputs as
```Python
>>> print('well water'+'river')
well waterriver
>>> print('well water '+'river') 
well water river
>>> print('well water'+' river')
well water river
>>> print('hello'*8)
hellohellohellohellohellohellohellohello
>>> print('hello\n'*8)
hello
hello
hello
hello
hello
hello
hello
hello
```
I will omit the outputs in the future notes, except when I find them necessary as hints.

But `print('hello'+8)` gives an error, because we cannot mix different types of data in one calculation.

## Python data types
I am going to list the categories of data together with examples. 
There are several _categories_ labelled as __bold__ and then _subcategories_ in the nested lists.
- __Numeric__: Data with a numeric value. Three categories of numerics:
  - Integer整型 `int`: Positive/negative integer
  ```Python
  15
  8
  233333
  ```
  Remark that there are two types of integers `int` and `long` in Python2.x, but they do not make many differences in Python.
  Also, Python reads the binary system(labelled by B)二进制, such as binary 100 means 2^2=4 in the decimal system十进制; the octal number system(O)八进制, such as octal number 100 means decimal 8^2=64; the decimal system(D); and the hexadecimal system(X)十六进制, like hexadecimal B means decimal 11, hexa 100 means decimal 256.
  ```Python
  >>> print(0b100)
  4
  >>> print(0o100)
  64
  >>> print(0xb) #lowercase can be used for both system symbol and the number itself
  11
  >>> print(0x100)
  256
  >>> 0xB #this also works
  11
  ```
  
  - Float浮点型 `float` : Real number, whose fractional component is written as a decimal part or scienfic notation.
  ```Python
  1.5
  0.08
  2.33e7
  ```
  - Complex number `complex`: A number `x+yj` or `x+yJ` with a real part `x` and an imaginary part `y`, where `x` and `y` are floats. 
  Note you must write 1j or 1J but not j or J.
  ```Python
  1+8j
  
  #calculate using complex numbers
  >>>1j*1j
  (-1+0j)
  ```
  Remark that if we only use integers in a calculation, the output will be an integer; once we include some float, the output will be a float. 
  ```Python
  >>> 5*5
  25
  >>> 5*5.0
  25.0
  >>> 5*5.00
  25.0
  ```
  This also reveals that we may mix integers and floats (which are both numerics) but not strings and numerics (shown by `'hello'+8` before);
  i.e. _subcategories_ are mixable but _categories_ are not (to be confirmed).
- __Boolean__ `bool`: Data with one of two built-in values `True` or `False`. They are actually a special type of integers. Note T and F here must be capital.
```Python
True
bool(3<5) #equals True, verified as follows
>>> bool(3<5))
True
#or by
>>> 3<5
True

#the following are similar
bool(4==5) #equals False
bool(0) #equals False
bool(2.33e5) #equals True
```
Remark that `bool(0)` refers to `False`, while inputting any non-zero number it gives `True`. \
Remark, True and False can be used exactly as 1 and 0 resp. in numeric calculations, like `True + False`, which gives `1`.
- __Text type__ String字符串型 `str` : A collection of one or more characters put in single, double or triple quotes, 
where a quote can be either a single or double quotation mark. Do not mix single and double quotation marks in one expression.
```Python
'Hello world!'
“Hello world!"
'''
Multiple lines 
of texts can be shown 
using three quotes
'''
```
Remark that the indents in each line between a pair of triple quotes will be shown in the output; verify this by inputting
```Python
>>>print(
       '''
more
       good
stuff
''')
```
- __Sequence type__: A sequence is an ordered collection of same or different data types. 
  - List `list`: An ordered collection of one or more data items, not necessarily of the same type, put in square brackets.
  ```Python
  ['apple', 'banana', 'orange']
  ```
  - Tuple `tuple`: An order collection of one or more data itmes, not necessarily of the same type, put in parentheses.
  ```Python
  ('apple', 'banana', 'orange')
  ```
  - Range `range`
  ```Python
  range(6)
  #see its equivalent expressions by typing or printing it in IDLE
  >>> range(6)
  range(0, 6)
  >>> print(range(6))
  range(0, 6)
  ```
  You can see its contents by converting it to a list
  ```Python
  >>> list(range(0, 6))
  [0, 1, 2, 3, 4, 5]
  ```
- __Mapping type__ Dictionary `dict`: An unordered collection of data ina key:value pair form. A collection of such pairs is encloed in curly brackets.
```Python
{1:'Steve', 2:'Bill', 3:'Ram', 4:'Farha'}
{'name':'Emily', 'age':12}
```
- __Set types__
  - Set `set`
  ```Python
  {'apple', 'banana', 'orange'}
  ```Python
  - Frozenset `frozenset`
  ```Python
  frozenset({'apple', 'banana', 'orange'})
  ```
- __Binary types__
  - Bytes`bytes`
  ```Python
  b'Hello'
  ```
  - Bytearray `bytearray`
  ```Python
  bytearray(5)
  ```
  - Memoryview `memoryview`
  ```Python
  memoryview(bytes(5))
  ```
  
There is a function `type()` to look up the type of some data, shown as below
```Python
>>>x=5
>>>print(type(x)) #or just type(x)
<class 'int'>
```
Also, there is a function `isinstance()` to compare whether a data(?) is of an assumed type
```Python
>>> isinstance('233', str)
True
>>> isinstance(233, str)
False
>>> isinstance(233.3, bool)
False
```

### Assign a date type to a variable
You can assign a value (of some data type) to a variable (to be explained in the next section) by `variable = value itself`. Like the examples listed for each data typein the last section, Python would automatically recognize the data type of the value. In this case, assignment is as simple as below
```Python
x='Hello world!'
y=1.5
z=False
w=['apple', 'banana', 'orange']
v={'name':'Emily', 'age':12}
u=bytearray(5)
t=True
```
But sometimes, we need to specify the data type of some value to avoid Python from misunderstanding. We can use the constructor functions to specify the data type as below
```Python
x=str('Hello world!')
y=float(1.5)
z=bool(False)
w=list(('apple', 'banana', 'orange'))
v=dict(name='Emily', age=12)
u=bytearray(5)
t=bool(5)
```
Note that the codes of `range`, `bytes`, `bytearray`, and `memoryview` are exactly the same in the two piles of expressions above;
those of `dict`, `frozenset` and some others differ by a little bit. See [summary from W3 schools](https://www.w3schools.com/python/python_datatypes.asp) for the full list (VPN needed).

### Change the data type
Additionally, you can change the type of some data using the following functions. These functions include (to be confirmed) the constructor functions (sepcifying the data type is basically converting the data type).
- `int()`: transform a numeric or a string to an integer; system (e.g. binary) can be specified
- `float()`: transform a string or an integer to a float
- `str()`: transform an arbitrary item to a string
- `chr()`: transform an integer to its corresponding string (as one single string)(?)
- `ord()`: transform one single string to its corresponding integer
For example,
```Python
>>> int(2.9)
2  
>>> int(2.33e2)
233    #simply keep the integer part of a float
>>> float(520)
520.0
>>> float('520')
520.0
>>> str(5.99)
'5.99'
>>> str(5e19)
'5e+19'
>>> str(5e-19)
'5e-19'
>>> chr(1)
'\x01'
```
Remark, we can use an existing function as a variable, like `str=5.99`; but it will cause problems, for example, you cannot use `str()` as it was originally, but only can use it as the variable you defined. So, avoid naming a variable as an existing function.\
Tip about `int()` (see details by `help(int)`): this function can interpret a number or string to an integer. But "If x is not a number or if base is given, then x must be a string, bytes, or bytearray instance representing an integer literal in the given base"; for example, `int(11.2, base=16)` gives an error, `int(11, base=16)` gives 17 (converting base-16 to base-10).

## Name the variables
A variable is an item to which we assign data. For example, the `x`, `y`, ..., `t` we had in the last section. There are some rules to name a variable.
- Basic rules
  - The name of a variable consists of Unicode letters, numbers and underlines ([What is Unicode?](https://baike.baidu.com/item/Unicode/750500?fr=aladdin); [Unicode official](https://home.unicode.org))
  - It does not begin with numbers
  - Case-sensitive (a lowercase "p" differs from an uppercase "P")
  - No commands or functions, except defined otherwise(to be confirmed)
- PEP 8 rules (A set of rules to make codes look beautiful; see [What is PEP 8?](https://www.python.org/dev/peps/pep-0008/); [Summary in CHN](https://blog.csdn.net/genius_jiang/article/details/91479711))
  - The name consists of lowercase letters
  - Connect multiple words using underlines
  - more...

#### Keys
- print()
- Data types
  - _Subcategories_ are mixable but _categories_ are not
  - `type()` and `isinstance()`
  - Assign data to variables
  - Change the data type
- Name the variables
- Must use English signs and symbols to type codes
