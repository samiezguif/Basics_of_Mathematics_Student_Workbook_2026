# Solution to Problem 13: A Recurrence Written in Matrix Form

## 1. Problem Statement

Let:
$$F=\begin{pmatrix}1&1\\1&0\end{pmatrix}$$

1. Compute $F^2$, $F^3$, $F^4$, and $F^5$.
2. Compare the numbers obtained with the Fibonacci sequence:
   $$F_0 = 0,\quad F_1 = 1,\quad F_2 = 1,\quad F_3 = 2,\quad F_4 = 3,\quad F_5 = 5,\quad F_6 = 8,\quad \dots$$
   and describe the relationship you observe.
3. Compute the product:
   $$F\begin{pmatrix}a\\b\end{pmatrix}$$
4. Explain how this matrix multiplication performs one recurrence step: how it creates the sum of two consecutive terms and preserves one of them for the subsequent step.

---

## 2. Theoretical Background and Concepts

- **Linear Recurrences and State-Space Representation:**  
  A second-order linear recurrence relation of the form:
  $$x_{n+1} = x_n + x_{n-1}$$
  can be represented as a first-order system of difference equations by defining a state vector containing two consecutive terms:
  $$\mathbf{v}_n = \begin{pmatrix} x_{n+1} \\ x_n \end{pmatrix}.$$
- **Transition (Companion) Matrix:**  
  The transition from state $\mathbf{v}_{n-1}$ to $\mathbf{v}_n$ is governed by the companion matrix $F$:
  $$\mathbf{v}_n = \begin{pmatrix} x_{n+1} \\ x_n \end{pmatrix} = \begin{pmatrix} 1 & 1 \\ 1 & 0 \end{pmatrix} \begin{pmatrix} x_n \\ x_{n-1} \end{pmatrix} = F \mathbf{v}_{n-1}.$$
  By repeated application:
  $$\mathbf{v}_n = F^n \mathbf{v}_0.$$
- **Matrix Powers and Cassini's Identity:**  
  The matrix $F = \begin{pmatrix}1&1\\1&0\end{pmatrix}$ has determinant $\det(F) = 1(0) - 1(1) = -1$. Because $\det(F^n) = (\det F)^n = (-1)^n$, the powers of $F$ directly encode Cassini's identity: $F_{n+1} F_{n-1} - F_n^2 = (-1)^n$.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute the Powers $F^2, F^3, F^4, F^5$

- **Compute $F^2 = F \cdot F$:**
  $$F^2 = \begin{pmatrix}1&1\\1&0\end{pmatrix}\begin{pmatrix}1&1\\1&0\end{pmatrix} = \begin{pmatrix}1(1)+1(1) & 1(1)+1(0) \\ 1(1)+0(1) & 1(1)+0(0)\end{pmatrix} = \begin{pmatrix}2&1\\1&1\end{pmatrix}$$

- **Compute $F^3 = F^2 \cdot F$:**
  $$F^3 = \begin{pmatrix}2&1\\1&1\end{pmatrix}\begin{pmatrix}1&1\\1&0\end{pmatrix} = \begin{pmatrix}2(1)+1(1) & 2(1)+1(0) \\ 1(1)+1(1) & 1(1)+1(0)\end{pmatrix} = \begin{pmatrix}3&2\\2&1\end{pmatrix}$$

- **Compute $F^4 = F^3 \cdot F$:**
  $$F^4 = \begin{pmatrix}3&2\\2&1\end{pmatrix}\begin{pmatrix}1&1\\1&0\end{pmatrix} = \begin{pmatrix}3(1)+2(1) & 3(1)+2(0) \\ 2(1)+1(1) & 2(1)+1(0)\end{pmatrix} = \begin{pmatrix}5&3\\3&2\end{pmatrix}$$

- **Compute $F^5 = F^4 \cdot F$:**
  $$F^5 = \begin{pmatrix}5&3\\3&2\end{pmatrix}\begin{pmatrix}1&1\\1&0\end{pmatrix} = \begin{pmatrix}5(1)+3(1) & 5(1)+3(0) \\ 3(1)+2(1) & 3(1)+2(0)\end{pmatrix} = \begin{pmatrix}8&5\\5&3\end{pmatrix}$$

---

### Step 2: Compare with the Fibonacci Sequence and Describe the Pattern

The standard Fibonacci sequence indexed from $n=0$ is:
$$F_0 = 0,\ F_1 = 1,\ F_2 = 1,\ F_3 = 2,\ F_4 = 3,\ F_5 = 5,\ F_6 = 8,\ F_7 = 13, \dots$$

Comparing each computed power to the Fibonacci terms:
- $F^1 = \begin{pmatrix}1&1\\1&0\end{pmatrix} = \begin{pmatrix}F_2 & F_1 \\ F_1 & F_0\end{pmatrix}$
- $F^2 = \begin{pmatrix}2&1\\1&1\end{pmatrix} = \begin{pmatrix}F_3 & F_2 \\ F_2 & F_1\end{pmatrix}$
- $F^3 = \begin{pmatrix}3&2\\2&1\end{pmatrix} = \begin{pmatrix}F_4 & F_3 \\ F_3 & F_2\end{pmatrix}$
- $F^4 = \begin{pmatrix}5&3\\3&2\end{pmatrix} = \begin{pmatrix}F_5 & F_4 \\ F_4 & F_3\end{pmatrix}$
- $F^5 = \begin{pmatrix}8&5\\5&3\end{pmatrix} = \begin{pmatrix}F_6 & F_5 \\ F_5 & F_4\end{pmatrix}$

**General Relationship Observed:**  
For every integer $n \ge 1$:
$$F^n = \begin{pmatrix}F_{n+1} & F_n \\ F_n & F_{n-1}\end{pmatrix}$$
The four entries of the matrix power $F^n$ involve three consecutive Fibonacci numbers ($F_{n-1}, F_n, F_{n+1}$), with $F_n$ appearing twice along the anti-diagonal.

---

### Step 3: Compute $F\begin{pmatrix}a\\b\end{pmatrix}$

$$F\begin{pmatrix}a\\b\end{pmatrix} = \begin{pmatrix}1&1\\1&0\end{pmatrix}\begin{pmatrix}a\\b\end{pmatrix} = \begin{pmatrix}1\cdot a + 1\cdot b \\ 1\cdot a + 0\cdot b\end{pmatrix} = \begin{pmatrix}a+b\\a\end{pmatrix}$$

---

### Step 4: Explanation of the Recurrence Step Mechanism

Consider the vector $\begin{pmatrix}a\\b\end{pmatrix}$ as storing two consecutive terms of a Fibonacci-type sequence:
- The top entry is the "current" term: $x_k = a$.
- The bottom entry is the "previous" term: $x_{k-1} = b$.

When we multiply this state vector by matrix $F$:
1. **Top Row Operation ($\begin{pmatrix}1 & 1\end{pmatrix}$):**  
   It computes $1 \cdot a + 1 \cdot b = a + b$. According to the recurrence rule $x_{k+1} = x_k + x_{k-1}$, this sum is precisely the **next term** of the sequence ($x_{k+1}$).
2. **Bottom Row Operation ($\begin{pmatrix}1 & 0\end{pmatrix}$):**  
   It extracts $1 \cdot a + 0 \cdot b = a$. This preserves the current term $x_k$ and demotes it to the "previous term" position for the next stage.

Thus, multiplying by $F$ acts as an exact clock-cycle update (a shift-and-add register):
$$\begin{pmatrix}x_k\\x_{k-1}\end{pmatrix} \xrightarrow{\ F\ } \begin{pmatrix}x_k + x_{k-1}\\x_k\end{pmatrix} = \begin{pmatrix}x_{k+1}\\x_k\end{pmatrix}.$$
This turns recursive scalar addition into linear matrix multiplication, enabling fast computation of the $n$-th Fibonacci term in $O(\log n)$ matrix multiplications via binary exponentiation.

---

## 4. Verification and Consistency Checks

1. **Cassini's Identity Check via Determinants:**  
   - $\det(F^1) = 1(0) - 1(1) = -1 = (-1)^1$
   - $\det(F^2) = 2(1) - 1(1) = 1 = (-1)^2$
   - $\det(F^3) = 3(1) - 2(2) = 3 - 4 = -1 = (-1)^3$
   - $\det(F^4) = 5(2) - 3(3) = 10 - 9 = 1 = (-1)^4$
   - $\det(F^5) = 8(3) - 5(5) = 24 - 25 = -1 = (-1)^5$  
   All determinants satisfy $\det(F^n) = F_{n+1} F_{n-1} - F_n^2 = (-1)^n \quad \checkmark$

2. **Eigenvalue Verification (Golden Ratio):**  
   The characteristic polynomial of $F$ is $\det(F - \lambda I) = \lambda^2 - \lambda - 1 = 0$, whose roots are the golden ratio $\phi = \frac{1+\sqrt{5}}{2}$ and $\psi = \frac{1-\sqrt{5}}{2}$.  
   The eigenvalues are identical to the characteristic roots of the Fibonacci recurrence, confirming the exact mathematical equivalence of the matrix model.

