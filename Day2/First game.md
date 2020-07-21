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

Here, the sign `==` means "equating", while `=` means value assingnment.
There are other signs?????????????

Note that the sign `:` will create indents in the follwoing lines automatically.
Remark, the cycles in Python are recognized by proper indents. For example, the `if ... else` cycle in the codes above, requires indents 
in front of the operations corresponding to `if` and `else` (printing two items for `if` and one for `else` here).

We have used some of the __built-in functions(BIFs)__, such as `print()`, `input()`, `int()`. To see how many BIFs existing in Python,
```Python
>>> dir(__builtins__)
```
To see help on some specific BIF, such as `input`,
```Python
>>> help(input)
```


### Keys
- `==` means "equating", while `=` means value assingnment

### Appendix
I created a flow chart of this game using LaTeX, saved in the folder "Python100days/Day2". (how to save/sync local files on github? to be continued)
