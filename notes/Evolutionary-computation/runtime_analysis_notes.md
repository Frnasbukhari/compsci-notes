
# Runtime Analysis of Evolutionary Algorithms  
*Lecture 17 – Intro & Lecture 18 – Continued*  
*Based on slides by Per Kristian Lehre – rewritten and expanded by Frnas*  

> **Why this document?**  
> The original slides give terse bullet‑points.  
> Below, every tricky concept is unpacked with plain‑English explanations, worked examples, and LaTeX‑style maths ($\dots$) ready for GitHub rendering.

---

## Table of Contents  

1. [Introduction & Motivation](#introduction--motivation)  
2. [Evolutionary Algorithms in a Nutshell](#evolutionary-algorithms-in-a-nutshell)  
3. [Computational Complexity for EAs](#computational-complexity-for-eas)  
4. [Tail Inequalities – Bounding Bad Luck](#tail-inequalities--bounding-bad-luck)  
5. [Artificial Fitness Levels (AFL) Method](#artificial-fitness-levels-afl-method)  
6. [Drift Analysis – Measuring Expected Progress](#drift-analysis--measuring-expected-progress)  
7. [Conclusions & Further Reading](#conclusions--further-reading)

---

## Introduction & Motivation

Classical algorithm analysis asks two questions: **Does it always output the right answer?** and **How much time/memory does it need as input size $n$ grows?**  

For **evolutionary algorithms (EAs)** we adapt these to match their stochastic nature:

| Classical CS | Evolutionary Algorithms |
|--------------|-------------------------|
| *Correctness*  | *Convergence:* does the EA reach a global optimum eventually? |
| *Running time* | *Time complexity:* how many **fitness function evaluations** until the optimum is first visited? |

Why count fitness evaluations? In most practical problems evaluating $f(x)$ dominates CPU cost, while mutation/selection bookkeeping is negligible.

---

## Evolutionary Algorithms in a Nutshell

### The $(\mu+\lambda)$ EA

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

#### Recommended mutation rate  
The empirical “sweet‑spot” $p=1/n$ flips one bit **on average**.  
We can see this formally: the number of flipped bits $X\sim\text{Bin}(n,p)$, hence  

$\operatorname{E}[X]=np = 1$ when $p=1/n$.

*Probability that **exactly one** bit flips*  

$\Pr[X=1] = \binom{n}{1}p(1-p)^{n-1} = (1-1/n)^{n-1} \ge 1/e\;\approx\;0.37$  

Even for $n=100$ you get a 37 % chance every iteration.

*Is two flips more likely than none?*  
With $p=1/n$,  

$\Pr[X=2] \approx \frac{1}{2e} \approx 0.18$ and $\Pr[X=0]\approx 1/e \approx 0.37$,  

so *no* – single‑bit flips dominate the search.

---

### Random Local Search (RLS)

Same loop as the $(1+1)$ EA **but force exactly one bit‑flip** instead of Binomial$\,(n,1/n)$.  
RLS is easier to analyse yet sometimes slower because it cannot perform useful multi‑bit jumps.

---

## Computational Complexity for EAs

Because runs are random, running time is a random variable $T_f$. Two standard metrics:

* **Expected runtime** $\operatorname{E}[T_f]$  
* **Success probability** $\Pr[T_f\le t]$ after $t$ evaluations (useful for time‑budgeted applications).

We summarise growth using *asymptotic notation*:

* $f(n)\in O(g(n))$ ⇔ eventually $f(n)\le c\,g(n)$  
* $f(n)\in Θ(g(n))$ ⇔ both upper & lower bounded by $g(n)$ up to constants, etc.

Polynomial expected time ($n^{O(1)}$) is considered *efficient*; exponential ($2^{Ω(n)}$) *inefficient*.

---

## Tail Inequalities – Bounding Bad Luck

To claim “the EA **usually** finishes in $O(n\log n)$” we need high‑probability bounds, not only the expectation.  
Key tools (names you’ll meet in the literature):

| Inequality | Statement (for non‑negative r.v. $X$) | Typical use |
|------------|----------------------------------------|-------------|
| **Markov** | $\Pr[X\ge a] \le \operatorname{E}[X]/a$ | crude, assumption‑free |
| **Chebyshev** | $\Pr[|X-\mu|\ge k\sigma] \le 1/k^2$ | needs variance |
| **Chernoff / Hoeffding** | exponentially small tails for sums of independent variables | analysing populations or bit flips |

*Example* – Using Chernoff we can show that in $c\,n\log n$ iterations the $(1+1)$ EA optimises **ONEMAX** with probability at least $1-1/n$.

*(Full proofs omitted here; see the drift section for sharper tools).*

---

## Artificial Fitness Levels (AFL) Method

A clever “charging argument” for **upper bounds**.

1. **Partition** the search space into fitness levels $A_1,\dots,A_m$ with strictly increasing fitness.  
2. Suppose once the EA hits level $A_i$ it needs expected time $1/u_i$ to *leave* it towards higher levels.  
3. Then $$\operatorname{E}[T] \le \sum_{i=1}^{m-1} \frac{1}{u_i}.$$

### Worked example – $(1+1)$ EA on ONEMAX

*Levels* $A_j := \{x\in\{0,1\}^n \mid \text{ONEMAX}(x)=j\}$ for $j=0,\dots,n$.  

At level $j$ there are $n-j$ zero bits.  
To improve we need **one** of them to flip to 1 while all others stay. Probability  

$$u_j \ge (n-j)\,\frac{1}{n}\,(1-1/n)^{n-1} \ge \frac{n-j}{e n}.$$

Therefore  

$$\operatorname{E}[T] \le \sum_{j=0}^{n-1} \frac{e n}{n-j} = e n\sum_{i=1}^{n}\frac{1}{i}= O(n\log n).$$

So the expected optimisation time is $\Theta(n\log n)$ – impressively efficient!

---

## Drift Analysis – Measuring Expected Progress

*Drift* is the expected one‑step change of a potential function $D_t$ that measures “distance to the goal”.

* **Additive drift theorem**  
  If $\operatorname{E}[D_t-D_{t+1}]\ge \delta$ for all $t$ while $D_0\le b$, then $\operatorname{E}[T]\le b/\delta$.  

* **Multiplicative drift theorem**  
  If the expected progress is a fixed fraction of current distance, runtimes become logarithmic.

### Sketch – Applying additive drift to ONEMAX

Let $D_t = n - \text{ONEMAX}(x^{(t)})$ (#zeros left).  
We already saw $\operatorname{E}[D_t-D_{t+1}] \ge (n-\text{ONEMAX})/(e n) = D_t/(e n)$.  
This is *multiplicative* → yields the same $O(n\log n)$ bound but via a more general framework that extends to rugged fitness landscapes.

---

## Conclusions & Further Reading

* Runtime analysis translates intuitive “it works” into provable guarantees.  
* Tools come in layers: basic expectation estimates → tail bounds → powerful drift theorems.  
* For simple benchmarks like **ONEMAX** the $(1+1)$ EA is near‑optimal.  
* Open frontier: multi‑modal functions, crossover operators, and heavy‑tailed mutation rates.

**Recommended papers**

* Doerr & Neumann (eds.): *Theory of Randomized Search Heuristics*  
* Lehre & Witt, 2012: “General drift theorem...”  
* Antipov & Doerr, 2020: “Runtime Analysis of Self‑Adjusting (1+λ) EA”.

---

*End of notes – happy optimizing!*  
