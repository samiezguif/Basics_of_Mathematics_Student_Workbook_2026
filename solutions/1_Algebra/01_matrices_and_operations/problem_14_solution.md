# Solution to Problem 14: Rotation Matrices

## 1. Problem Statement

The matrix representing a counterclockwise rotation through an angle $\theta$ in $\mathbb{R}^2$ is:
$$R(\theta)=\begin{pmatrix}\cos\theta&-\sin\theta\\\sin\theta&\cos\theta\end{pmatrix}$$

1. Compute the matrix product $R(\alpha)R(\beta)$.
2. Use the angle-sum trigonometric identities for sine and cosine to show that:
   $$R(\alpha)R(\beta)=R(\alpha+\beta)$$
3. Explain this algebraic result from a geometric perspective.

---

## 2. Theoretical Background and Concepts

- **Trigonometric Angle-Sum Identities:**
  $$\cos(\alpha + \beta) = \cos\alpha \cos\beta - \sin\alpha \sin\beta$$
  $$\sin(\alpha + \beta) = \sin\alpha \cos\beta + \cos\alpha \sin\beta$$
- **Rotation Operator in the Plane:**  
  A counterclockwise rotation about the origin by angle $\theta$ preserves lengths and angles (it is an element of the special orthogonal group $\mathrm{SO}(2)$).
- **Composition of Group Actions:**  
  If rotating by angle $\beta$ is followed by a rotation by angle $\alpha$, the net geometric rotation about the origin is through total angle $\alpha + \beta$. Matrix multiplication algebraically corresponds to the composition of linear transformations.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Write Down the Matrices and Compute $R(\alpha)R(\beta)$

The two rotation matrices are:
$$R(\alpha) = \begin{pmatrix}\cos\alpha & -\sin\alpha \\ \sin\alpha & \cos\alpha\end{pmatrix},\qquad R(\beta) = \begin{pmatrix}\cos\beta & -\sin\beta \\ \sin\beta & \cos\beta\end{pmatrix}$$

Multiplying row-by-column:
$$R(\alpha)R(\beta) = \begin{pmatrix}\cos\alpha & -\sin\alpha \\ \sin\alpha & \cos\alpha\end{pmatrix} \begin{pmatrix}\cos\beta & -\sin\beta \\ \sin\beta & \cos\beta\end{pmatrix}$$

We calculate each of the four entries:

1. **Row 1, Column 1:**
   $$(\text{row } 1) \cdot (\text{col } 1) = (\cos\alpha)(\cos\beta) + (-\sin\alpha)(\sin\beta) = \cos\alpha\cos\beta - \sin\alpha\sin\beta$$

2. **Row 1, Column 2:**
   $$(\text{row } 1) \cdot (\text{col } 2) = (\cos\alpha)(-\sin\beta) + (-\sin\alpha)(\cos\beta) = -(\sin\alpha\cos\beta + \cos\alpha\sin\beta)$$

3. **Row 2, Column 1:**
   $$(\text{row } 2) \cdot (\text{col } 1) = (\sin\alpha)(\cos\beta) + (\cos\alpha)(\sin\beta) = \sin\alpha\cos\beta + \cos\alpha\sin\beta$$

4. **Row 2, Column 2:**
   $$(\text{row } 2) \cdot (\text{col } 2) = (\sin\alpha)(-\sin\beta) + (\cos\alpha)(\cos\beta) = \cos\alpha\cos\beta - \sin\alpha\sin\beta$$

Combining these four entries into a single matrix:
$$R(\alpha)R(\beta) = \begin{pmatrix} \cos\alpha\cos\beta - \sin\alpha\sin\beta & -(\sin\alpha\cos\beta + \cos\alpha\sin\beta) \\ \sin\alpha\cos\beta + \cos\alpha\sin\beta & \cos\alpha\cos\beta - \sin\alpha\sin\beta \end{pmatrix}$$

---

### Step 2: Apply the Angle-Sum Formulas

Using the angle-sum identities:
$$\cos\alpha\cos\beta - \sin\alpha\sin\beta = \cos(\alpha + \beta)$$
$$\sin\alpha\cos\beta + \cos\alpha\sin\beta = \sin(\alpha + \beta)$$

Substituting these identities directly into the matrix entries:
$$R(\alpha)R(\beta) = \begin{pmatrix} \cos(\alpha+\beta) & -\sin(\alpha+\beta) \\ \sin(\alpha+\beta) & \cos(\alpha+\beta) \end{pmatrix}$$

By definition of the rotation matrix evaluated at angle $(\alpha + \beta)$:
$$R(\alpha+\beta) = \begin{pmatrix}\cos(\alpha+\beta) & -\sin(\alpha+\beta) \\ \sin(\alpha+\beta) & \cos(\alpha+\beta)\end{pmatrix}$$

Therefore:
$$R(\alpha)R(\beta) = R(\alpha+\beta)$$
which proves the identity.

---

### Step 3: Geometric Explanation

- **Composition of Rotations:**  
  Let $v \in \mathbb{R}^2$ be a vector. Multiplying $v$ by $R(\beta)$ yields a new vector $v_1 = R(\beta)v$, which is vector $v$ rotated counterclockwise by angle $\beta$ about the origin.
- When $v_1$ is then multiplied by $R(\alpha)$, the resulting vector $v_2 = R(\alpha)v_1 = R(\alpha)(R(\beta)v)$ rotates $v_1$ further counterclockwise by angle $\alpha$.
- Since both rotations are centered at the origin in the same orientation (counterclockwise) in the 2D plane, their cumulative geometric effect is a single rotation about the origin through total angle $\alpha + \beta$.
- **Commutativity of 2D Rotations:**  
  Because scalar addition is commutative ($\alpha + \beta = \beta + \alpha$):
  $$R(\alpha)R(\beta) = R(\alpha+\beta) = R(\beta+\alpha) = R(\beta)R(\alpha).$$
  Although general matrix multiplication is noncommutative, 2D planar rotation matrices always commute with each other. Rotating by $\beta$ then $\alpha$ produces the exact same orientation as rotating by $\alpha$ then $\beta$.

---

## 4. Verification and Consistency Checks

1. **Orthogonality Check:**  
   Every rotation matrix in $\mathbb{R}^2$ must be orthogonal ($R^T R = I$) with determinant $+1$:
   $$\det(R(\theta)) = \cos^2\theta - (-\sin^2\theta) = \cos^2\theta + \sin^2\theta = 1$$
   $$\det(R(\alpha)R(\beta)) = \det(R(\alpha))\det(R(\beta)) = 1 \cdot 1 = 1 = \det(R(\alpha+\beta)) \quad \checkmark$$

2. **Inverse / Reversal Test:**  
   Let $\beta = -\alpha$. Then:
   $$R(\alpha)R(-\alpha) = R(\alpha - \alpha) = R(0) = \begin{pmatrix}\cos 0 & -\sin 0 \\ \sin 0 & \cos 0\end{pmatrix} = \begin{pmatrix}1&0\\0&1\end{pmatrix} = I \quad \checkmark$$
   This proves that $R(-\alpha) = R(\alpha)^{-1} = R(\alpha)^T$, confirming the group property of rotations.

3. **Concrete Numerical Value Check ($\alpha = 30^\circ$, $\beta = 60^\circ$):**  
   - $\alpha = \pi/6$: $R(\pi/6) = \begin{pmatrix}\sqrt{3}/2 & -1/2 \\ 1/2 & \sqrt{3}/2\end{pmatrix}$
   - $\beta = \pi/3$: $R(\pi/3) = \begin{pmatrix}1/2 & -\sqrt{3}/2 \\ \sqrt{3}/2 & 1/2\end{pmatrix}$
   - Product:
     $$R(\pi/6)R(\pi/3) = \begin{pmatrix} \frac{\sqrt{3}}{4} - \frac{\sqrt{3}}{4} & -\frac{3}{4} - \frac{1}{4} \\ \frac{1}{4} + \frac{3}{4} & -\frac{\sqrt{3}}{4} + \frac{\sqrt{3}}{4} \end{pmatrix} = \begin{pmatrix}0 & -1 \\ 1 & 0\end{pmatrix} = R(\pi/2) = R\left(\frac{\pi}{6} + \frac{\pi}{3}\right) \quad \checkmark$$
   The formula is perfectly verified.

