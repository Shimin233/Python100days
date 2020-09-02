## The tower of Hanoi
We shall solve the problem of the tower of Hanoi using recursion. In this problem, there are 64 plates in ascending order at one pole X, with another two poles Y and Z. We want to move the plates to another pole, still in ascending order. Only one plate (which is on the top at each pole) can be moved each time, and we can only put smaller plates over a larger one.

To simplify the problem, we divide it into three main steps:
1. Move the first 63 plates from X to Y;
2. Move the 64-th (largest) plate from X to Z;
3. Move those 63 plates from Y to Z.

So there are two questions:
a Move the first 63 plates from X to Y, using Z;
b Move theose 63 plates from Y to Z, using X.

Moreover, we can divide question a into more smaller questions:
a.1 Move the first 62 plates from X to Z;
a.2 Move the 63-rd plate from X to Y;
a.3 Move those 62 plates from Z to Y.
Also, divide question b likewise:
b.1 Move the first 62 plates from Y to X;
b.2 Move the 63-rd from Y to Z;
b.3 Move those 62 plates from X to Z.

And we can divide them into even more questions...... We apply recursions to those of the same form, in particular, the questions x.1 and x.3.

```Python
def hanoi(n, x, y, z):   #assign the names of the three poles to x, y, and z
    if n == 1:
        print(x, '--->', z)  #this reveals that the variable x = the starting pole and z = the ending pole, with y = assisting moving
    else:
        hanoi(n-1, x, z, y) #move the first (n-1) plates from x to y #x = the starting pole and y = the ending pole, with z = assisting moving
        print(x, '___>', z) #move the bottom (largest) from x to z   #I use ___> here to make it easier to recognize
        hanoi(n-1, y, x, z) #move those (n-1) plates from y to z #y = the starting pole and z = the ending pole, with x = assisting moving

n = int(input('Insert the number of layers of the tower of Hanoi: '))
hanoi(n, 'X', 'Y', 'Z')
```
Run it and input 3
```Python
Insert the number of layers of the tower of Hanoi: 3
X ---> Z #Hanoi(1, 'X', 'Y', 'Z'), from Hanoi(2, 'X', 'Z', 'Y')
X ___> Y #print('X', '___>', 'Y'), from Hanoi(2, 'X', 'Z', 'Y')
Z ---> Y #Hanoi(1, 'Z', 'X', 'Y'), from Hanoi(2, 'X', 'Z', 'Y')
X ___> Z #print('X', '___>', 'Z'), from Hanoi(3, 'X', 'Y', 'Z')
Y ---> X #the following three lines all come from Hanoi(2, 'Y', 'X', 'Z')
Y ___> Z
X ---> Z
```
The output is exactly guiding us to move the plates as desired.

## Keys
Recursion: tower of Hanoi 
- split steps into smaller ones, and recognize the part of repeating itself (so apply recursion there)
