---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

(lecture8)=

# Lecture8 - Columns and rows of matrix A

## The geometry of linear equations
Consider the two below equations. We want to solve x and y.
\begin{eqnarray*}
2x - y &=& 0 \\\\
-x + 2y &=& 3
\end{eqnarray*}

We can write them in matrix form:
\begin{eqnarray*}
\underbrace{\begin{bmatrix}
2 & -1 \\
-1 & 2
\end{bmatrix}}_{A}
\underbrace{\begin{bmatrix}
x \\
y
\end{bmatrix}}_{\vec{x}}
=
\underbrace{\begin{bmatrix}
0 \\
3
\end{bmatrix}}_{\vec{b}}
\end{eqnarray*}

- row picture

- column picture (linear combination of columns)
\begin{eqnarray*}
x
\underbrace{\begin{bmatrix}
2 \\
-1
\end{bmatrix}}_{\vec{col1}}
+
y
\underbrace{\begin{bmatrix}
-1 \\
2
\end{bmatrix}}_{\vec{col2}}
=
\underbrace{\begin{bmatrix}
0 \\
3
\end{bmatrix}}_{\vec{b}}
\end{eqnarray*}

Row picture shows more intuitive depictions, at least, in three dimensional questions. For example:
\begin{eqnarray*}
2x-y &=& 0 \\\\
-x+2y-z &=& -1 \\\\
-3y+4z &=& 4
\end{eqnarray*}

In matrix form:
\begin{eqnarray*}
\underbrace{\begin{bmatrix}
2 & -1 & 0 \\
-1 & 2 & -1 \\
0 & -3 & 4
\end{bmatrix}}_{A}
\underbrace{\begin{bmatrix}
x \\
y \\
z
\end{bmatrix}}_{\vec{x}}
=
\underbrace{\begin{bmatrix}
0 \\
-1 \\
4
\end{bmatrix}}_{\vec{b}}
\end{eqnarray*}

- row picture

- column picture
\begin{eqnarray*}
x
\underbrace{\begin{bmatrix}
2 \\
-1 \\
0
\end{bmatrix}}_{\vec{col1}}
+
y
\underbrace{\begin{bmatrix}
-1 \\
2 \\
3
\end{bmatrix}}_{\vec{col2}}
+
z
\underbrace{\begin{bmatrix}
0 \\
-1 \\
4
\end{bmatrix}}_{\vec{col3}}
=
\underbrace{\begin{bmatrix}
0 \\
-1 \\
4
\end{bmatrix}}_{\vec{b}}
\end{eqnarray*}

We can solve this system. If we change the vector on right hand side:
\begin{eqnarray*}
x
\underbrace{\begin{bmatrix}
2 \\
-1 \\
0
\end{bmatrix}}_{\vec{col1}}
+
y
\underbrace{\begin{bmatrix}
-1 \\
2 \\
3
\end{bmatrix}}_{\vec{col2}}
+
z
\underbrace{\begin{bmatrix}
0 \\
-1 \\
4
\end{bmatrix}}_{\vec{col3}}
=
\underbrace{\begin{bmatrix}
1 \\
1 \\
-3
\end{bmatrix}}_{\vec{b}}
\end{eqnarray*}
can we still solve it? So a more general questions is: 
1. can we solve Ax = b fpr every b?
2. do the linear combinations of the collumns fill 3-D space?

For this matrix A, yes because A is nonsingular or invertible!

## Ax is a linear combination of columns of A
\begin{eqnarray*}
\begin{bmatrix}
2 & 5 \\
1 & 3 \\
\end{bmatrix}
\begin{bmatrix}
1 \\
2 \\
\end{bmatrix}
=
1
\underbrace{\begin{bmatrix}
2 \\
1 \\
\end{bmatrix}}_{col1}
+
2
\underbrace{\begin{bmatrix}
5 \\
3 \\
\end{bmatrix}}_{col2}
=
\begin{bmatrix}
12 \\
7 \\
\end{bmatrix}
\end{eqnarray*}


## Elimination with matrices
\begin{eqnarray*}
x+2y+z &=& 2 \\\\
3x+8y+z &=& 12 \\\\
4y+z &=& 2
\end{eqnarray*}

In matrix form:
\begin{eqnarray*}
\underbrace{\begin{bmatrix}
1 & 2 & 1 \\
3 & 8 & 1 \\
0 & 4 & 1
\end{bmatrix}}_{A}
\underbrace{\begin{bmatrix}
x \\
y \\
z
\end{bmatrix}}_{\vec{x}}
=
\underbrace{\begin{bmatrix}
2 \\
12 \\
2
\end{bmatrix}}_{\vec{b}}
\end{eqnarray*}

Three keys:
1. back-substitution
2. elimination matrices
3. matrix multiplication

We consider augumented matrix along with back-substitution:
\begin{eqnarray*}
&\begin{matrix}
1 & 2 & 1 & 2 \\
3 & 8 & 1 & 12 \\
0 & 4 & 1 & 2
\end{matrix}&\\\\
\Longrightarrow
&\begin{matrix}
1 & 2 & 1 & 2 \\
0 & 2 & -2 & 6 \\
0 & 4 & 1 & 2
\end{matrix}&\\\\
\Longrightarrow
\text{  }
&\begin{matrix}
1 & 2 & 1 & 2 \\
0 & 2 & -2 & 6 \\
0 & 0 & 5 & -10
\end{matrix}&
\end{eqnarray*}

Now we use back-substitution:
\begin{eqnarray*}
x+2y+z &=& 2 \\\\
  2y-2z &=& 6 \\\\
     5z &=& -10\\\\
\Longrightarrow
x=2, y=1, z&=&-2
\end{eqnarray*}

```{note}
\begin{eqnarray*}
\begin{bmatrix}
x & x & x \\
x & x & x \\
x & x & x 
\end{bmatrix}
\begin{bmatrix}
3 \\
4 \\
5
\end{bmatrix}
=3\times column_{1} + 4\times cololumn_{2} + 5\times column_{3}
\end{eqnarray*}

\begin{eqnarray*}
\begin{bmatrix}
1 & 2 & 7
\end{bmatrix}
\begin{bmatrix}
x & x & x \\
x & x & x \\
x & x & x
\end{bmatrix}
= 1\times row_{1} + 2\times row_{2} + 7\times row_{3}
\end{eqnarray*}
```

## Elimination with elementary matrices
1. substract 3*row1 from row2 
\begin{eqnarray*}

\underbrace{\begin{bmatrix}
1 & 0 & 0 \\
-3 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}}_{E_{21}}

\underbrace{\begin{bmatrix}
1 & 2 & 1 \\
3 & 8 & 1 \\
0 & 4 & 1
\end{bmatrix}}_{A}

=

\begin{bmatrix}
1 & 2 & 1 \\
0 & 2 & -2 \\
0 & 4 & 1
\end{bmatrix}

\end{eqnarray*}

2. subtract 2*row2 from row3
\begin{eqnarray*}

\underbrace{\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & -2 & 1
\end{bmatrix}}_{E_{32}}

\begin{bmatrix}
1 & 2 & 1 \\
0 & 2 & -2 \\
0 & 4 & 1
\end{bmatrix}

\underbrace{\begin{bmatrix}
1 & 2 & 1 \\
0 & 2 & -2 \\
0 & 0 & 5
\end{bmatrix}}_{U}

\end{eqnarray*}

\begin{eqnarray*}
\Longrightarrow E_{32}(E_{21}A) = U \Longrightarrow (E_{32}E_{21})A = U
\end{eqnarray*}

```{note}
Inverse of elementary matrix
\begin{eqnarray*}

\underbrace{\begin{bmatrix}
1 & 0 & 0 \\
3 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}}_{E_{21}^{-1}}

\underbrace{\begin{bmatrix}
1 & 0 & 0 \\
-3 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}}_{E_{21}}

= \begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}

\end{eqnarray*}

```

## Permutation matrices

row operation on the left:
\begin{eqnarray*}

\begin{bmatrix}
0 & 1 \\
1 & 0 
\end{bmatrix}

\begin{bmatrix}
a & b \\
c & d 
\end{bmatrix}

= 

\begin{bmatrix}
c & d \\
a & b 
\end{bmatrix}

\end{eqnarray*}

column operation on the right:
\begin{eqnarray*}

\begin{bmatrix}
a & b \\
c & d 
\end{bmatrix}

\begin{bmatrix}
0 & 1 \\
1 & 0
\end{bmatrix}

= 

\begin{bmatrix}
b & a \\
d & c
\end{bmatrix}

\end{eqnarray*}

