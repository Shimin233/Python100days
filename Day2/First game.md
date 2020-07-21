Create a new file in IDLE (command + N) and enter the following codes
```Python
print('---------My first game---------')
temp=input('Guess one number') #assign anything we type to the variable temp
guess=int(temp) #transform the thing we type to an integer
if guess==8: 
    print('Right!')
    print('Happy guessing!')
else:
    print('Wrong...')
print('The End')
```
Save this file (command + S) in a new folder called Day2 in the folder Python100days; name this file as First _game.py_

Click the "Run" menu and then Run module (F5, = fn + F5). You will see the shell is running your program.

Here, the sign `==` means "equating", while `=` means value assingnment.
There are 
Note that the sign `:` will create indents in the follwoing lines automatically.
Remark, the cycles in Python are recognized by proper indents. For example, the `if ... else` cycle in the codes above, requires indents 
in front of the operations corresponding to `if` and `else` (`print()` here).

### Keys
- `==` means "equating", while `=` means value assingnment
