# Solution to Problem 12: Formula for a Matrix Power

## 1. Problem Statement

Let:
$$A=\begin{pmatrix}1&1\\0&1\end{pmatrix}$$

1. Compute $A^2$, $A^3$, and $A^4$.
2. Formulate a conjecture for the general power $A^n$ for all positive integers $n \in \mathbb{N}$.
3. Prove the conjecture by mathematical induction: assume the formula holds for $n$, compute $A^{n+1} = A^n \cdot A$, and verify that the formula for $n+1$ is obtained.

---

## 2. Theoretical Background and Concepts

- **Powers of a Matrix:**  
  For any square matrix $A \in \mathbb{R}^{m \times m}$ and $n \in \mathbb{N}$, the $n$-th power is defined recursively:
  $$A^1 = A, \qquad A^{n+1} = A^n \cdot A.$$
- **Shear Mapping Interpretation:**  
  The matrix $A = \begin{pmatrix}1&1\\0&1\end{pmatrix}$ represents a standard horizontal shear mapping of the plane:
  $$\begin{pmatrix}x\\y\end{pmatrix} \mapsto \begin{pmatrix}x+y\\y\end{pmatrix}.$$
  Every point is shifted parallel to the $x$-axis by an amount proportional to its $y$-coordinate. Applying this transformation $n$ times intuitively displaces points by $n \cdot y$ along the $x$-axis while preserving their $y$-coordinates.
- **Mathematical Induction:**  
  To prove a statement $P(n)$ for all $n \ge 1$:
  1. **Base Case:** Prove $P(1)$ is true.
  2. **Inductive Step:** Show that if $P(k)$ is assumed true (inductive hypothesis), then $P(k+1)$ must also be true.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute $A^2$, $A^3$, and $A^4$

- **Compute $A^2 = A \cdot A$:**
  $$A^2 = \begin{pmatrix}1&1\\0&1\end{pmatrix}\begin{pmatrix}1&1\\0&1\end{pmatrix} = \begin{pmatrix}1(1)+1(0) & 1(1)+1(1) \\ 0(1)+1(0) & 0(1)+1(1)\end{pmatrix} = \begin{pmatrix}1 & 1+1 \\ 0 & 1\end{pmatrix} = \begin{pmatrix}1&2\\0&1\end{pmatrix}$$

- **Compute $A^3 = A^2 \cdot A$:**
  $$A^3 = \begin{pmatrix}1&2\\0&1\end{pmatrix}\begin{pmatrix}1&1\\0&1\end{pmatrix} = \begin{pmatrix}1(1)+2(0) & 1(1)+2(1) \\ 0(1)+1(0) & 0(1)+1(1)\end{pmatrix} = \begin{pmatrix}1 & 1+2 \\ 0 & 1\end{pmatrix} = \begin{pmatrix}1&3\\0&1\end{pmatrix}$$

- **Compute $A^4 = A^3 \cdot A$:**
  $$A^4 = \begin{pmatrix}1&3\\0&1\end{pmatrix}\begin{pmatrix}1&1\\0&1\end{pmatrix} = \begin{pmatrix}1(1)+3(0) & 1(1)+3(1) \\ 0(1)+1(0) & 0(1)+1(1)\end{pmatrix} = \begin{pmatrix}1 & 1+3 \\ 0 & 1\end{pmatrix} = \begin{pmatrix}1&4\\0&1\end{pmatrix}$$

---

### Step 2: Formulate the Conjecture for $A^n$

Examining the computed powers:
- For $n=1$: $A^1 = \begin{pmatrix}1&1\\0&1\end{pmatrix}$
- For $n=2$: $A^2 = \begin{pmatrix}1&2\\0&1\end{pmatrix}$
- For $n=3$: $A^3 = \begin{pmatrix}1&3\\0&1\end{pmatrix}$
- For $n=4$: $A^4 = \begin{pmatrix}1&4\\0&1\end{pmatrix}$

In every power:
- The diagonal entries remain fixed at $1$.
- The bottom-left entry remains $0$.
- The top-right entry equals the exponent $n$.

**Conjecture:**  
For any integer $n \ge 1$:
$$A^n = \begin{pmatrix}1&n\\0&1\end{pmatrix}$$

---

### Step 3: Proof by Mathematical Induction

- **Base Case ($n = 1$):**  
  For $n = 1$:
  $$\begin{pmatrix}1&1\\0&1\end{pmatrix} = A^1 = A$$
  The formula holds for $n=1$.

- **Inductive Hypothesis:**  
  Assume the formula holds for an arbitrary positive integer $n = k$:
  $$A^k = \begin{pmatrix}1&k\\0&1\end{pmatrix}$$

- **Inductive Step (Computing $A^{k+1}$):**  
  Using the definition of matrix power $A^{k+1} = A^k \cdot A$ and substituting the inductive hypothesis:
  $$A^{k+1} = \begin{pmatrix}1&k\\0&1\end{pmatrix}\begin{pmatrix}1&1\\0&1\end{pmatrix}$$

  Carrying out the matrix multiplication:
  - Entry $(1,1)$: $1(1) + k(0) = 1$
  - Entry $(1,2)$: $1(1) + k(1) = 1 + k = k + 1$
  - Entry $(2,1)$: $0(1) + 1(0) = 0$
  - Entry $(2,2)$: $0(1) + 1(1) = 1$

  Therefore:
  $$A^{k+1} = \begin{pmatrix}1 & k+1 \\ 0 & 1\end{pmatrix}$$

This is precisely the claimed formula with $n$ replaced by $k+1$.  
By the Principle of Mathematical Induction, the formula:
$$A^n = \begin{pmatrix}1&n\\0&1\end{pmatrix}$$
holds for all $n \in \mathbb{N}$.

---

## 4. Verification and Consistency Checks

1. **Binomial Expansion Check:**  
   Write $A = I + N$, where $I = \begin{pmatrix}1&0\\0&1\end{pmatrix}$ and $N = \begin{pmatrix}0&1\\0&0\end{pmatrix}$.  
   Note that $N^2 = \begin{pmatrix}0&0\\0&0\end{pmatrix}$.  
   Since $I$ and $N$ commute ($IN = NI = N$), the binomial theorem gives:
   $$A^n = (I + N)^n = \sum_{j=0}^n \binom{n}{j} I^{n-j} N^j = \binom{n}{0} I + \binom{n}{1} N + 0 = I + nN$$
   $$A^n = \begin{pmatrix}1&0\\0&1\end{pmatrix} + n \begin{pmatrix}0&1\\0&0\end{pmatrix} = \begin{pmatrix}1&n\\0&1\end{pmatrix} \quad \checkmark$$

2. **Inverse Power Extension ($n = -1$):**  
   If the formula extends to negative integers: $A^{-1} = \begin{pmatrix}1&-1\\0&1\end{pmatrix}$.  
   Checking $A \cdot A^{-1}$:
   $$\begin{pmatrix}1&1\\0&1\end{pmatrix}\begin{pmatrix}1&-1\\0&1\end{pmatrix} = \begin{pmatrix}1& -1+1 \\ 0 & 1\end{pmatrix} = \begin{pmatrix}1&0\\0&1\end{pmatrix} = I \quad \checkmark$$
   The formula is robust and universally consistent across all integers $\mathbb{Z}$.

