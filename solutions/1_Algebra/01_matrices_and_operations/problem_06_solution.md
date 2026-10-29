# Solution to Problem 06: Transpose

## 1. Problem Statement

Given:
$$A=\begin{pmatrix}1&2&3\\4&5&6\end{pmatrix},\qquad B=\begin{pmatrix}1&0\\2&1\\-1&3\end{pmatrix}$$

1. Compute the transpose matrix $A^T$.
2. Compute the transpose matrix $B^T$.
3. Compute the product $AB$.
4. Verify in this example that:
   $$(AB)^T = B^T A^T$$

---

## 2. Theoretical Background and Concepts

- **Transpose of a Matrix:**  
  Let $M$ be an $m \times n$ matrix. The transpose $M^T$ is an $n \times m$ matrix obtained by swapping rows and columns:
  $$(M^T)_{ij} = M_{ji} \quad \text{for all } 1 \le i \le n,\ 1 \le j \le m.$$
- **Transpose of a Product (Reversal Law):**  
  For any two conformable matrices $A \in \mathbb{R}^{m \times k}$ and $B \in \mathbb{R}^{k \times n}$, the transpose of their product satisfies:
  $$(AB)^T = B^T A^T.$$
  *Reason for order reversal:* The product $AB$ has size $m \times n$, so $(AB)^T$ has size $n \times m$. Looking at the components:
  $$(AB)^T_{ij} = (AB)_{ji} = \sum_{r=1}^k a_{jr} b_{ri} = \sum_{r=1}^k b_{ri} a_{jr} = \sum_{r=1}^k (B^T)_{ir} (A^T)_{rj} = (B^T A^T)_{ij}.$$
  Notice that $A^T$ has size $k \times m$ and $B^T$ has size $n \times k$. The naive candidate product $A^T B^T$ is defined if and only if the inner dimensions match, which requires $m = n$ ($k$ need not equal them). Even when $m = n$ (as in this exercise, where $m = n = 2$ and $k = 3$), the product $A^T B^T$ is defined but has size $k \times k$ ($3 \times 3$), which cannot equal the $n \times m$ ($2 \times 2$) matrix $(AB)^T$. In contrast, $B^T A^T$ has dimensions $(n \times k) \times (k \times m) = n \times m$, naturally matching the dimensions of $(AB)^T$, and the entrywise derivation above confirms they are identical.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute $A^T$
Matrix $A$ has dimensions $2 \times 3$:
$$A = \begin{pmatrix}1&2&3\\4&5&6\end{pmatrix}$$
Swapping rows into columns gives a $3 \times 2$ matrix:
$$A^T = \begin{pmatrix}1&4\\2&5\\3&6\end{pmatrix}$$

### Step 2: Compute $B^T$
Matrix $B$ has dimensions $3 \times 2$:
$$B = \begin{pmatrix}1&0\\2&1\\-1&3\end{pmatrix}$$
Swapping rows into columns gives a $2 \times 3$ matrix:
$$B^T = \begin{pmatrix}1&2&-1\\0&1&3\end{pmatrix}$$

### Step 3: Compute $AB$
$A$ is $2 \times 3$ and $B$ is $3 \times 2$, so their product $AB$ is a $2 \times 2$ matrix:
$$AB = \begin{pmatrix}1&2&3\\4&5&6\end{pmatrix}\begin{pmatrix}1&0\\2&1\\-1&3\end{pmatrix}$$

Calculating each entry:
- **Entry $(1,1)$:** $1(1) + 2(2) + 3(-1) = 1 + 4 - 3 = 2$
- **Entry $(1,2)$:** $1(0) + 2(1) + 3(3) = 0 + 2 + 9 = 11$
- **Entry $(2,1)$:** $4(1) + 5(2) + 6(-1) = 4 + 10 - 6 = 8$
- **Entry $(2,2)$:** $4(0) + 5(1) + 6(3) = 0 + 5 + 18 = 23$

Thus:
$$AB = \begin{pmatrix}2 & 11 \\ 8 & 23\end{pmatrix}$$

### Step 4: Transpose the Product $(AB)^T$
Taking the transpose of the resulting $2 \times 2$ matrix:
$$(AB)^T = \begin{pmatrix}2 & 11 \\ 8 & 23\end{pmatrix}^T = \begin{pmatrix}2 & 8 \\ 11 & 23\end{pmatrix}$$

### Step 5: Compute $B^T A^T$ and Verify Equality
$B^T$ is $2 \times 3$ and $A^T$ is $3 \times 2$, so their product $B^T A^T$ is well-defined and has size $2 \times 2$:
$$B^T A^T = \begin{pmatrix}1&2&-1\\0&1&3\end{pmatrix}\begin{pmatrix}1&4\\2&5\\3&6\end{pmatrix}$$

Calculating each entry:
- **Entry $(1,1)$:** $1(1) + 2(2) + (-1)(3) = 1 + 4 - 3 = 2$
- **Entry $(1,2)$:** $1(4) + 2(5) + (-1)(6) = 4 + 10 - 6 = 8$
- **Entry $(2,1)$:** $0(1) + 1(2) + 3(3) = 0 + 2 + 9 = 11$
- **Entry $(2,2)$:** $0(4) + 1(5) + 3(6) = 0 + 5 + 18 = 23$

Thus:
$$B^T A^T = \begin{pmatrix}2 & 8 \\ 11 & 23\end{pmatrix}$$

Comparing $(AB)^T$ and $B^T A^T$:
$$(AB)^T = \begin{pmatrix}2 & 8 \\ 11 & 23\end{pmatrix} = B^T A^T$$
The identity $(AB)^T = B^T A^T$ is fully verified.

---

## 4. Verification and Consistency Checks

1. **Dimension Matching:**
   - $A: 2 \times 3 \implies A^T: 3 \times 2$
   - $B: 3 \times 2 \implies B^T: 2 \times 3$
   - $AB: 2 \times 2 \implies (AB)^T: 2 \times 2$
   - $B^T A^T: (2 \times 3) \times (3 \times 2) = 2 \times 2$. Dimensions match.

2. **Invariance of Trace and Determinant:**
   - $\operatorname{tr}((AB)^T) = 2 + 23 = 25$
   - $\operatorname{tr}(B^T A^T) = 2 + 23 = 25 \quad \checkmark$
   - $\det((AB)^T) = \det(AB) = 2(23) - 11(8) = 46 - 88 = -42$
   - $\det(B^T A^T) = 2(23) - 8(11) = 46 - 88 = -42 \quad \checkmark$

