QUESTION 1 – “ENGINEERING / LOCAL-SEARCH DESIGN”
(single-objective, often constrained)

Q1-A  Aircraft-Wing Weight Minimisation
A structural engineer wants the lightest wing spar that satisfies stress and deflection limits.
(a) Formulate the design variables, objective, and all constraints mathematically. [5]
(b) Propose an evolutionary algorithm:
  (i) chromosome encoding (justify) [3]
  (ii) mutation & crossover operators tailored to real-valued dimensions [3]
  (iii) a dynamic penalty strategy: rule + parameter schedule [4]
(c) Give two quantitative metrics (other than final mass) you would record in a runtime study and explain why. [5]

Q1-B  Nurse-Rostering with Tabu Search
A week-long rota must cover 3 shifts/day obeying legal rest rules.
(a) Define decision variables and hard/soft constraints. [5]
(b) Describe a tabu-search neighbourhood and tabu mechanism suited to this problem. [5]
(c) Explain how you would hybridise the tabu search with one EA operator to improve exploration. [5]
(d) Outline an experiment to compare pure VRP 2-opt, your tabu search, and the hybrid. [5]

Q1-C  Circuit-Board Component Placement
Electronic parts must be placed on a fixed grid to minimise total wire length; parts cannot overlap.
(a) Binary vs permutation encodings: discuss pros/cons for this task. [4]
(b) Give pseudocode for Simulated Annealing with a Manhattan-distance cost and cooling schedule 
𝑇
𝑘
=
𝑇
0
/
log
⁡
(
𝑘
+
1
)
T 
k
​
 =T 
0
​
 /log(k+1). [6]
(c) Explain how a static death-penalty for overlaps changes the acceptance function; give a worked 4-component example. [4]
(d) Two strategies to escape long plateaux—criticise each. [6]

Q1-D  0/1-Knapsack with Adaptive Penalties
Capacity = W, n items.
(a) Write the fitness function for an EA using adaptive penalty coefficients updated every 50 generations. [6]
(b) Derive the acceptance probability if you embed that EA inside a Metropolis-Hastings wrapper. [4]
(c) The EA converges prematurely. Give three representation-level fixes and rank them by likely impact. [6]
(d) Sketch a runtime plot you would expect if adaptive penalties are too aggressive; annotate the symptoms. [4]

Q1-E  Chemical-Blend Cost Minimisation
Four raw chemicals must be mixed to hit target purity ±1 %.
(a) Formulate the optimisation including equality and inequality constraints. [5]
(b) Compare blend crossover (arithmetic) vs Gaussian mutation for real vectors; when does each help? [4]
(c) Propose an ε-constraint handling approach and show a 2-dimensional dominance example where it beats weighted sums. [6]
(d) List three domain-specific heuristics you would embed as repair operators and justify each briefly. [5]

QUESTION 2 – “MULTI-OBJECTIVE / CO-EVOLUTION / POPULATION THEORY”
Q2-A  Multi-Objective Vehicle Routing (distance & CO₂)
(a) Define dominance and illustrate with three labelled routes 
𝐴
,
𝐵
,
𝐶
A,B,C. [4]
(b) Write pseudocode for one generation of NSGA-II, clearly indicating where crowding-distance is used. [6]
(c) Suppose we drop the crowding step. Predict two concrete pathologies and link each to lost diversity. [4]
(d) Design a hypervolume-based stopping criterion and prove it will terminate for any finite graph. [6]

Q2-B  Wind-Turbine Blade Design (efficiency vs cost)
(a) Sketch the expected Pareto front shape and explain its convex/concave sections physically. [4]
(b) Show why weighted-sum scalarisation may miss solutions on a concave front. Provide a numeric 2-point example. [5]
(c) Explain the role of ε-dominance archiving in steady-state MOEAs; give pseudocode. [5]
(d) Devise a test to decide if your algorithm suffers from extreme solution bias; include the statistic and threshold rule. [6]

Q2-C  Hyperparameter Tuning (accuracy vs inference-time)
(a) Formalise the objectives and constraints for tuning a neural net on a fixed hardware budget. [4]
(b) Propose an Estimation of Distribution Algorithm (EDA) variant for this discrete + continuous space; show one iteration. [6]
(c) Discuss the risk of model bias in EDAs on epistatic hyperparameters and how to detect it experimentally. [4]
(d) Explain how transfer-learning across datasets can be cast as a multi-objective problem; outline an MO-EA extension. [6]

Q2-D  Predator–Prey Grid-World Co-Evolution
(a) Write the payoff matrix for a minimal 2×2 predator/prey strategy set. [4]
(b) Derive the replicator dynamics and find fixed points. [6]
(c) Define Red-Queen dynamics and give a concrete grid-world trajectory that exhibits it. [4]
(d) Propose a Hall-of-Fame archive rule to stabilise progress; analyse its time complexity. [6]

Q2-E  Symbolic Regression via Genetic Programming (error vs complexity)
(a) Define parsimony pressure and embed it as a third objective. [4]
(b) Write subtree-crossover pseudocode for type-safe GP trees. [5]
(c) Explain and exemplify bloat; then design a lexicographic parsimony tie-breaker to mitigate it. [5]
(d) Show, with a numeric example, how crowding distance fails to punish bloated individuals when error≈0. [6]

QUESTION 3 – “THEORY / RIGOUR / META-ANALYSIS”
Q3-A  No-Free-Lunch, Again
(a) State the No-Free-Lunch theorem for optimisation in your own words. [4]
(b) Provide a 4-point search space example where two algorithms tie on average but one dominates on a structured subset; explain why NFL still holds. [6]
(c) Critique two almost-free-lunch results and say what extra assumptions break NFL. [4]
(d) You claim to have found “the universally best optimiser”. List three empirical protocol flaws that could lead to this false conclusion. [6]

Q3-B  Runtime of the (μ+λ) EA on OneMax
Assume 
𝜇
=
𝜆
=
𝑛
μ=λ=n and mutation rate 
1
/
𝑛
1/n.
(a) Define expected optimisation time. [3]
(b) Using the Artificial-Fitness-Levels (AFL) method, upper-bound the expected time; show all steps. [9]
(c) Discuss how the bound changes if mutation rate is scaled to 
𝑐
/
𝑛
c/n for constant 
𝑐
>
1
c>1. [4]
(d) Give one experimental sanity-check to verify your theoretical trend. [4]

Q3-C  Convergence of UMDA on a Deceptive Trap
(a) Describe the 4-bit deceptive trap function and why it fools univariate EDAs. [4]
(b) Prove that UMDA with population size 
𝑂
(
𝑛
log
⁡
𝑛
)
O(nlogn) converges to the local optimum with probability ≥0.9. [8]
(c) Suggest a pairwise factor model that fixes the issue; analyse parameter storage cost. [4]
(d) Briefly relate this to the concept of linkage learning in modern EDAs. [4]

Q3-D  Dynamic Penalty Schedules – Formal Analysis
(a) Write the penalty-augmented fitness for a single constraint 
𝑔
(
𝑥
)
≤
0
g(x)≤0 using a time-varying coefficient 
𝛼
(
𝑡
)
alpha(t). [3]
(b) Assume 
𝛼
(
𝑡
)
=
𝛼
0
⋅
𝑡
alpha(t)=alpha0⋅t. Prove that for any 
𝜀
>
0
epsilon>0 a feasible optimum is reached in expected 
𝑂
(
𝑛
/
𝜀
)
O(n/epsilon) evaluations under a (1+1) EA. [9]
(c) Discuss why too-rapid growth of 
𝛼
(
𝑡
)
alpha(t) can recreate a death-penalty scenario; illustrate with a 2-point search space. [4]
(d) Outline one alternative (e.g., ε-constraint, feasibility rules) and compare its theoretical guarantees. [4]

Q3-E  Optimal Mutation Rate for an n-Bit Trap
(a) Define the deceptive trap of order 
𝑘
k and its parameterisation. [4]
(b) Derive the success probability of one bit-flip mutation escaping the trap for rate 
𝑝
p. [6]
(c) Optimise 
𝑝
p to maximise the expected one-step progress; give the closed-form 
𝑝
* 
p* . [6]
(d) Contrast this result with the classic 
1
/
𝑛
1/n guideline on OneMax; summarise the practical lesson. [4]
