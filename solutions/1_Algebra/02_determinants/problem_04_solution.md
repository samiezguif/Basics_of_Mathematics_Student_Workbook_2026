# Solution to Problem 04: Triangular Matrix

## 1. Problem Statement

Without expanding the determinant, compute:
$$\det\begin{pmatrix}2&4&1\\0&-3&5\\0&0&7\end{pmatrix}$$

State the general rule for the determinant of an arbitrary triangular matrix and explain why it holds using this example.

---

## 2. Theoretical Background and Concepts

- **Triangular Matrices:**
  - An $n \times n$ matrix $T$ is **upper triangular** if all entries strictly below the main diagonal are zero ($t_{ij} = 0$ for all $i > j$).
  - An $n \times n$ matrix $T$ is **lower triangular** if all entries strictly above the main diagonal are zero ($t_{ij} = 0$ for all $i < j$).
  - A matrix is **diagonal** if it is both upper and lower triangular ($t_{ij} = 0$ for all $i \ne j$).
- **Determinant of a Triangular Matrix:**  
  The determinant of any triangular matrix equals the product of its main diagonal entries:
  $$\det T = \prod_{i=1}^n t_{ii} = t_{11} \cdot t_{22} \cdot \cdots \cdot t_{nn}.$$
- **Justification by Recursive Expansion:**  
  Expanding an upper triangular matrix repeatedly along its first column (or a lower triangular matrix along its first row) isolates one diagonal element at each step, because all other entries in that column (or row) are zero.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Identify the Structure and Compute the Determinant

The given matrix is:
$$T = \begin{pmatrix}2&4&1\\0&-3&5\\0&0&7\end{pmatrix}$$

Inspecting the entries below the main diagonal:
$$t_{21} = 0, \quad t_{31} = 0, \quad t_{32} = 0$$
Since all entries below the diagonal are zero, $T$ is an **upper triangular matrix**.

Using the diagonal product rule:
$$\det T = t_{11} \cdot t_{22} \cdot t_{33} = 2 \cdot (-3) \cdot 7 = -42$$

---

### Step 2: Explanation of the Rule Using this Example

To understand why only the diagonal product survives, we evaluate the determinant by successive Laplace expansions along the first column:

1. **First Column Expansion of $T$:**
   $$\det T = 2 \cdot \begin{vmatrix}-3&5\\0&7\end{vmatrix} - 0 \cdot \begin{vmatrix}4&1\\0&7\end{vmatrix} + 0 \cdot \begin{vmatrix}4&1\\-3&5\end{vmatrix}$$
   Because $t_{21}=0$ and $t_{31}=0$, the second and third cofactor terms vanish completely, leaving only:
   $$\det T = 2 \cdot \begin{vmatrix}-3&5\\0&7\end{vmatrix}$$

2. **First Column Expansion of the $2 \times 2$ Minor:**
   $$\begin{vmatrix}-3&5\\0&7\end{vmatrix} = (-3)(7) - 5(0) = (-3)(7)$$
   Here again, the zero below the diagonal cancels the off-diagonal term.

3. **Combining the Results:**
   $$\det T = 2 \cdot [(-3) \cdot 7] = 2 \cdot (-3) \cdot 7 = -42$$

This recursive decoupling occurs in any dimension $n$. In any Leibniz permutation expansion $\det T = \sum_{\sigma} \operatorname{sgn}(\sigma) \prod_{i=1}^n t_{i,\sigma(i)}$, any permutation other than the identity $\sigma = \operatorname{id}$ must map some row $i$ to a column $\sigma(i) < i$ where $t_{i,\sigma(i)} = 0$. Hence, all $(n! - 1)$ other terms in the Leibniz sum are zero, leaving only the diagonal product.

---

## 4. Verification and Consistency Checks

1. **Sarrus' Rule Cross-Check:**
   $$\begin{array}{ccc|cc}
   2 & 4 & 1 & 2 & 4 \\
   0 & -3 & 5 & 0 & -3 \\
   0 & 0 & 7 & 0 & 0
   \end{array}$$
   - Main diagonals:
     $(2 \cdot (-3) \cdot 7) + (4 \cdot 5 \cdot 0) + (1 \cdot 0 \cdot 0) = -42 + 0 + 0 = -42$
   - Anti-diagonals:
     $(0 \cdot (-3) \cdot 1) + (0 \cdot 5 \cdot 2) + (7 \cdot 0 \cdot 4) = 0 + 0 + 0 = 0$
   - Result:
     $$\det T = -42 - 0 = -42 \quad \checkmark$$

2. **Eigenvalues Check:**  
   The eigenvalues of a triangular matrix are precisely its diagonal entries: $\lambda_1 = 2$, $\lambda_2 = -3$, $\lambda_3 = 7$.  
   Since the determinant is the product of the eigenvalues:
   $$\det T = \lambda_1 \lambda_2 \lambda_3 = 2 \cdot (-3) \cdot 7 = -42 \quad \checkmark$$
