## Improve our game
There are some suggested improvemnt of the game we created during previous days, such as
- give hints for the wrong guesses, for example, "your guess is larger or smaller than the correct one"
- provide multiple chances for the players to guess
- the correct guess can be random
We shall introduce more techniques to be prepared for improving the game.

## Improvement1: Conditional branching条件分支
Recall the following operators
|Python Comparison Operators                          |
|Python Comparison Operators|      Description        |
|---------------------------| ------------------------|
| `>`                       | strictly larger than|
| `>=`                      | no smaller than|
| `<`                       | strictly smaller than|
| `<=`                      | no larger than|
| `==`                      | equals|
| `!=`                      | does not equal|

As we have seen before, `1<5` will be interpreted as `True`, and other comparison operators work similarly.

The conditional branching in Python is of the following structure:
```Python
if condition is True:     #note there is a colon":" , same for else
   the operations in the case of True, may have several lines
else:
     the operations in the case of False, may have several lines
```
Again note that the indents are required to show operations for `True` and for `False`.

Now we are ready to make the first improvement of our game: give hints for the wrong guesses. 
Open _First game.py_ in IDLE and revise as follows
```Python
print('---------My first game---------')
temp=input('Guess one number:')
guess=int(temp)
if guess == 8:
    print('Right!')
    print('Happy guessing!')
else:
    if guess > 8:
        print('Too large')
    else:
        print('Too small')
print('The End')
```
Actually, it is just replacing `print('Unfortunately... I prefer 8')` with the second `if...else` cycle above.

To see the logic more clearly, look at the corresponding new flow chart tiltled "After improvemnet1" in the folder Python100days/Day3/Flow chart.

## Improvement2: While cycle
We are going to allow multiple trials for the game, using the cycle of `while`. First we can recognize the process that we want to repeat should start with inputting the guess and end with the second `if...else` branching.

The `while` cycle is of the following structure:
```Python
while condition is True:
     the operations in the case of True
```
Apply this to our game with small revisions, to ensure that `guess` is defined before `while` cycle looks at whether `guess != 8`.
Note the indents implying the contents in `while` cycle.
```Python
print('---------My first game---------')
temp=input('Guess one number:')
guess=int(temp)
while guess != 8:
    temp=input('Guess again:')
    guess=int(temp)
    if guess==8:
        print('Right!')
        print('Happy guessing!')
    else:
        if guess > 8:
            print('Too large')
        else:
            print('Too small')
print('The End')
```
Now the game will repeat infinitely many times until you guess `8`.
Now another problem occurs: in the first turn, no matter your guess is correct or nor, it will ask you to `guess again`, then enters the two cycles telling `too large` or `too small`. (I guess we needs more advanced technique) To be fixed later...

_Exercise1: If we would like to allow only one extra trial, how to do that?_
_See the end of this file for my solution._

You may use `and` operator; input two booleans and it outputs one boolean.
```Python
# it gives True only when two inputs are both True; it gives False otherwise
>>> True and True
True
>>> 1<2 and (3 == 8-5)   #parentheses are to ensure this calculations are done first
True
>>> False and 2<3
False
>>> False and False
False
```
## Improvement3: Random module随机模块
You may have noticed that the codes of our first game are typed in a field called "module". Now we introduce another tool called random module, which is used in our "module" field. 
I feel the "modules" in Python can refer to two things: the first is a package containing previously defined functions and other tools (just like the packages in LaTeX), such as the random module; the second is the field where we type codes of a program, distinct from the shell where we interact with the program by inputting.
We are going to use the function `randient()` in the random module, which gives a random integer. Again in the module where we have typed our codes of the game
```Python
import random    #import the random module before
secret = random.randient(1,10)   #assign the value randomly produced in the range of (1,10) by randient function, to the variable called secret
print('---------My first game---------')
temp=input('Guess one number:')
guess=int(temp)
while guess != secret:  #replace every "8" in original codes with secret
    temp=input('Guess again:')
    guess=int(temp)
    if guess== secret:
        print('Right!')
        print('Happy guessing!')
    else:
        if guess > secret:
            print('Too large')
        else:
            print('Too small')
print('The End')
```

There is an embarrassing case in the codes above: if the randomly generated value of `secret` is exactly the guess, it will directly print `The End`, which is very confusing. So, the following exercise is to improve the codes.

_Exercise2: Revise the codes such that if the first guess is correct, then there will be "Right!" "Happy guessing!" printed._

## My solutions to the exercises
Exercise1
_To evaluate the number operations of `while` cycle, it needs rounds counting and `and` operator simultaneously, thus I tried an alternative solution:  deleting `while` and adding one more `if...else`._
```Python
print('---------My first game---------')
temp=input('Guess one number:')
guess=int(temp)
if guess==8:
    print('Right!')
    print('Happy guessing!')
else:
    if guess > 8:
        print('Too large')
    else:
        print('Too small')
    temp=input('Guess again:')
    guess=int(temp)
    if guess==8:
        print('Right!')
        print('Happy guessing!')
    else:
        print('Unfortunately... I prefer 8')
print('The End')
```

Exercise2
```Python
import random    #import the random module before
secret = random.randient(1,10)   #assign the value randomly produced in the range of (1,10) by randient function, to the variable called secret
print('---------My first game---------')
temp=input('Guess one number:')
guess=int(temp)
if guess == secret:
    print('Right!')
    print('Happy guessing!')
else: 
    while 
    temp=input('Guess again:')
    guess=int(temp)
    if guess== secret:
        print('Right!')
        print('Happy guessing!')
    else:
        if guess > secret:
            print('Too large')
        else:
            print('Too small')
print('The End')
```



