# Solution to Problem 09: Composing Transformations

## 1. Problem Statement

Let:
$$S=\begin{pmatrix}2&0\\0&1\end{pmatrix},\qquad R=\begin{pmatrix}0&-1\\1&0\end{pmatrix},\qquad x=\begin{pmatrix}1\\2\end{pmatrix}$$

The matrix $S$ describes nonuniform scaling (stretching along the $x$-axis by a factor of 2), while $R$ describes a $90^\circ$ counterclockwise rotation.

1. Compute $RSx$.
2. Compute $SRx$.
3. Compare the results and explain geometrically why the order of these transformations matters.

---

## 2. Theoretical Background and Concepts

- **Linear Transformations and Matrices:**  
  Every $2 \times 2$ real matrix defines a linear transformation $T: \mathbb{R}^2 \to \mathbb{R}^2$ via matrix-vector multiplication $T(v) = Mv$.
- **Composition of Transformations:**  
  Applying transformation $T_1$ (matrix $M_1$) followed by $T_2$ (matrix $M_2$) corresponds to the matrix product $M_2 M_1$:
  $$(T_2 \circ T_1)(v) = M_2(M_1 v) = (M_2 M_1)v.$$
- **Geometric Role of Order:**  
  Because matrix multiplication is noncommutative, the composition of spatial transformations typically depends on the sequence in which they are performed ($T_2 \circ T_1 \ne T_1 \circ T_2$). Nonuniform scaling treats coordinates along different axes differently; therefore, whether a rotation is performed before or after scaling affects which physical axes are stretched.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute $RSx$

We first compute $Sx$ (scaling first):
$$Sx = \begin{pmatrix}2&0\\0&1\end{pmatrix}\begin{pmatrix}1\\2\end{pmatrix} = \begin{pmatrix}2(1)+0(2)\\0(1)+1(2)\end{pmatrix} = \begin{pmatrix}2\\2\end{pmatrix}$$

Next, we apply the rotation $R$ to the result $Sx$:
$$RSx = R(Sx) = \begin{pmatrix}0&-1\\1&0\end{pmatrix}\begin{pmatrix}2\\2\end{pmatrix} = \begin{pmatrix}0(2) + (-1)(2)\\1(2) + 0(2)\end{pmatrix} = \begin{pmatrix}-2\\2\end{pmatrix}$$

Alternatively, computing the combined transformation matrix $RS$:
$$RS = \begin{pmatrix}0&-1\\1&0\end{pmatrix}\begin{pmatrix}2&0\\0&1\end{pmatrix} = \begin{pmatrix}0(2)+(-1)(0) & 0(0)+(-1)(1) \\ 1(2)+0(0) & 1(0)+0(1)\end{pmatrix} = \begin{pmatrix}0&-1\\2&0\end{pmatrix}$$
$$(RS)x = \begin{pmatrix}0&-1\\2&0\end{pmatrix}\begin{pmatrix}1\\2\end{pmatrix} = \begin{pmatrix}0(1)-1(2)\\2(1)+0(2)\end{pmatrix} = \begin{pmatrix}-2\\2\end{pmatrix}$$

### Step 2: Compute $SRx$

We first compute $Rx$ (rotation first):
$$Rx = \begin{pmatrix}0&-1\\1&0\end{pmatrix}\begin{pmatrix}1\\2\end{pmatrix} = \begin{pmatrix}0(1) + (-1)(2)\\1(1) + 0(2)\end{pmatrix} = \begin{pmatrix}-2\\1\end{pmatrix}$$

Next, we apply the scaling $S$ to the result $Rx$:
$$SRx = S(Rx) = \begin{pmatrix}2&0\\0&1\end{pmatrix}\begin{pmatrix}-2\\1\end{pmatrix} = \begin{pmatrix}2(-2) + 0(1)\\0(-2) + 1(1)\end{pmatrix} = \begin{pmatrix}-4\\1\end{pmatrix}$$

Alternatively, computing the combined transformation matrix $SR$:
$$SR = \begin{pmatrix}2&0\\0&1\end{pmatrix}\begin{pmatrix}0&-1\\1&0\end{pmatrix} = \begin{pmatrix}2(0)+0(1) & 2(-1)+0(0) \\ 0(0)+1(1) & 0(-1)+1(0)\end{pmatrix} = \begin{pmatrix}0&-2\\1&0\end{pmatrix}$$
$$(SR)x = \begin{pmatrix}0&-2\\1&0\end{pmatrix}\begin{pmatrix}1\\2\end{pmatrix} = \begin{pmatrix}0(1)-2(2)\\1(1)+0(2)\end{pmatrix} = \begin{pmatrix}-4\\1\end{pmatrix}$$

### Step 3: Comparison and Geometric Interpretation

Comparing the outputs:
$$RSx = \begin{pmatrix}-2\\2\end{pmatrix} \ne \begin{pmatrix}-4\\1\end{pmatrix} = SRx$$

**Geometric Explanation:**
- **In $RSx$ (Scale first, then Rotate):**
  1. The point $(1,2)$ is scaled horizontally by a factor of 2, moving to $(2,2)$. The $x$-coordinate doubled, while the $y$-coordinate was preserved.
  2. The point $(2,2)$ is then rotated $90^\circ$ counterclockwise. Under this rotation, the original horizontal component (which was doubled to 2) is mapped to the positive $y$-axis (giving $y=2$), while the vertical component (2) is mapped to the negative $x$-axis (giving $x=-2$). The final point is $(-2, 2)$.
- **In $SRx$ (Rotate first, then Scale):**
  1. The point $(1,2)$ is rotated $90^\circ$ counterclockwise first, placing it at $(-2,1)$. Here, the original $y$-value became the negative $x$-coordinate ($-2$).
  2. Now the horizontal stretch $S$ acts on this rotated vector. It doubles whatever is currently along the $x$-axis: the $-2$ becomes $-4$. The $y$-coordinate remains $1$. The final point is $(-4, 1)$.

Because the scaling is **anisotropic** (it acts exclusively along the $x$-axis), changing the order alters which of the original components ends up aligned with the stretch axis when the scaling is applied. Hence, the order of composition produces entirely different geometric results.

---

## 4. Verification and Consistency Checks

1. **Matrix Invariants:**
   - $\det(S) = 2 \cdot 1 - 0 \cdot 0 = 2$ (scaling by area factor 2).
   - $\det(R) = 0 \cdot 0 - (-1)(1) = 1$ (rigid rotation preserves area and orientation).
   - $\det(RS) = \det(R)\det(S) = 1 \cdot 2 = 2$. Check: $\det\begin{pmatrix}0&-1\\2&0\end{pmatrix} = 0 - (-2) = 2 \quad \checkmark$
   - $\det(SR) = \det(S)\det(R) = 2 \cdot 1 = 2$. Check: $\det\begin{pmatrix}0&-2\\1&0\end{pmatrix} = 0 - (-2) = 2 \quad \checkmark$
   Both preserve the oriented area scaling factor of 2.

2. **Vector Length Check:**
   - $\|x\| = \sqrt{1^2 + 2^2} = \sqrt{5}$.
   - $\|RSx\| = \sqrt{(-2)^2 + 2^2} = \sqrt{8} = 2\sqrt{2}$. (Since $R$ is an isometry, $\|RSx\| = \|Sx\| = \sqrt{2^2 + 2^2} = \sqrt{8} \quad \checkmark$).
   - $\|SRx\| = \sqrt{(-4)^2 + 1^2} = \sqrt{17}$.
   Since $\|RSx\| \ne \|SRx\|$, the vectors clearly cannot be equal.

