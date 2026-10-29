# Solution to Problem 11: When Do Matrices Commute?

## 1. Problem Statement

Given the matrices:
$$A=\begin{pmatrix}1&1\\0&1\end{pmatrix},\qquad B=\begin{pmatrix}a&b\\c&d\end{pmatrix}$$

1. Find the necessary and sufficient conditions on the real parameters $a, b, c, d$ under which $AB=BA$.
2. Describe the general form of all such matrices $B$ that commute with $A$.

---

## 2. Theoretical Background and Concepts

- **Commutator and Centralizer:**  
  Two square matrices $A$ and $B$ commute if and only if their commutator vanishes:
  $$[A, B] = AB - BA = 0.$$
  The set of all matrices that commute with a given matrix $A$ is called the **centralizer** (or commutant) of $A$, denoted $C(A) = \{B \in \mathbb{R}^{n \times n} : AB = BA\}$.
- **Properties of the Centralizer:**
  - $C(A)$ is a linear subspace of $\mathbb{R}^{n \times n}$ and a subalgebra (closed under addition, scalar multiplication, and matrix multiplication).
  - $C(A)$ always contains the identity matrix $I$ and all scalar powers $A^k$, as well as any polynomial in $A$: $p(A) = \sum c_k A^k$.
  - For a non-derogatory matrix (like a single Jordan block), the centralizer consists precisely of all polynomials in $A$ of degree at most $n-1$.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute the Product $AB$

$$AB = \begin{pmatrix}1&1\\0&1\end{pmatrix}\begin{pmatrix}a&b\\c&d\end{pmatrix}$$

Computing each entry:
- Row 1, Col 1: $1(a) + 1(c) = a + c$
- Row 1, Col 2: $1(b) + 1(d) = b + d$
- Row 2, Col 1: $0(a) + 1(c) = c$
- Row 2, Col 2: $0(b) + 1(d) = d$

Thus:
$$AB = \begin{pmatrix}a+c & b+d \\ c & d\end{pmatrix}$$

### Step 2: Compute the Product $BA$

$$BA = \begin{pmatrix}a&b\\c&d\end{pmatrix}\begin{pmatrix}1&1\\0&1\end{pmatrix}$$

Computing each entry:
- Row 1, Col 1: $a(1) + b(0) = a$
- Row 1, Col 2: $a(1) + b(1) = a + b$
- Row 2, Col 1: $c(1) + d(0) = c$
- Row 2, Col 2: $c(1) + d(1) = c + d$

Thus:
$$BA = \begin{pmatrix}a & a+b \\ c & c+d\end{pmatrix}$$

### Step 3: Set $AB = BA$ and Derive Conditions on $a, b, c, d$

For two matrices to be equal, their corresponding entries must be equal:
$$\begin{pmatrix}a+c & b+d \\ c & d\end{pmatrix} = \begin{pmatrix}a & a+b \\ c & c+d\end{pmatrix}$$

This yields a system of four scalar equations:
1. **Entry $(1,1)$:** $a + c = a \implies c = 0$
2. **Entry $(1,2)$:** $b + d = a + b \implies d = a$
3. **Entry $(2,1)$:** $c = c \implies \text{satisfied for all } c$ (with $c=0$, $0=0$)
4. **Entry $(2,2)$:** $d = c + d \implies c = 0$

Equations (1) and (4) both require:
$$c = 0$$
Equation (2) requires:
$$d = a$$
There are no constraints imposed on $b$ or $a$. Hence, $a$ and $b$ can be any arbitrary real numbers.

**Summary of Conditions:**
$$c = 0 \quad \text{and} \quad d = a, \qquad \text{with } a, b \in \mathbb{R} \text{ free parameters.}$$

### Step 4: Describe the General Form of Matrix $B$

Substituting $c = 0$ and $d = a$ into $B$:
$$B = \begin{pmatrix}a & b \\ 0 & a\end{pmatrix}, \qquad \text{for any } a, b \in \mathbb{R}$$

We can express this general matrix as a linear combination of two basis matrices:
$$B = a \begin{pmatrix}1&0\\0&1\end{pmatrix} + b \begin{pmatrix}0&1\\0&0\end{pmatrix} = a I + b N$$
where $I = \begin{pmatrix}1&0\\0&1\end{pmatrix}$ and $N = \begin{pmatrix}0&1\\0&0\end{pmatrix}$.

Notice that $N = A - I$, so:
$$B = a I + b(A - I) = (a - b)I + b A.$$
Letting $\alpha = a - b$ and $\beta = b$, this shows that every commuting matrix $B$ is a linear polynomial in $A$:
$$B = \alpha I + \beta A, \qquad \alpha, \beta \in \mathbb{R}.$$
Thus, the centralizer $C(A)$ is the 2-dimensional subspace of upper triangular Toeplitz matrices:
$$\mathcal{T}_2 = \left\{ \begin{pmatrix}a & b \\ 0 & a\end{pmatrix} : a, b \in \mathbb{R} \right\}.$$

---

## 4. Verification and Consistency Checks

1. **Direct Commutator Evaluation:**  
   Take an arbitrary matrix of the general form $B = \begin{pmatrix}a & b \\ 0 & a\end{pmatrix}$.
   - $AB = \begin{pmatrix}1&1\\0&1\end{pmatrix}\begin{pmatrix}a&b\\0&a\end{pmatrix} = \begin{pmatrix}1(a)+1(0) & 1(b)+1(a) \\ 0(a)+1(0) & 0(b)+1(a)\end{pmatrix} = \begin{pmatrix}a & a+b \\ 0 & a\end{pmatrix}$
   - $BA = \begin{pmatrix}a&b\\0&a\end{pmatrix}\begin{pmatrix}1&1\\0&1\end{pmatrix} = \begin{pmatrix}a(1)+b(0) & a(1)+b(1) \\ 0(1)+a(0) & 0(1)+a(1)\end{pmatrix} = \begin{pmatrix}a & a+b \\ 0 & a\end{pmatrix}$
   Since $AB = BA = \begin{pmatrix}a & a+b \\ 0 & a\end{pmatrix}$ for all $a, b$, every matrix of this form commutes with $A$.

2. **Counterexample for Non-Commuting Matrix:**  
   Let $B = \begin{pmatrix}1 & 0 \\ 1 & 1\end{pmatrix}$ (where $c = 1 \ne 0$).
   - $AB = \begin{pmatrix}1&1\\0&1\end{pmatrix}\begin{pmatrix}1&0\\1&1\end{pmatrix} = \begin{pmatrix}2&1\\1&1\end{pmatrix}$
   - $BA = \begin{pmatrix}1&0\\1&1\end{pmatrix}\begin{pmatrix}1&1\\0&1\end{pmatrix} = \begin{pmatrix}1&1\\1&2\end{pmatrix}$
   Since $\begin{pmatrix}2&1\\1&1\end{pmatrix} \ne \begin{pmatrix}1&1\\1&2\end{pmatrix}$, violating the condition $c=0$ indeed causes noncommutativity.

