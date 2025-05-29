# GPT Exam Style Practice Questions 

## QUESTION 1 – “ENGINEERING / LOCAL-SEARCH DESIGN”
*(single-objective, often constrained)*

### Q1-A  Aircraft-Wing Weight Minimisation
A structural engineer wants the lightest wing spar that satisfies stress and deflection limits.

**(a) Formulate the design variables, objective, and all constraints mathematically.** [5]

**(b) Propose an evolutionary algorithm:**
1. **Chromosome encoding** (justify) [3]
2. **Mutation & crossover operators** tailored to real-valued dimensions [3]
3. **Dynamic penalty strategy:** rule + parameter schedule [4]

**(c) Give two quantitative metrics (other than final mass) you would record in a runtime study and explain why.** [5]

---

### Q1-B  Nurse-Rostering with Tabu Search
A week-long rota must cover 3 shifts/day obeying legal rest rules.

1. **Define decision variables and hard/soft constraints.** [5]
2. **Describe a tabu-search neighbourhood and tabu mechanism suited to this problem.** [5]
3. **Explain how you would hybridise the tabu search with one EA operator to improve exploration.** [5]
4. **Outline an experiment to compare pure VRP 2-opt, your tabu search, and the hybrid.** [5]

---

### Q1-C  Circuit-Board Component Placement
Electronic parts must be placed on a fixed grid to minimise total wire length; parts cannot overlap.

1. **Binary vs permutation encodings:** discuss pros/cons for this task. [4]
2. **Simulated Annealing pseudocode** Manhattan cost, cooling $T_k = T_0 / \log(k+1)$. [6]
3. **Static death-penalty for overlaps:** effect on acceptance; worked 4-component example. [4]
4. **Two strategies to escape long plateaux—criticise each.** [6]

---

### Q1-D  0/1-Knapsack with Adaptive Penalties
Capacity $= W$, $n$ items.

1. **Fitness function** for an EA using adaptive penalty coefficients updated every 50 generations. [6]
2. **Acceptance probability** if embedding that EA inside a Metropolis–Hastings wrapper. [4]
3. **Three representation-level fixes** for premature convergence; rank by likely impact. [6]
4. **Sketch a runtime plot** when adaptive penalties are too aggressive; annotate symptoms. [4]

---

### Q1-E  Chemical-Blend Cost Minimisation
Four raw chemicals must be mixed to hit target purity $\pm 1\%$.

1. **Formulate the optimisation** including equality and inequality constraints. [5]
2. **Compare blend crossover (arithmetic) vs Gaussian mutation** for real vectors; when each helps. [4]
3. **ε-constraint handling approach:** show a 2D dominance example where it beats weighted sums. [6]
4. **Three domain-specific repair heuristics** and brief justifications. [5]

---

## QUESTION 2 – “MULTI-OBJECTIVE / CO-EVOLUTION / POPULATION THEORY”

### Q2-A  Multi-Objective Vehicle Routing (distance & CO₂)
1. **Define dominance**; illustrate with three labelled routes $A,B,C$. [4]
2. **NSGA-II pseudocode** for one generation (highlight crowding-distance). [6]
3. **Pathologies** if crowding step dropped; link to lost diversity. [4]
4. **Hypervolume-based stopping criterion:** design + termination proof for finite graph. [6]

---

### Q2-B  Wind-Turbine Blade Design (efficiency vs cost)
1. **Sketch expected Pareto front shape**; explain convex/concave sections physically. [4]
2. **Why weighted-sum may miss concave solutions:** numeric 2-point example. [5]
3. **ε-dominance archiving** in steady-state MOEAs; provide pseudocode. [5]
4. **Test for extreme solution bias:** include statistic + threshold rule. [6]

---

### Q2-C  Hyperparameter Tuning (accuracy vs inference-time)
1. **Formalise objectives & constraints** for a neural net on fixed hardware budget. [4]
2. **EDA variant** for discrete+continuous space; show one iteration. [6]
3. **Risk of model bias** in EDAs on epistatic hyperparams; detection experiment. [4]
4. **Transfer-learning as multi-objective:** outline MO-EA extension. [6]

---

### Q2-D  Predator–Prey Grid-World Co-Evolution
1. **Payoff matrix** for a minimal $2	imes2$ predator/prey strategy set. [4]
2. **Replicator dynamics:** derive + find fixed points. [6]
3. **Red-Queen dynamics:** define + give a grid-world trajectory. [4]
4. **Hall-of-Fame archive rule:** propose + analyse time complexity. [6]

---

### Q2-E  Symbolic Regression via Genetic Programming (error vs complexity)
1. **Parsimony pressure** as third objective. [4]
2. **Type-safe subtree-crossover pseudocode** for GP trees. [5]
3. **Bloat & lexicographic parsimony tie-breaker** to mitigate it. [5]
4. **Example** showing crowding distance fails on bloated individuals when error≈0. [6]

---

## QUESTION 3 – “THEORY / RIGOUR / META-ANALYSIS”

### Q3-A  No-Free-Lunch, Again
1. **State NFL theorem** in own words. [4]
2. **4-point search space example:** tie on average but structured subset dominance; why NFL holds. [6]
3. **Critique two almost-free-lunch results:** extra assumptions breaking NFL. [4]
4. **Three empirical protocol flaws** leading to false “best optimiser” claim. [6]

---

### Q3-B  Runtime of the (μ+λ) EA on OneMax
Assume $\mu=\lambda=n$, mutation rate $1/n$.

1. **Define expected optimisation time.** [3]
2. **AFL method:** upper-bound expected time with full steps. [9]
3. **Effect of mutation rate $c/n$ ($c>1$).** [4]
4. **Experimental sanity-check** for theoretical trend. [4]

---

### Q3-C  Convergence of UMDA on a Deceptive Trap
1. **4-bit deceptive trap function** & why it fools univariate EDAs. [4]
2. **Proof for UMDA** ($O(n\log n)$ pop.) converging to local optimum with ≥0.9 probability. [8]
3. **Pairwise factor model** fix; analyse storage cost. [4]
4. **Linkage learning** relation in modern EDAs. [4]

---

### Q3-D  Dynamic Penalty Schedules – Formal Analysis
1. **Penalty-augmented fitness:** constraint $g(x) \le 0$, coefficient $\alpha(t)$. [3]
2. **Proof** for $\alpha(t)=\alpha_0 \cdot t$ reaching a feasible optimum in $O(n/\epsilon)$ evaluations. [9]
3. **Rapid $\alpha(t)$ growth:** recreating a death-penalty scenario; illustrated with a 2-point search example. [4]
4. **Alternative approach** (e.g., ε-constraint; feasibility rules) and comparison of theoretical guarantees. [4]

---

### Q3-E  Optimal Mutation Rate for an $n$-Bit Trap
1. **Define deceptive trap** of order $k$ and parameterisation. [4]
2. **Success probability** of one-bit-flip mutation escaping trap at rate $p$. [6]
3. **Optimise $p$** for expected one-step progress; closed-form $p^*$. [6]
4. **Contrast** result with classic $1/n$ guideline on OneMax; practical lesson. [4]
