So far, we've seen what vectors and matrices are, how we can manipulate them, and also some special types of matrices. We can also perform basic operations on them such as matrix addition and multiplication.

This activity is our first look at **linear transformation** and **eigendecomposition**. These are complex topics that are crucial to various parts of the machine learning process.

### Linear Transformation (a.k.a. Matrix Multiplication)

We can imagine matrix multiplication **A**_**x_* = **b** as a _linear transformation_ of a vector **x** with a matrix **A**. This multiplcation results in the coordinates of vector **x** being transformed into new coordinates of vector **b**.

Note

We can _linearly transform_ _n_ vectors at once by composing them to a matrix **X**=[**x**1,**x**2,...,**x**n]T. Now we have an equation **A**_**X_* = **B** similar to the one mentioned above where **A** is a transformation matrix, **X** is a matrix composed of the vectors we want to transform, and **B** is a matrix of the transformed vectors.

Instruction

Read about [**linear transformation in this resource by Math is Fun**](https://www.mathsisfun.com/algebra/matrix-transform.html). Focus on the transformation app at the beginning of the page and play around with different transformations.

### Eigendecomposition

_Eigendecomposition_ of a matrix is a type of decomposition that involves decomposing a square matrix into a set of **eigenvectors** and **eigenvalues**.

Warning

_Eigendecomposition_ is only possible on **square** matrices!

Instruction

Watch the video below to learn about the concepts of eigendecomposition.

To fully understand the concepts you can combine the knowledge from the video with the article below.

Instruction

Read about [eigendecomposition in this resource by Math is Fun](https://www.mathsisfun.com/algebra/eigenvalue.html).