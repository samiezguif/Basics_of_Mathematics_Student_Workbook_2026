# Solution to Problem 04: Matrix Multiplication and Noncommutativity

## 1. Problem Statement

Given the matrices:
$$A=\begin{pmatrix}1&2\\0&1\end{pmatrix},\qquad B=\begin{pmatrix}2&0\\3&1\end{pmatrix}$$

1. Compute the product $AB$.
2. Compute the product $BA$.
3. Determine whether $AB=BA$.
4. Use this example to explain what noncommutativity of matrix multiplication means.

---

## 2. Theoretical Background and Concepts

- **Matrix Multiplication:** Let $A \in \mathbb{R}^{m \times k}$ and $B \in \mathbb{R}^{k \times n}$. The entry in row $i$ and column $j$ of the product $C = AB \in \mathbb{R}^{m \times n}$ is given by the dot product of the $i$-th row of $A$ and the $j$-th column of $B$:
  $$c_{ij} = \sum_{r=1}^k a_{ir} b_{rj} = a_{i1}b_{1j} + a_{i2}b_{2j} + \cdots + a_{ik}b_{kj}.$$
- **Commutativity vs. Noncommutativity:**  
  A binary operation $*$ on a set is commutative if $x * y = y * x$ for all elements. Real number multiplication is commutative ($a \cdot b = b \cdot a$).  
  In matrix algebra, even when both matrices are square of the same dimension $n \times n$ (so that both $AB$ and $BA$ are always defined and have the same dimensions), generally:
  $$AB \ne BA.$$
  Matrix multiplication represents the composition of linear transformations. In general, applying transformation $B$ followed by $A$ does not yield the same mapping as applying $A$ followed by $B$.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute $AB$

$$AB = \begin{pmatrix}1&2\\0&1\end{pmatrix}\begin{pmatrix}2&0\\3&1\end{pmatrix}$$

Computing each entry individually:
- **Entry $(1,1)$:** $(\text{row } 1 \text{ of } A) \cdot (\text{col } 1 \text{ of } B) = 1(2) + 2(3) = 2 + 6 = 8$
- **Entry $(1,2)$:** $(\text{row } 1 \text{ of } A) \cdot (\text{col } 2 \text{ of } B) = 1(0) + 2(1) = 0 + 2 = 2$
- **Entry $(2,1)$:** $(\text{row } 2 \text{ of } A) \cdot (\text{col } 1 \text{ of } B) = 0(2) + 1(3) = 0 + 3 = 3$
- **Entry $(2,2)$:** $(\text{row } 2 \text{ of } A) \cdot (\text{col } 2 \text{ of } B) = 0(0) + 1(1) = 0 + 1 = 1$

Thus:
$$AB = \begin{pmatrix}8 & 2 \\ 3 & 1\end{pmatrix}$$

### Step 2: Compute $BA$

$$BA = \begin{pmatrix}2&0\\3&1\end{pmatrix}\begin{pmatrix}1&2\\0&1\end{pmatrix}$$

Computing each entry individually:
- **Entry $(1,1)$:** $(\text{row } 1 \text{ of } B) \cdot (\text{col } 1 \text{ of } A) = 2(1) + 0(0) = 2 + 0 = 2$
- **Entry $(1,2)$:** $(\text{row } 1 \text{ of } B) \cdot (\text{col } 2 \text{ of } A) = 2(2) + 0(1) = 4 + 0 = 4$
- **Entry $(2,1)$:** $(\text{row } 2 \text{ of } B) \cdot (\text{col } 1 \text{ of } A) = 3(1) + 1(0) = 3 + 0 = 3$
- **Entry $(2,2)$:** $(\text{row } 2 \text{ of } B) \cdot (\text{col } 2 \text{ of } A) = 3(2) + 1(1) = 6 + 1 = 7$

Thus:
$$BA = \begin{pmatrix}2 & 4 \\ 3 & 7\end{pmatrix}$$

### Step 3: Determine Whether $AB = BA$

Comparing the two matrices:
$$AB = \begin{pmatrix}8 & 2 \\ 3 & 1\end{pmatrix} \ne \begin{pmatrix}2 & 4 \\ 3 & 7\end{pmatrix} = BA$$
Clearly, entry $(1,1)$ ($8 \ne 2$), entry $(1,2)$ ($2 \ne 4$), and entry $(2,2)$ ($1 \ne 7$) differ.
Therefore, **$AB \ne BA$**.

### Step 4: Explanation of Noncommutativity

In arithmetic with numbers, the order of multiplication is irrelevant ($2 \times 3 = 3 \times 2 = 6$). In linear algebra, however, matrices act as operators on spaces.
- Matrix $A$ represents a horizontal shear mapping ($x \mapsto x + 2y, y \mapsto y$).
- Matrix $B$ represents a vertical shear combined with horizontal scaling ($x \mapsto 2x, y \mapsto 3x + y$).
When we compute $ABx = A(Bx)$, the transformation $B$ is applied first, and $A$ acts on the resulting output. When we compute $BAx = B(Ax)$, transformation $A$ acts first, and $B$ acts second. Because the spatial transformations alter coordinates along different axes, applying them in reverse sequence changes where points in the plane end up. Hence, matrix multiplication is **noncommutative**.

---

## 4. Verification and Consistency Checks

1. **Determinant Multiplicative Property Check:**  
   A necessary property of matrix multiplication is $\det(MN) = \det(M)\det(N)$.
   - $\det(A) = 1(1) - 2(0) = 1$
   - $\det(B) = 2(1) - 0(3) = 2$
   - Expected determinant of both products: $\det(AB) = \det(BA) = 1 \cdot 2 = 2$.
   - Checking $AB$: $\det(AB) = 8(1) - 2(3) = 8 - 6 = 2 \quad \checkmark$
   - Checking $BA$: $\det(BA) = 2(7) - 4(3) = 14 - 12 = 2 \quad \checkmark$

2. **Trace Property Check:**  
   For any square matrices, the trace is cyclic: $\operatorname{tr}(AB) = \operatorname{tr}(BA)$.
   - $\operatorname{tr}(AB) = 8 + 1 = 9$
   - $\operatorname{tr}(BA) = 2 + 7 = 9$
   - $\operatorname{tr}(AB) = \operatorname{tr}(BA) = 9 \quad \checkmark$

Both invariant checks hold as useful consistency checks (note that while determinant and trace agreement confirm global algebraic properties of the products, entrywise correctness is verified by the direct row-column dot products computed in Section 3).

