# Solution to Problem 07: Identity Matrix, Zero Matrix, and Powers

## 1. Problem Statement

Given:
$$A=\begin{pmatrix}2&1\\0&2\end{pmatrix}$$

1. Compute $AI$, $IA$, and $A+0$ (where $I$ and $0$ are the $2 \times 2$ identity and zero matrices).
2. Compute the powers $A^2$ and $A^3$.
3. Explain the roles of the matrices $I$ and $0$.
4. Describe the pattern observed in successive powers of $A$.

---

## 2. Theoretical Background and Concepts

- **Identity Matrix ($I$):** The identity matrix $I_n$ is the $n \times n$ diagonal matrix with ones on the main diagonal and zeros elsewhere ($I_{ij} = \delta_{ij}$, the Kronecker delta). It serves as the multiplicative identity element:
  $$M I = I M = M \quad \text{for any compatible matrix } M.$$
- **Zero Matrix ($0$):** The zero matrix $0_{m \times n}$ has all entries equal to 0. It serves as the additive identity element:
  $$M + 0 = 0 + M = M.$$
- **Nilpotent Decomposition:** The matrix $A$ can be decomposed as:
  $$A = 2I + N, \quad \text{where } N = \begin{pmatrix}0&1\\0&0\end{pmatrix}.$$
  Since $2I$ commutes with any matrix, the binomial theorem applies to $(2I + N)^k$. Since $N^2 = \begin{pmatrix}0&0\\0&0\end{pmatrix}$ ($N$ is nilpotent of index 2), all higher power terms $N^k$ for $k \ge 2$ vanish.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute $AI$, $IA$, and $A+0$

The $2 \times 2$ identity and zero matrices are:
$$I = \begin{pmatrix}1&0\\0&1\end{pmatrix},\qquad 0 = \begin{pmatrix}0&0\\0&0\end{pmatrix}$$

- **Compute $AI$:**
  $$AI = \begin{pmatrix}2&1\\0&2\end{pmatrix}\begin{pmatrix}1&0\\0&1\end{pmatrix} = \begin{pmatrix}2(1)+1(0) & 2(0)+1(1) \\ 0(1)+2(0) & 0(0)+2(1)\end{pmatrix} = \begin{pmatrix}2&1\\0&2\end{pmatrix} = A$$

- **Compute $IA$:**
  $$IA = \begin{pmatrix}1&0\\0&1\end{pmatrix}\begin{pmatrix}2&1\\0&2\end{pmatrix} = \begin{pmatrix}1(2)+0(0) & 1(1)+0(2) \\ 0(2)+1(0) & 0(1)+1(2)\end{pmatrix} = \begin{pmatrix}2&1\\0&2\end{pmatrix} = A$$

- **Compute $A+0$:**
  $$A+0 = \begin{pmatrix}2&1\\0&2\end{pmatrix} + \begin{pmatrix}0&0\\0&0\end{pmatrix} = \begin{pmatrix}2+0 & 1+0 \\ 0+0 & 2+0\end{pmatrix} = \begin{pmatrix}2&1\\0&2\end{pmatrix} = A$$

### Step 2: Compute $A^2$ and $A^3$

- **Compute $A^2 = A \cdot A$:**
  $$A^2 = \begin{pmatrix}2&1\\0&2\end{pmatrix}\begin{pmatrix}2&1\\0&2\end{pmatrix} = \begin{pmatrix}2(2)+1(0) & 2(1)+1(2) \\ 0(2)+2(0) & 0(1)+2(2)\end{pmatrix} = \begin{pmatrix}4 & 2+2 \\ 0 & 4\end{pmatrix} = \begin{pmatrix}4&4\\0&4\end{pmatrix}$$

- **Compute $A^3 = A^2 \cdot A$:**
  $$A^3 = \begin{pmatrix}4&4\\0&4\end{pmatrix}\begin{pmatrix}2&1\\0&2\end{pmatrix} = \begin{pmatrix}4(2)+4(0) & 4(1)+4(2) \\ 0(2)+4(0) & 0(1)+4(2)\end{pmatrix} = \begin{pmatrix}8 & 4+8 \\ 0 & 8\end{pmatrix} = \begin{pmatrix}8&12\\0&8\end{pmatrix}$$

### Step 3: Explanation of the Roles of $I$ and $0$

- **Role of $I$ (Neutral Element for Multiplication):**  
  Just as the number $1$ is the multiplicative identity in $\mathbb{R}$ ($a \cdot 1 = 1 \cdot a = a$), the identity matrix $I$ leaves any square matrix unchanged when multiplied from the left or right ($IA = AI = A$). In terms of linear maps, $I$ corresponds to the identity operator $\operatorname{id}(v) = v$.
- **Role of $0$ (Neutral Element for Addition):**  
  Just as the number $0$ is the additive identity in $\mathbb{R}$ ($a + 0 = a$), the zero matrix leaves any matrix unchanged under matrix addition ($A + 0 = A$).

### Step 4: Describe the Pattern in Successive Powers of $A$

Let us inspect the powers:
- $A^1 = \begin{pmatrix}2&1\\0&2\end{pmatrix} = \begin{pmatrix}2^1 & 1 \cdot 2^0 \\ 0 & 2^1\end{pmatrix}$
- $A^2 = \begin{pmatrix}4&4\\0&4\end{pmatrix} = \begin{pmatrix}2^2 & 2 \cdot 2^1 \\ 0 & 2^2\end{pmatrix}$
- $A^3 = \begin{pmatrix}8&12\\0&8\end{pmatrix} = \begin{pmatrix}2^3 & 3 \cdot 2^2 \\ 0 & 2^3\end{pmatrix}$

**Pattern Observation:**  
For any integer $n \ge 1$:
$$A^n = \begin{pmatrix}2^n & n \cdot 2^{n-1} \\ 0 & 2^n\end{pmatrix}$$
- The diagonal entries always equal $2^n$.
- The lower-left entry remains $0$ (the matrix remains upper-triangular).
- The upper-right entry equals $n \cdot 2^{n-1}$, which is the derivative $\frac{d}{d\lambda}[\lambda^n]|_{\lambda=2}$ (reflecting the Jordan block structure of $A$).

---

## 4. Verification and Consistency Checks

1. **Binomial Expansion Check:**
   Write $A = 2I + N$ with $N = \begin{pmatrix}0&1\\0&0\end{pmatrix}$. Note that $N^2 = \begin{pmatrix}0&0\\0&0\end{pmatrix}$.
   Because $(2I)N = N(2I) = 2N$, we can expand by the binomial theorem:
   $$A^n = (2I + N)^n = \sum_{k=0}^n \binom{n}{k} (2I)^{n-k} N^k = \binom{n}{0} 2^n I + \binom{n}{1} 2^{n-1} N + 0 = 2^n I + n 2^{n-1} N$$
   $$A^n = 2^n \begin{pmatrix}1&0\\0&1\end{pmatrix} + n 2^{n-1} \begin{pmatrix}0&1\\0&0\end{pmatrix} = \begin{pmatrix}2^n & n 2^{n-1} \\ 0 & 2^n\end{pmatrix}$$
   This algebraically proves the observed pattern for all $n \in \mathbb{N}$.

2. **Associativity of Power $A^3 = A \cdot A^2$:**
   $$A \cdot A^2 = \begin{pmatrix}2&1\\0&2\end{pmatrix}\begin{pmatrix}4&4\\0&4\end{pmatrix} = \begin{pmatrix}2(4)+1(0) & 2(4)+1(4) \\ 0(4)+2(0) & 0(4)+2(4)\end{pmatrix} = \begin{pmatrix}8 & 8+4 \\ 0 & 8\end{pmatrix} = \begin{pmatrix}8&12\\0&8\end{pmatrix} \quad \checkmark$$
   The product $A \cdot A^2$ equals $A^2 \cdot A$, verifying associativity.

