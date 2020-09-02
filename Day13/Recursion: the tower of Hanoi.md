## The tower of Hanoi
We shall solve the problem of the tower of Hanoi using recursion. In this problem, there are 64 plates in ascending order at one pole X, with another two poles Y and Z. We want to move the plates to another pole, still in ascending order. Only one plate can be moved each time, and we can only put smaller plates over a larger one.

To simplify the problem, we divide it into three main steps:
1. Move the first 63 plates from X to Y;
2. Move the 64-th (largest) plate from X to Z;
3. Move those 63 plates from Y to Z.

So there are two questions:
1. Move the first 63 plates from X to Y, using Z;
2. Move theose 63 plates from Y to Z, using X.
