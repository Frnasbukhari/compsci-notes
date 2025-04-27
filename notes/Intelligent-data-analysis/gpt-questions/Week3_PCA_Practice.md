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

$\Sigma = $  

|2|1|
|--|--|
|1|2|

1. Find the eigenvalues and their associated eigenvectors.  
2. Compute the proportion of total variance explained by the first principal component.

---

### Q4 Centering a point cloud  
Three points in $\mathbb R^{2}$ are $p_1=(2,4)$, $p_2=(5,1)$, $p_3=(3,3)$.  

1. Form the data matrix $X$ (points as columns).  

$X = $  



2. Compute the mean vector $\mu$.  

$\mu = $  



3. Construct the centered matrix $X' = X-\mu \mathbf 1^{T}$.

$X' = $  



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

$A = $  

|4|0|
|--|--|
|0|9|

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

$\Sigma = $  

|25|-15|
|--|--|
|-15|25|

1. **Diagonalise** $\Sigma$ via eigendecomposition.  
2. **Interpret** the eigenvectors in plain English: what portfolio directions do they represent?  
3. A regulatory cap says you may ignore any component explaining <5 % variance. Under this rule, how many dimensions survive? Show numbers.  

---

## **Solutions**

<details>
<summary>Click to reveal</summary>

### Q1 Solution  
1. $\bar X = \dfrac{4+2+5+3+4}{5}=3.6$,  $\bar Y = \dfrac{7+3+6+4+5}{5}=5.0$.  
2. $s_{XY}=\dfrac{1}{4}\sum(x_i-\bar X)(y_i-\bar Y)=1.65$.

---

### Q2 Solution  
a F b T c F d T  

---

### Q3 Solution  
Characteristic polynomial: $|\Sigma-\lambda I|=(2-\lambda)^2-1$.  
Eigenvalues: $\lambda_1=3$, $\lambda_2=1$.  

Eigenvectors: $v_1=\tfrac{1}{\sqrt2}[1,1]^T$, $v_2=\tfrac{1}{\sqrt2}[1,-1]^T$.  

Total variance $=4$ so PC1 explains $75\%$.

---

### Q4 Solution  

$X$ 

|2|5|3|
|--|--|--|
|4|1|3|


$\mu$ 

|3.33|
|--|
|2.67|



$X'$ 

|-1.33|1.67|-0.33|
|--|--|--|
|1.33|-1.67|0.33|

---

### Q5 Solution  
**D.** Real symmetric covariance matrices are positive‑semi‑definite and have orthogonal eigenvectors. Trace equals the **sum**, not product, of eigenvalues.

---

### Q6 Solution  
$Av\neq\lambda v$ for any scalar $\lambda$, so **no**, $v$ is not an eigenvector.

---

### Q7 Solution  

1. $\mu=[2.5,1.0,1.0]$.  

2. Covariance matrix  

|1.1|-0.2|0.4|
|--|--|--|
|-0.2|0.8|0.0|
|0.4|0.0|0.8|

3. Eigenvalues $\lambda=[1.422,0.800,0.478]$ and eigenvectors  

|-0.79|0.18|-0.59|
|--|--|--|
|0.18|0.98|0.07|
|0.59|0.07|-0.81|

> These can look different than yours. Look at my answer sheet to verify.
4. Cumulative variance after PC2: $82\%$.  

5. Scores:

| Week | PC1 | PC2 |
|-----:|----:|----:|
|1| -0.91|  0.20|
|2| -0.38| -0.65|
|3|  0.83| -0.06|
|4| -1.21|  0.04|
|5|  0.64|  0.63|
|6|  1.04| -0.16|

> These too can look different. Check my answer.

6. **Yes** — 82 % variance retention meets common thresholds.

---

### Q8 Solution  
1. Eigenvalues: 40 and 10.  

2. Eigenvectors: $[1,-1]^T/\sqrt2$ (long/short) and $[1,1]^T/\sqrt2$ (balanced).  

3. Variance shares: 80 % and 20 %. Both >5 %, so **2 dimensions survive**.

</details>
