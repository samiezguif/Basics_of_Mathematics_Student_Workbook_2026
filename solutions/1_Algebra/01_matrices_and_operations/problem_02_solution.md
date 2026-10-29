# Solution to Problem 02: Addition and Scalar Multiplication

## 1. Problem Statement

Given the matrices:
$$A=\begin{pmatrix}1&2\\-1&3\end{pmatrix},\qquad B=\begin{pmatrix}4&-2\\0&5\end{pmatrix}$$

1. Compute $A+B$.
2. Compute $A-B$.
3. Compute $3A-2B$.
4. Explain why matrix addition is possible only for matrices of the same size.

---

## 2. Theoretical Background and Concepts

- **Matrix Addition:** Let $A, B \in \mathbb{R}^{m \times n}$. The sum $C = A + B$ is an $m \times n$ matrix whose entries are defined componentwise:
  $$c_{ij} = a_{ij} + b_{ij} \quad \text{for all } 1 \le i \le m,\ 1 \le j \le n.$$
- **Matrix Subtraction:** The difference $D = A - B$ is defined componentwise as:
  $$d_{ij} = a_{ij} - b_{ij} \quad \text{for all } 1 \le i \le m,\ 1 \le j \le n.$$
- **Scalar Multiplication:** For any scalar $\alpha \in \mathbb{R}$ and matrix $A \in \mathbb{R}^{m \times n}$, the product $\alpha A$ is defined by:
  $$(\alpha A)_{ij} = \alpha \cdot a_{ij}.$$
- **Linear Combination of Matrices:** For scalars $\alpha, \beta$ and matrices $A, B$ of identical dimensions:
  $$(\alpha A + \beta B)_{ij} = \alpha a_{ij} + \beta b_{ij}.$$

---

## 3. Detailed Step-by-Step Solution

Both $A$ and $B$ are $2 \times 2$ matrices, so all requested linear combinations are well-defined and yield $2 \times 2$ matrices.

### Step 1: Compute $A + B$
$$A+B = \begin{pmatrix}1&2\\-1&3\end{pmatrix} + \begin{pmatrix}4&-2\\0&5\end{pmatrix} = \begin{pmatrix}1+4 & 2+(-2) \\ -1+0 & 3+5\end{pmatrix} = \begin{pmatrix}5 & 0 \\ -1 & 8\end{pmatrix}$$

### Step 2: Compute $A - B$
$$A-B = \begin{pmatrix}1&2\\-1&3\end{pmatrix} - \begin{pmatrix}4&-2\\0&5\end{pmatrix} = \begin{pmatrix}1-4 & 2-(-2) \\ -1-0 & 3-5\end{pmatrix} = \begin{pmatrix}-3 & 4 \\ -1 & -2\end{pmatrix}$$

### Step 3: Compute $3A - 2B$
First, perform scalar multiplications:
$$3A = 3\begin{pmatrix}1&2\\-1&3\end{pmatrix} = \begin{pmatrix}3\cdot 1 & 3\cdot 2 \\ 3\cdot(-1) & 3\cdot 3\end{pmatrix} = \begin{pmatrix}3 & 6 \\ -3 & 9\end{pmatrix}$$

$$2B = 2\begin{pmatrix}4&-2\\0&5\end{pmatrix} = \begin{pmatrix}2\cdot 4 & 2\cdot(-2) \\ 2\cdot 0 & 2\cdot 5\end{pmatrix} = \begin{pmatrix}8 & -4 \\ 0 & 10\end{pmatrix}$$

Now subtract $2B$ from $3A$:
$$3A - 2B = \begin{pmatrix}3 & 6 \\ -3 & 9\end{pmatrix} - \begin{pmatrix}8 & -4 \\ 0 & 10\end{pmatrix} = \begin{pmatrix}3 - 8 & 6 - (-4) \\ -3 - 0 & 9 - 10\end{pmatrix} = \begin{pmatrix}-5 & 10 \\ -3 & -1\end{pmatrix}$$

### Step 4: Justification for Dimension Compatibility in Addition

Matrix addition is defined as an entry-by-entry (componentwise) operation:
$$(A+B)_{ij} = a_{ij} + b_{ij}.$$
This requires a one-to-one correspondence between the entries of $A$ and the entries of $B$. If $A$ is $m \times n$ and $B$ is $p \times q$ with $m \ne p$ or $n \ne q$, there would be indices $(i, j)$ that exist in one matrix but not in the other. There is no mathematically canonical way to pair or complete missing entries without altering the algebraic structure (a vector space of matrices requires a closure property over identical dimensions). Hence, matrix addition is defined if and only if both matrices have identical dimensions.

---

## 4. Verification and Consistency Checks

1. **Additive Inverses and Reconstruction:**
   $$(A+B) - B = \begin{pmatrix}5 & 0 \\ -1 & 8\end{pmatrix} - \begin{pmatrix}4 & -2 \\ 0 & 5\end{pmatrix} = \begin{pmatrix}5-4 & 0-(-2) \\ -1-0 & 8-5\end{pmatrix} = \begin{pmatrix}1 & 2 \\ -1 & 3\end{pmatrix} = A \quad \checkmark$$
   $$(A-B) + B = \begin{pmatrix}-3 & 4 \\ -1 & -2\end{pmatrix} + \begin{pmatrix}4 & -2 \\ 0 & 5\end{pmatrix} = \begin{pmatrix}-3+4 & 4-2 \\ -1+0 & -2+5\end{pmatrix} = \begin{pmatrix}1 & 2 \\ -1 & 3\end{pmatrix} = A \quad \checkmark$$

2. **Linear Combination Consistency:**
   $$(3A - 2B) + 2B = \begin{pmatrix}-5 & 10 \\ -3 & -1\end{pmatrix} + \begin{pmatrix}8 & -4 \\ 0 & 10\end{pmatrix} = \begin{pmatrix}3 & 6 \\ -3 & 9\end{pmatrix} = 3A \quad \checkmark$$
   Dividing by 3 gives $A = \begin{pmatrix}1&2\\-1&3\end{pmatrix}$. All calculations are completely consistent.

