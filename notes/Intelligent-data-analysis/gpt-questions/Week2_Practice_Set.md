# Week 2 Practice Set – Basis, Coordinate Systems & Classic Decompositions

This set aligns with the Week 2 slides/notes on basis changes, GLM, Fourier, wavelets, PCA and manifold embedding.

---

## Practice questions  
*(Mini ≈ 10 min each  •  Extended ≈ 25‑30 min each)*

### Mini questions  

1. **Basis verification**  
   Consider $E = \{(1,0,1),(0,1,1),(1,1,0)\}$ in $\mathbb R^{3}$.  
   1. Show that $E$ is a basis.  
   2. Determine its dimension.

2. **Coordinate conversion (simple)**  
   Vector $v=(4,1)$ is expressed in the canonical basis of $\mathbb R^{2}$.  
   Express $v$ in the slanted basis $B=\{(1,1),(1,-1)\}$.

3. **Impulse decomposition**  
   Let $x[n]=[3,0,2]$ for $n=0,1,2$ (zero elsewhere).  
   Write $x[n]$ using the impulse representation $x[n]=\sum_k x[k]\,\delta[n-k]$.

4. **Fourier coefficient identification**  
   A discrete signal of length $N=4$ has DFT coefficients $X=[0,2,0,2]$.  
   What is the time‑domain signal $x[n]$?

5. **GLM terminology quick‑fire**  
   Match each term with its GLM role: {design matrix, coefficient vector, residuals}.  
   a) $\beta$ b) $X$ c) $\varepsilon$.

6. **PCA eigen‑intuition**  
   A 2‑D dataset has covariance matrix $\begin{pmatrix}9&0\\0&1\end{pmatrix}$.  
   Which axis carries more variance, and by what factor?

7. **Tool‑to‑task mapping**  
   Pick the best decomposition for each task:  
   - a) Noise‑robust image compression.  
   - b) Removing 50 Hz mains interference from EEG.  
   - c) Discovering nonlinear 2‑D embedding of 100‑D word vectors.

---

### Extended questions  

8. **Coordinate change (exam style)**  
   Bases in $\mathbb R^{2}$:  
   $$A=\bigl\{\begin{pmatrix}2\\1\end{pmatrix},\begin{pmatrix}0\\1\end{pmatrix}\bigr\},\qquad
     B=\bigl\{\begin{pmatrix}0\\-2\end{pmatrix},\begin{pmatrix}3\\-1\end{pmatrix}\bigr\}.$$  
   A point $p$ has coordinates $(1,-2)_A$.  
   1. Find $p$ in canonical coordinates.  
   2. Compute its coordinates in basis $B$.

9. **GLM regression & geometric view**  
   Dataset: $(0,1.4),(1,2.1),(3,3.3),(4,3.9)$.  
   1. Fit $y=\beta_1 x+\beta_0$ using least squares.  
   2. Give the coordinate representation $(\beta_0,\beta_1)$ of this line in the “space of lines”.  
   3. Suppose we low‑pass filter by setting $\beta_1=0$. Interpret the resulting model.

10. **Fourier low‑pass filtering**  
    Signal $x[n]=\{2,0,1,1\}$ for $n=0\dots3$.  
    1. Compute the 4‑point DFT $X[k]$.  
    2. Zero the high‑frequency bins ($k=2,3$) and inverse‑DFT to obtain $\hat x[n]$.  
    3. Comment on the smoothing effect.

11. **PCA dimensionality reduction**  
    Covariance matrix  
    $$C=\begin{pmatrix}4&3\\3&9\end{pmatrix}.$$  
    1. Find eigenvalues and eigenvectors.  
    2. Project sample $s=(4,6)$ onto the first principal component.  
    3. Reconstruct $s$ from the 1‑D projection and compute reconstruction error.

12. **Conceptual: manifold embedding vs. PCA**  
    In ≤150 words compare Isomap with PCA on the task of unfolding a “Swiss‑roll” dataset.  
    Mention coordinate‑basis perspective and the trade‑off in computational cost.

---

## Solutions  

### Mini  

1. *Answer*  
   The three vectors are linearly independent (determinant of the matrix with rows as vectors is $1$). $\dim\mathbb R^{3}=3\Rightarrow E$ is a basis.  

2. *Answer*  
   Solve $v=\alpha(1,1)+\beta(1,-1)$. Gives $\alpha=2.5,\;\beta=1.5$.  

3. *Answer*  
   $x[n]=3\,\delta[n]+0\,\delta[n-1]+2\,\delta[n-2]$.  

4. *Answer*  
   Inverse DFT: $x=[1,0,1,0]$.  

5. a) coefficient vector b) design matrix c) residuals.  

6. Variance ratio $9:1$ → first axis carries 9× more variance.  

7. a) Wavelet b) Fourier (notch) c) Manifold embedding (Isomap/LLE).

---

### Extended  

8.  
   1. $p=\begin{pmatrix}2\\-1\end{pmatrix}$.  
   2. $B^{-1}\!Ap_A$ yields coordinates $\approx(0.16,0.66)_B$.  

9.  
   1. $\beta_1=0.55,\;\beta_0=1.46$.  
   2. Point $(1.46,0.55)$ in coefficient space.  
   3. Setting $\beta_1=0$ gives horizontal line $y=1.46$ — a low‑pass model ignoring trend.  

10.  
    1. $X=[4,1-\!j,2,1+\!j]$.  
    2. Zeroing $k=2,3$ → $\hat X=[4,1-\!j,0,0]$ → $\hat x=[1.5,0.5,1.5,0.5]$.  
    3. High‑frequency wiggles removed; signal smoothed toward mean.  

11.  
    1. $\lambda_{1,2}=\{10,3\}$, $v_1\propto(1,3),v_2\propto(-3,1)$.  
    2. Projection scalar $z=s\cdot v_1/\|v_1\|\approx6.32$.  
    3. Reconstructed $\tilde s=z v_1/\|v_1\|\approx(1.9,5.7)$, error $\|s-\tilde s\|\approx2.2$.  

12. *Model answer*  
    PCA finds a **global linear** basis that maximises variance; it cannot unwrap the Swiss‑roll because the first PCs still lie on the curved manifold. Isomap constructs a graph of neighbourhood geodesics, preserves shortest‑path distances, and embeds the data into a lower‑dimensional Euclidean space where the roll is flattened. In coordinate‑basis terms, Isomap builds **many local bases** and stitches them into a nonlinear global chart, whereas PCA forces one linear basis. The cost is an $\mathcal O(n^3)$ eigen‑decomposition of the graph distance matrix plus $k$‑NN search, far heavier than PCA’s covariance eigen‑solve but essential when linear assumptions break down.

---

*Mini problems are suited for quick checks; extended problems deepen conceptual & computational fluency. Enjoy exploring coordinate magic!*