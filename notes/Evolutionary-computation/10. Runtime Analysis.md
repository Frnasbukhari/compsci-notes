# Runtime Analysis of Evolutionary Algorithms  

## 1. Introduction & Motivation

Classical algorithm analysis asks two questions: **Does it always output the right answer?** and **How much time/memory does it need as input size $n$ grows?**  

For **evolutionary algorithms (EAs)** we adapt these to match their stochastic nature:

| Classical CS | Evolutionary Algorithms |
|--------------|-------------------------|
| *Correctness*  | *Convergence:* does the EA reach a global optimum eventually? |
| *Running time* | *Time complexity:* how many **fitness function evaluations** until the optimum is first visited? |

> Why count fitness evaluations?            
> In most practical problems evaluating $f(x)$ dominates CPU cost, while mutation/selection bookkeeping is negligible.

---

## 2. Evolutionary Algorithms in a Nutshell

### 2.1 The $(\mu+\lambda)$ EA

```text
Initialise population P₀ with μ random bit‑strings of length n.
for t = 0,1,2,… until stop‑condition:
    • Produce λ offspring:
          pick parent x ∈ Pₜ uniformly
          mutate every bit independently with probability p
    • Form Pₜ₊₁ by the best μ individuals out of (μ+λ) parents+offspring  (elitism)
```

*Special cases*  
* $(1+1)$ EA → set $\mu=\lambda=1$.  
* **Genetic Algorithm (GA)** → add crossover & probabilistic selection.  

#### 2.1.1 Recommended mutation rate  
The empirical “sweet‑spot” $p=1/n$ flips one bit **on average**.  
We can see this formally: the number of flipped bits $X\sim\text{Bin}(n,p)$, hence  

$\mathrm{E}[X]=np = 1$ when $p=1/n$.

#### 2.1.2 $(\mu+\lambda)$ Probabilities

- *Probability that **exactly one** bit flips*  ? $\Pr[X=j] = \binom{n}{j}p(1-p)^{n-1}$
    - $\Pr[X=1] = \binom{n}{1}p(1-p)^{n-1} = (1-1/n)^{n-1} \ge 1/e\;\approx\;0.37$
    - Even for $n=100$ you get a 37 % chance every iteration.

- *Is two flips more likely than none?*
    - With $p=1/n$,
    - $\Pr[X=2] \approx \frac{1}{2e} \approx 0.18$ and $\Pr[X=0]\approx 1/e \approx 0.37$,
    - so *no* – single‑bit flips dominate the search.


### 2.2 Random Local Search (RLS)

Same loop as the $(1+1)$ EA **but force exactly one bit‑flip** instead of Binomial $\,(n,1/n)$.  
RLS is easier to analyse yet sometimes slower because it cannot perform useful multi‑bit jumps.

---

## 3. Computational Complexity for EAs

Because runs are random, running time is a random variable $T_f$. Two standard metrics:

* **Expected runtime** $\mathrm{E}[T_f]$  
* **Success probability** $\Pr[T_f\le t]$ after $t$ evaluations (useful for time‑budgeted applications).

We summarise growth using *asymptotic notation*:

* $f(n)\in O(g(n))$ ⇔ eventually $f(n)\le c\,g(n)$  
* $f(n)\in Θ(g(n))$ ⇔ both upper & lower bounded by $g(n)$ up to constants, etc.

Polynomial expected time ($n^{O(1)}$) is considered *efficient*; exponential ($2^{Ω(n)}$) *inefficient*.

---

## 4. Artificial Fitness Levels (AFL) Method

A clever “charging argument” for **upper bounds**.

1. **Partition** the search space into fitness levels $A_1,\dots,A_m$ with strictly increasing fitness.  
2. Suppose once the EA hits level $A_i$ it needs expected time $1/u_i$ to *leave* it towards higher levels.  
3. Then $$\mathrm{E}[T] \le \sum_{i=1}^{m-1} \frac{1}{u_i}.$$

### Worked example – $(1+1)$ EA on ONEMAX

*Levels* $A_j := \{\,x\in\{0,1\}^n\;\mid\;\mathrm{ONEMAX}(x)=j\}$ for $j=0,\dots,n$.

At level $j$ there are $n-j$ zero bits.  
To improve we need **one** of them to flip to 1 while all others stay. Probability  

$$u_j \ge (n-j)\,\frac{1}{n}\,(1-1/n)^{n-1} \ge \frac{n-j}{e n}.$$

Therefore  

$$\mathrm{E}[T] \le \sum_{j=0}^{n-1} \frac{e n}{n-j} = e n\sum_{i=1}^{n}\frac{1}{i}= O(n\log n).$$

So the expected optimisation time is $\Theta(n\log n)$ – impressively efficient!
