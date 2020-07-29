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

We look at some of these operators in detail. For example, `+=`, `-=`, `*=`, `/=`, `%=` and others in the last row of the table simplify the update of value.
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
>>> 10//8
1
>>> 3.0//2
1.0
```
To take the remainder after division, we use the form `dividend % divisor`.
```Python
>>> 5%2
1     #5=2*1+1
>>> 11%2
1
```



1.0


## Branchings and cycles
