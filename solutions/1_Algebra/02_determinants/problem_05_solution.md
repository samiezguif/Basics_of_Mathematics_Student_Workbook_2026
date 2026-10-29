# Solution to Problem 05: Row Operations

## 1. Problem Statement

Given the matrix:
$$A=\begin{pmatrix}1&2&3\\2&1&0\\-1&4&2\end{pmatrix}$$

Find $\det A$ by simplifying the matrix into upper triangular form using elementary row operations. At each step, explicitly record whether and how the value of the determinant is affected.

---

## 2. Theoretical Background and Concepts

Elementary row operations affect the determinant of an $n \times n$ matrix in three distinct, well-defined ways:
1. **Row Replacement ($R_i \leftarrow R_i + c R_j$ with $i \ne j$):**  
   Adding a scalar multiple of one row to another row **leaves the determinant unchanged**:
   $$\det(A_{\text{new}}) = \det(A).$$
2. **Row Scaling ($R_i \leftarrow c R_i$ with $c \ne 0$):**  
   Multiplying a single row by a non-zero scalar $c$ **multiplies the determinant by $c$**:
   $$\det(A_{\text{new}}) = c \cdot \det(A) \iff \det(A) = \frac{1}{c} \det(A_{\text{new}}).$$
3. **Row Swapping ($R_i \leftrightarrow R_j$ with $i \ne j$):**  
   Interchanging two rows **reverses the sign of the determinant**:
   $$\det(A_{\text{new}}) = -\det(A) \iff \det(A) = -\det(A_{\text{new}}).$$

Once the matrix is transformed into upper triangular form $U$, its determinant is simply the product of its diagonal entries: $\det U = \prod u_{ii}$.

---

## 3. Detailed Step-by-Step Solution

### Initial Matrix:
$$A = \begin{pmatrix}1&2&3\\2&1&0\\-1&4&2\end{pmatrix}$$

---

### Step 1: Eliminate the entry in position $(2,1)$
Perform:
$$R_2 \leftarrow R_2 - 2R_1$$

- **Effect on determinant:** Row replacement does not change the determinant ($\det A = \det A_1$).
- **Row computation:**
  $$R_2 - 2R_1 = \begin{pmatrix}2 - 2(1) & 1 - 2(2) & 0 - 2(3)\end{pmatrix} = \begin{pmatrix}0 & -3 & -6\end{pmatrix}$$

The matrix becomes:
$$A_1 = \begin{pmatrix}1&2&3\\0&-3&-6\\-1&4&2\end{pmatrix}, \qquad \det A = \det A_1$$

---

### Step 2: Eliminate the entry in position $(3,1)$
Perform:
$$R_3 \leftarrow R_3 + R_1$$

- **Effect on determinant:** Row replacement does not change the determinant ($\det A_1 = \det A_2$).
- **Row computation:**
  $$R_3 + R_1 = \begin{pmatrix}-1 + 1 & 4 + 2 & 2 + 3\end{pmatrix} = \begin{pmatrix}0 & 6 & 5\end{pmatrix}$$

The matrix becomes:
$$A_2 = \begin{pmatrix}1&2&3\\0&-3&-6\\0&6&5\end{pmatrix}, \qquad \det A = \det A_2$$

---

### Step 3: Eliminate the entry in position $(3,2)$
We use Row 2 to clear the entry $6$ in Row 3. Perform:
$$R_3 \leftarrow R_3 + 2R_2$$

- **Effect on determinant:** Row replacement does not change the determinant ($\det A_2 = \det A_3$).
- **Row computation:**
  $$R_3 + 2R_2 = \begin{pmatrix}0 + 2(0) & 6 + 2(-3) & 5 + 2(-6)\end{pmatrix} = \begin{pmatrix}0 & 6 - 6 & 5 - 12\end{pmatrix} = \begin{pmatrix}0 & 0 & -7\end{pmatrix}$$

The matrix is now in upper triangular form:
$$A_3 = \begin{pmatrix}1&2&3\\0&-3&-6\\0&0&-7\end{pmatrix}, \qquad \det A = \det A_3$$

---

### Step 4: Compute the Determinant of the Triangular Matrix

Because $A_3$ is upper triangular, its determinant equals the product of its diagonal entries:
$$\det A_3 = (1) \cdot (-3) \cdot (-7) = 21$$

Since none of the three operations involved row swaps or row scalings:
$$\det A = \det A_3 = 21$$

---

## 4. Verification and Consistency Checks

1. **Sarrus' Rule Cross-Check on the Original Matrix $A$:**
   $$\begin{array}{ccc|cc}
   1 & 2 & 3 & 1 & 2 \\
   2 & 1 & 0 & 2 & 1 \\
   -1 & 4 & 2 & -1 & 4
   \end{array}$$
   - Main diagonal products:
     - $1 \cdot 1 \cdot 2 = 2$
     - $2 \cdot 0 \cdot (-1) = 0$
     - $3 \cdot 2 \cdot 4 = 24$
     - Sum: $S_{\text{main}} = 2 + 0 + 24 = 26$
   - Anti-diagonal products:
     - $3 \cdot 1 \cdot (-1) = -3$
     - $1 \cdot 0 \cdot 4 = 0$
     - $2 \cdot 2 \cdot 2 = 8$
     - Sum: $S_{\text{anti}} = -3 + 0 + 8 = 5$
   - Determinant:
     $$\det A = S_{\text{main}} - S_{\text{anti}} = 26 - 5 = 21 \quad \checkmark$$

2. **Elementary Matrix Multiplicativity Verification:**  
   The three row operations correspond to elementary lower-triangular matrices with 1s on the diagonal (unitriangular matrices):
   $$E_1 = \begin{pmatrix}1&0&0\\-2&1&0\\0&0&1\end{pmatrix},\quad E_2 = \begin{pmatrix}1&0&0\\0&1&0\\1&0&1\end{pmatrix},\quad E_3 = \begin{pmatrix}1&0&0\\0&1&0\\0&2&1\end{pmatrix}$$
   Because $\det(E_1) = \det(E_2) = \det(E_3) = 1$:
   $$\det(A_3) = \det(E_3 E_2 E_1 A) = \det(E_3)\det(E_2)\det(E_1)\det(A) = 1 \cdot 1 \cdot 1 \cdot \det(A) = \det(A) \quad \checkmark$$
   The elimination method is fully verified.
