# Solution to Problem 12: A Parameter Revealed by a Row Operation

## 1. Problem Statement

Given the parameterized matrix family:
$$A(t)=\begin{pmatrix}1&2&3\\2&4&t\\0&1&1\end{pmatrix}$$

1. Perform the row operation $R_2 \leftarrow R_2 - 2R_1$ before evaluating the determinant, and record the resulting structure.
2. Using the resulting simplified structure, compute $\det A(t)$ and find all values of $t$ for which the matrix $A(t)$ is not invertible.
3. Explain what special relationship occurs among the rows of the original matrix for the critical value of $t$ found.

---

## 2. Theoretical Background and Concepts

- **Determinant Invariance Under Row Replacement:**  
  The operation $R_2 \leftarrow R_2 - 2R_1$ replaces the second row by the sum of itself and $-2$ times the first row. This elementary operation does not change the determinant:
  $$\det A(t) = \det(A_{\text{new}}(t)).$$
- **Cofactor Expansion of Sparse Matrices:**  
  When an elementary operation creates multiple zeros in a single row or column, expanding along that row or column drastically simplifies the determinant computation to a single lower-order minor.
- **Invertibility and Linear Dependence:**  
  A matrix is not invertible if and only if $\det A(t) = 0$. In terms of row vectors, $\det A(t) = 0$ occurs if and only if the rows are linearly dependent.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Perform the Prescribed Row Operation

Initial matrix:
$$A(t) = \begin{pmatrix}1&2&3\\2&4&t\\0&1&1\end{pmatrix}$$

Apply $R_2 \leftarrow R_2 - 2R_1$:
$$R_2 - 2R_1 = \begin{pmatrix}2 - 2(1) & 4 - 2(2) & t - 2(3)\end{pmatrix} = \begin{pmatrix}0 & 0 & t - 6\end{pmatrix}$$

The resulting matrix is:
$$A_1(t) = \begin{pmatrix}1&2&3\\0&0&t-6\\0&1&1\end{pmatrix}, \qquad \text{with } \det A(t) = \det A_1(t)$$

Notice the resulting structure: Row 2 now has two zeros and only one potentially non-zero entry, located in Column 3.

---

### Step 2: Compute $\det A_1(t)$ and Find Values Where $A(t)$ is Not Invertible

We expand $\det A_1(t)$ along Row 2:
$$\det A_1(t) = (-1)^{2+1} \cdot 0 \cdot M_{21} + (-1)^{2+2} \cdot 0 \cdot M_{22} + (-1)^{2+3} \cdot (t - 6) \cdot M_{23}$$
$$= -(t - 6) \cdot M_{23}$$

The minor $M_{23}$ is obtained by deleting Row 2 and Column 3 of $A_1(t)$:
$$M_{23} = \begin{vmatrix}1&2\\0&1\end{vmatrix} = (1)(1) - (2)(0) = 1$$

Therefore:
$$\det A(t) = -(t - 6) \cdot 1 = 6 - t$$

Matrix $A(t)$ is not invertible if and only if its determinant is zero:
$$\det A(t) = 0 \iff 6 - t = 0 \iff t = 6$$

Thus, the matrix $A(t)$ is not invertible for:
$$t = 6$$

---

### Step 3: Explanation of What Happens to the Rows for $t = 6$

Substitute $t = 6$ into the original matrix $A(t)$:
$$A(6) = \begin{pmatrix}1&2&3\\2&4&6\\0&1&1\end{pmatrix}$$

Examine the row vectors:
$$\mathbf{r}_1 = \begin{pmatrix}1 & 2 & 3\end{pmatrix}$$
$$\mathbf{r}_2 = \begin{pmatrix}2 & 4 & 6\end{pmatrix}$$
$$\mathbf{r}_3 = \begin{pmatrix}0 & 1 & 1\end{pmatrix}$$

Notice that:
$$\mathbf{r}_2 = 2 \mathbf{r}_1 \implies \mathbf{r}_2 - 2\mathbf{r}_1 = \mathbf{0}$$

**What special happens:**  
1. When $t = 6$, the second row is an **exact scalar multiple of the first row** ($\mathbf{r}_2 = 2\mathbf{r}_1$).
2. In the transformed matrix $A_1(6)$, the entire second row became a **zero row**: $\begin{pmatrix}0 & 0 & 0\end{pmatrix}$.
3. This creates an immediate linear dependence: $2\mathbf{r}_1 - \mathbf{r}_2 + 0\mathbf{r}_3 = \mathbf{0}$. The rank of the matrix drops from 3 to 2, compressing 3D space into a 2D plane, causing $\det A(6) = 0$ and rendering the matrix non-invertible.

---

## 4. Verification and Consistency Checks

1. **Sarrus' Rule Verification on $A(t)$:**
   $$\begin{array}{ccc|cc}
   1 & 2 & 3 & 1 & 2 \\
   2 & 4 & t & 2 & 4 \\
   0 & 1 & 1 & 0 & 1
   \end{array}$$
   - Main diagonals:
     $(1 \cdot 4 \cdot 1) + (2 \cdot t \cdot 0) + (3 \cdot 2 \cdot 1) = 4 + 0 + 6 = 10$
   - Anti-diagonals:
     $(0 \cdot 4 \cdot 3) + (1 \cdot t \cdot 1) + (1 \cdot 2 \cdot 2) = 0 + t + 4 = t + 4$
   - Determinant:
     $$\det A(t) = 10 - (t + 4) = 6 - t \quad \checkmark$$
   The formula $\det A(t) = 6 - t$ is confirmed.

2. **Invertibility for $t \ne 6$ Check ($t = 0$):**  
   For $t = 0$: $\det A(0) = 6 - 0 = 6 \ne 0 \implies$ invertible.  
   For $t = 6$: $\det A(6) = 0 \implies$ singular.  
   The condition $t = 6$ is uniquely confirmed.
