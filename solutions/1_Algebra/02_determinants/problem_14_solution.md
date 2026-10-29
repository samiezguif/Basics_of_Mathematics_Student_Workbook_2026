# Solution to Problem 14: A System of Equations and the Determinant

## 1. Problem Statement

Consider the linear system $Ax = b$, where:
$$A=\begin{pmatrix}1&2\\k&4\end{pmatrix},\qquad x=\begin{pmatrix}x_1\\x_2\end{pmatrix},\qquad b=\begin{pmatrix}b_1\\b_2\end{pmatrix}$$

1. Determine all values of the parameter $k$ for which the system has exactly one solution for every right-hand side vector $b$.
2. For the remaining value of $k$:
   - Provide an example of a right-hand side $b$ for which the system has infinitely many solutions, and find the general solution.
   - Provide an example of a right-hand side $b$ for which the system has no solutions (inconsistent).

---

## 2. Theoretical Background and Concepts

- **Determinant and Unique Solvability (Cramer's Rule):**  
  For a square $n \times n$ linear system $Ax = b$, the system possesses a unique solution for every vector $b \in \mathbb{R}^n$ if and only if the coefficient matrix $A$ is invertible:
  $$\text{Unique solution for every } b \iff \det A \ne 0.$$
- **Singular Case ($\det A = 0$):**  
  When $\det A = 0$, the matrix has deficient rank ($\operatorname{rank}(A) < n$). By the Rouché–Capelli Theorem:
  - If the right-hand side vector $b$ lies in the column space of $A$ ($\operatorname{rank}(A) = \operatorname{rank}(A|b)$), the system is **consistent with infinitely many solutions**.
  - If $b$ does not lie in the column space ($\operatorname{rank}(A|b) > \operatorname{rank}(A)$), the equations contradict each other, and there are **no solutions**.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute $\det A$ and Find the Condition for a Unique Solution

The coefficient matrix is:
$$A = \begin{pmatrix}1&2\\k&4\end{pmatrix}$$

Compute its determinant:
$$\det A = (1)(4) - (2)(k) = 4 - 2k$$

The system $Ax = b$ has a unique solution for every $b$ if and only if:
$$\det A \ne 0 \iff 4 - 2k \ne 0 \iff 2k \ne 4 \iff k \ne 2$$

**Conclusion for Part 1:**  
The system has exactly one solution for every right-hand side vector $b$ if and only if:
$$k \ne 2$$

---

### Step 2: Analyze the Remaining Case $k = 2$

For the remaining value $k = 2$, the system becomes:
$$\begin{pmatrix}1&2\\2&4\end{pmatrix}\begin{pmatrix}x_1\\x_2\end{pmatrix} = \begin{pmatrix}b_1\\b_2\end{pmatrix}$$

In equation form:
$$\begin{cases}
1x_1 + 2x_2 = b_1 & \quad (\text{Eq. 1}) \\
2x_1 + 4x_2 = b_2 & \quad (\text{Eq. 2})
\end{cases}$$

Notice that the left-hand side of Equation 2 is exactly twice the left-hand side of Equation 1:
$$2(x_1 + 2x_2) = 2x_1 + 4x_2.$$
For the system to be consistent, the right-hand sides must satisfy the exact same proportion:
$$b_2 = 2b_1.$$

---

### Step 3: Example with Infinitely Many Solutions ($b_2 = 2b_1$)

Choose $b_1 = 1$, which requires $b_2 = 2(1) = 2$:
$$b = \begin{pmatrix}1\\2\end{pmatrix}$$

The system becomes:
$$\begin{cases}
x_1 + 2x_2 = 1 \\
2x_1 + 4x_2 = 2
\end{cases}$$

Dividing the second equation by 2 yields $x_1 + 2x_2 = 1$, which is completely redundant with the first equation.  
We choose $x_2 = t \in \mathbb{R}$ as a free parameter:
$$x_1 = 1 - 2t$$

The general solution vector is:
$$x = \begin{pmatrix}1 - 2t\\t\end{pmatrix} = \begin{pmatrix}1\\0\end{pmatrix} + t \begin{pmatrix}-2\\1\end{pmatrix}, \qquad t \in \mathbb{R}$$
Since $t$ can be any real number, there are **infinitely many solutions**.

---

### Step 4: Example with No Solution ($b_2 \ne 2b_1$)

Choose $b_1 = 1$ and $b_2 = 3$ (so $b_2 \ne 2b_1$):
$$b = \begin{pmatrix}1\\3\end{pmatrix}$$

The system becomes:
$$\begin{cases}
x_1 + 2x_2 = 1 & \quad (\text{Eq. 1}) \\
2x_1 + 4x_2 = 3 & \quad (\text{Eq. 2})
\end{cases}$$

Multiply Equation 1 by 2:
$$2x_1 + 4x_2 = 2$$
Subtract this from Equation 2:
$$(2x_1 + 4x_2) - (2x_1 + 4x_2) = 3 - 2 \implies 0 = 1$$
This is an impossible contradiction ($0 \ne 1$).  
Therefore, for $b = \begin{pmatrix}1\\3\end{pmatrix}$, the system is inconsistent and has **no solution**.

---

## 4. Verification and Consistency Checks

1. **Cramer's Rule Verification for $k \ne 2$:**  
   For arbitrary $b = \begin{pmatrix}b_1\\b_2\end{pmatrix}$:
   $$x_1 = \frac{\begin{vmatrix}b_1&2\\b_2&4\end{vmatrix}}{\det A} = \frac{4b_1 - 2b_2}{4 - 2k} = \frac{2b_1 - b_2}{2 - k}$$
   $$x_2 = \frac{\begin{vmatrix}1&b_1\\k&b_2\end{vmatrix}}{\det A} = \frac{b_2 - k b_1}{4 - 2k}$$
   For every $k \ne 2$, the denominator is non-zero, guaranteeing a unique solution for every $b \in \mathbb{R}^2 \quad \checkmark$.

2. **Rank Check for $k = 2$:**
   - Coefficient matrix rank: $\operatorname{rank}\begin{pmatrix}1&2\\2&4\end{pmatrix} = 1$.
   - For $b = \begin{pmatrix}1\\2\end{pmatrix}$: $\operatorname{rank}\begin{pmatrix}1&2&1\\2&4&2\end{pmatrix} = 1 = \operatorname{rank}(A) < 2 \implies$ infinitely many solutions $\quad \checkmark$.
   - For $b = \begin{pmatrix}1\\3\end{pmatrix}$: $\operatorname{rank}\begin{pmatrix}1&2&1\\2&4&3\end{pmatrix} = 2 > \operatorname{rank}(A) \implies$ no solution $\quad \checkmark$.
