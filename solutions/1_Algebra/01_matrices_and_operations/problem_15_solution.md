# Solution to Problem 15: Associativity of Multiplication and Different Calculation Paths

## 1. Problem Statement

Given the matrices:
$$A=\begin{pmatrix}1&2&0\\0&1&1\end{pmatrix},\quad B=\begin{pmatrix}1&0\\2&1\\-1&3\end{pmatrix},\quad C=\begin{pmatrix}2&1\\0&-1\end{pmatrix}$$

1. Compute the product $(AB)C$ by parenthesizing $(AB)$ first.
2. Compute the product $A(BC)$ by parenthesizing $(BC)$ first.
3. Compare the final results.
4. Compare the computational complexity (number of scalar multiplications and additions) of the two calculation paths.
5. Explain what the associativity of matrix multiplication means in this context.

---

## 2. Theoretical Background and Concepts

- **Associativity of Matrix Multiplication:**  
  For any three conformable matrices $A \in \mathbb{R}^{m \times k}$, $B \in \mathbb{R}^{k \times p}$, and $C \in \mathbb{R}^{p \times n}$, matrix multiplication is associative:
  $$(AB)C = A(BC).$$
  *Reason:* Matrix multiplication represents function composition:
  $$T_A \circ (T_B \circ T_C) = (T_A \circ T_B) \circ T_C.$$
  Because composition of mappings is inherently associative, the grouping of adjacent matrix multiplications does not affect the final linear transformation.
- **Computational Cost of Matrix Multiplication:**  
  Multiplying an $m \times k$ matrix by a $k \times n$ matrix produces an $m \times n$ matrix.
  - Computing each of the $m \cdot n$ entries requires $k$ scalar multiplications and $k - 1$ scalar additions.
  - Total scalar multiplications: $m \cdot k \cdot n$.
  - Total scalar additions: $m \cdot (k - 1) \cdot n$.
  Although $(AB)C = A(BC)$ mathematically, the computational efficiency of the two parenthesizations can differ significantly (the basis of the *Matrix Chain Multiplication* problem).

---

## 3. Detailed Step-by-Step Solution

Let us first record the dimensions of each matrix:
- $A$ is $2 \times 3$ ($m=2, k=3$)
- $B$ is $3 \times 2$ ($k=3, p=2$)
- $C$ is $2 \times 2$ ($p=2, n=2$)

---

### Step 1: Compute Path 1: $(AB)C$

#### First sub-step: Compute $AB$
$A$ is $2 \times 3$ and $B$ is $3 \times 2 \implies AB$ is $2 \times 2$.
$$AB = \begin{pmatrix}1&2&0\\0&1&1\end{pmatrix}\begin{pmatrix}1&0\\2&1\\-1&3\end{pmatrix}$$

Computing each entry:
- $(AB)_{11} = 1(1) + 2(2) + 0(-1) = 1 + 4 + 0 = 5$
- $(AB)_{12} = 1(0) + 2(1) + 0(3) = 0 + 2 + 0 = 2$
- $(AB)_{21} = 0(1) + 1(2) + 1(-1) = 0 + 2 - 1 = 1$
- $(AB)_{22} = 0(0) + 1(1) + 1(3) = 0 + 1 + 3 = 4$

$$AB = \begin{pmatrix}5&2\\1&4\end{pmatrix}$$

#### Second sub-step: Compute $(AB)C$
$(AB)$ is $2 \times 2$ and $C$ is $2 \times 2 \implies (AB)C$ is $2 \times 2$.
$$(AB)C = \begin{pmatrix}5&2\\1&4\end{pmatrix}\begin{pmatrix}2&1\\0&-1\end{pmatrix}$$

Computing each entry:
- $[(AB)C]_{11} = 5(2) + 2(0) = 10 + 0 = 10$
- $[(AB)C]_{12} = 5(1) + 2(-1) = 5 - 2 = 3$
- $[(AB)C]_{21} = 1(2) + 4(0) = 2 + 0 = 2$
- $[(AB)C]_{22} = 1(1) + 4(-1) = 1 - 4 = -3$

$$(AB)C = \begin{pmatrix}10&3\\2&-3\end{pmatrix}$$

---

### Step 2: Compute Path 2: $A(BC)$

#### First sub-step: Compute $BC$
$B$ is $3 \times 2$ and $C$ is $2 \times 2 \implies BC$ is $3 \times 2$.
$$BC = \begin{pmatrix}1&0\\2&1\\-1&3\end{pmatrix}\begin{pmatrix}2&1\\0&-1\end{pmatrix}$$

Computing each entry:
- $(BC)_{11} = 1(2) + 0(0) = 2 + 0 = 2$
- $(BC)_{12} = 1(1) + 0(-1) = 1 + 0 = 1$
- $(BC)_{21} = 2(2) + 1(0) = 4 + 0 = 4$
- $(BC)_{22} = 2(1) + 1(-1) = 2 - 1 = 1$
- $(BC)_{31} = -1(2) + 3(0) = -2 + 0 = -2$
- $(BC)_{32} = -1(1) + 3(-1) = -1 - 3 = -4$

$$BC = \begin{pmatrix}2&1\\4&1\\-2&-4\end{pmatrix}$$

#### Second sub-step: Compute $A(BC)$
$A$ is $2 \times 3$ and $(BC)$ is $3 \times 2 \implies A(BC)$ is $2 \times 2$.
$$A(BC) = \begin{pmatrix}1&2&0\\0&1&1\end{pmatrix}\begin{pmatrix}2&1\\4&1\\-2&-4\end{pmatrix}$$

Computing each entry:
- $[A(BC)]_{11} = 1(2) + 2(4) + 0(-2) = 2 + 8 + 0 = 10$
- $[A(BC)]_{12} = 1(1) + 2(1) + 0(-4) = 1 + 2 + 0 = 3$
- $[A(BC)]_{21} = 0(2) + 1(4) + 1(-2) = 0 + 4 - 2 = 2$
- $[A(BC)]_{22} = 0(1) + 1(1) + 1(-4) = 0 + 1 - 4 = -3$

$$A(BC) = \begin{pmatrix}10&3\\2&-3\end{pmatrix}$$

---

### Step 3: Comparison of the Results

Both evaluation paths yield the identical $2 \times 2$ matrix:
$$(AB)C = A(BC) = \begin{pmatrix}10&3\\2&-3\end{pmatrix}$$

---

### Step 4: Comparison of Intermediate Operations

Let us count the scalar operations for each path:

1. **Path 1: $(AB)C$**
   - **Product $AB$:** Matrix sizes $(2 \times 3) \times (3 \times 2) \to 2 \times 2$:
     - Multiplications: $2 \times 3 \times 2 = 12$
     - Additions: $2 \times (3 - 1) \times 2 = 8$
   - **Product $(AB)C$:** Matrix sizes $(2 \times 2) \times (2 \times 2) \to 2 \times 2$:
     - Multiplications: $2 \times 2 \times 2 = 8$
     - Additions: $2 \times (2 - 1) \times 2 = 4$
   - **Path 1 Totals:** **$12 + 8 = 20$ multiplications**, **$8 + 4 = 12$ additions** (Total arithmetic ops: 32).

2. **Path 2: $A(BC)$**
   - **Product $BC$:** Matrix sizes $(3 \times 2) \times (2 \times 2) \to 3 \times 2$:
     - Multiplications: $3 \times 2 \times 2 = 12$
     - Additions: $3 \times (2 - 1) \times 2 = 6$
   - **Product $A(BC)$:** Matrix sizes $(2 \times 3) \times (3 \times 2) \to 2 \times 2$:
     - Multiplications: $2 \times 3 \times 2 = 12$
     - Additions: $2 \times (3 - 1) \times 2 = 8$
   - **Path 2 Totals:** **$12 + 12 = 24$ multiplications**, **$6 + 8 = 14$ additions** (Total arithmetic ops: 38).

**Conclusion:**  
Path 1 requires **20 scalar multiplications**, whereas Path 2 requires **24 scalar multiplications**. Computing $(AB)C$ first is computationally cheaper than computing $A(BC)$ first by $16.7\%$ in multiplications.

---

### Step 5: Meaning of Associativity

Associativity means that the grouping of multiplications in a chain of matrices does not alter the algebraic result:
$$(AB)C = A(BC) = ABC.$$
In geometric terms:
- Matrix $C: \mathbb{R}^2 \to \mathbb{R}^2$
- Matrix $B: \mathbb{R}^2 \to \mathbb{R}^3$
- Matrix $A: \mathbb{R}^3 \to \mathbb{R}^2$

The compound operation represents the linear mapping $T = T_A \circ T_B \circ T_C: \mathbb{R}^2 \to \mathbb{R}^2$.  
Grouping as $(AB)C$ means first synthesizing the transformation $T_{AB} = T_A \circ T_B: \mathbb{R}^2 \to \mathbb{R}^2$ and then composing it with $T_C$.  
Grouping as $A(BC)$ means first synthesizing the transformation $T_{BC} = T_B \circ T_C: \mathbb{R}^2 \to \mathbb{R}^3$ and then composing it with $T_A$.  
Because both paths describe the exact same sequence of vector transformations applied from right to left to any input vector $v \in \mathbb{R}^2$, the resulting transformation matrix is guaranteed to be identical.

---

## 4. Verification and Consistency Checks

1. **Vector Test Check:**  
   Apply the final matrix to a test vector $v = \begin{pmatrix}1\\1\end{pmatrix}$:
   $$Mv = \begin{pmatrix}10&3\\2&-3\end{pmatrix}\begin{pmatrix}1\\1\end{pmatrix} = \begin{pmatrix}13\\-1\end{pmatrix}$$
   Now test through Path 1:
   - $w = Cv = \begin{pmatrix}2&1\\0&-1\end{pmatrix}\begin{pmatrix}1\\1\end{pmatrix} = \begin{pmatrix}3\\-1\end{pmatrix}$
   - $(AB)w = \begin{pmatrix}5&2\\1&4\end{pmatrix}\begin{pmatrix}3\\-1\end{pmatrix} = \begin{pmatrix}15 - 2 \\ 3 - 4\end{pmatrix} = \begin{pmatrix}13\\-1\end{pmatrix} \quad \checkmark$
   Now test through Path 2:
   - $u = (BC)v = \begin{pmatrix}2&1\\4&1\\-2&-4\end{pmatrix}\begin{pmatrix}1\\1\end{pmatrix} = \begin{pmatrix}3\\5\\-6\end{pmatrix}$
   - $Au = \begin{pmatrix}1&2&0\\0&1&1\end{pmatrix}\begin{pmatrix}3\\5\\-6\end{pmatrix} = \begin{pmatrix}1(3) + 2(5) + 0(-6) \\ 0(3) + 1(5) + 1(-6)\end{pmatrix} = \begin{pmatrix}13\\-1\end{pmatrix} \quad \checkmark$
   Both paths transform the test vector to $\begin{pmatrix}13\\-1\end{pmatrix}$ identically.

2. **Determinant Multiplicativity Check:**  
   Note that $AB$ and $C$ are square matrices:
   - $\det(AB) = 5(4) - 2(1) = 20 - 2 = 18$
   - $\det(C) = 2(-1) - 1(0) = -2$
   - $\det((AB)C) = \det(AB) \cdot \det(C) = 18 \cdot (-2) = -36$
   - Direct determinant of the final result:
     $$\det\begin{pmatrix}10&3\\2&-3\end{pmatrix} = 10(-3) - 3(2) = -30 - 6 = -36 \quad \checkmark$$
   The determinant is strictly verified.

