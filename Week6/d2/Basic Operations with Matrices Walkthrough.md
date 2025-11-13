This activity introduces some important functions in `Python/NumPy`. Most `machine-learning` algorithms in `Python` use this library to manipulate data and do computations so it is important to get comfortable using it.

We will begin our practice by creating and manipulating _vectors_ and _matrices_ through examples.

### Importing the NumPy Library

Before we start using [NumPy](https://numpy.org/) for our work, we have to import it into our Jupyter notebook:

```python
import numpy as np
```

### Creating Vectors and Matrices with `Numpy`

We will start by creating **a vector**. This is a [numpy.ndarray](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.html) (n-dimensional array) with one dimension:

```python
x = np.array([1, 2, 3, 4])
x
```

Now, create a (3x2) **matrix** (a 2-dimensional array) with nested brackets: `python A = np.array([[1,2],[3,4],[5,6]]) A`

By using a Python built-in function `type()`, we can check that both objects are represented as `numpy.ndarray`: `python type(x)`

```python
type(A)
```

### Shape

**The shape** of an array tells us the number of values for each dimension. For a 2-dimensional array, it will give us the number of rows and the number of columns. Let’s find _the shape_ of the previous 2-dimensional matrix **A**. Since **A** is a `numpy.ndarray` (it was created with the `array()` function), we can access its `shape` attribute with:

```python
A.shape
```

We can see that **A** has 3 rows and 2 columns.

Let’s check _the shape_ of our vector **x**:

```python
x.shape
```

As expected, we can see that **x** has only one dimension. The number corresponds to the length of the array:

```python
len(x)
```

### Transposition of a Matrix

We can access the `transpose()` method of a `numpy.ndarray` object by:

```python
A_T = A.T
```

or

```python
A_T = A.transpose()
```

We can check the dimensions of the _transposed matrix_:

```python
A_T.shape
```

We can see that, after _transposition_, the number of columns becomes the number of rows and vice versa.

### Matrix Addition

With `Numpy` we can **add up matrices** just as we would scalars.

Create a new matrix **B**:

```python
B = np.array([[2, 5], [7, 4], [4, 3]])
B
```

_Add_ the matrix **A** to **B** and save the result in a matrix **C**: `python C = A + B C`

It is also possible to _add_ a scalar to a matrix. That means _adding_ this scalar to each cell of the matrix: `python D = A + 1 D`

`Numpy` can handle operations on arrays of different shapes. A smaller array will be extended to match the shape of a bigger one. This is called **broadcasting**. The advantage is that it is done under the hood – in C (like any other vectorized operation in `Numpy`). Actually, we've already used _broadcasting_ in the example above. The scalar was converted to an array of the same _shape_ as the matrix **A**.

Warning

_Broadcasting_ works only if the first array has the same number of rows as the second one, and one of the arrays has only one column (e.g. a matrix **B**i,1 can be _broadcast_ across **A**i,j). _Broadcasting_ of a scalar value works every time.

### Matrix Multiplication

The standard way to **multiply** matrices is **not** to multiply each element of one matrix with each element of another one (called the element-wise product), but to calculate the sum of the products between the rows and the columns. A **matrix product** is also called a `dot product`.

The number of columns of the first matrix must be equal to the number of rows of the second one. If the dimensions of the first matrix are (m×n), the second matrix needs to be of shape (n×x). The resulting matrix will have the shape (m×x).

To compute _a matrix product_ we can use the `Numpy` function `dot()`.

Define a matrix **A** with the shape (3x2): `python A = np.array([[1, 2], [3, 4], [5, 6]]) A`

Define a matrix **B** with the shape (2x1): `python B = np.array([[2], [4]]) B`

Because the matrix **A** has 2 columns and the matrix **B** has 2 rows, we can multiply them and store the result in a matrix **C**: `python C = np.dot(A, B) C`

It is equivalent to using the `dot()` method of `numpy.ndarray`:

```python
C = A.dot(B)
C
```

Let’s check the shape: `python C.shape`

As expected, the new matrix **C** has the shape (3x1).

Warning

_Matrix multiplication_ is not commutative ( **AB**!=**BA**)

### Identity Matrices

An **identity matrix **I**n** is a special square (nxn) matrix which has 1s on the main diagonal and 0s everywhere else.

_An identity matrix_ can be created with the `Numpy` function `eye()`:

Let’s check the result: `python I = np.eye(3) I`

When multiplying _an identity matrix_ with another matrix the result is the same matrix:

```python
IA = I.dot(A)
IA
```

### Determinant

To compute **a determinant** of a matrix using `Numpy`, we have to use the **linalg module**. The [numpy.linalg](https://docs.scipy.org/doc/numpy/reference/routines.linalg.html) module specializes in linear algebra with matrices and vectors.

Define a new matrix **M** with the shape (2x2):

```python
M = np.array([[1,2],[3,4]])
M
```

Compute the determinant of the matrix **M**: `python det_M = np.linalg.det(M) det_M`

Warning

_Determinants_ can be computed only from square matrices.

This code shows a `LinAlgError`:

```python
M = np.array([[1,2],[3,4],[5,6]])
det_M = np.linalg.det(M)
det_M
```

### Inverse Matrices

**The inverse matrix** of **A** with shape (nxn) is denoted as **A**-1. It is a matrix that when multiplied by **A**, resultsin an identity matrix. (**AA**-1 = **I**n). This means that if we apply a linear transformation to the matrix with **A**, it is possible to go back with **A**-1. This provides a way to cancel the transformation.

For this example, we will use the `Numpy` function `linalg.inv()` to calculate _the inverse_ of **A**. Let’s start by creating **A** with the shape (3x3):

```python
A = np.array([[3, 0, 2], [2, 0, -2], [0, 1, 1]])
A
```

Now we calculate its _inverse_:

```python
A_inv = np.linalg.inv(A)
A_inv
```

We can check that **A_inv** is really _the inverse_ of **A**:

```python
I = A_inv.dot(A)
I
```

Instruction

Read more about the available [`numpy.ndarray` methods](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.html).