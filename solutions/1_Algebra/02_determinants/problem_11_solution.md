# Solution to Problem 11: Shortening the Calculation with Row Operations

## 1. Problem Statement

Compute the determinant:
$$\det\begin{pmatrix}1&2&3\\1&3&4\\1&4&6\end{pmatrix}$$

by first performing row operations to create as many zeros as possible. State explicitly which operations do not change the determinant.

---

## 2. Theoretical Background and Concepts

- **Invariance Under Row Replacement:**  
  The elementary row operation:
  $$R_i \leftarrow R_i + c R_j \quad (i \ne j)$$
  which adds a scalar multiple $c$ of row $j$ to row $i$, **leaves the determinant invariant**:
  $$\det(A_{\text{new}}) = \det(A).$$
- **Strategic Zero Creation:**  
  When an entire column contains identical entries (such as the first column consisting of all ones: $a_{11} = a_{21} = a_{31} = 1$), subtracting the pivot row from each of the remaining rows immediately clears the entire column below the pivot without altering the determinant value.
- **Determinant of a Triangular Matrix:**  
  Once zeros are created below the main diagonal, reducing the matrix to upper triangular form $U$, the determinant is simply the product of the main diagonal entries:
  $$\det U = u_{11} \cdot u_{22} \cdot \cdots \cdot u_{nn}.$$

---

## 3. Detailed Step-by-Step Solution

### Initial Matrix:
Let:
$$A = \begin{pmatrix}1&2&3\\1&3&4\\1&4&6\end{pmatrix}$$

Notice that all three entries in the first column are equal to $1$. We choose Row 1 as our pivot row.

---

### Step 1: Create Zeros in the First Column

1. **Operation on Row 2:**
   $$R_2 \leftarrow R_2 - R_1$$
   - **Type:** Row replacement ($c = -1, j = 1, i = 2$).
   - **Determinant Effect:** **Does not change the determinant** ($\det$ multiplied by $1$).
   - **Calculation:**
     $$R_2 - R_1 = \begin{pmatrix}1 - 1 & 3 - 2 & 4 - 3\end{pmatrix} = \begin{pmatrix}0 & 1 & 1\end{pmatrix}$$

2. **Operation on Row 3:**
   $$R_3 \leftarrow R_3 - R_1$$
   - **Type:** Row replacement ($c = -1, j = 1, i = 3$).
   - **Determinant Effect:** **Does not change the determinant** ($\det$ multiplied by $1$).
   - **Calculation:**
     $$R_3 - R_1 = \begin{pmatrix}1 - 1 & 4 - 2 & 6 - 3\end{pmatrix} = \begin{pmatrix}0 & 2 & 3\end{pmatrix}$$

After these two invariant operations, the matrix becomes:
$$A_1 = \begin{pmatrix}1&2&3\\0&1&1\\0&2&3\end{pmatrix}, \qquad \text{with } \det A = \det A_1$$

---

### Step 2: Create a Zero in Position $(3,2)$ to Reach Triangular Form

Now use Row 2 (with pivot $1$) to eliminate the entry $2$ in Row 3:
$$R_3 \leftarrow R_3 - 2R_2$$

- **Type:** Row replacement ($c = -2, j = 2, i = 3$).
- **Determinant Effect:** **Does not change the determinant** ($\det$ multiplied by $1$).
- **Calculation:**
  $$R_3 - 2R_2 = \begin{pmatrix}0 - 2(0) & 2 - 2(1) & 3 - 2(1)\end{pmatrix} = \begin{pmatrix}0 & 0 & 1\end{pmatrix}$$

The matrix is now in upper triangular form:
$$A_2 = \begin{pmatrix}1&2&3\\0&1&1\\0&0&1\end{pmatrix}, \qquad \text{with } \det A = \det A_2$$

---

### Step 3: Compute the Determinant

Because $A_2$ is upper triangular, its determinant is simply the product of the main diagonal entries:
$$\det A_2 = 1 \cdot 1 \cdot 1 = 1$$

Since all row operations performed were row replacements that strictly preserve the determinant:
$$\det A = \det A_2 = 1$$

---

## 4. Verification and Consistency Checks

1. **Direct Sarrus' Rule Evaluation of $A$:**
   $$\begin{array}{ccc|cc}
   1 & 2 & 3 & 1 & 2 \\
   1 & 3 & 4 & 1 & 3 \\
   1 & 4 & 6 & 1 & 4
   \end{array}$$
   - Main diagonal products:
     - $1 \cdot 3 \cdot 6 = 18$
     - $2 \cdot 4 \cdot 1 = 8$
     - $3 \cdot 1 \cdot 4 = 12$
     - $S_{\text{main}} = 18 + 8 + 12 = 38$
   - Anti-diagonal products:
     - $3 \cdot 3 \cdot 1 = 9$
     - $1 \cdot 4 \cdot 4 = 16$
     - $2 \cdot 1 \cdot 6 = 12$
     - $S_{\text{anti}} = 9 + 16 + 12 = 37$
   - Determinant:
     $$\det A = S_{\text{main}} - S_{\text{anti}} = 38 - 37 = 1 \quad \checkmark$$

2. **Laplace Expansion Along Column 1 of $A_1$:**
   $$A_1 = \begin{pmatrix}1&2&3\\0&1&1\\0&2&3\end{pmatrix} \implies \det A_1 = 1 \cdot \begin{vmatrix}1&1\\2&3\end{vmatrix} = 1 \cdot (1 \cdot 3 - 1 \cdot 2) = 3 - 2 = 1 \quad \checkmark$$
   The result $\det A = 1$ is verified through three independent pathways.
