# Solution to Problem 15: Combining Determinant Properties

## 1. Problem Statement

Let $A$ and $B$ be invertible $2 \times 2$ matrices with determinants:
$$\det A = -2, \qquad \det B = 3$$

Without determining or assuming specific numerical entries for $A$ and $B$:
1. Compute the determinant:
   $$\det\left(B^{-1}A^TB\right)$$
2. State all the determinant properties used in your derivation, in the exact order they are applied.
3. Explain why the factors involving matrix $B$ eventually cancel.

---

## 2. Theoretical Background and Concepts

Let $M, N \in \mathbb{R}^{n \times n}$ be square matrices. The following fundamental algebraic properties govern determinants:

1. **Multiplicative Property (Product Rule):**  
   The determinant of a product of square matrices equals the product of their individual determinants:
   $$\det(MN) = \det(M) \cdot \det(N).$$
   By associativity of scalar multiplication, this extends to any finite product of matrices:
   $$\det(M_1 M_2 \cdots M_k) = \det(M_1) \cdot \det(M_2) \cdots \det(M_k).$$
2. **Determinant of an Inverse Matrix:**  
   If $M$ is invertible ($\det M \ne 0$), then $M M^{-1} = I$. Since $\det I = 1$:
   $$\det(M) \cdot \det(M^{-1}) = 1 \implies \det(M^{-1}) = \frac{1}{\det M} = (\det M)^{-1}.$$
3. **Determinant of a Transpose Matrix:**  
   Transposing a matrix does not alter its determinant:
   $$\det(M^T) = \det(M).$$
4. **Similarity Invariance:**  
   Two matrices $X$ and $Y$ are similar if $X = P^{-1} Y P$ for an invertible matrix $P$. Similar matrices represent the same linear operator under different coordinate bases and share the exact same determinant, trace, and characteristic polynomial.

---

## 3. Detailed Step-by-Step Solution

### Step 1: Apply Determinant Properties in Order

We compute $\det(B^{-1} A^T B)$ step by step:

- **Property 1: Multiplicative Property of Determinants**  
  We separate the determinant of the three-matrix product into the product of three scalar determinants:
  $$\det\left(B^{-1}A^TB\right) = \det(B^{-1}) \cdot \det(A^T) \cdot \det(B)$$

- **Property 2: Determinant of an Inverse Matrix**  
  Since $B$ is invertible with $\det B = 3 \ne 0$, we express $\det(B^{-1})$ in terms of $\det B$:
  $$\det(B^{-1}) = \frac{1}{\det B} = \frac{1}{3}$$

- **Property 3: Transposition Invariance**  
  The determinant of the transpose matrix $A^T$ is identical to $\det A$:
  $$\det(A^T) = \det A = -2$$

---

### Step 2: Perform the Scalar Calculation

Substitute the scalar values into the factored product:
$$\det\left(B^{-1}A^TB\right) = \left(\frac{1}{\det B}\right) \cdot (\det A) \cdot (\det B)$$
$$= \left(\frac{1}{3}\right) \cdot (-2) \cdot (3)$$

Using the commutativity of scalar multiplication in $\mathbb{R}$:
$$= (-2) \cdot \left(\frac{1}{3} \cdot 3\right) = (-2) \cdot 1 = -2$$

Therefore:
$$\det\left(B^{-1}A^TB\right) = -2$$

---

### Step 3: Explanation of Why the Factors Involving $B$ Cancel

The cancellation of matrix $B$ can be understood from two complementary viewpoints:

1. **Algebraic Viewpoint (Commutativity of Scalars):**  
   Matrix multiplication is generally noncommutative ($B^{-1} A^T B \ne A^T$), meaning matrices $B^{-1}$ and $B$ cannot simply be commuted past $A^T$ in matrix form.  
   However, the determinant function maps matrices to the field of real numbers:
   $$\det: \mathbb{R}^{2 \times 2} \to \mathbb{R}.$$
   In $\mathbb{R}$, multiplication is commutative. Once the determinant operator distributes across the product, $\det(B^{-1})$ and $\det(B)$ become ordinary real numbers:
   $$\det(B^{-1}) \cdot \det(A^T) \cdot \det(B) = \det(A^T) \cdot [\det(B^{-1}) \cdot \det(B)] = \det(A) \cdot \left[\frac{1}{\det B} \cdot \det B\right] = \det(A) \cdot 1.$$
   The scalar $\frac{1}{3}$ and $3$ are multiplicative inverses in $\mathbb{R}$, so they cancel completely.

2. **Geometric Viewpoint (Coordinate Transformation / Similarity):**  
   The expression $B^{-1} A^T B$ describes a **change of basis** applied to the linear transformation $A^T$:
   - The matrix $B$ changes coordinates from a new basis to the standard basis.
   - The matrix $A^T$ executes the transformation in the standard basis.
   - The matrix $B^{-1}$ transforms the result back to the new basis.
   Geometrically, the determinant measures the factor by which oriented volumes (or areas in 2D) are scaled. Transformation $B$ scales areas by a factor of $3$. Transformation $B^{-1}$ scales areas by $\frac{1}{3}$. The initial distortion and final restoration of the coordinate grid cancel out entirely, leaving only the intrinsic volume scaling factor of $A^T$, which is $\det A = -2$.

---

## 4. Verification and Consistency Checks

### Concrete Numerical Test
To confirm that this holds for arbitrary concrete matrices, choose simple matrices satisfying the determinant conditions:
- Let $A = \begin{pmatrix}-2&0\\0&1\end{pmatrix} \implies \det A = (-2)(1) - 0 = -2$.
  $$A^T = \begin{pmatrix}-2&0\\0&1\end{pmatrix}$$
- Let $B = \begin{pmatrix}1&1\\1&4\end{pmatrix} \implies \det B = 1(4) - 1(1) = 3$.
  $$B^{-1} = \frac{1}{3}\begin{pmatrix}4&-1\\-1&1\end{pmatrix}$$

Now compute the conjugate product $M = B^{-1} A^T B$:
1. Compute $A^T B$:
   $$A^T B = \begin{pmatrix}-2&0\\0&1\end{pmatrix}\begin{pmatrix}1&1\\1&4\end{pmatrix} = \begin{pmatrix}-2&-2\\1&4\end{pmatrix}$$
2. Compute $B^{-1} (A^T B)$:
   $$M = \frac{1}{3}\begin{pmatrix}4&-1\\-1&1\end{pmatrix}\begin{pmatrix}-2&-2\\1&4\end{pmatrix} = \frac{1}{3}\begin{pmatrix}4(-2)+(-1)(1) & 4(-2)+(-1)(4) \\ -1(-2)+1(1) & -1(-2)+1(4)\end{pmatrix}$$
   $$M = \frac{1}{3}\begin{pmatrix}-8-1 & -8-4 \\ 2+1 & 2+4\end{pmatrix} = \frac{1}{3}\begin{pmatrix}-9&-12\\3&6\end{pmatrix} = \begin{pmatrix}-3&-4\\1&2\end{pmatrix}$$

3. Compute $\det M$ directly:
   $$\det M = (-3)(2) - (-4)(1) = -6 - (-4) = -6 + 4 = -2$$

The direct calculation of $\det M$ yields $-2$, exactly matching the property-derived result $\det(B^{-1} A^T B) = -2 \quad \checkmark$.
