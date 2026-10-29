# Solution to Problem 07: Using Properties Instead of Recomputing

## 1. Problem Statement

Suppose that for a $3 \times 3$ matrix $A$, its determinant is given by:
$$\det A = -4$$

Without knowing the individual entries of $A$, compute:
1. $\det(2A)$
2. $\det(A^T)$
3. $\det(A^2)$
4. $\det(-A)$

Justify each result using the corresponding algebraic property of determinants.

---

## 2. Theoretical Background and Concepts

Let $M$ be an arbitrary $n \times n$ matrix, and let $c \in \mathbb{R}$ be a scalar.

1. **Scalar Multiplication Property:**  
   Because the determinant is an $n$-linear function (linear in each of its $n$ rows separately), scaling every entry of an $n \times n$ matrix by $c$ pulls out a factor of $c$ from each of the $n$ rows:
   $$\det(cM) = c^n \det(M).$$
2. **Transposition Invariance Property:**  
   Reflecting a matrix across its main diagonal preserves all algebraic permutations in the Leibniz formula. Thus:
   $$\det(M^T) = \det(M).$$
3. **Multiplicative Property (Product Rule):**  
   For any two $n \times n$ matrices $M$ and $N$:
   $$\det(MN) = \det(M) \cdot \det(N).$$
   In particular, for positive integer powers:
   $$\det(M^k) = (\det M)^k.$$
4. **Negation Property:**  
   Negating a matrix is equivalent to scalar multiplication by $c = -1$:
   $$\det(-M) = \det((-1)M) = (-1)^n \det(M).$$

---

## 3. Detailed Step-by-Step Solution

Here, matrix $A$ has dimension $n = 3$, and $\det A = -4$.

### Step 1: Compute $\det(2A)$

- **Applicable Property:** $\det(cA) = c^n \det(A)$ with $c = 2$ and $n = 3$.
- **Calculation:**
  $$\det(2A) = 2^3 \cdot \det(A) = 8 \cdot (-4) = -32$$
- **Justification:** Multiplying $A$ by $2$ multiplies each of its $3$ rows by $2$. Since each row operation scales the determinant by $2$, the total determinant scales by $2 \cdot 2 \cdot 2 = 2^3 = 8$.

---

### Step 2: Compute $\det(A^T)$

- **Applicable Property:** $\det(A^T) = \det(A)$.
- **Calculation:**
  $$\det(A^T) = \det(A) = -4$$
- **Justification:** Transposing a matrix swaps rows with columns. Since column operations have the exact same effect on determinants as row operations, the value of the determinant is invariant under transposition.

---

### Step 3: Compute $\det(A^2)$

- **Applicable Property:** $\det(A^2) = \det(A \cdot A) = \det(A) \cdot \det(A) = (\det A)^2$.
- **Calculation:**
  $$\det(A^2) = (-4)^2 = 16$$
- **Justification:** By the Cauchy–Binet multiplicative formula, the determinant of a matrix product is the product of their individual determinants.

---

### Step 4: Compute $\det(-A)$

- **Applicable Property:** $\det(-A) = (-1)^n \det(A)$ with $n = 3$.
- **Calculation:**
  $$\det(-A) = (-1)^3 \cdot \det(A) = (-1) \cdot (-4) = 4$$
- **Justification:** Negating matrix $A$ scales all $3$ rows by $-1$. Because the dimension $n = 3$ is odd, $(-1)^3 = -1$, which flips the sign of the original determinant.

---

## 4. Verification and Consistency Checks

### Concrete Test Matrix Verification
To confirm all properties simultaneously, consider a simple diagonal $3 \times 3$ matrix with determinant $-4$:
$$A = \begin{pmatrix}1&0&0\\0&1&0\\0&0&-4\end{pmatrix}$$
Clearly, $\det A = 1 \cdot 1 \cdot (-4) = -4$.

1. **Check $\det(2A)$:**
   $$2A = \begin{pmatrix}2&0&0\\0&2&0\\0&0&-8\end{pmatrix} \implies \det(2A) = 2 \cdot 2 \cdot (-8) = -32 \quad \checkmark$$

2. **Check $\det(A^T)$:**
   $$A^T = \begin{pmatrix}1&0&0\\0&1&0\\0&0&-4\end{pmatrix} = A \implies \det(A^T) = -4 \quad \checkmark$$

3. **Check $\det(A^2)$:**
   $$A^2 = \begin{pmatrix}1&0&0\\0&1&0\\0&0&16\end{pmatrix} \implies \det(A^2) = 1 \cdot 1 \cdot 16 = 16 \quad \checkmark$$

4. **Check $\det(-A)$:**
   $$-A = \begin{pmatrix}-1&0&0\\0&-1&0\\0&0&4\end{pmatrix} \implies \det(-A) = (-1) \cdot (-1) \cdot 4 = 4 \quad \checkmark$$

All four property-derived results match the explicit test evaluations exactly.
