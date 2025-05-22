# Intelligent Interactive Systems – **Comprehensive Study Guide**

*Built from 2023–2024 past papers, mock paper, essay hand‑outs and professor’s own “possible questions” list.*

---

## 0 · How the exam works

| Item | Pattern |
|------|---------|
| **Questions** | 3 compulsory, 20 marks each (total 60 → rescaled) |
| **Sub‑parts** | (a) *Define/compute* ~6 marks (b) *Apply/design* ~6–8 marks (c) *Critique/ethics* ~8 marks |
| **Timing** | 2 h ⇒ ~40 min/question ⇒ 6–6–8 min per sub‑part |
| **Answer length** | ≈ 10 words per mark (200–250 words per sub‑part) |
| **Rubric tip** | Each sub‑part is **self‑contained** – no cross‑references |

**Strategy:** open with a one‑sentence scenario recap, keep maths neat, end critiques with 2–3 concrete safeguards.

---

## 1 · Core technical theories

### 1.1 Markov Decision Processes (MDPs)

```text
MDP = 〈S, A, P, R, γ〉
```

* **States (S)** – exhaustive, mutually exclusive world descriptions  
* **Actions (A)** – choices available to the agent in each state  
* **Transition function (P)** – \(P(s' | s,a)\)  
* **Reward (R)** – scalar feedback \(R(s,a,s')\)  
* **Discount (γ)** – \(0 ≤ γ<1\), present‑values the future  

#### Bellman optimality equation

\[
V^\*(s)=\max_a \sum_{s'} P(s'\mid s,a)\,[R(s,a,s') + γ V^\*(s')]
\]

Mnemonic: **“Reward + γ Value‑next”**.

#### Two‑state example

| Element | Healthy (H) | Sick (S) |
|---------|-------------|----------|
| Actions | Exercise / Rest | Medicate / Ignore |
| Rewards | +1 / 0 | −1 / −2 |
| Transition | Exercise→ H 0.9/S 0.1 … | … |

Practise filling such a table from scratch in <3 min.

---

### 1.2 Reinforcement Learning (Q‑learning)

1. Initialize table \(Q(s,a)\) arbitrarily  
2. For each step: observe \(s,a,r,s'\)  
3. Update  

\[
Q(s,a) \leftarrow Q(s,a) + α\,[r + γ \max_{a'} Q(s',a') - Q(s,a)]
\]

*Exploration → exploitation* via ε‑greedy, soft‑max or UCB.  
**Challenges in chatbots:** huge state space (contexts), sparse rewards, non‑stationary users.

---

### 1.3 Bayesian reasoning & natural frequencies

\[
P(H\mid +)=rac{P(+\mid H)\,P(H)}{P(+)}
\]

* Convert everything into **“x out of 1000 people”** to avoid base‑rate neglect.  
* Example (2024 Q1a): prevalence 1 %. Test sensitivity 80 %, false‑positive 9 %. Out of **1000**: 10 sick→8 TP, 990 healthy→89 FP → posterior \(8/(8+89)=8.2 %\). Chatbot should **reassure & advise confirmatory test**.

---

### 1.4 Prospect Theory

* **Value function**: concave for gains, convex for losses, kink at 0  
* **Loss aversion λ ≈ 2.2** – “losses loom larger”  
* **Probability weighting**: small \(p\) overweighted, large \(p\) underweighted  
* **Reference dependence**: outcomes judged relative to a neutral baseline  

**Framing trick:** present “85 % chance to *keep* £100” vs “15 % chance to *lose* £100”.

---

### 1.5 Game Theory essentials

* **Payoff matrix** for 2‑player, \(m×n\) actions  
* **Best response**: arg‑max over opponent’s actions  
* **Nash equilibrium**: mutual best responses  

Example Rock‑Paper‑Scissors: no pure NE, unique mixed \( (⅓,⅓,⅓)\).

---

### 1.6 Classification metrics

| Metric | Formula | When to use |
|--------|---------|-------------|
| Precision | TP / (TP+FP) | When **false positives** are costly |
| Recall | TP / (TP+FN) | When **misses** are costly |
| F1 | 2 · P·R / (P+R) | Balance P & R |

---

### 1.7 Sensorimotor noise & human models

* **Execution noise** – hand jitter, key‑press variance  
* **Perception noise** – latency, resolution limits  
Systems adapt by widening buttons (Fitts’ law), or predictive cursor smoothing.

---

### 1.8 Topic modelling with Latent Dirichlet Allocation (LDA)

* **Generative**: documents drawn from mixture of topics; topics are word distributions.  
* Recommender pipeline: corpus → LDA → user topic profile → movie similarity → ranked list.

---

## 2 · Ethics & Responsible AI

| Risk | Manifestation | Mitigation |
|------|---------------|------------|
| **Privacy** | Storing chat logs | Hashing, differential privacy |
| **Bias** | Skewed training data | Re‑sample, fairness constraints |
| **Opacity** | Black‑box RL | Post‑hoc explainers, model cards |
| **Autonomy** | Manipulative framing | Consent banners, opt‑out |
| **Accountability** | Who pays for harm? | Human‑in‑the‑loop, audit trails |

Essay template (15 marks):

1. Intro: state dilemma & stance  
2. Analyse 3–4 risks (privacy, bias, transparency, autonomy)  
3. Counter‑arguments / benefits  
4. Propose safeguards, cite GDPR, IEEE 7000  
5. Conclusion: balanced judgement + future work

---

## 3 · Signature application scenarios

| Scenario | Theory hooks |
|----------|--------------|
| **Medical chatbot** | Bayes + Prospect + Ethics |
| **Financial advisor bot** | Prospect + Q‑learning challenges |
| **Recommender (healthcare / movies)** | MDP design + LDA |
| **Spam filter** | Bayesian classification |
| **Cyberbullying detector** | CNN + Precision/Recall tuning |
| **Autonomous robot/vehicle** | Game theory + RL safety |

---

## 4 · Fully‑worked mini‑problems

<details>
<summary>Bayes medical test (walk‑through)</summary>

1. Prior: 1 % → 10/1000  
2. Likelihood: 80 % sensitivity → 8 TP  
3. False positives: 9 % × 990 = 89  
4. Posterior: 8 / (8+89)=0.082  
5. Advice: “Positive but still 92 % chance you’re healthy; consult doctor.”
</details>

<details>
<summary>Two‑state MDP diet choice</summary>

*States*: Hungry (H), Full (F)  
*Actions*: Eat, Skip  
*γ*: 0.9  
Transition & rewards… *(complete table and compute policy)*.
</details>

<details>
<summary>Prospect‑theory chatbot framing</summary>

“**Gain frame:** *‘Invest £100 and there’s an 80 % chance you’ll *gain* £20.’*  
**Loss frame:** *‘Invest £100 and there’s a 20 % chance you’ll *lose* £20.’*  
Users pick opposite options despite identical EV due to loss aversion λ > 1.”
</details>

<details>
<summary>Rock‑Paper‑Scissors payoff & NE</summary>

| | R | P | S |
|---|---|---|---|
| **R** | 0 | −1 | +1 |
| **P** | +1 | 0 | −1 |
| **S** | −1 | +1 | 0 |

Mixed NE \(p=(⅓,⅓,⅓)\).
</details>

<details>
<summary>Precision vs Recall tweak</summary>

*Increase threshold →* ↑precision ↓recall  
*Lower threshold →* ↑recall ↓precision  
Use dev set + Precision‑Recall curve to pick operating point.
</details>

---

## 5 · Memory aids & mnemonics

* **Bellman = “**R + γV**”**  
* **Bayes = “**Like × Prior / Evidence**”**  
* **Prospect = “**LOSS LOST**”** (Loss‑Over‑Shifts, Small‑p‑Overweight, Large‑p‑Underweight, Reference‑Shifted, **T**‑funk curve)  
* **Ethics = “**PPBAT**”** (Privacy, Bias, Accountability, Transparency)

---

## 6 · Seven‑day crash plan

| Day | Focus | Tasks |
|-----|-------|-------|
| 1 | Bellman & MDPs | Derive eqn, build 3 toy MDPs |
| 2 | Bayesian drills | 10 frequency tables + commentary |
| 3 | Prospect theory | Write 3 framing dialogues |
| 4 | Game theory | Solve 5 payoff matrices |
| 5 | Classification | Compute P/R/F1 on sample data |
| 6 | Ethics essay | Draft AI‑recruitment essay in 25 min |
| 7 | Full mock | Sit 2024 paper under timed conditions |

---

### Final checklist (tick them!)

- [ ] Recite Bellman without notes  
- [ ] Convert any Bayes problem to 1000‑person table  
- [ ] Sketch prospect value curve from memory  
- [ ] Identify mixed NE in 2×2 and 3×3 games  
- [ ] Explain precision vs recall trade‑off  
- [ ] Recall five AI ethics principles & mitigations  
- [ ] Produce timing plan: 6‑6‑8 min / part  

---

Good luck – **you’ve got this**!
