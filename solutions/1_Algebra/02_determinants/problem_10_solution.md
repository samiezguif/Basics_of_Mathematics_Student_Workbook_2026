# Solution to Problem 10: Detecting Dependence

## 1. Problem Statement

Given the matrix:
$$A = \begin{pmatrix}1&2&3\\2&4&6\\0&1&5\end{pmatrix}$$

1. Without carrying out a full determinant expansion, explain why $\det A = 0$.
2. Identify a specific linear dependence between the rows of $A$.
3. Connect this linear dependence with the non-invertibility of the matrix.

---

## 2. Theoretical Background and Concepts

- **Linear Dependence of Vectors:**  
  A set of vectors $\{\mathbf{v}_1, \mathbf{v}_2, \dots, \mathbf{v}_k\}$ is linearly dependent if there exist scalars $c_1, c_2, \dots, c_k$, not all zero, such that:
  $$c_1 \mathbf{v}_1 + c_2 \mathbf{v}_2 + \dots + c_k \mathbf{v}_k = \mathbf{0}.$$
  For two vectors, linear dependence simply means one is a scalar multiple of the other: $\mathbf{v}_2 = c \mathbf{v}_1$.
- **Determinant and Linear Dependence:**  
  If the rows (or columns) of an $n \times n$ matrix are linearly dependent, its determinant is identically zero:
  $$\det A = 0.$$
  *Proof sketch:* If $\mathbf{r}_2 = c \mathbf{r}_1$, we can apply the row replacement $R_2 \leftarrow R_2 - c R_1$. This operation does not alter the determinant. But the new second row becomes entirely zeros: $(0, 0, \dots, 0)$. Expanding along this zero row yields $\det A = 0$.
- **Rank and the Invertible Matrix Theorem:**  
  For an $n \times n$ matrix $A$, the following statements are equivalent:
  - $A$ is invertible.
  - $\det A \ne 0$.
  - The rows (and columns) of $A$ are linearly independent.
  - $\operatorname{rank}(A) = n$ (full rank).
  - The null space of $A$ contains only the zero vector ($\ker A = \{\mathbf{0}\}$).

---

## 3. Detailed Step-by-Step Solution

### Step 1: Identify the Specific Row Dependence

Let us examine the three row vectors of matrix $A$:
$$\mathbf{r}_1 = \begin{pmatrix}1 & 2 & 3\end{pmatrix}$$
$$\mathbf{r}_2 = \begin{pmatrix}2 & 4 & 6\end{pmatrix}$$
$$\mathbf{r}_3 = \begin{pmatrix}0 & 1 & 5\end{pmatrix}$$

Comparing Row 1 and Row 2 entry-by-entry:
$$2 = 2 \cdot 1, \qquad 4 = 2 \cdot 2, \qquad 6 = 2 \cdot 3$$
Clearly:
$$\mathbf{r}_2 = 2 \mathbf{r}_1$$

Rewriting this in standard linear dependence form:
$$2 \mathbf{r}_1 - 1 \mathbf{r}_2 + 0 \mathbf{r}_3 = \begin{pmatrix}0 & 0 & 0\end{pmatrix}$$
With non-zero coefficients $(c_1, c_2, c_3) = (2, -1, 0)$, the rows of $A$ are **linearly dependent**.

---

### Step 2: Conclude Why $\det A = 0$ Without Full Expansion

Because Row 2 is proportional to Row 1:
1. Performing the elementary row operation $R_2 \leftarrow R_2 - 2R_1$ preserves the value of the determinant.
2. Under this operation:
   $$R_2 - 2R_1 = \begin{pmatrix}2-2 & 4-4 & 6-6\end{pmatrix} = \begin{pmatrix}0 & 0 & 0\end{pmatrix}$$
3. The resulting matrix has an entire row of zeros:
   $$\det A = \det \begin{pmatrix}1&2&3\\0&0&0\\0&1&5\end{pmatrix}$$
4. Expanding along the second row gives:
   $$\det A = -0 \cdot M_{21} + 0 \cdot M_{22} - 0 \cdot M_{23} = 0.$$

---

### Step 3: Connect Row Dependence with Non-Invertibility

1. **Dimensional Compression (Rank Deficiency):**  
   The three row vectors do not span $\mathbb{R}^3$. Because $\mathbf{r}_2 \in \operatorname{span}(\mathbf{r}_1)$, the row space is spanned by only two vectors $\{\mathbf{r}_1, \mathbf{r}_3\}$:
   $$\operatorname{dim}(\operatorname{Row}(A)) = \operatorname{rank}(A) \le 2 < 3.$$
2. **Failure of Surjectivity:**  
   Since the column rank equals the row rank, the column space (image) of $A$ is at most a 2D plane in $\mathbb{R}^3$. The linear transformation $x \mapsto Ax$ cannot reach any vector outside this plane; hence, it is not surjective (onto).
3. **Failure of Injectivity:**  
   By the Rank-Nullity Theorem:
   $$\operatorname{dim}(\ker A) = 3 - \operatorname{rank}(A) \ge 3 - 2 = 1.$$
   There exist infinitely many non-zero vectors $x$ mapped to zero ($Ax = \mathbf{0}$). An operator that maps multiple vectors to the same output cannot be inverted.
4. **Conclusion:**  
   Because the rows are linearly dependent, the matrix has deficient rank, collapses 3D space into at most 2 dimensions, and is therefore **not invertible (singular)**.

---

## 4. Verification and Consistency Checks

1. **Sarrus' Rule Check (for confirmation):**
   $$\begin{array}{ccc|cc}
   1 & 2 & 3 & 1 & 2 \\
   2 & 4 & 6 & 2 & 4 \\
   0 & 1 & 5 & 0 & 1
   \end{array}$$
   - Main diagonals: $(1 \cdot 4 \cdot 5) + (2 \cdot 6 \cdot 0) + (3 \cdot 2 \cdot 1) = 20 + 0 + 6 = 26$
   - Anti-diagonals: $(0 \cdot 4 \cdot 3) + (1 \cdot 6 \cdot 1) + (5 \cdot 2 \cdot 2) = 0 + 6 + 20 = 26$
   - $\det A = 26 - 26 = 0 \quad \checkmark$

2. **Explicit Null Space Vector Check:**  
   Notice that Column 2 is twice Column 1: $\mathbf{c}_2 = 2 \mathbf{c}_1$.  
   Therefore, $-2 \mathbf{c}_1 + 1 \mathbf{c}_2 + 0 \mathbf{c}_3 = \mathbf{0}$.  
   Testing $x = \begin{pmatrix}-2\\1\\0\end{pmatrix} \ne \mathbf{0}$:
   $$Ax = \begin{pmatrix}1&2&3\\2&4&6\\0&1&5\end{pmatrix}\begin{pmatrix}-2\\1\\0\end{pmatrix} = \begin{pmatrix}-2 + 2 + 0\\-4 + 4 + 0\\0 + 1 + 0\end{pmatrix} \dots$$
   Wait, let's find the exact kernel vector:
   $$\begin{cases} x_1 + 2x_2 + 3x_3 = 0 \\ x_2 + 5x_3 = 0 \implies x_2 = -5x_3 \end{cases}$$
   Then $x_1 = -2(-5x_3) - 3x_3 = 10x_3 - 3x_3 = 7x_3$.  
   Choose $x_3 = 1 \implies x = \begin{pmatrix}7\\-5\\1\end{pmatrix}$.  
   Testing:
   $$Ax = \begin{pmatrix}1(7) + 2(-5) + 3(1)\\2(7) + 4(-5) + 6(1)\\0(7) + 1(-5) + 5(1)\end{pmatrix} = \begin{pmatrix}7 - 10 + 3\\14 - 20 + 6\\-5 + 5\end{pmatrix} = \begin{pmatrix}0\\0\\0\end{pmatrix} \quad \checkmark$$
   The non-zero vector $(7, -5, 1)^T$ lies in the kernel of $A$, proving singularity.
