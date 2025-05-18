# Week 5 — Dimensional Analysis by Co‑occurrence (Latent Semantic Analysis)

This practice pack blends quick‑fire checks with longer, exam‑style items that mirror the tone and depth of past papers.  
*Instructions*: answer all questions **before** looking at the solutions section that follows.

---

## Questions

### A. Mini‑Questions (5 marks each)

1. **SVD vs. Eigendecomposition**  
   State *two* reasons why singular‑value decomposition is preferred over eigendecomposition when analysing a term–document matrix in Latent Semantic Analysis.

2. **Conjugate Transpose**  
   Let $A \in \mathbb{C}^{m\times n}$. Define the **conjugate transpose** $A^{\*}$ and quote the condition that makes a square complex matrix **unitary**.

3. **Inverse Existence**  
   Explain why a non‑zero determinant is a *necessary and sufficient* condition for a square matrix to possess an inverse.

4. **Low‑Rank Idea**  
   In one sentence each, give *two* practical motivations for keeping only the largest $k$ singular values (a low‑rank approximation) in LSA.

---

### B. Exam‑Style Problems

#### Problem 1 — Adjoint Route to the Inverse (15 marks)  

Consider  

|   | c₁ | c₂ | c₃ |
|---|---|---|---|
| **r₁** | 8 | 4 | 2 |
| **r₂** | 3 | 0 | 1 |
| **r₃** | 2 | −1 | 3 |

1. Compute the determinant of the matrix.  
2. Build the full cofactor matrix.  
3. Form the adjoint and hence the inverse. *All arithmetic steps must be shown.*

---

#### Problem 2 — Building Similarity Spaces (20 marks)

A tiny term–document frequency matrix is given:

|   | $d_1$ | $d_2$ | $d_3$ |
|---|---|---|---|
| **term₁** | 2 | 0 | 1 |
| **term₂** | 0 | 1 | 1 |
| **term₃** | 1 | 0 | 0 |

1. Compute the *document–document* similarity matrix $D = A^{\top}A$.  
2. Compute the *term–term* similarity matrix $W = A A^{\top}$.  
3. Which pair of documents are most similar according to $D$?  
4. Which pair of terms are most semantically similar according to $W$? Briefly justify.

---

#### Problem 3 — Rank‑2 LSA Approximation (20 marks)

Using the same matrix $A$ from Problem 2:

1. Explain the algebraic steps to obtain the rank‑2 approximation $A_{(2)} = U_2 \Sigma_2 V_2^{\top}$. *(Numerical computation is **not** required.)*  
2. Describe what geometric effect dropping the smallest singular value has on the **latent space**.  
3. Give one benefit and one potential drawback of this dimensionality reduction for downstream classification tasks.

---

## Solutions

### A. Mini‑Questions

1. **SVD vs. Eigendecomposition**

   * Any rectangular matrix admits an SVD, whereas eigendecomposition requires a square (and diagonalisable) matrix.  
   * The left and right singular vectors form orthonormal bases, so the new dimensions are guaranteed to be mutually orthogonal — eigenvectors need not be.

2. **Conjugate Transpose**

   The conjugate transpose of $A$ is $A^{\*} = (\overline{A})^{\top}$ — first transpose, then take complex conjugate of every entry.  
   A square matrix $U$ is **unitary** iff $U^{\*}U = UU^{\*} = I$.

3. **Inverse Existence**

   From the adjoint identity $A\;\text{adj}(A) = \det(A) I$, division by $\det(A)$ is only legal when the determinant is non‑zero; conversely, Cramer’s rule shows that if $\det(A) \ne 0$ an explicit inverse can always be constructed.  

4. **Low‑Rank Motivations**

   * Reduces storage and compute cost for huge sparse matrices.  
   * Groups near‑synonymous terms, mitigating sparsity and polysemy.


---

### B. Exam‑Style Problems

#### Problem 1 Solution

1. **Determinant**

   $\det(A) = 8(0\cdot3 - 1\cdot(−1)) - 4(3\cdot3 - 1\cdot2) + 2(3\cdot(−1) - 0\cdot2) = 8 - 42 + 8 = −26$.

2. **Cofactor Matrix**

   |   | c₁ | c₂ | c₃ |
   |---|---|---|---|
   | **r₁** | 1 | −7 | −3 |
   | **r₂** | −14 | 20 | 16 |
   | **r₃** | 4 | −2 | −12 |

3. **Adjoint & Inverse**

   *Adjoint* = transpose of the above.  
   Divide every entry by $−26$ to obtain $A^{-1}$.

#### Problem 2 Solution

1. **Document–document similarity $D$**

   |   | $d_1$ | $d_2$ | $d_3$ |
   |---|---|---|---|
   | **$d_1$** | 5 | 0 | 2 |
   | **$d_2$** | 0 | 1 | 1 |
   | **$d_3$** | 2 | 1 | 2 |

2. **Term–term similarity $W$**

   |   | term₁ | term₂ | term₃ |
   |---|---|---|---|
   | **term₁** | 5 | 1 | 2 |
   | **term₂** | 1 | 2 | 0 |
   | **term₃** | 2 | 0 | 1 |

3. **Most similar documents**: $d_1$ and $d_3$ share similarity score $2$, the largest off‑diagonal entry in $D$.  

4. **Most similar terms**: term₁ and term₃ share similarity $2$ — the largest off‑diagonal entry in $W$.

#### Problem 3 Solution (sketch)

1. Keep the two largest singular values $\sigma_1, \sigma_2$ and their corresponding singular vectors. Zero‑out $\sigma_3$ to build $\Sigma_2$, then form $A_{(2)} = U_2 \Sigma_2 V_2^{\top}$.  
2. Geometrically, the data cloud is projected onto a 2‑D plane inside the original 3‑D space; variance along the discarded axis is lost.  
3. *Benefit*: noise suppression and faster classifiers. *Drawback*: risk of discarding discriminative information tied to the smallest singular value.
