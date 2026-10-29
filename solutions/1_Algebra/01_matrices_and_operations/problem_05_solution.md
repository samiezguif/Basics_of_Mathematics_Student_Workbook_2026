# Solution to Problem 05: Matrix Times Vector

## 1. Problem Statement

Given:
$$A=\begin{pmatrix}2&-1\\1&3\end{pmatrix},\qquad x=\begin{pmatrix}4\\2\end{pmatrix}$$

1. Compute the product $Ax$.
2. Express $Ax$ as a linear combination of the columns of $A$, with coefficients coming from the vector $x$.

---

## 2. Theoretical Background and Concepts

- **Row-by-Column Definition of $Ax$:**  
  For $A \in \mathbb{R}^{m \times n}$ and $x \in \mathbb{R}^{n \times 1}$, the $i$-th entry of the product vector $y = Ax \in \mathbb{R}^{m \times 1}$ is the dot product of the $i$-th row of $A$ with $x$:
  $$y_i = \sum_{j=1}^n a_{ij} x_j.$$
- **Column Perspective of Matrix-Vector Multiplication:**  
  If we partition the matrix $A$ by its columns:
  $$A = \begin{pmatrix} \mathbf{a}_1 & \mathbf{a}_2 & \cdots & \mathbf{a}_n \end{pmatrix},$$
  then multiplying $A$ by the vector $x = \begin{pmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{pmatrix}$ produces a linear combination of the column vectors of $A$ weighted by the components of $x$:
  $$Ax = x_1 \mathbf{a}_1 + x_2 \mathbf{a}_2 + \cdots + x_n \mathbf{a}_n = \sum_{j=1}^n x_j \mathbf{a}_j.$$
  This perspective is fundamental in linear algebra because it establishes that the range (image) of a matrix is the span of its columns (the column space).

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute $Ax$ Using the Standard Row-Column Method

$$Ax = \begin{pmatrix}2&-1\\1&3\end{pmatrix}\begin{pmatrix}4\\2\end{pmatrix}$$

Compute each component of the resulting $2 \times 1$ vector:
- **First row:**
  $$(Ax)_1 = 2(4) + (-1)(2) = 8 - 2 = 6$$
- **Second row:**
  $$(Ax)_2 = 1(4) + 3(2) = 4 + 6 = 10$$

Thus:
$$Ax = \begin{pmatrix}6\\10\end{pmatrix}$$

### Step 2: Express $Ax$ as a Linear Combination of the Columns of $A$

First, identify the individual columns of matrix $A$:
$$\mathbf{a}_1 = \begin{pmatrix}2\\1\end{pmatrix},\qquad \mathbf{a}_2 = \begin{pmatrix}-1\\3\end{pmatrix}$$

The components of $x$ provide the scalar weights:
$$x_1 = 4,\qquad x_2 = 2$$

Now, form the linear combination:
$$Ax = x_1 \mathbf{a}_1 + x_2 \mathbf{a}_2 = 4\begin{pmatrix}2\\1\end{pmatrix} + 2\begin{pmatrix}-1\\3\end{pmatrix}$$

Carrying out the scalar multiplication and vector addition:
$$4\begin{pmatrix}2\\1\end{pmatrix} + 2\begin{pmatrix}-1\\3\end{pmatrix} = \begin{pmatrix}4 \cdot 2 \\ 4 \cdot 1\end{pmatrix} + \begin{pmatrix}2 \cdot (-1) \\ 2 \cdot 3\end{pmatrix} = \begin{pmatrix}8\\4\end{pmatrix} + \begin{pmatrix}-2\\6\end{pmatrix} = \begin{pmatrix}8 + (-2) \\ 4 + 6\end{pmatrix} = \begin{pmatrix}6\\10\end{pmatrix}$$

Both methods yield precisely the vector $\begin{pmatrix}6\\10\end{pmatrix}$.

---

## 4. Verification and Consistency Checks

1. **Agreement of Perspectives:**
   - Row perspective result: $\begin{pmatrix}6\\10\end{pmatrix}$.
   - Column combination result: $\begin{pmatrix}8 - 2 \\ 4 + 6\end{pmatrix} = \begin{pmatrix}6\\10\end{pmatrix}$.
   The two methods match identically.

2. **Linear System Check:**  
   If $Ax = \begin{pmatrix}6\\10\end{pmatrix}$, then solving $\begin{pmatrix}2&-1\\1&3\end{pmatrix}\begin{pmatrix}x_1\\x_2\end{pmatrix} = \begin{pmatrix}6\\10\end{pmatrix}$ should recover $x = \begin{pmatrix}4\\2\end{pmatrix}$.
   Using Cramer's Rule:
   - $\det(A) = 2(3) - (-1)(1) = 6 + 1 = 7 \ne 0$.
   - $x_1 = \frac{\det\begin{pmatrix}6&-1\\10&3\end{pmatrix}}{\det(A)} = \frac{6(3) - (-1)(10)}{7} = \frac{18 + 10}{7} = \frac{28}{7} = 4 \quad \checkmark$
   - $x_2 = \frac{\det\begin{pmatrix}2&6\\1&10\end{pmatrix}}{\det(A)} = \frac{2(10) - 6(1)}{7} = \frac{20 - 6}{7} = \frac{14}{7} = 2 \quad \checkmark$
   The solution vector $x = \begin{pmatrix}4\\2\end{pmatrix}$ is uniquely verified.

