# Solution to Problem 03: Swapping Two Rows

## 1. Problem Statement

Given the matrix:
$$A=\begin{pmatrix}1&2&0\\0&3&1\\2&1&1\end{pmatrix}$$

1. Compute $\det A$.
2. Form the matrix $B$ by swapping the first and second rows of $A$ ($R_1 \leftrightarrow R_2$).
3. Predict $\det B$ using a fundamental property of the determinant.
4. Verify the prediction by direct calculation of $\det B$.

---

## 2. Theoretical Background and Concepts

- **Row Swapping Property (Alternating Property):**  
  The determinant is an alternating multilinear form with respect to its rows (and columns). If two rows (or two columns) of an $n \times n$ matrix are interchanged, the sign of the determinant changes:
  $$\text{If } B \text{ is obtained from } A \text{ by } R_i \leftrightarrow R_j \ (i \ne j), \text{ then } \det B = -\det A.$$
- **Permutation Matrices:**  
  Swapping two rows corresponds to multiplying on the left by an elementary permutation matrix $P$:
  $$B = P A, \quad \text{where } P = \begin{pmatrix}0&1&0\\1&0&0\\0&0&1\end{pmatrix}.$$
  Since a transposition of two elements has odd parity (sign $\operatorname{sgn}(P) = -1$), $\det P = -1$. By the multiplicative property of determinants:
  $$\det B = \det(PA) = \det(P)\det(A) = (-1)\det(A) = -\det A.$$

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute $\det A$

Given:
$$A = \begin{pmatrix}1&2&0\\0&3&1\\2&1&1\end{pmatrix}$$

We compute $\det A$ by Laplace expansion along the first row (exploiting the entry $a_{13}=0$):
$$\det A = 1 \cdot \begin{vmatrix}3&1\\1&1\end{vmatrix} - 2 \cdot \begin{vmatrix}0&1\\2&1\end{vmatrix} + 0 \cdot \begin{vmatrix}0&3\\2&1\end{vmatrix}$$

Evaluating the $2 \times 2$ determinants:
- $\begin{vmatrix}3&1\\1&1\end{vmatrix} = 3(1) - 1(1) = 3 - 1 = 2$
- $\begin{vmatrix}0&1\\2&1\end{vmatrix} = 0(1) - 1(2) = 0 - 2 = -2$

Substituting back:
$$\det A = 1(2) - 2(-2) + 0 = 2 + 4 = 6$$

---

### Step 2: Form Matrix $B$

Swapping Row 1 and Row 2 of $A$:
$$B = \begin{pmatrix}0&3&1\\1&2&0\\2&1&1\end{pmatrix}$$

---

### Step 3: Predict $\det B$ Using the Row Swap Property

Since matrix $B$ is obtained from $A$ by a single row swap ($R_1 \leftrightarrow R_2$), the alternating property dictates:
$$\det B = -\det A = -6$$

---

### Step 4: Verify the Prediction by Direct Calculation of $\det B$

We compute $\det B$ directly by Laplace expansion along its first row:
$$B = \begin{pmatrix}0&3&1\\1&2&0\\2&1&1\end{pmatrix}$$

$$\det B = 0 \cdot C_{11} - 3 \cdot \begin{vmatrix}1&0\\2&1\end{vmatrix} + 1 \cdot \begin{vmatrix}1&2\\2&1\end{vmatrix}$$

Evaluating each minor:
- $\begin{vmatrix}1&0\\2&1\end{vmatrix} = 1(1) - 0(2) = 1$
- $\begin{vmatrix}1&2\\2&1\end{vmatrix} = 1(1) - 2(2) = 1 - 4 = -3$

Combining terms:
$$\det B = 0 - 3(1) + 1(-3) = -3 - 3 = -6$$

The direct calculation yields $\det B = -6$, confirming the theoretical prediction $\det B = -\det A$.

---

## 4. Verification and Consistency Checks

1. **Sarrus' Rule Cross-Check on Matrix $B$:**
   $$\begin{array}{ccc|cc}
   0 & 3 & 1 & 0 & 3 \\
   1 & 2 & 0 & 1 & 2 \\
   2 & 1 & 1 & 2 & 1
   \end{array}$$
   - Main diagonals:
     $(0 \cdot 2 \cdot 1) + (3 \cdot 0 \cdot 2) + (1 \cdot 1 \cdot 1) = 0 + 0 + 1 = 1$
   - Anti-diagonals:
     $(2 \cdot 2 \cdot 1) + (1 \cdot 0 \cdot 0) + (1 \cdot 1 \cdot 3) = 4 + 0 + 3 = 7$
   - Determinant:
     $$\det B = S_{\text{main}} - S_{\text{anti}} = 1 - 7 = -6 \quad \checkmark$$

2. **Permutation Matrix Determinant Product Check:**
   $$\det P = 0(0 - 0) - 1(1 - 0) + 0 = -1$$
   $$\det B = \det(PA) = \det(P)\det(A) = (-1)(6) = -6 \quad \checkmark$$
