# Solution to Problem 09: Area and the Determinant

## 1. Problem Statement

Given the vectors in $\mathbb{R}^2$:
$$u=\begin{pmatrix}3\\1\end{pmatrix},\qquad v=\begin{pmatrix}1\\4\end{pmatrix}$$

1. Compute the area of the parallelogram spanned by vectors $u$ and $v$ using a determinant.
2. Form the matrix with the vectors in reversed order ($v$ first, then $u$) and compute its determinant.
3. Explain what changes in the determinant and what does not change in the area.

---

## 2. Theoretical Background and Concepts

- **Signed Area and Determinant in $\mathbb{R}^2$:**  
  For two vectors $u = \begin{pmatrix}u_1\\u_2\end{pmatrix}$ and $v = \begin{pmatrix}v_1\\v_2\end{pmatrix}$, the determinant of the matrix formed by placing them as columns:
  $$\det\begin{pmatrix}u & v\end{pmatrix} = \begin{vmatrix}u_1&v_1\\u_2&v_2\end{vmatrix} = u_1 v_2 - u_2 v_1$$
  computes the **oriented (signed) area** of the parallelogram spanned by $u$ and $v$.
- **Orientation:**
  - $\det(u, v) > 0$ indicates that the shortest angle from $u$ to $v$ is oriented **counterclockwise** (a right-handed coordinate basis).
  - $\det(u, v) < 0$ indicates that the rotation from $u$ to $v$ is oriented **clockwise** (a left-handed coordinate basis).
  - $\det(u, v) = 0$ indicates that $u$ and $v$ are collinear (linearly dependent), enclosing zero area.
- **Geometric (Unsigned) Area:**  
  The physical area of a geometric figure is always a non-negative real quantity:
  $$\operatorname{Area}(P) = |\det(u, v)| = |\det(v, u)|.$$

---

## 3. Detailed Step-by-Step Solution

### Step 1: Compute the Area Using the Ordered Basis $(u, v)$

Form the matrix $M_1$ with columns $u$ and $v$:
$$M_1 = \begin{pmatrix}u & v\end{pmatrix} = \begin{pmatrix}3&1\\1&4\end{pmatrix}$$

Compute the determinant:
$$\det M_1 = (3)(4) - (1)(1) = 12 - 1 = 11$$

Since the determinant is positive, the geometric area of the parallelogram is:
$$\operatorname{Area} = |\det M_1| = |11| = 11$$

---

### Step 2: Reverse the Order of Vectors and Compute the Determinant

Form the matrix $M_2$ with columns $v$ and $u$:
$$M_2 = \begin{pmatrix}v & u\end{pmatrix} = \begin{pmatrix}1&3\\4&1\end{pmatrix}$$

Compute the determinant:
$$\det M_2 = (1)(1) - (3)(4) = 1 - 12 = -11$$

---

### Step 3: Explanation of What Changes and What Remains Invariant

1. **What changes in the determinant:**  
   The **algebraic sign** of the determinant changes from $+11$ to $-11$.  
   - Swapping two columns of a matrix corresponds to swapping two inputs in the alternating multilinear form, negating the value: $\det(v, u) = -\det(u, v)$.
   - Geometrically, this reflects a change in **orientation**: rotating from $u$ to $v$ is counterclockwise ($+11$), whereas rotating from $v$ to $u$ is clockwise ($-11$).

2. **What does not change in the area:**  
   The **geometric area** remains completely unchanged:
   $$\operatorname{Area} = |-11| = 11.$$
   The physical parallelogram in the plane is bounded by the same four vertices: $(0,0)$, $(3,1)$, $(1,4)$, and $(4,5)$. The actual surface space enclosed by these boundaries depends only on the set of points, completely independent of the arbitrary ordering in which we list the two spanning edge vectors.

---

## 4. Verification and Consistency Checks

1. **Cross Product Magnitude Check:**  
   Embed $u$ and $v$ into $\mathbb{R}^3$ as $u = (3, 1, 0)$ and $v = (1, 4, 0)$.  
   The area of the parallelogram is given by the Euclidean norm of the cross product:
   $$u \times v = \begin{vmatrix}\mathbf{i}&\mathbf{j}&\mathbf{k}\\3&1&0\\1&4&0\end{vmatrix} = \mathbf{k}(3 \cdot 4 - 1 \cdot 1) = 11 \mathbf{k}$$
   $$\operatorname{Area} = \|u \times v\| = \|11\mathbf{k}\| = 11 \quad \checkmark$$
   Similarly:
   $$v \times u = -11\mathbf{k} \implies \|v \times u\| = 11 \quad \checkmark$$

2. **Geometric Box (Shoelace) Formula:**  
   Vertices in counterclockwise order: $(0,0) \to (3,1) \to (4,5) \to (1,4) \to (0,0)$.
   $$2 \cdot \operatorname{Area} = |(0 \cdot 1 - 0 \cdot 3) + (3 \cdot 5 - 1 \cdot 4) + (4 \cdot 4 - 5 \cdot 1) + (1 \cdot 0 - 4 \cdot 0)|$$
   $$2 \cdot \operatorname{Area} = |0 + (15 - 4) + (16 - 5) + 0| = |11 + 11| = 22 \implies \operatorname{Area} = 11 \quad \checkmark$$
   The area is verified to be exactly 11.
