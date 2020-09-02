## The tower of Hanoi
We shall solve the problem of the tower of Hanoi using recursion. In this problem, there are 64 plates in ascending order at one pole X, with another two poles Y and Z. We want to move the plates to another pole, still in ascending order. Only one plate can be moved each time, and we can only put smaller plates over a larger one.

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

And we can divide them into even more questions...... 

```Python
def hanoi(n, x, y, z):
    if n == 1:
        print(x, '--->', z)
    else:
        hanoi(n-1, x, z, y) #move the first (n-1) plates from x to y
        print(x, '___>', z) #move the bottom (largest) from x to z   #I use ___> here to make it easier to recognize
        hanoi(n-1, y, x, z) #move those (n-1) plates from y to z

n = int(input('Insert the number of layers of the tower of Hanoi: '))
hanoi(n, 'X', 'Y', 'Z')
```
Run it and input 3
```Python
Insert the number of layers of the tower of Hanoi: 3
X ---> Z
X ___> Y
Z ---> Y
X ___> Z
Y ---> X
Y ___> Z
X ---> Z
```
