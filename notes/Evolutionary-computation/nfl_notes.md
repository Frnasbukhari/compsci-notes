---
title: "Lecture 16 — The No Free Lunch Theorem"
author: "Expanded notes prepared by ChatGPT"
date: "27 May 2025"
---

> **Module:** Evolutionary Computation  
> **Original lecturer:** Per Kristian Lehre  
> **Original slides date:** 14 March 2024  

These notes follow the structure of the original lecture while adding:

* **Plain‑language explanations** of every definition and theorem.  
* **Worked examples** to illustrate abstract concepts.  
* **Step‑by‑step proofs** with intuitive commentary.  
* **Practical take‑aways** to help you recognise when NFL‐style limits *do* and *do not* matter in real optimisation work.

Mathematical expressions use $…$ delimiters so they render cleanly on GitHub.

---

## Outline

1. Black‑Box Optimisation Algorithms  
2. The No Free Lunch (NFL) Theorem  
   1. Statement  
   2. Proof  
3. The *Almost* No Free Lunch Theorem  
4. Conclusion  

---

# 1  Black‑Box Optimisation Algorithms

### 1.1  Problem setting

* **Search space** $X$ — a finite collection of candidate solutions (e.g. all bit‑strings of length $n$).  
* **Objective function** $f : X \to Y$ where $Y \subseteq \mathbb{R}$.  
  * We assume *maximisation*; the goal is to find $x^*\in X$ with $$f(x^*) = \max_{y\in X} f(y).$$
* The optimiser may **query** the function at points of its choice but receives only the scalar output $f(x)$.  
  * No gradients, derivatives or structural hints: hence *black‑box*.

### 1.2  Runtime notions

* **Runtime of algorithm $A$ on function $f$**

  $$T_{A,f}\;:=\;\min\!\bigl\{\,t\in\mathbb{N} \;\big|\; f(x_t) \ge f(y)\;\forall y\in X\bigr\}$$

  where $x_t$ is the $t$‑th point sampled.  
  *In words:* the number of evaluations until $A$ *first* queries a global optimum.

* **Average expected runtime over a class $\mathcal{F}$**

  $$\mathbb{E}\bigl[T_{A,\mathcal{F}}\bigr]\;:=\;\sum_{f\in\mathcal{F}} \Pr[f] \, \mathbb{E}[T_{A,f}]$$

  The probability $\Pr[f]$ encodes our belief (or an adversary’s choice) about which function will appear.  fileciteturn1file0

### 1.3  General scheme of a black‑box optimiser

```text
1. Choose an initial probability distribution p₀ over X.
2. Sample x₀ ~ p₀; set R₀ = {x₀}.
3. Evaluate f(x₀).
4. For t = 1 … |X|:
       a. History H_t = ((x₀,f(x₀)), … , (x_{t-1},f(x_{t-1}))).
       b. Choose new distribution p_t on X \ R_{t-1} (may depend on H_t).
       c. Sample x_t ~ p_t; update R_t = R_{t-1} ∪ {x_t}.
       d. Evaluate f(x_t).
```

*The only state the algorithm receives is the **history of queried points and their fitness values**.  Any search heuristic that respects this interface—from Random Search to CMA‑ES—fits inside the black‑box model.*

---

# 2  The No Free Lunch Theorem

### 2.1  Informal meaning

> *Averaged across *all* possible functions, every optimiser performs equally well.*  
> If you refuse to assume structure in your objective, **there is no universally superior algorithm**.

### 2.2  Formal statement (Wolpert & Macready 1997)

Let $X$ and $Y\subseteq\mathbb{R}$ be finite.  Let $\mathcal{F}$ be **any** set of functions $f:X\to Y$ that is **closed under permutation** (defined below).  Then for **any** two black‑box optimisation algorithms $A$ and $B$,

$$\mathbb{E}\bigl[T_{A,\mathcal{F}}\bigr] \;=\; \mathbb{E}\bigl[T_{B,\mathcal{F}}\bigr].$$

In other words, **average runtime depends only on the function class, never on the algorithm**.

---

### 2.3  Key definition — *closed under permutation* (c.u.p.)

A set of functions $\mathcal{F}$ is **closed under permutation** if  
$$f \in \mathcal{F} \;\Rightarrow\; f\circ \sigma \in \mathcal{F}\quad\text{for every permutation } \sigma:X\twoheadrightarrow X.$$

*Intuition:* if a landscape sits in the class, every possible relabelling of the search points also sits there.  Hence the class contains *no* structural bias about where good solutions lie.

#### Worked micro‑example (|X| = 3)

| $x$ | $f_1(x)$ | $f_2(x)$ | $f_3(x)$ |
|-----|----------|----------|----------|
| ●   | 1        | 2        | 3        |
| ■   | 2        | 3        | 1        |
| ▲   | 3        | 1        | 2        |

The set $\{f_1,f_2,f_3\}$ is *not* c.u.p.; adding the three remaining permutations ($f_4,f_5,f_6$) yields a c.u.p. family of six functions.

---

### 2.4  Proof sketch

The proof proceeds in two layers:

1. **Deterministic algorithms** — by induction on $|X|$.  
   * Base case $|X|=1$ is trivial.  
   * Inductive step partitions $\mathcal{F}$ according to the first point queried and the value returned, then applies the hypothesis because each partition is itself c.u.p.

2. **Randomised algorithms** — any randomised method is a probability distribution over finitely many deterministic ones.  Linearity of expectation carries the result across.

Full algebraic details are in the original paper; see the *Step‑by‑Step Proof* section below for an annotated walkthrough. fileciteturn1file0

---

### 2.5  Consequences

* **No universal best heuristic.**  Optimiser rankings can flip when you change the problem distribution.  
* **Assumptions are unavoidable.**  To justify why, say, CMA‑ES beats Genetic Algorithms on your workload you *must* articulate structural properties *not* captured by c.u.p.—for example, smoothness, separability, or low‑effective dimensionality.

---

# 3  Step‑by‑Step Proof (annotated)

Below we expand the induction argument in plain language.

<details><summary>Click to unfold the full derivation</summary>

### 3.1  Induction hypothesis  

Assume the theorem holds for all search spaces of size $N$.

### 3.2  Inductive step: space size $N+1$

*Let $A$ pick $x$ first; let $B$ pick $y$ first (possibly $x=y$).*

1. **Condition on the first feedback.**  
   After $A$ sees $f(x)=b$ the remaining uncertainty is the restricted class
   $$\mathcal{F}(x,b)\;:=\;\bigl\{f\in\mathcal{F}\mid f(x)=b\bigr\}.$$
   By permutation closure, $\mathcal{F}(x,b)$ is c.u.p. over the *reduced* search space $X\setminus\{x\}$.  The same holds for $\mathcal{F}(y,b)$.

2. **Isomorphism.**  
   There exists a bijection mapping $\mathcal{F}(x,b)$ onto $\mathcal{F}(y,b)$, implying the two subproblems are *identical up to relabelling*.  

3. **Apply induction.**  
   Because the reduced space has size $N$, the expectation of continuing runtime is the same for any algorithm.  

4. **Re‑assemble expectations.**  
   Break the total expectation into the event “$x$ is already optimal” (probability $p$) plus the residual expectation given $f(x)=b$ for $b \ne \text{optimal value}$.  Symmetry in all pieces yields  
   $$\mathbb{E}[T_{A,\mathcal{F}}] = \mathbb{E}[T_{B,\mathcal{F}}].$$

5. **Randomised algorithms.**  
   If $A$ tosses coins to choose among deterministics $A_1,\dots,A_m$ then linearity gives  
   $$\mathbb{E}[T_{A,\mathcal{F}}] = \sum_i \Pr[A\text{ chooses }A_i] \; \mathbb{E}[T_{A_i,\mathcal{F}}] = \mathbb{E}[T_{\mathcal{F}}].$$

Hence the theorem holds for size $N{+}1$, completing induction.

</details>

---

# 4  How realistic is the NFL scenario?

### 4.1  Counting argument

Suppose $X$ is the set of 100‑bit strings (size $2^{100}$) and $Y$ the 32‑bit integers (size $2^{32}$).  The number of distinct functions is  

$$|\mathcal{F}| = |Y|^{|X|} = 2^{32\,·\,2^{100}}.$$

A simple information‑theoretic bound shows that *at least half* of those functions require programs of length $\ge 32·2^{100}-1$ bits—on the order of $10^{20}$ terabytes! fileciteturn1file0

> **Take‑away:** The adversarial “draw a totally random function” thought experiment is wildly unrealistic.  Real‑world objectives are generated by physics, economics, or human design—**not** arbitrary bitstrings.

### 4.2  Almost No Free Lunch (Droste et al. 2002)

Even when you *do* assume some structure, mildly adversarial tweaks can defeat a fixed optimiser.

* Given any algorithm $A$ and any function $f:\{0,1\}^n\to\{0,\dots,N{-}1\}$, there exist **at least $N\,2^{n/3-1}$ functions** $f^*$ that  
  * differ from $f$ on at most $2^{n/3}$ inputs; yet  
  * $A$ fails to locate a maximum within $2^{n/3}$ evaluations with probability $\ge 1-2^{-n/3}$.  

Moreover these “trap” functions can be kept only $O(n)$ bits more complex than $f$.

*Practical moral:* **Domain knowledge matters**—but robustness matters too.  Favor heuristics whose *assumptions* align with your problem *and* whose performance degrades gracefully when the assumptions are imperfect.

---

# 5  Practical implications

* **Algorithm selection must be context‑dependent.**  
  Profile representative benchmarks or leverage theoretical insight about your landscape.

* **Hybrid / adaptive schemes** can bypass NFL by *changing behaviour* on‑the‑fly, effectively conditioning on observed structure.

* **Explain your assumptions.**  When publishing results, specify which landscape features (e.g. smoothness, locality, decomposability) underpin the performance claims.

---

# 6  Conclusion

The No Free Lunch theorem is *not* a reason for pessimism; it is a **reminder to match tools to tasks**.  By explicitly or implicitly restricting the function class, you open the door to algorithms that exploit that structure—and *that* is where evolutionary computation, Bayesian optimisation, and related heuristics shine.

---

## References

* Wolpert, D. H. & Macready, W. G. (1997). “No Free Lunch Theorems for Optimisation.” *IEEE Trans. Evolutionary Computation*, 1(1): 67–82.  
* Droste, S., Jansen, T., & Wegener, I. (2002). “Optimization with Randomized Search Heuristics—The (A)NFL Theorem, Realistic Scenarios, and Difficult Functions.” *Theor. Comput. Sci.*, 287(1): 131–144.  
* Droste, S., Jansen, T., & Wegener, I. (2006). “Upper and Lower Bounds for Randomized Search Heuristics in Black‑Box Optimization.” *Theory of Computing Systems*, 39(4): 525–544.  

---

*Prepared for Frnas, 27 May 2025.*  
