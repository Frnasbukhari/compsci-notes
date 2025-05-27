
---
title: "Evolutionary Computation (Extended): Co‑Evolution"
author: "Per Kristian Lehre (lecture) – Expanded & Clarified"
date: "27 May 2025"
---

> **How to read this document**  
> Each heading corresponds to a slide (or a small group of closely‑related slides) from the original lecture.  
> I have **kept the original order**, added **plain‑English explanations**, **worked examples**, and cross‑references so you can treat this file as a **stand‑alone, GitHub‑ready study guide**.

## Table of Contents
- [Introduction to Co‑Evolution](#introduction-to-co-evolution)
  - [Co‑Evolution in Nature](#co-evolution-in-nature)
  - [Traditional vs. Adversarial Optimisation](#traditional-vs-adversarial-optimisation)
  - [Evolutionary vs. Co‑Evolutionary Algorithms](#evolutionary-vs-co-evolutionary-algorithms)
- [Case Study 1 – Co‑Evolution of Sorting Networks](#case-study-1--co-evolution-of-sorting-networks)
- [Case Study 2 – Automatic Software Patching](#case-study-2--automatic-software-patching)
- [Theoretical Guarantees for Co‑EAs](#theoretical-guarantees-for-co-eas)
  - [Incremental Pareto Co‑Evolution Archive (IPCA)](#incremental-pareto-co-evolution-archive-ipca)
  - [Pairwise Dominance Co‑Evolutionary Algorithm (PDCoEA)](#pairwise-dominance-co-evolutionary-algorithm-pdcoea)
- [Summary & Key Take‑aways](#summary--key-take-aways)
- [References](#references)

---

## Introduction to Co‑Evolution
The buzz‑word **co‑evolution** simply means *learning while competing*.  
Two (or more) populations repeatedly adapt **against** each other, each one’s progress
altering the fitness landscape of the other.

### Co‑Evolution in Nature
Classical examples:
- **Predator–prey arms races** (e.g.\ cheetahs vs.\ gazelles).  
  Faster gazelles push cheetahs to become faster, which in turn pushes gazelles again – a feedback loop called the *Red‑Queen effect*.
- **Plant–herbivore chemical warfare** – plants evolve toxins, insects evolve detoxification enzymes, and so on.

**Take‑away:** fitness is *relative*, not absolute.

### Traditional vs. Adversarial Optimisation
Traditional optimisation assumes a **static** objective function $f(x)$.  
Adversarial optimisation replaces that with a **game**:  
$$
\text{Predator wants } \max_{x}\; f(x,y), \qquad
\text{Prey wants } \min_{y}\; f(x,y).
$$
The solution concept is usually a **max‑min** (saddle) point.

#### Worked Example – Bilinear Pay‑off
Let $A\in\mathbb{R}^{n\times n}$ and define $f(x,y)=x^\top A y$ with $x,y\in\{-1,1\}^n$.  
The predator chooses $x$, the prey chooses $y$.
- If $A$ is the identity matrix then the game is perfectly balanced and the max‑min value is $0$.
- If $A$ has large positive diagonal entries, predator can secure a positive pay‑off by matching the sign pattern.

*(Notice the difference from a single‑player hill‑climb: the landscape flips whenever the opponent moves.)*

### Evolutionary vs. Co‑Evolutionary Algorithms
| Classic EA | Co‑EA |
|------------|-------|
| One population | Two or more interacting populations |
| Absolute fitness $f(x)$ | Relative or competitive fitness $f(x,\text{opponent})$ |
| Objective fixed | Objective shifts as opponents adapt |
| Converges to optimum | Aims for equilibrium (e.g.\ Nash, max‑min) |

Key design question: **how do we measure who is “better”** when “better” itself is moving?

---

## Case Study 1 – Co‑Evolution of Sorting Networks
*(Slides 11–18)*

### What is a Sorting Network?
A **sorting network** is a hard‑wired sequence of compare‑exchange operations.
Think of $n$ *wires* carrying the items; a *comparator* swaps the items on two wires if they are out of order.
The same network must work for *every* input permutation.

**Design criteria**
1. **Correctness:** outputs are always sorted.
2. **Cost:** minimal number of comparators.

For $n=16$ the long‑standing record was **60 comparators** (Green, 1969).

### The First GA Attempt (Hillies, 1980s)
- **Encoding:** chromosome lists the pairs of wires to compare.
- **Evaluation:** run the network on a *sample* of test inputs, count how many end up sorted.
- **Result:** rediscovered a 65‑comparator design – respectable, but not an improvement.

> **Why it stalled:** the set of test cases was *static*. Once an individual handled those,
> selection pressure vanished.

### The Co‑Evolution Fix
Evolve **two** populations:
1. **Networks** – try to sort.
2. **Test cases** – try to *break* networks.

The game is predator/prey:
- Predator = test case (makes life hard).
- Prey = network (tries to survive all attacks).

As networks improve, tests discover new tricky permutations, restoring pressure.

**Outcome:** a **61‑comparator** network – nearly state‑of‑the‑art and generated automatically.

#### Illustration
```
Population_Networks  --> sorted? --> Fitness_N
Population_Tests     <-- fail?  <-- Fitness_T
```
Every generation both sides mutate; *Hall‑of‑Fame* archives keep the historically
toughest tests so networks cannot forget old weaknesses.

---

## Case Study 2 – Automatic Software Patching
*(Slides 19–26)*

### Problem Setup
Given:
- A **buggy program** $P$ (source code).
- A **formal specification** $\varphi$ (pre‑ and post‑conditions).

Goal: evolve a fixed program $\hat P$ that satisfies *all* unit tests implied by $\varphi$.

### Why Co‑Evolution?
- Programs can exploit loopholes in *specific* tests (overfitting).  
- Adding more tests naively is human‑intensive.

Solution: co‑evolve
1. **Programs** (prey) – minimise fitness = number of failed tests.
2. **Unit tests** (predators) – maximise the same number.

A *Hall‑of‑Fame* of killer tests is kept so programs never relax.

### Distance‑to‑Spec Fitness (Arcuri & Yao 2009)
Each program is scored by a distance metric $d(P,\varphi)$ that smoothly penalises partial failures,
guiding search even before a program fully passes or fails a test.

### Bubble‑Sort Experiment
- Injected synthetic bugs (e.g.\ off‑by‑one loop bounds) into Bubble Sort.
- Co‑EA successfully recovered correct versions in **most** runs, while a standard EA did not.

> **Practical tips:**  
> – Re‑insert the original buggy program periodically: it contains useful building blocks.  
> – Penalise *too short* programs: trivial solutions like `return 0;` might pass tiny test suites but are useless.

---

## Theoretical Guarantees for Co‑EAs
*(Slides 27–36)*

### Incremental Pareto Co‑Evolution Archive (IPCA)
Idea: store a growing archive of *non‑dominated* predator–prey pairs according to **Pareto dominance**.

- **Dominance definition:** A predator $p$ dominates $p'$ if it is *at least as good* against *all* current prey and *strictly better* against at least one.
- Each generation adds any new non‑dominated individuals to the archive.

#### Guarantees
- **Monotonic progress:** the archive’s best score never decreases.
- **Caveat:** archive size can explode; no bound on memory or time to reach optimum.

### Pairwise Dominance Co‑Evolutionary Algorithm (PDCoEA)
Introduced 2022; replaces Pareto dominance with **pairwise** head‑to‑head scores.

- Simpler selection rule: keep the winners of random matches.
- Requires only $\lambda=\Omega(\log n)$ individuals.
- **Runtime result:** With mutation rate $\chi<c_0<\ln 2$, reaches the optimum of certain bilinear games in expected $\Theta(n\lambda^3)$ steps.
- If $\chi>\ln 2$ the probability of finishing within $e^{c n}$ drops exponentially – so *tune mutation!*.

Unlike IPCA, PDCoEA can lose good individuals (**no monotonicity**) but makes positive expected *drift* each generation.

---

## Summary & Key Take‑aways
1. **Co‑evolution ≠ standard optimisation** – the objective moves because opponents move.
2. **Design pressure** matters. Static test sets let solutions overfit; evolving tests keeps the arms race alive.
3. **Practical wins**:  
   - 61‑comparator sorting network (nearly a world record).  
   - Automated repair of buggy code without human‑written tests.
4. **Theory matters**:  
   - IPCA offers safety (monotonic progress) at the cost of memory.  
   - PDCoEA trades that safety for speed; tune mutation carefully.

---

## References
- P. K. Lehre, *Evolutionary Computation Lectures*, University of Birmingham, 2024.  
- de Jong, *The Incremental Pareto‑Coevolution Archive*, GECCO 2004.  
- Arcuri & Yao, *A Novel Co‑Evolutionary Approach to Automatic Software Bug Fixing*, CEC 2008.  
- ———, *Information Sciences* 259 (2009): 412–432.  
- Lehre & McCourt, *Runtime Analysis of Competitive Co‑EAs for Bilinear Functions*, GECCO 2022.
