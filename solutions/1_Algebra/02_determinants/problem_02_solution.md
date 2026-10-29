# Solution to Problem 02: Determinant of a 3×3 Matrix

## 1. Problem Statement

Given the matrix:
$$A=\begin{pmatrix}1&2&-1\\0&3&4\\2&1&5\end{pmatrix}$$

1. Compute $\det A$ using Sarrus' rule.
2. Perform one verification check of the result using a chosen property of the determinant.

---

## 2. Theoretical Background and Concepts

- **Sarrus' Rule:**  
  For any $3 \times 3$ matrix:
  $$M = \begin{pmatrix}a&b&c\\d&e&f\\g&h&i\end{pmatrix},$$
  the determinant can be calculated by summing the products along the three main diagonal directions and subtracting the products along the three anti-diagonal directions:
  $$\det M = (aei + bfg + cdh) - (ceg + afh + bdi).$$
  *(Note: Sarrus' rule applies strictly to $3 \times 3$ matrices and cannot be generalized to higher dimensions).*
- **Laplace Expansion (Cofactor Expansion):**  
  The determinant can also be computed along any row $i$ or column $j$:
  $$\det M = \sum_{k=1}^n (-1)^{i+k} m_{ik} M_{ik},$$
  where $M_{ik}$ is the $(n-1) \times (n-1)$ minor obtained by deleting row $i$ and column $k$. Choosing a row or column containing zeros substantially simplifies the computation.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute $\det A$ Using Sarrus' Rule

Write down matrix $A$ and repeat its first two columns to visualize the diagonals:
$$\begin{array}{ccc|cc}
1 & 2 & -1 & 1 & 2 \\
0 & 3 & 4  & 0 & 3 \\
2 & 1 & 5  & 2 & 1
\end{array}$$

1. **Calculate the products along the three main diagonals (from top-left to bottom-right):**
   - First diagonal: $1 \cdot 3 \cdot 5 = 15$
   - Second diagonal: $2 \cdot 4 \cdot 2 = 16$
   - Third diagonal: $(-1) \cdot 0 \cdot 1 = 0$
   - **Sum of main diagonal terms:**
     $$S_{\text{main}} = 15 + 16 + 0 = 31$$

2. **Calculate the products along the three anti-diagonals (from bottom-left to top-right):**
   - First anti-diagonal: $2 \cdot 3 \cdot (-1) = -6$
   - Second anti-diagonal: $1 \cdot 4 \cdot 1 = 4$
   - Third anti-diagonal: $5 \cdot 0 \cdot 2 = 0$
   - **Sum of anti-diagonal terms:**
     $$S_{\text{anti}} = (-6) + 4 + 0 = -2$$

3. **Subtract the anti-diagonal sum from the main diagonal sum:**
   $$\det A = S_{\text{main}} - S_{\text{anti}} = 31 - (-2) = 31 + 2 = 33$$

---

## 4. Verification and Consistency Checks

### Chosen Check: Laplace Expansion along Column 1
Matrix $A$ has a zero in the first column at entry $a_{21} = 0$:
$$A = \begin{pmatrix}1&2&-1\\0&3&4\\2&1&5\end{pmatrix}$$

Expanding along Column 1 reduces the calculation to only two $2 \times 2$ determinants:
$$\det A = a_{11} C_{11} + a_{21} C_{21} + a_{31} C_{31}$$
where $C_{ij} = (-1)^{i+j} M_{ij}$.

- **Term 1 ($i=1, j=1$):**
  $$a_{11} C_{11} = 1 \cdot (-1)^{1+1} \begin{vmatrix}3&4\\1&5\end{vmatrix} = 1 \cdot [3(5) - 4(1)] = 1 \cdot (15 - 4) = 11$$

- **Term 2 ($i=2, j=1$):**
  $$a_{21} C_{21} = 0 \cdot C_{21} = 0$$

- **Term 3 ($i=3, j=1$):**
  $$a_{31} C_{31} = 2 \cdot (-1)^{3+1} \begin{vmatrix}2&-1\\3&4\end{vmatrix} = 2 \cdot [2(4) - (-1)(3)] = 2 \cdot (8 + 3) = 2 \cdot 11 = 22$$

Summing the cofactor contributions:
$$\det A = 11 + 0 + 22 = 33$$

Both Sarrus' rule and Laplace column expansion independently yield $\det A = 33$, verifying the result.
