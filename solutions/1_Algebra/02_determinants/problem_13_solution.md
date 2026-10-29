# Solution to Problem 13: Determinant by Elimination

## 1. Problem Statement

Compute the determinant of the matrix:
$$A=\begin{pmatrix}1&2&3\\2&5&7\\1&0&2\end{pmatrix}$$

using Gaussian elimination to reduce the matrix to upper triangular form. Carefully record the effect of every row operation used on the value of the determinant.

---

## 2. Theoretical Background and Concepts

- **Determinant by Gaussian Elimination:**  
  Gaussian elimination transforms an arbitrary square matrix into an upper triangular matrix $U$ using elementary row operations (EROs).
- **Tracking ERO Effects on the Determinant:**  
  - **Row Replacement ($R_i \leftarrow R_i + c R_j$ with $i \ne j$):** Leaves the determinant unchanged ($\det A_{\text{new}} = \det A$).
  - **Row Scaling ($R_i \leftarrow c R_i$ with $c \ne 0$):** Multiplies the determinant by $c$ ($\det A = \frac{1}{c} \det A_{\text{new}}$).
  - **Row Swapping ($R_i \leftrightarrow R_j$ with $i \ne j$):** Negates the determinant ($\det A = -\det A_{\text{new}}$).
- **Evaluating Upper Triangular Matrices:**  
  When an upper triangular matrix $U$ is reached, its determinant is the product of its diagonal entries:
  $$\det U = \prod_{i=1}^n u_{ii}.$$
  Tracking the operation factors $k$ allows the original determinant to be reconstructed: $\det A = k \cdot \det U$.

---

## 3. Detailed Step-by-Step Solution

### Initial Matrix:
$$A = \begin{pmatrix}1&2&3\\2&5&7\\1&0&2\end{pmatrix}$$

---

### Step 1: Eliminate Position $(2,1)$

We use Row 1 (with pivot entry $a_{11} = 1$) to eliminate the entry $2$ in Row 2:
$$R_2 \leftarrow R_2 - 2R_1$$

- **Operation Type:** Row replacement ($c = -2, j = 1, i = 2$).
- **Effect on Determinant:** **Unchanged** ($\det A = \det A_1$).
- **Calculation:**
  $$R_2 - 2R_1 = \begin{pmatrix}2 - 2(1) & 5 - 2(2) & 7 - 2(3)\end{pmatrix} = \begin{pmatrix}0 & 1 & 1\end{pmatrix}$$

The matrix becomes:
$$A_1 = \begin{pmatrix}1&2&3\\0&1&1\\1&0&2\end{pmatrix}, \qquad \det A = \det A_1$$

---

### Step 2: Eliminate Position $(3,1)$

We use Row 1 to eliminate the entry $1$ in Row 3:
$$R_3 \leftarrow R_3 - R_1$$

- **Operation Type:** Row replacement ($c = -1, j = 1, i = 3$).
- **Effect on Determinant:** **Unchanged** ($\det A_1 = \det A_2$).
- **Calculation:**
  $$R_3 - R_1 = \begin{pmatrix}1 - 1 & 0 - 2 & 2 - 3\end{pmatrix} = \begin{pmatrix}0 & -2 & -1\end{pmatrix}$$

The matrix becomes:
$$A_2 = \begin{pmatrix}1&2&3\\0&1&1\\0&-2&-1\end{pmatrix}, \qquad \det A = \det A_2$$

---

### Step 3: Eliminate Position $(3,2)$

We use Row 2 (with pivot entry $1$) to eliminate the entry $-2$ in Row 3:
$$R_3 \leftarrow R_3 + 2R_2$$

- **Operation Type:** Row replacement ($c = 2, j = 2, i = 3$).
- **Effect on Determinant:** **Unchanged** ($\det A_2 = \det A_3$).
- **Calculation:**
  $$R_3 + 2R_2 = \begin{pmatrix}0 + 2(0) & -2 + 2(1) & -1 + 2(1)\end{pmatrix} = \begin{pmatrix}0 & 0 & 1\end{pmatrix}$$

The matrix is now in upper triangular form:
$$A_3 = \begin{pmatrix}1&2&3\\0&1&1\\0&0&1\end{pmatrix}, \qquad \det A = \det A_3$$

---

### Step 4: Compute the Determinant of the Final Triangular Matrix

Matrix $A_3$ is upper triangular. Its determinant equals the product of its diagonal elements:
$$\det A_3 = 1 \cdot 1 \cdot 1 = 1$$

Because all three operations were row replacements (each preserving the determinant):
$$\det A = \det A_3 = 1$$

---

## 4. Verification and Consistency Checks

1. **Direct Calculation via Sarrus' Rule on Original Matrix $A$:**
   $$\begin{array}{ccc|cc}
   1 & 2 & 3 & 1 & 2 \\
   2 & 5 & 7 & 2 & 5 \\
   1 & 0 & 2 & 1 & 0
   \end{array}$$
   - Main diagonal products:
     - $1 \cdot 5 \cdot 2 = 10$
     - $2 \cdot 7 \cdot 1 = 14$
     - $3 \cdot 2 \cdot 0 = 0$
     - Sum: $S_{\text{main}} = 10 + 14 + 0 = 24$
   - Anti-diagonal products:
     - $3 \cdot 5 \cdot 1 = 15$
     - $1 \cdot 7 \cdot 0 = 0$
     - $2 \cdot 2 \cdot 2 = 8$
     - Sum: $S_{\text{anti}} = 15 + 0 + 8 = 23$
   - Determinant:
     $$\det A = S_{\text{main}} - S_{\text{anti}} = 24 - 23 = 1 \quad \checkmark$$

2. **Laplace Expansion Along Row 3 of $A$:**
   Row 3 of $A$ is $(1, 0, 2)$:
   $$\det A = 1 \cdot \begin{vmatrix}2&3\\5&7\end{vmatrix} - 0 \cdot M_{32} + 2 \cdot \begin{vmatrix}1&2\\2&5\end{vmatrix}$$
   - $\begin{vmatrix}2&3\\5&7\end{vmatrix} = 2(7) - 3(5) = 14 - 15 = -1$
   - $\begin{vmatrix}1&2\\2&5\end{vmatrix} = 1(5) - 2(2) = 5 - 4 = 1$
   - $\det A = 1(-1) + 2(1) = -1 + 2 = 1 \quad \checkmark$

Both alternative calculation methods confirm that $\det A = 1$.
