# Eigenvalue


Eigenvalue algorithms are used to compute the eigenvalues and eigenvectors of a matrix. These concepts are fundamental in linear algebra and have numerous applications in physics, engineering, computer science, and more.


Given a square matrix A of size n x n, an eigenvector v is a non-zero vector that satisfies the following equation:
A * v = lambda * v
Where:
lambda (often written as λ) is a scalar known as the eigenvalue corresponding to the eigenvector v.
The matrix A transforms the vector v into a scalar multiple of itself.


To find the eigenvalues of a matrix A, we solve the characteristic equation:
det(A - lambda * I) = 0
Where:
I is the identity matrix of the same size as A.
det denotes the determinant of a matrix.
This equation is a polynomial of degree n in lambda, and the roots of this polynomial are the eigenvalues of A.


Several algorithms are used to compute the eigenvalues and eigenvectors of a matrix, with the two most common being Power Iteration and QR Algorithm.

Power Iteration:
Used to find the largest eigenvalue (in absolute magnitude) and its corresponding eigenvector.
The idea is to iteratively apply the matrix A to a random vector b and normalize the result at each step.
Over many iterations, the vector b converges to the eigenvector corresponding to the largest eigenvalue.

1. Start with a random vector b (often with norm 1).
2. Iterate: b_{k+1} = A * b_k / ||A * b_k||
3. Repeat until convergence.
4. The largest eigenvalue lambda is approximated by the Rayleigh quotient:
   lambda = (b.T * A * b) / (b.T * b)

Example
For a matrix A:
A = [[2, 1],
     [1, 3]]
We want to find the largest eigenvalue and its corresponding eigenvector.

Start with a random vector b:
b = [1, 1]

Iterate:
b_1 = A * b = [3, 4]
Normalize: b_1 = [0.6, 0.8]
b_2 = A * b_1 = [2.6, 3.8]
Normalize: b_2 = [0.573, 0.819]

Continue until convergence...
Approximate the largest eigenvalue using the Rayleigh quotient:
lambda = (b.T * A * b) / (b.T * b)


QR Algorithm:
Used to find all eigenvalues of a matrix.
This algorithm repeatedly decomposes the matrix A_k into a product of an orthogonal matrix Q and an upper triangular matrix R using QR decomposition:
A_k = Q_k * R_k
A_{k+1} = R_k * Q_k
Over many iterations, the matrix A_k converges to a form where the diagonal elements approximate the eigenvalues of A.

Example
For a matrix A:
A = [[1, 2],
     [2, 1]]
     
Compute the QR decomposition:
A_1 = Q_1 * R_1

Update the matrix:
A_2 = R_1 * Q_1
Repeat the process, and after several iterations, the matrix A_k will converge to an upper triangular matrix with the diagonal elements being the eigenvalues.


Time Complexity
Power Iteration: O(n^2) per iteration for a matrix of size n x n. The number of iterations required depends on the convergence criteria.
QR Algorithm: O(n^3) per iteration due to the QR decomposition, but it computes all eigenvalues simultaneously.
