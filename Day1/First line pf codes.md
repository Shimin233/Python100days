## First code: print()
Open the _IDLE_, the shell of Python. You can see the first few lines are like
```
Python 3.8.4 (v3.8.4:dfa645a65e, Jul 13 2020, 10:45:06) 
[Clang 6.0 (clang-600.0.57)] on darwin
Type "help", "copyright", "credits" or "license()" for more information.
>>>
```
The set of signs ">>>" means Python has been prepared for you to type more codes.
 
Now type `print('hello world')` or `print("hello world")` right after `>>>`, so you will have
```
>>> print('hello world')
```
Press "Return"/"Enter" button, and you will get a response from Python, which is printing a line of text and a new ">>>" is provided. 
```
>>> print('hello world')
hello world
>>>
```
You can type more codes right after the newly prvided ">>>". I will omit ">>>" in the following texts, except for complete presentation of my codes.

Now try `print(5+3)` or `5+3`, you will get `8`. 
Try other codes and see their outputs as
```
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
- __Numeric__: Data with a numeric value. Three categories of numerics:
  - Integer: Positive/negative integer
  ```
  15
  8
  233333
  ```
  - Float: Real number, whose fractional component is written as a decimal part or scienfic notation.
  ```
  1.5
  0.08
  2.33e7
  ```
  - Complex number: A number `x+yj` or `x+yJ` with a real part `x` and an imaginary part `y`, where `x` and `y` are floats. 
  Note you must write 1j or 1J but not j or J.
  ```
  1+8j
  >>>1j*1j
  (-1+0j)
  ```
- __Boolean__: Data with one of two built-in values `True` or `False`. Note T and F here must be capital.
- __Sequence type__: A sequence is an ordered collection of same or different data types. 
  - String: A collection of one or more characters put in single, double or triple quotes
  - List: An ordered collection of one or more data items, not necessarily of the same type, put in square brackets.
  - Tuple: An order collection of one or more data itmes, not necessarily of the same type, put in parentheses.
- __Dictionary__: An unordered collection of data ina key:value pair form. A collection of such pairs is encloed in curly brackets.
```
{1:'Steve', 2:'Bill', 3:'Ram', 4:'Farha'}
```

There is a trick to look up the type of some data, shown as below
```
>>>x=5
>>>print(type(x))
<class 'int'>
```
#### Keys
- 
- print()
- print('blahblahblah')
- Must use English signs and symbols to type codes.
