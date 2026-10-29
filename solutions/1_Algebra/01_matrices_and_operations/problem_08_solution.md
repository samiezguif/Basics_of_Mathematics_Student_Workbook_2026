# Solution to Problem 08: Row Operations and Their Reversibility

## 1. Problem Statement

Given the matrix:
$$A=\begin{pmatrix}1&2&-1\\2&4&1\\-1&1&3\end{pmatrix}$$

Perform, in order, the following elementary row operations:
1. $R_2 \leftarrow R_2 - 2R_1$
2. $R_3 \leftarrow R_3 + R_1$
3. Interchange $R_2$ and $R_3$ ($R_2 \leftrightarrow R_3$)

Write the resulting matrix after each step. Then, for each of the three operations, state the exact operation that reverses it.

---

## 2. Theoretical Background and Concepts

- **Elementary Row Operations (EROs):** There are three types of EROs used in Gaussian elimination:
  1. **Row Addition/Subtraction:** $R_i \leftarrow R_i + c R_j$ (adds a scalar multiple of row $j$ to row $i$, $i \ne j$).
  2. **Row Scaling:** $R_i \leftarrow c R_i$ ($c \ne 0$).
  3. **Row Swapping (Permutation):** $R_i \leftrightarrow R_j$.
- **Reversibility of EROs:** Every elementary row operation is strictly invertible:
  - The inverse of $R_i \leftarrow R_i + c R_j$ is $R_i \leftarrow R_i - c R_j$.
  - The inverse of $R_i \leftarrow c R_i$ is $R_i \leftarrow \frac{1}{c} R_i$.
  - The inverse of $R_i \leftrightarrow R_j$ is the same operation: $R_i \leftrightarrow R_j$.
- **Elementary Matrices:** Each ERO corresponds to multiplying $A$ on the left by an elementary matrix $E$:
  $$A_{\text{new}} = E \cdot A.$$
  Because each elementary matrix is invertible, row operations preserve the solution set of linear systems and the rank of the matrix.

---

## 3. Detailed Step-by-Step Solution

### Initial Matrix:
$$A = \begin{pmatrix}1&2&-1\\2&4&1\\-1&1&3\end{pmatrix}$$

### Step 1: Perform $R_2 \leftarrow R_2 - 2R_1$

We keep Row 1 and Row 3 unchanged and update Row 2:
$$R_2 - 2R_1 = \begin{pmatrix}2 & 4 & 1\end{pmatrix} - 2\begin{pmatrix}1 & 2 & -1\end{pmatrix} = \begin{pmatrix}2 - 2(1) & 4 - 2(2) & 1 - 2(-1)\end{pmatrix} = \begin{pmatrix}0 & 0 & 3\end{pmatrix}$$

The matrix after Step 1 is:
$$A_1 = \begin{pmatrix}1&2&-1\\0&0&3\\-1&1&3\end{pmatrix}$$

- **Reverse Operation for Step 1:**  
  $$R_2 \leftarrow R_2 + 2R_1$$

---

### Step 2: Perform $R_3 \leftarrow R_3 + R_1$

We keep Row 1 and Row 2 of $A_1$ unchanged and update Row 3:
$$R_3 + R_1 = \begin{pmatrix}-1 & 1 & 3\end{pmatrix} + \begin{pmatrix}1 & 2 & -1\end{pmatrix} = \begin{pmatrix}-1 + 1 & 1 + 2 & 3 + (-1)\end{pmatrix} = \begin{pmatrix}0 & 3 & 2\end{pmatrix}$$

The matrix after Step 2 is:
$$A_2 = \begin{pmatrix}1&2&-1\\0&0&3\\0&3&2\end{pmatrix}$$

- **Reverse Operation for Step 2:**  
  $$R_3 \leftarrow R_3 - R_1$$

---

### Step 3: Interchange $R_2$ and $R_3$ ($R_2 \leftrightarrow R_3$)

Swap the second and third rows of $A_2$:
Row 2 becomes $\begin{pmatrix}0 & 3 & 2\end{pmatrix}$ and Row 3 becomes $\begin{pmatrix}0 & 0 & 3\end{pmatrix}$.

The matrix after Step 3 is:
$$A_3 = \begin{pmatrix}1&2&-1\\0&3&2\\0&0&3\end{pmatrix}$$

- **Reverse Operation for Step 3:**  
  Interchange the rows again:
  $$R_2 \leftrightarrow R_3$$

Notice that the resulting matrix $A_3$ is in upper triangular form (row echelon form).

---

## 4. Verification and Consistency Checks

1. **Step-by-Step Inverse Execution (Reconstructing $A$ from $A_3$):**  
   We apply the reverse operations in reverse order:
   - Start with $A_3 = \begin{pmatrix}1&2&-1\\0&3&2\\0&0&3\end{pmatrix}$.
   - Apply Reverse Step 3 ($R_2 \leftrightarrow R_3$):
     $$\begin{pmatrix}1&2&-1\\0&0&3\\0&3&2\end{pmatrix} = A_2 \quad \checkmark$$
   - Apply Reverse Step 2 ($R_3 \leftarrow R_3 - R_1$):
     $$R_3 \to \begin{pmatrix}0 - 1 & 3 - 2 & 2 - (-1)\end{pmatrix} = \begin{pmatrix}-1 & 1 & 3\end{pmatrix}$$
     $$\begin{pmatrix}1&2&-1\\0&0&3\\-1&1&3\end{pmatrix} = A_1 \quad \checkmark$$
   - Apply Reverse Step 1 ($R_2 \leftarrow R_2 + 2R_1$):
     $$R_2 \to \begin{pmatrix}0 + 2(1) & 0 + 2(2) & 3 + 2(-1)\end{pmatrix} = \begin{pmatrix}2 & 4 & 1\end{pmatrix}$$
     $$\begin{pmatrix}1&2&-1\\2&4&1\\-1&1&3\end{pmatrix} = A \quad \checkmark$$
   The original matrix $A$ is reconstructed exactly.

2. **Elementary Matrix Formulation Check:**  
   The elementary matrices representing the three steps are:
   $$E_1 = \begin{pmatrix}1&0&0\\-2&1&0\\0&0&1\end{pmatrix},\quad E_2 = \begin{pmatrix}1&0&0\\0&1&0\\1&0&1\end{pmatrix},\quad E_3 = \begin{pmatrix}1&0&0\\0&0&1\\0&1&0\end{pmatrix}$$
   Their overall product is:
   $$E = E_3 E_2 E_1 = E_3 \begin{pmatrix}1&0&0\\-2&1&0\\1&0&1\end{pmatrix} = \begin{pmatrix}1&0&0\\1&0&1\\-2&1&0\end{pmatrix}$$
   Computing $E \cdot A$:
   $$EA = \begin{pmatrix}1&0&0\\1&0&1\\-2&1&0\end{pmatrix}\begin{pmatrix}1&2&-1\\2&4&1\\-1&1&3\end{pmatrix} = \begin{pmatrix}1&2&-1\\1(1)+(-1)&1(2)+1&1(-1)+3\\-2(1)+2&-2(2)+4&-2(-1)+1\end{pmatrix} = \begin{pmatrix}1&2&-1\\0&3&2\\0&0&3\end{pmatrix} = A_3 \quad \checkmark$$
   The result is verified via elementary matrix multiplication.

