# Week&nbsp;3 Practice Set  
**Dimensional Analysis by Covariance — Eigendecomposition & PCA**

---

## How to use this deck
* **Mini‑sprints** (Q1–Q6) hone recall & quick‑calc reflexes.  
* **Board‑room scenarios** (Q7–Q8) mimic the 20‑mark exam blocks: scaffold, compute, interpret.  
* **Full solutions** sit at the back — keep them quarantined until you’ve pulled your own numbers.

Math is rendered with **$...$** delimiters.

---

## Mini‑sprint Questions

### Q1 Covariance on a napkin  
A bivariate sample has five observations:

| $i$ | $X$ | $Y$ |
|----:|----:|----:|
| 1 | 4 | 7 |
| 2 | 2 | 3 |
| 3 | 5 | 6 |
| 4 | 3 | 4 |
| 5 | 4 | 5 |

1. Compute the sample means $\bar X$ and $\bar Y$.  
2. Compute the sample covariance $s_{XY}$.

---

### Q2 Concept check — scatterplot truths  
Mark each statement **True** or **False**.

a. A trend‑line drawn through a scatterplot guarantees a causal relationship.  
b. Removing a single high‑leverage point can flip the sign of the covariance.  
c. Covariance is scale‑invariant.  
d. The variance of a variable equals its covariance with itself.

---

### Q3 Two‑by‑two PCA warm‑up  
Given the covariance matrix  
[ 2   1 ]       
[ 1   2 ]  

1. Find the eigenvalues and their associated eigenvectors.  
2. Compute the proportion of total variance explained by the first principal component.

---

### Q4 Centering a point cloud  
Three points in $\mathbb R^{2}$ are $p_1=(2,4)$, $p_2=(5,1)$, $p_3=(3,3)$.  

1. Form the data matrix $X$ (points as columns).  
2. Compute the mean vector $\mu$.  
3. Construct the centered matrix $X' = X-\mu \mathbf 1^{T}$, where $\mathbf 1$ is a row vector of ones.

---

### Q5 Multiple‑choice — eigen lore  
Which of the following is **always** true for a real symmetric covariance matrix?  

A. All eigenvalues are positive or zero.  
B. Eigenvectors corresponding to distinct eigenvalues are orthogonal.  
C. The trace equals the product of the eigenvalues.  
D. Options A and B.

---

### Q6 Fast eigen‑test  
Let  
$A =$    
[ 4   0 ]         
[ 0   9 ]      
and $v =$      
[ 1 ]      
[ 3 ] 

Is $v$ an eigenvector of $A$? If **yes**, state the eigenvalue; if **no**, justify briefly.

---

## Board‑room Scenarios

### Q7 Full‑cycle PCA on a 3‑D portfolio  
You manage a micro‑fund tracking three risk metrics $\{R_1,R_2,R_3\}$. Six weekly observations are:

| Week | $R_1$ | $R_2$ | $R_3$ |
|-----:|------:|------:|------:|
| 1 | 2 | 0 | 1 |
| 2 | 3 | 1 | 0 |
| 3 | 2 | 2 | 2 |
| 4 | 1 | 1 | 0 |
| 5 | 3 | 2 | 1 |
| 6 | 4 | 0 | 2 |

1. **Center** the data and report the mean vector.  
2. **Compute** the $3\times3$ sample covariance matrix.  
3. **Extract** eigenvalues and eigenvectors (rounded to three decimals).  
4. **Rank** the principal components by explained variance; give the cumulative percentage after two components.  
5. **Project** the six observations onto the 2‑D PC subspace and tabulate the scores.  
6. Briefly critique whether dropping to 2 D is defensible for risk‑reporting.

---

### Q8 Eigen‑driven investment hedge  
A $2\times2$ covariance matrix for returns is

[ 25   -15 ]      
[ -15   25 ]

1. **Diagonalise** $\Sigma$ via eigendecomposition.  
2. **Interpret** the eigenvectors in plain English: what portfolio directions do they represent?  
3. A regulatory cap says you may ignore any component explaining <5 % variance. Under this rule, how many dimensions survive? Show numbers.  

---

## **Solutions**

<details>
<summary>Click to reveal</summary>

### Q1 Solution  
1. $\bar X = \dfrac{4+2+5+3+4}{5}=3.6$,  $\bar Y = \dfrac{7+3+6+4+5}{5}=5.0$.  
2. $s_{XY}=\dfrac{1}{4}\sum(x_i-\bar X)(y_i-\bar Y)=\dfrac{1}{4}\left[(0.4)(2)+( -1.6)(-2)+ (1.4)(1)+(-0.6)(-1)+(0.4)(0)\right]=1.65$.

---

### Q2 Solution  
a F b T c F d T  

Covariance changes with units; doubling $X$ doubles $s_{XY}$.

---

### Q3 Solution  
Characteristic polynomial: $|\Sigma-\lambda I|=(2-\lambda)^2-1=\lambda^2-4\lambda+3=0$.  
Eigenvalues: $\lambda_1=3$, $\lambda_2=1$.  

Eigenvectors: for $\lambda_1$: $v_1=\tfrac{1}{\sqrt2}\begin{bmatrix}1\\1\end{bmatrix}$;  
for $\lambda_2$: $v_2=\tfrac{1}{\sqrt2}\begin{bmatrix}1\\-1\end{bmatrix}$.  

Total variance $=3+1=4$ so PC1 explains $\tfrac{3}{4}=75\%$.

---

### Q4 Solution  
$X=\begin{bmatrix}2&5&3\\4&1&3\end{bmatrix}$, $\mu=\begin{bmatrix}3.33\\2.67\end{bmatrix}$.  
$X' = \begin{bmatrix}-1.33&1.67&-0.33\\1.33&-1.67&0.33\end{bmatrix}$.

---

### Q5 Solution  
**D.** Real symmetric covariance matrices are positive‑semi‑definite (A) and have orthogonal eigenvectors (B). The trace equals the **sum**, not the product, of eigenvalues.

---

### Q6 Solution  
$Av=\begin{bmatrix}4\\27\end{bmatrix}\neq\lambda v$ for any scalar $\lambda$, so **no**, $v$ is not an eigenvector.

---

### Q7 Solution  
1. $\mu=[2.5,1.0,1.0]$.  
2. $\text{Cov}=\begin{bmatrix}1.1&-0.2&0.4\\-0.2&0.8&0.0\\0.4&0.0&0.8\end{bmatrix}$.  
3. $\lambda=[1.422,0.800,0.478]$, eigenvectors in columns of  
$V=\begin{bmatrix}-0.79&0.18&-0.59\\0.18&0.98&0.07\\0.59&0.07&-0.81\end{bmatrix}$.  
4. Cumulative variance after PC2: ${(1.422+0.800)}/{2.700}=0.823\;\approx82\%$.  
5. Scores $Z = V^T X'$ (rounded):

| Week | PC1 | PC2 |
|-----:|----:|----:|
|1| -0.91|  0.20|
|2| -0.38| -0.65|
|3|  0.83| -0.06|
|4| -1.21|  0.04|
|5|  0.64|  0.63|
|6|  1.04| -0.16|

6. **Yes** — 82 % variance retention comfortably exceeds the common 70 % board metric, and PC3 adds mainly idiosyncratic noise.

---

### Q8 Solution  
1. Eigenvalues: $\lambda_1=40,\;\lambda_2=10$. Eigenvectors (unit) $v_1=\tfrac{1}{\sqrt2}[1\; -1]^T$, $v_2=\tfrac{1}{\sqrt2}[1\; 1]^T$.  
2. $v_1$ = long/short mirror portfolio (equal weights, opposite signs). $v_2$ = fully diversified 50–50 basket.  
3. Total variance $=50$. Component shares: 80 % and 20 %. Both exceed 5 %, so **2 dimensions survive**.

</details>
