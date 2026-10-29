# Solution to Problem 08: Determinant of a Product

## 1. Problem Statement

Let $A$ and $B$ be square matrices of the same dimension such that:
$$\det A = 3, \qquad \det B = -5$$

1. Compute $\det(AB)$.
2. Compute $\det(BA)$.
3. Determine whether $\det(A^{-1}B)$ exists, and if so, compute its value.
4. Explain why $\det(AB) = \det(BA)$ holds even though, in general, matrix multiplication is noncommutative ($AB \ne BA$).

---

## 2. Theoretical Background and Concepts

- **Multiplicative Property of Determinants:**  
  For any two square matrices $A, B \in \mathbb{R}^{n \times n}$:
  $$\det(AB) = \det(A) \cdot \det(B).$$
- **Determinant of an Inverse Matrix:**  
  If $A$ is invertible ($\det A \ne 0$), then $A A^{-1} = I$. Taking determinants of both sides:
  $$\det(A A^{-1}) = \det(A) \cdot \det(A^{-1}) = \det(I) = 1 \implies \det(A^{-1}) = \frac{1}{\det A}.$$
- **Commutativity of the Field $\mathbb{R}$:**  
  The determinant is a scalar-valued function $\det: \mathbb{R}^{n \times n} \to \mathbb{R}$. While the matrix ring $(\mathbb{R}^{n \times n}, +, \cdot)$ is non-abelian (noncommutative under multiplication), the field of real numbers $(\mathbb{R}, +, \cdot)$ is commutative.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute $\det(AB)$

Using the product formula:
$$\det(AB) = \det(A) \cdot \det(B) = (3) \cdot (-5) = -15$$

---

### Step 2: Compute $\det(BA)$

Using the product formula:
$$\det(BA) = \det(B) \cdot \det(A) = (-5) \cdot (3) = -15$$

---

### Step 3: Compute $\det(A^{-1}B)$

First, we verify whether $A^{-1}$ exists:
- A matrix is invertible if and only if its determinant is non-zero.
- Since $\det A = 3 \ne 0$, matrix $A$ is invertible, so $A^{-1}$ exists.
- The determinant of $A^{-1}$ is:
  $$\det(A^{-1}) = \frac{1}{\det A} = \frac{1}{3}$$

Now, compute the determinant of the product $A^{-1}B$:
$$\det(A^{-1}B) = \det(A^{-1}) \cdot \det(B) = \left(\frac{1}{3}\right) \cdot (-5) = -\frac{5}{3}$$

---

### Step 4: Explanation of Why $\det(AB) = \det(BA)$

In general linear algebra, the transformation $AB$ (first applying $B$, then $A$) is geometrically and algebraically distinct from $BA$ (first applying $A$, then $B$):
$$AB \ne BA \quad \text{in general}.$$
However, their determinants must be equal because:
1. Matrix multiplication maps to the multiplication of real numbers:
   $$\det(AB) = \det(A)\det(B), \qquad \det(BA) = \det(B)\det(A).$$
2. Scalar multiplication of real numbers is commutative:
   $$\det(A)\det(B) = \det(B)\det(A) \quad \text{for all } \det(A), \det(B) \in \mathbb{R}.$$
3. **Geometric Meaning:** The determinant measures the net volume scaling factor of a transformation. If transformation $B$ scales volume by $-5$ (scaling by 5 and reversing spatial orientation) and transformation $A$ scales volume by $3$, then composing both transformations—regardless of sequence—scales volume by a cumulative factor of $3 \times (-5) = -15$. The geometric orientation and volume distortion of the composition are identical.

---

## 4. Verification and Consistency Checks

1. **Similarity Transformation Consistency Check:**  
   If $A$ is invertible, $BA$ is similar to $AB$:
   $$BA = A^{-1} (AB) A.$$
   Taking the determinant of both sides:
   $$\det(BA) = \det(A^{-1} (AB) A) = \det(A^{-1}) \cdot \det(AB) \cdot \det(A) = \frac{1}{\det A} \cdot \det(AB) \cdot \det A = \det(AB) \quad \checkmark$$
   This proves equality purely from similarity without assuming prior knowledge of $\det(BA)$.

2. **Explicit Numerical Test:**  
   Let $A = \begin{pmatrix}3&0\\0&1\end{pmatrix}$ ($\det A = 3$) and $B = \begin{pmatrix}1&0\\0&-5\end{pmatrix}$ ($\det B = -5$).
   - $AB = \begin{pmatrix}3&0\\0&-5\end{pmatrix} \implies \det(AB) = 3(-5) - 0 = -15 \quad \checkmark$
   - $BA = \begin{pmatrix}3&0\\0&-5\end{pmatrix} \implies \det(BA) = -15 \quad \checkmark$
   - $A^{-1} = \begin{pmatrix}1/3&0\\0&1\end{pmatrix} \implies A^{-1}B = \begin{pmatrix}1/3&0\\0&-5\end{pmatrix} \implies \det(A^{-1}B) = \frac{1}{3}(-5) = -\frac{5}{3} \quad \checkmark$
