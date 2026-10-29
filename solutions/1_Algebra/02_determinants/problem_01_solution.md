# Solution to Problem 01: Determinant of a 2×2 Matrix

## 1. Problem Statement

Compute the determinants of the following two matrices:
$$M_1 = \begin{pmatrix}3&-2\\5&4\end{pmatrix},\qquad M_2 = \begin{pmatrix}1&7\\2&14\end{pmatrix}$$

Determine which matrix is invertible, and justify your answer based on the computed determinants.

---

## 2. Theoretical Background and Concepts

- **Determinant of a $2 \times 2$ Matrix:**  
  For an arbitrary $2 \times 2$ matrix $M = \begin{pmatrix}a&b\\c&d\end{pmatrix}$, its determinant is defined by the difference of the diagonal products:
  $$\det M = \begin{vmatrix}a&b\\c&d\end{vmatrix} = ad - bc.$$
- **Invertibility Criterion (Invertible Matrix Theorem):**  
  A square matrix $M \in \mathbb{R}^{n \times n}$ is invertible (non-singular) if and only if its determinant is non-zero:
  $$M \text{ is invertible} \iff \det M \ne 0.$$
- **Geometric Interpretation:**  
  The determinant represents the signed area scaling factor of the linear transformation defined by the matrix. If $\det M = 0$, the transformation collapses 2D space into a 1D line or a point, losing information and preventing the existence of an inverse mapping.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute $\det M_1$

For $M_1 = \begin{pmatrix}3&-2\\5&4\end{pmatrix}$:
$$\det M_1 = (3)(4) - (-2)(5) = 12 - (-10) = 12 + 10 = 22$$

### Step 2: Compute $\det M_2$

For $M_2 = \begin{pmatrix}1&7\\2&14\end{pmatrix}$:
$$\det M_2 = (1)(14) - (7)(2) = 14 - 14 = 0$$

### Step 3: Determine Invertibility and Justify

- **Matrix $M_1$:**  
  Since $\det M_1 = 22 \ne 0$, **matrix $M_1$ is invertible**. Its inverse exists and is explicitly given by:
  $$M_1^{-1} = \frac{1}{\det M_1}\begin{pmatrix}4&2\\-5&3\end{pmatrix} = \frac{1}{22}\begin{pmatrix}4&2\\-5&3\end{pmatrix} = \begin{pmatrix}\frac{2}{11} & \frac{1}{11} \\ -\frac{5}{22} & \frac{3}{22}\end{pmatrix}.$$

- **Matrix $M_2$:**  
  Since $\det M_2 = 0$, **matrix $M_2$ is not invertible (it is singular)**.  
  Notice that the second row is an exact scalar multiple of the first row:
  $$\mathbf{r}_2 = 2 \mathbf{r}_1 \implies (2, 14) = 2(1, 7).$$
  Consequently, the rows (and columns) are linearly dependent, meaning the range of $M_2$ has dimension 1 (rank 1), so $M_2$ cannot have an inverse.

---

## 4. Verification and Consistency Checks

1. **Direct Matrix Multiplication Check for $M_1$:**  
   $$M_1 M_1^{-1} = \begin{pmatrix}3&-2\\5&4\end{pmatrix} \cdot \frac{1}{22}\begin{pmatrix}4&2\\-5&3\end{pmatrix} = \frac{1}{22}\begin{pmatrix}3(4)+(-2)(-5) & 3(2)+(-2)(3) \\ 5(4)+4(-5) & 5(2)+4(3)\end{pmatrix} = \frac{1}{22}\begin{pmatrix}22&0\\0&22\end{pmatrix} = \begin{pmatrix}1&0\\0&1\end{pmatrix} = I \quad \checkmark$$

2. **Null Space Check for $M_2$:**  
   If $M_2$ were invertible, the only solution to $M_2 x = 0$ would be $x = 0$.  
   Testing the non-zero vector $x = \begin{pmatrix}-7\\1\end{pmatrix}$:
   $$M_2 x = \begin{pmatrix}1&7\\2&14\end{pmatrix}\begin{pmatrix}-7\\1\end{pmatrix} = \begin{pmatrix}1(-7)+7(1)\\2(-7)+14(1)\end{pmatrix} = \begin{pmatrix}0\\0\end{pmatrix}.$$
   Since the null space is non-trivial ($\ker M_2 \ne \{\mathbf{0}\}$), $M_2$ is not injective and cannot be invertible.
