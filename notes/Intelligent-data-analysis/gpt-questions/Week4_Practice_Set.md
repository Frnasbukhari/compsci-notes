# Intelligent Data Analysis – Week&nbsp;4 Practice Workbook  
**Topic:** Dimensional analysis by statistical independence (Independent Component Analysis)  

*All questions are original and tuned to the depth & tone of past exam papers.  
Marks in square brackets are guidance only.*

---

## Section I – Quick‑fire Checks  (1 mark each)

1. State the formal condition for statistical independence of two random variables $X$ and $Y$ using their joint distribution.
2. Explain in one sentence why uncorrelated variables are **not necessarily** independent.
3. Let $f(x)$ be a probability **density** function. Write the two normalisation conditions it must satisfy.
4. Write the definition of the Shannon entropy $H(X)$ of a discrete variable $X$ with outcomes $x_i$.
5. State **two** assumptions (besides independence) that ICA makes about the source signals.
6. In a blind‑source separation setting, what is meant by *whitening* (or *sphering*) the data?

---

## Section II – Short Worked Questions  (5 – 8 marks each)

### Q2  Discrete Entropy  
A fair 4‑sided die has faces {1,2,3,4}. A **loaded** die is biased so that  
$P(1)=0.05$, $P(2)=0.15$, $P(3)=0.3$, $P(4)=0.5$.  

1. Compute the Shannon entropy of the fair die (use base 2).  
2. Compute the Shannon entropy of the loaded die.  
3. Which die is “more informative’’ and **why**?

---

### Q3  Joint Distribution & Independence  
Two binary variables $A$ and $B$ have joint probabilities:

| | $B=0$ | $B=1$ |
|-------|-------|-------|
| **$A=0$** | 0.20 | 0.30 |
| **$A=1$** | 0.25 | 0.25 |

1. Compute the marginals $P(A)$ and $P(B)$.  
2. Test **independence** by comparing $P(A,B)$ with $P(A)P(B)$ for every cell. State your conclusion.

---

### Q4  PDF Skills  
Let the pdf of a continuous variable $X$ be $f(x)=k x^2$ on $x\in[0,2]$ and zero elsewhere.

1. Determine the normalising constant $k$.  
2. Compute $P(0.5<X<1.5)$.  
3. Find the cumulative distribution function $F(x)$ for $0\le x\le2$.

---

### Q5  Un‑mixing Step (single iteration)  
Observed mixtures $Y$ are obtained from **two** sources $X$ by  

|   | $x_1$ | $x_2$ |
|---|-------|-------|
| **$y_1$** | 0.6   | 0.4   |
| **$y_2$** | 0.3   | 0.7   |

1. Write $Y=X\beta$ explicitly using the values above.  
2. Assume $X$ has unit variance and zero mean, and we have an initial un‑mixing matrix  

|   | $y_1$ | $y_2$ |
|---|-------|-------|
| **$w_1$** | 1     | 0     |
| **$w_2$** | 0     | 1     |

   Apply **one** gradient‑ascent step  
   $W_{\text{new}} = W_{\text{old}} + h \nabla H$  
   with learning rate $h=0.1$ and (toy) gradient matrix **∇H**

   |        | **y₁** | **y₂** |
   |--------|-------:|-------:|
   | **w₁** | 0.20   | −0.10  |
   | **w₂** | 0.05   | 0.03   |
   
   Provide $W_{\text{new}}$ (write it as a table).

*(You may leave answers as decimals to 3 dp.)*

---

## Section III – Extended Exam‑style Problems  (20 marks each)

### Problem A  “Mini Cocktail Party’’  
You record two microphone signals in a room with **two** people speaking simultaneously.  
The sensor model is  

```text
[y₁(t)]   [0.7  0.5] [s₁(t)]
[y₂(t)] = [0.3  0.8] [s₂(t)]
```

where $s_1$ and $s_2$ are statistically independent speech sources.

1. *(a)* Explain **why** PCA alone cannot fully separate the sources.  
2. *(b)* Describe the pre‑processing steps you would perform **before** running an ICA algorithm such as FastICA.  
3. *(c)* Assuming perfectly estimated un‑mixing matrix $W$, write expressions for the recovered sources $\hat s_1,\hat s_2$.  
4. *(d)* Give **two** practical difficulties that arise when the true number of sources exceeds the number of sensors.  
5. *(e)* If $s_1$ is Gaussian and $s_2$ is strongly super‑Gaussian, comment on how this affects ICA’s ability to separate them.

---

### Problem B  Entropy Maximisation Proof Sketch  
Show that, under a **volume‑preserving** (det W=1) linear transform of whitened data,  
maximising the **negentropy**

$$J(X)=H(X_{\text{gauss}})-H(X)$$  

is equivalent to minimising the differential entropy $H(X)$.  
Outline each logical step and state any theorems you invoke.

---

## **Solutions**

*(Do **not** scroll further if you want to attempt the questions first!)*

<details>
<summary>Click to reveal solutions</summary>

### Section I Solutions

1. $X$ and $Y$ are independent if and only if $P(X=x,Y=y)=P(X=x)\,P(Y=y)$ for all $(x,y)$.  
2. Uncorrelated variables can still be dependent if their relationship is nonlinear, which correlation doesn't capture.
3. (i) $f(x)\ge0$ ∀$x$; (ii) $\int_{-\infty}^{\infty} f(x)\,dx =1$.  
4. $H(X)=-\sum_i P(x_i)\log_2 P(x_i)$.  
5. Sources have **non‑Gaussian** distributions and zero mean (data are centred); also the mixing is **linear & stationary**.  
6. Whitening rescales/rotates the centered data so that $\text{cov}(Y)=I$, i.e. unit variance and uncorrelated dimensions.

---

### Section II Solutions

#### Q2  
1. Fair die: $H=-4\times\frac14\log_2\frac14 =2$ bits.  
2. Loaded:
       
```text
H = −(0.05·log₂ 0.05 + 0.15·log₂ 0.15
      + 0.30·log₂ 0.30 + 0.50·log₂ 0.50)
  = 1.685 bits   (3 dp)
```
       
3. The fair die has higher entropy ⇒ each outcome is less predictable ⇒ it conveys more information.

---

#### Q3  
Marginals: $P(A=0)=0.5$, $P(A=1)=0.5$; $P(B=0)=0.45$, $P(B=1)=0.55$.  
Test a single cell, say $(A=0,B=0)$:  
$P(A)P(B)=0.5\times0.45=0.225\ne0.20$ ⇒ independence fails.  
Since at least one cell violates the factorisation, $A$ and $B$ are **not** independent.

---

#### Q4  
1. $\int_0^2 kx^2dx =1 \;\Rightarrow\; k\frac{x^3}{3}\Big|_0^2=1 \Rightarrow k=\frac{3}{8}. $  
2. $P(0.5<X<1.5)=\frac38\int_{0.5}^{1.5}x^2dx=\frac38\bigl[\tfrac{x^3}{3}\bigr]_{0.5}^{1.5}=0.3125$.  
3. For $0\le x\le2$, $F(x)=\int_0^{x}\frac38 t^2dt=\frac38\frac{x^3}{3}=\frac{x^3}{8}$.

---

#### Q5  
2. Gradient step:  

|   | $y_1$ | $y_2$ |
|---|-------|-------|
| **$w_1$ (new)** | $1+0.1\times0.2=1.020$ | $0+0.1\times(-0.1)=-0.010$ |
| **$w_2$ (new)** | $0+0.1\times0.05=0.005$ | $1+0.1\times0.03=1.003$ |

---

### Section III Solutions (Outline)

#### Problem A  
(a) PCA enforces **orthogonality**; independence is a stronger, nonlinear criterion, so PCA can at best decorrelate but not fully demix sources that are still dependent in higher‑order statistics.  
(b) Steps: centre the data; whiten (eigen‑ or SVD‑based); optionally reduce dimensionality; initialise $W$.  
(c) $\hat s=W y$ with **W = β⁻¹**

|        | **y₁** | **y₂** |
|--------|-------:|-------:|
| **s₁** | 1.333  | −0.833 |
| **s₂** | −0.500 | 1.167  |

, etc.  
(d) More sources than sensors → mixing matrix non‑square: not invertible; need sparse or temporal structure to separate; under‑determined ICA.  
(e) Super‑Gaussian signals usually dominate the contrast functions (e.g. kurtosis); the Gaussian source may be poorly separated because its negentropy is zero.

---

#### Problem B  
- For whitened data $\text{cov}(X)=I$.  
- det $W=1$ preserves volume ⇒ no Jacobian term in entropy change.  
- $J=H_{\text{gauss}}-H(X)$ with $H_{\text{gauss}}$ constant; maximising $J$ ⇔ minimising $H(X)$.  
- By maximum‑entropy theorem, Gaussian has highest entropy among equal‑covariance distributions; hence minimising $H$ moves away from Gaussianity, which underlies ICA’s contrast functions.

</details>

---
