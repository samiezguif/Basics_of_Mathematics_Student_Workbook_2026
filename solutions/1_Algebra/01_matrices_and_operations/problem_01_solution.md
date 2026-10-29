# Solution to Problem 01: Matrix Size and Entries

## 1. Problem Statement

Given the matrices:
$$A=\begin{pmatrix}2&-1&3\\0&4&5\end{pmatrix},\qquad B=\begin{pmatrix}1&0\\-2&3\\4&1\end{pmatrix}$$

1. State the sizes (dimensions) of matrices $A$ and $B$.
2. Read off the entries $a_{12}$, $a_{23}$, $b_{21}$, and $b_{32}$.
3. Write the second row of $A$ and the first column of $B$ as vectors.

---

## 2. Theoretical Background and Concepts

- **Matrix Dimension (Size):** A matrix $M$ with $m$ rows and $n$ columns has size $m \times n$ (read "$m$ by $n$"). The row count always precedes the column count.
- **Matrix Entry Indexing:** The notation $m_{ij}$ denotes the entry in row $i$ and column $j$ of matrix $M$, where $1 \le i \le m$ and $1 \le j \le n$.
- **Row and Column Vectors:**
  - The $i$-th row of an $m \times n$ matrix is a $1 \times n$ row vector $\begin{pmatrix} m_{i1} & m_{i2} & \cdots & m_{in} \end{pmatrix}$.
  - The $j$-th column of an $m \times n$ matrix is an $m \times 1$ column vector $\begin{pmatrix} m_{1j} \\ m_{2j} \\ \vdots \\ m_{mj} \end{pmatrix}$.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Determine the Sizes of $A$ and $B$

- **Matrix $A$:**
  $$A = \begin{pmatrix}2&-1&3\\0&4&5\end{pmatrix}$$
  Counting the rows: Row 1 is $(2, -1, 3)$, Row 2 is $(0, 4, 5)$ $\implies 2$ rows.  
  Counting the columns: Column 1 is $\begin{pmatrix}2\\0\end{pmatrix}$, Column 2 is $\begin{pmatrix}-1\\4\end{pmatrix}$, Column 3 is $\begin{pmatrix}3\\5\end{pmatrix}$ $\implies 3$ columns.  
  Therefore, the size of $A$ is **$2 \times 3$**.

- **Matrix $B$:**
  $$B = \begin{pmatrix}1&0\\-2&3\\4&1\end{pmatrix}$$
  Counting the rows: Row 1 is $(1, 0)$, Row 2 is $(-2, 3)$, Row 3 is $(4, 1)$ $\implies 3$ rows.  
  Counting the columns: Column 1 is $\begin{pmatrix}1\\-2\\4\end{pmatrix}$, Column 2 is $\begin{pmatrix}0\\3\\1\end{pmatrix}$ $\implies 2$ columns.  
  Therefore, the size of $B$ is **$3 \times 2$**.

### Step 2: Read Off the Requested Entries

- $a_{12}$: Entry located in Row 1, Column 2 of $A$:
  $$a_{12} = -1$$
- $a_{23}$: Entry located in Row 2, Column 3 of $A$:
  $$a_{23} = 5$$
- $b_{21}$: Entry located in Row 2, Column 1 of $B$:
  $$b_{21} = -2$$
- $b_{32}$: Entry located in Row 3, Column 2 of $B$:
  $$b_{32} = 1$$

### Step 3: Write Row and Column Vectors

- **Second row of $A$:**
  Taking $i = 2$ from $A$:
  $$\mathbf{r}_2(A) = \begin{pmatrix} 0 & 4 & 5 \end{pmatrix} \in \mathbb{R}^{1 \times 3} \quad (\text{or as an ordered tuple } (0, 4, 5))$$

- **First column of $B$:**
  Taking $j = 1$ from $B$:
  $$\mathbf{c}_1(B) = \begin{pmatrix} 1 \\ -2 \\ 4 \end{pmatrix} \in \mathbb{R}^{3 \times 1} \quad (\text{or as the transposed tuple } (1, -2, 4)^T)$$

---

## 4. Verification and Consistency Checks

1. **Dimension Consistency:** 
   - $A \in \mathbb{R}^{2 \times 3}$ has $2 \cdot 3 = 6$ entries. Counting entries: $2, -1, 3, 0, 4, 5$ (6 entries). Correct.
   - $B \in \mathbb{R}^{3 \times 2}$ has $3 \cdot 2 = 6$ entries. Counting entries: $1, 0, -2, 3, 4, 1$ (6 entries). Correct.
2. **Index Bounds:**
   - $a_{12}$: $1 \le 1 \le 2$ and $1 \le 2 \le 3$ (valid).
   - $a_{23}$: $1 \le 2 \le 2$ and $1 \le 3 \le 3$ (valid).
   - $b_{21}$: $1 \le 2 \le 3$ and $1 \le 1 \le 2$ (valid).
   - $b_{32}$: $1 \le 3 \le 3$ and $1 \le 2 \le 2$ (valid).
3. **Vector Lengths:**
   - Row 2 of $A$ has length 3, matching the column count of $A$.
   - Column 1 of $B$ has length 3, matching the row count of $B$.

