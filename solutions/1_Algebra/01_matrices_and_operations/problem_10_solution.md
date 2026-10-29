# Solution to Problem 10: Columns of a Matrix Product

## 1. Problem Statement

Given the matrices:
$$A=\begin{pmatrix}1&2&0\\0&1&1\end{pmatrix},\qquad B=\begin{pmatrix}1&2\\-1&0\\3&1\end{pmatrix}$$

Denote the columns of $B$ by $\mathbf{b}_1$ and $\mathbf{b}_2$.

1. Compute $A\mathbf{b}_1$ and $A\mathbf{b}_2$.
2. Compute the matrix product $AB$.
3. Compare the results and explain why the columns of $AB$ are exactly the vectors $A\mathbf{b}_1$ and $A\mathbf{b}_2$.

---

## 2. Theoretical Background and Concepts

- **Column-by-Column Interpretation of Matrix Multiplication:**  
  Let $A \in \mathbb{R}^{m \times k}$ and let $B \in \mathbb{R}^{k \times n}$ be partitioned by its column vectors:
  $$B = \begin{pmatrix} \mathbf{b}_1 & \mathbf{b}_2 & \cdots & \mathbf{b}_n \end{pmatrix}$$
  where each $\mathbf{b}_j \in \mathbb{R}^{k \times 1}$.
  The matrix product $AB$ is then partitioned as:
  $$AB = A \begin{pmatrix} \mathbf{b}_1 & \mathbf{b}_2 & \cdots & \mathbf{b}_n \end{pmatrix} = \begin{pmatrix} A\mathbf{b}_1 & A\mathbf{b}_2 & \cdots & A\mathbf{b}_n \end{pmatrix}.$$
- **Index Proof:**  
  The entry in row $i$ and column $j$ of the product $AB$ is given by:
  $$(AB)_{ij} = \sum_{r=1}^k a_{ir} b_{rj}.$$
  On the other hand, the $i$-th component of the vector obtained by multiplying matrix $A$ by the $j$-th column vector $\mathbf{b}_j$ is:
  $$(A\mathbf{b}_j)_i = \sum_{r=1}^k a_{ir} (\mathbf{b}_j)_r = \sum_{r=1}^k a_{ir} b_{rj}.$$
  Since this holds for every row index $i$ and column index $j$, the $j$-th column of the product matrix $AB$ is identically the vector $A\mathbf{b}_j$.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Identify Columns of $B$ and Compute $A\mathbf{b}_1$ and $A\mathbf{b}_2$

From matrix $B = \begin{pmatrix}1&2\\-1&0\\3&1\end{pmatrix}$, its columns are:
$$\mathbf{b}_1 = \begin{pmatrix}1\\-1\\3\end{pmatrix},\qquad \mathbf{b}_2 = \begin{pmatrix}2\\0\\1\end{pmatrix}$$

Now compute $A\mathbf{b}_1$:
$$A\mathbf{b}_1 = \begin{pmatrix}1&2&0\\0&1&1\end{pmatrix}\begin{pmatrix}1\\-1\\3\end{pmatrix} = \begin{pmatrix}1(1) + 2(-1) + 0(3) \\ 0(1) + 1(-1) + 1(3)\end{pmatrix} = \begin{pmatrix}1 - 2 + 0 \\ 0 - 1 + 3\end{pmatrix} = \begin{pmatrix}-1\\2\end{pmatrix}$$

Now compute $A\mathbf{b}_2$:
$$A\mathbf{b}_2 = \begin{pmatrix}1&2&0\\0&1&1\end{pmatrix}\begin{pmatrix}2\\0\\1\end{pmatrix} = \begin{pmatrix}1(2) + 2(0) + 0(1) \\ 0(2) + 1(0) + 1(1)\end{pmatrix} = \begin{pmatrix}2 + 0 + 0 \\ 0 + 0 + 1\end{pmatrix} = \begin{pmatrix}2\\1\end{pmatrix}$$

### Step 2: Compute the Full Product $AB$

$A$ is $2 \times 3$ and $B$ is $3 \times 2$, so $AB$ is a $2 \times 2$ matrix:
$$AB = \begin{pmatrix}1&2&0\\0&1&1\end{pmatrix}\begin{pmatrix}1&2\\-1&0\\3&1\end{pmatrix}$$

Computing each entry using the row-by-column method:
- **Entry $(1,1)$:** $1(1) + 2(-1) + 0(3) = 1 - 2 + 0 = -1$
- **Entry $(1,2)$:** $1(2) + 2(0) + 0(1) = 2 + 0 + 0 = 2$
- **Entry $(2,1)$:** $0(1) + 1(-1) + 1(3) = 0 - 1 + 3 = 2$
- **Entry $(2,2)$:** $0(2) + 1(0) + 1(1) = 0 + 0 + 1 = 1$

Thus:
$$AB = \begin{pmatrix}-1 & 2 \\ 2 & 1\end{pmatrix}$$

### Step 3: Comparison and Explanation

Examining the matrix $AB$:
- Column 1 of $AB$ is $\begin{pmatrix}-1\\2\end{pmatrix}$, which matches $A\mathbf{b}_1$ exactly.
- Column 2 of $AB$ is $\begin{pmatrix}2\\1\end{pmatrix}$, which matches $A\mathbf{b}_2$ exactly.

Therefore:
$$AB = \begin{pmatrix} A\mathbf{b}_1 & A\mathbf{b}_2 \end{pmatrix} = \begin{pmatrix}-1 & 2 \\ 2 & 1\end{pmatrix}$$

**Why this holds:**
Matrix multiplication can be viewed not just as dot products of rows and columns, but as the simultaneous transformation of multiple vectors. When $A$ multiplies $B$, matrix $A$ acts linearly on each column of $B$ independently. Column $j$ of $B$ indicates how the standard basis vector $\mathbf{e}_j$ is transformed by $B$; multiplying by $A$ then maps that result to $A(B\mathbf{e}_j) = A\mathbf{b}_j$. Concatenating these image vectors side-by-side produces the full matrix $AB$.

---

## 4. Verification and Consistency Checks

1. **Row-by-Row Perspective Comparison:**
   - Row 1 of $A$ is $\mathbf{r}_1 = (1, 2, 0)$.
     - $\mathbf{r}_1 \cdot \mathbf{b}_1 = 1(1) + 2(-1) + 0(3) = -1 = (AB)_{11} \quad \checkmark$
     - $\mathbf{r}_1 \cdot \mathbf{b}_2 = 1(2) + 2(0) + 0(1) = 2 = (AB)_{12} \quad \checkmark$
   - Row 2 of $A$ is $\mathbf{r}_2 = (0, 1, 1)$.
     - $\mathbf{r}_2 \cdot \mathbf{b}_1 = 0(1) + 1(-1) + 1(3) = 2 = (AB)_{21} \quad \checkmark$
     - $\mathbf{r}_2 \cdot \mathbf{b}_2 = 0(2) + 1(0) + 1(1) = 1 = (AB)_{22} \quad \checkmark$

2. **Column Combination Verification:**
   - $A\mathbf{b}_1 = 1 \begin{pmatrix}1\\0\end{pmatrix} - 1 \begin{pmatrix}2\\1\end{pmatrix} + 3 \begin{pmatrix}0\\1\end{pmatrix} = \begin{pmatrix}1 - 2 + 0 \\ 0 - 1 + 3\end{pmatrix} = \begin{pmatrix}-1\\2\end{pmatrix} \quad \checkmark$
   - $A\mathbf{b}_2 = 2 \begin{pmatrix}1\\0\end{pmatrix} + 0 \begin{pmatrix}2\\1\end{pmatrix} + 1 \begin{pmatrix}0\\1\end{pmatrix} = \begin{pmatrix}2 + 0 + 0 \\ 0 + 0 + 1\end{pmatrix} = \begin{pmatrix}2\\1\end{pmatrix} \quad \checkmark$

All three perspectives (row dot product, matrix-vector product, column linear combination) produce identical results.

