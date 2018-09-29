# Class: Matrix
A matrix represents a mathematical matrix containing generic values.
This allows to make linear operations with matrices containing specific
objects representing maths or other scientific datas.

Users must be careful with method aliases: this type has methods
which modify the content of a matrix, and others which return a new one.
The first ones usually end with `!`, but there are some exceptions
like `Matrix#[]=`

## Defined in:
Matrix.cr

---
## Index:
  * [#*](#m--number---------new_matrix)
  * [#+](#m--other_matrix---new_matrix)
  * [#-](#m---other_matrix---new_matrix)
  * [#[]](#mrowscols---------------object)
  * [#[]=](#mrowcol--object)
  * [#each](#meach&block---m)
  * [#init](#initrowscols----------matrix)
  * [#to_s](#to_s---string)
  * [#tr](#mtr---new_matrix)

---
### m * number       -> new_matrix
### m * other_matrix -> new_matrix

If the argument is a number, a new matrix will be returned
with each component set to `m[i,j] * number`.

If the argument is a matrix, a matricial product is performed.
If matrices are incompatible, an error is raised
```
m1 := |1,2,3; 4,5,6|
m2 := |1,5; 1,6; 0,2|
m3 := |2,7; 9,8|

m1 + 3
#=> |3,6,9;
12,15,18|
m1 * m2
#=> |3,23;
9,62|

m1 * m3 #=> MathError: Incompatible matrices for product
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/Matrix.cr#L469)

---

### m + other_matrix -> new_matrix

It performs the sum [A] + [B] of two matrices.

If `m` and `other_matrix` do not have the same shape
an error will be raised.
```
m1 := |1,2,3; 4,5,6|
m2 := |1,0,1; 2,0,2|
m3 := |6,7; 8,9|

m1 + m2
#=> |2,2,4;
6,5,8|

m1 + m3 #=> MathError: Incompatible matrices for sum
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/Matrix.cr#L379)

---

### m - other_matrix -> new_matrix

It performs the difference [A] - [B] of two matrices.

If `m` and `other_matrix` do not have the same shape
an error will be raised.
```
m1 := |1,2,3; 4,5,6|
m2 := |1,0,1; 2,0,2|
m3 := |6,7; 8,9|

m1 - m2
#=> |0,2,2;
2,5,4|

m1 - m3 #=> MathError: Incompatible matrices for difference
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/Matrix.cr#L423)

---

### m[rows,cols]             -> object
### m[rows,cols_range]       -> matrix
### m[rows_range,cols]       -> matrix
### m[rows_range,cols_range] -> matrix

Returns a component of a matrix or a submatrix.
Indexes starts from `0`.
```
m := |1,2,3; 4,5,6; 7,8,9|
m[1,1]       #=> 5
m[0,1..2]    #=> |2,3|

m[1..2,1]    
#=> |5;
8| 

m[1..2,1..2]
#=> |5,6;
8,9|
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/Matrix.cr#L269)

---

### m[row,col] := object

It assigns to a component the given value (object).

If `row` or `col` is out of bounds, an error will be raised
```
m := |1,2; 3,4|
m[1,1] := 9
#=> |1,2;
3,9|

m[2,3] := 9 #=> IndexError: (Index [2,3] out of matrix)
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/Matrix.cr#L344)

---

### m.each(&block) -> m

Iterates over each component of a matrix
passing it to the given block
```
m := |1,2; 3,4|
m.each() { (v) printl v }
#=>
1
2
3
4
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/Matrix.cr#L566)

---

### init(rows,cols)        -> matrix
### init(rows,cols,&block) -> matrix

Initializes a matrix instance given the number of rows and columns.
If a block is provided, each component will be set to block return
value, else `null` will be used.
```coffee
new Matrix(2,2)
=> |null,null;
null,null|

new Matrix(2,2) { (i,j) i + j * 2}
=> |0,2;
1,3|
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/Matrix.cr#L151)

---

### to_s() -> string

Converts a matrix into a string. It is already formatted
by rows.
```
a := |1,2,3;4,5,6|
a.to_s() 
#=> |1,2,3;
4,5,6|
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/Matrix.cr#L206)

---

### m.tr() -> new_matrix

It transposes a matrix
```
m2 := |1,5; 1,6; 0,2|
m2.tr()
#=> |1,1,0;
5,6,2|
```

[see definition](https://github.com/LinCAS-lang/LinCAS/blob/master/src/Internal/Matrix.cr#L536)

---

