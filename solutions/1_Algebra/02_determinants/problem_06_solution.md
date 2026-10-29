# Solution to Problem 06: Parameter and Invertibility

## 1. Problem Statement

Given the parameterized family of matrices:
$$A(t)=\begin{pmatrix}t&1\\2&t\end{pmatrix}$$

1. Find all values of the real parameter $t$ for which the matrix $A(t)$ is not invertible.
2. Explain the fundamental mathematical connection between non-invertibility and the vanishing of the determinant.

---

## 2. Theoretical Background and Concepts

- **Determinant of a $2 \times 2$ Matrix:**  
  For $M = \begin{pmatrix}a&b\\c&d\end{pmatrix}$, $\det M = ad - bc$.
- **Invertibility Criterion:**  
  A square matrix $A$ is invertible if and only if there exists a matrix $A^{-1}$ such that $A A^{-1} = A^{-1} A = I$. By the Invertible Matrix Theorem:
  $$A \text{ is invertible} \iff \det A \ne 0.$$
  Conversely:
  $$A \text{ is not invertible (singular)} \iff \det A = 0.$$
- **Geometric and Algebraic Meaning of $\det A = 0$:**
  - **Geometric:** The matrix defines a linear map $T_A: \mathbb{R}^2 \to \mathbb{R}^2$. The determinant measures how the map scales oriented areas. When $\det A = 0$, areas are collapsed to zero, compressing the 2D plane into a 1D line (or the origin). A collapsed dimension cannot be uniquely undone, meaning no inverse map exists.
  - **Algebraic:** $\det A = 0$ implies that the columns (and rows) of $A$ are linearly dependent. Consequently, the null space $\ker(A)$ contains non-trivial vectors ($Ax = \mathbf{0}$ for some $x \ne \mathbf{0}$), violating injectivity.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute the Determinant of $A(t)$

For $A(t) = \begin{pmatrix}t&1\\2&t\end{pmatrix}$:
$$\det A(t) = (t)(t) - (1)(2) = t^2 - 2$$

---

### Step 2: Solve for Values of $t$ Where $A(t)$ is Not Invertible

The matrix $A(t)$ fails to be invertible if and only if its determinant is zero:
$$\det A(t) = 0 \iff t^2 - 2 = 0 \iff t^2 = 2$$

Taking the square root on both sides yields two real solutions:
$$t = \sqrt{2} \quad \text{or} \quad t = -\sqrt{2}$$

Thus, the matrix $A(t)$ is not invertible precisely when:
$$t \in \{-\sqrt{2}, \sqrt{2}\}$$

---

### Step 3: Detailed Explanation of the Connection Between $\det A = 0$ and Non-Invertibility

Let us examine the explicit row and column structure of $A(t)$ at these critical parameter values:

1. **Case $t = \sqrt{2}$:**
   $$A(\sqrt{2}) = \begin{pmatrix}\sqrt{2}&1\\2&\sqrt{2}\end{pmatrix}$$
   Notice that the second row is $\sqrt{2}$ times the first row:
   $$\mathbf{r}_2 = \begin{pmatrix}2 & \sqrt{2}\end{pmatrix} = \sqrt{2} \begin{pmatrix}\sqrt{2} & 1\end{pmatrix} = \sqrt{2}\mathbf{r}_1.$$
   Because the rows are linearly dependent, the matrix has rank $1 < 2$. The linear map maps all of $\mathbb{R}^2$ onto the 1D line spanned by $\begin{pmatrix}\sqrt{2}\\2\end{pmatrix}$.

2. **Case $t = -\sqrt{2}$:**
   $$A(-\sqrt{2}) = \begin{pmatrix}-\sqrt{2}&1\\2&-\sqrt{2}\end{pmatrix}$$
   Here, the second row is $-\sqrt{2}$ times the first row:
   $$\mathbf{r}_2 = \begin{pmatrix}2 & -\sqrt{2}\end{pmatrix} = -\sqrt{2} \begin{pmatrix}-\sqrt{2} & 1\end{pmatrix} = -\sqrt{2}\mathbf{r}_1.$$
   Again, the rows are linearly dependent, and the rank is 1.

For any $t \notin \{-\sqrt{2}, \sqrt{2}\}$, $\det A(t) = t^2 - 2 \ne 0$, the rows are linearly independent, and the inverse matrix is well-defined:
$$A(t)^{-1} = \frac{1}{t^2 - 2}\begin{pmatrix}t&-1\\-2&t\end{pmatrix}.$$
When $t = \pm\sqrt{2}$, this formula would involve division by zero, reflecting the non-existence of the inverse.

---

## 4. Verification and Consistency Checks

1. **Null Space Check for $t = \sqrt{2}$:**  
   Find a non-zero vector $v = \begin{pmatrix}x\\y\end{pmatrix}$ such that $A(\sqrt{2})v = \mathbf{0}$:
   $$\begin{pmatrix}\sqrt{2}&1\\2&\sqrt{2}\end{pmatrix}\begin{pmatrix}x\\y\end{pmatrix} = \begin{pmatrix}\sqrt{2}x + y\\2x + \sqrt{2}y\end{pmatrix} = \begin{pmatrix}0\\0\end{pmatrix}$$
   Setting $x = 1$, we get $y = -\sqrt{2}$. Testing $v = \begin{pmatrix}1\\-\sqrt{2}\end{pmatrix} \ne \mathbf{0}$:
   $$A(\sqrt{2})\begin{pmatrix}1\\-\sqrt{2}\end{pmatrix} = \begin{pmatrix}\sqrt{2}(1) + 1(-\sqrt{2})\\2(1) + \sqrt{2}(-\sqrt{2})\end{pmatrix} = \begin{pmatrix}0\\0\end{pmatrix} \quad \checkmark$$
   The kernel contains non-zero vectors, confirming non-invertibility.

2. **Null Space Check for $t = -\sqrt{2}$:**  
   Testing $v = \begin{pmatrix}1\\\sqrt{2}\end{pmatrix} \ne \mathbf{0}$:
   $$A(-\sqrt{2})\begin{pmatrix}1\\\sqrt{2}\end{pmatrix} = \begin{pmatrix}-\sqrt{2}(1) + 1(\sqrt{2})\\2(1) - \sqrt{2}(\sqrt{2})\end{pmatrix} = \begin{pmatrix}0\\0\end{pmatrix} \quad \checkmark$$
   The kernel is again non-trivial, confirming non-invertibility.
