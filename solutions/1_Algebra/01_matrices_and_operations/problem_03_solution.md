# Solution to Problem 03: When Can Matrices Be Multiplied?

## 1. Problem Statement

Given matrices with the following sizes:
$$A_{2\times3},\qquad B_{3\times4},\qquad C_{4\times2},\qquad D_{2\times2}$$

For each of the candidate products:
$$AB,\quad BA,\quad BC,\quad CB,\quad AC,\quad CA,\quad AD,\quad DA$$

determine whether the product is defined. If defined, state the size of the resulting matrix. Justify each decision using the dimension compatibility condition.

---

## 2. Theoretical Background and Concepts

- **Matrix Multiplication Compatibility Condition:**  
  The matrix product $M \cdot N$ is defined if and only if the **number of columns in the first matrix ($M$)** equals the **number of rows in the second matrix ($N$)**.
  $$\text{If } M \text{ is } m \times k \text{ and } N \text{ is } k \times n, \text{ then } MN \text{ is defined and has size } m \times n.$$
- **Inner and Outer Dimensions:**
  - The "inner dimensions" must match: $(m \times \mathbf{k}) \cdot (\mathbf{k} \times n)$.
  - The "outer dimensions" determine the size of the resulting product: $\mathbf{m} \times \mathbf{n}$.
- If the inner dimensions do not match, the inner product (dot product) between rows of the first matrix and columns of the second matrix cannot be formed because the vectors have different lengths.

---

## 3. Detailed Step-by-Step Solution

### Analysis of Each Product:

1. **Product $AB$:**
   - Sizes: $A$ is $2 \times \mathbf{3}$, $B$ is $\mathbf{3} \times 4$.
   - Inner dimensions: $3 = 3$ (they match).
   - **Conclusion:** **Defined**.
   - Result size: **$2 \times 4$**.

2. **Product $BA$:**
   - Sizes: $B$ is $3 \times \mathbf{4}$, $A$ is $\mathbf{2} \times 3$.
   - Inner dimensions: $4 \ne 2$ (they do not match).
   - **Conclusion:** **Undefined**. Rows of $B$ have 4 elements, but columns of $A$ have only 2 elements.

3. **Product $BC$:**
   - Sizes: $B$ is $3 \times \mathbf{4}$, $C$ is $\mathbf{4} \times 2$.
   - Inner dimensions: $4 = 4$ (they match).
   - **Conclusion:** **Defined**.
   - Result size: **$3 \times 2$**.

4. **Product $CB$:**
   - Sizes: $C$ is $4 \times \mathbf{2}$, $B$ is $\mathbf{3} \times 4$.
   - Inner dimensions: $2 \ne 3$ (they do not match).
   - **Conclusion:** **Undefined**.

5. **Product $AC$:**
   - Sizes: $A$ is $2 \times \mathbf{3}$, $C$ is $\mathbf{4} \times 2$.
   - Inner dimensions: $3 \ne 4$ (they do not match).
   - **Conclusion:** **Undefined**.

6. **Product $CA$:**
   - Sizes: $C$ is $4 \times \mathbf{2}$, $A$ is $\mathbf{2} \times 3$.
   - Inner dimensions: $2 = 2$ (they match).
   - **Conclusion:** **Defined**.
   - Result size: **$4 \times 3$**.

7. **Product $AD$:**
   - Sizes: $A$ is $2 \times \mathbf{3}$, $D$ is $\mathbf{2} \times 2$.
   - Inner dimensions: $3 \ne 2$ (they do not match).
   - **Conclusion:** **Undefined**.

8. **Product $DA$:**
   - Sizes: $D$ is $2 \times \mathbf{2}$, $A$ is $\mathbf{2} \times 3$.
   - Inner dimensions: $2 = 2$ (they match).
   - **Conclusion:** **Defined**.
   - Result size: **$2 \times 3$**.

---

## 4. Verification and Consistency Checks

### Summary Table

| Product | Form: $(m \times k) \times (p \times n)$ | Inner Match ($k = p$)? | Status | Result Size |
| :---: | :---: | :---: | :---: | :---: |
| $AB$ | $(2 \times 3) \times (3 \times 4)$ | $3 = 3$ | **Defined** | $2 \times 4$ |
| $BA$ | $(3 \times 4) \times (2 \times 3)$ | $4 \ne 2$ | **Undefined** | — |
| $BC$ | $(3 \times 4) \times (4 \times 2)$ | $4 = 4$ | **Defined** | $3 \times 2$ |
| $CB$ | $(4 \times 2) \times (3 \times 4)$ | $2 \ne 3$ | **Undefined** | — |
| $AC$ | $(2 \times 3) \times (4 \times 2)$ | $3 \ne 4$ | **Undefined** | — |
| $CA$ | $(4 \times 2) \times (2 \times 3)$ | $2 = 2$ | **Defined** | $4 \times 3$ |
| $AD$ | $(2 \times 3) \times (2 \times 2)$ | $3 \ne 2$ | **Undefined** | — |
| $DA$ | $(2 \times 2) \times (2 \times 3)$ | $2 = 2$ | **Defined** | $2 \times 3$ |

### Linear Transformation Interpretation Check
- $A: \mathbb{R}^3 \to \mathbb{R}^2$
- $B: \mathbb{R}^4 \to \mathbb{R}^3$
- $C: \mathbb{R}^2 \to \mathbb{R}^4$
- $D: \mathbb{R}^2 \to \mathbb{R}^2$

Checking compositions:
- $A \circ B: \mathbb{R}^4 \xrightarrow{B} \mathbb{R}^3 \xrightarrow{A} \mathbb{R}^2$ is valid ($\mathbb{R}^4 \to \mathbb{R}^2$, matrix size $2 \times 4$).
- $B \circ C: \mathbb{R}^2 \xrightarrow{C} \mathbb{R}^4 \xrightarrow{B} \mathbb{R}^3$ is valid ($\mathbb{R}^2 \to \mathbb{R}^3$, matrix size $3 \times 2$).
- $C \circ A: \mathbb{R}^3 \xrightarrow{A} \mathbb{R}^2 \xrightarrow{C} \mathbb{R}^4$ is valid ($\mathbb{R}^3 \to \mathbb{R}^4$, matrix size $4 \times 3$).
- $D \circ A: \mathbb{R}^3 \xrightarrow{A} \mathbb{R}^2 \xrightarrow{D} \mathbb{R}^2$ is valid ($\mathbb{R}^3 \to \mathbb{R}^2$, matrix size $2 \times 3$).

Every defined product matches the domain and codomain chaining of the corresponding linear transformations.

