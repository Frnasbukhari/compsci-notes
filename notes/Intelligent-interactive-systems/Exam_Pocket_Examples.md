# **Pocket Examples – Intelligent Interactive Systems**


## 1 · Markov Decision Process (MDP) “Two‑State Health” Template

> **Scenario placeholder:** *[Replace with chatbot coaching users on exercise]*

| Element            | State H *(Healthy)* | State S *(Sick)* |
|--------------------|---------------------|------------------|
| **Actions**        | Exercise (E) / Rest (R) | Medicate (M) / Ignore (I) |
| **Rewards**        | +1 (E) / 0 (R) | −1 (M) / −2 (I) |
| **Transitions**    | P(H→H|E)=0.9, H→S=0.1 | P(S→H|M)=0.6, S→S=0.4 |

*Bellman optimality sketch*

$$
\begin{aligned}
V(H) &= \max\Bigl\\{\,1 + 0.9\,V(H) + 0.1\,V(S),\; V(H)\\Bigr\\}\\
V(S) &= \max\Bigl\\{\,-1 + 0.6\,V(H) + 0.4\,V(S),\; -2 + V(S)\\Bigr\\}
\end{aligned}
$$


Solve quickly:
1. Assume optimal actions *E* in **H**, *M* in **S**.
2. Substitute and solve 2 linear equations →  
   $V(H)=\tfrac{1+0.9·V(H)+0.1·V(S)}{1}$ etc.  
3. Get **policy** π\* = {H:E, S:M}.

> **Fast customisation:** swap “Healthy/Sick” for any binary state (e.g. *Battery Full/Low*, *Happy/Frustrated*).

---

## 2 · Q‑Learning One‑Pass Update Cheat

*Given episode (H, E) → reward +1 → next H*

Here is the Q-update rule in state **H** with action **E**:

$$
Q_{\text{new}}(H,E)
  = Q_{\text{old}}(H,E)
    + \alpha
      \Bigl[
        1
        + \gamma
          \max_{a'} Q(H,a')
        - Q_{\text{old}}(H,E)
      \Bigr]
$$





*Plug α=0.5, γ=0.9, Q_{old}(H,E)=0.4 → **0.7***.

> Memorise formula, then just insert numbers.

---

## 3 · Bayesian Natural‑Frequency Table (Medical Test)

|                       | **Disease** | **No disease** | **Total** |
|-----------------------|------------:|---------------:|----------:|
| **Positive result**   | 8           | 89             | **97** |
| **Negative result**   | 2           | 901            | **903** |
| **Total (1000)**      | 10          | 990            | 1000 |

*Numbers derive from*: prevalence 1 % (→10), sensitivity 80 % (→8 TP), false‑positive 9 % (→89 FP).  

$$
P(Disease\,|\,+) = \frac{8}{97} \approx 8.2\,\%
$$

> **Swap prevalence/sensitivity/FP rate**, recalc three cells, then divide.

---

## 4 · Prospect‑Theory Framing Pair

*Gain frame*:  
> “If the customer invests **£100**, there is an **80 % chance to **gain** £20**.”

*Loss frame*:  
> “If the customer invests **£100**, there is a **20 % chance to **lose** £20**.”

Explain: identical expected value, but users flip choices because **loss aversion λ > 1**.

> Replace money & percentages to match domain (diet calories, time saved, etc.).

---

## 5 · Game‑Theory Payoff Matrix Templates

### 5.1 *2×2* “Co‑op vs Defect” (Prisoner‑style)

|             | **User cooperates** | **User defects** |
|-------------|--------------------:|-----------------:|
| **AI cooperates** | (3, 3) | (0, 5) |
| **AI defects**    | (5, 0) | (1, 1) |

*Best responses*: defect/defect → **single Nash equilibrium (1,1)**.  
> Shift numbers to any interactive recommender (share data vs withhold).

### 5.2 *3×3* “Pedestrian Crossing” (yield, go slow, speed)

Include generic matrix then describe mixed strategy:

|          | **Yield Y** | **Slow S** | **Speed F** |
|----------|------------:|-----------:|------------:|
| **Car Y** | 0,0 | 2,1 | −3,3 |
| **Car S** | 1,2 | −1,−1 | 4,−4 |
| **Car F** | 3,−3 | −4,4 | −2,−2 |

Find **mixed NE** by equalising expected payoffs (show one line, skip algebra in text).

> Memorise pattern: diagonal often worst/worst, off‑diagonals asymmetric.

---

## 6 · Classification Confusion Matrix & Metrics

|               | **Predicted Pos** | **Predicted Neg** |
|---------------|------------------:|------------------:|
| **Actual Pos** | TP = 90 | FN = 10 |
| **Actual Neg** | FP = 30 | TN = 870 |

- Precision = 90 / (90+30) = **0.75**  
- Recall = 90 / (90+10) = **0.90**  
- F1 ≈ **0.82**

> Increase threshold → FP↓ Precision↑ Recall↓ (vice‑versa).

---

## 7 · Concerns, Risks, and Mitigations

### Mitigation Sentence Bank (mix ’n match)

* **Data:** “Apply **differential privacy** so individual records barely influence gradients.”  
* **Fairness:** “Inject **re‑weighting or re‑sampling** to equalise TPR across demographic groups.”  
* **Transparency:** “Publish a **model card** outlining intended use, limits, and evaluation metrics.”  
* **Accountability:** “Maintain **immutable audit logs** capturing version, hyper‑params, and approver sign‑off.”  
* **Robustness:** “Add **adversarial training** on perturbed inputs to harden against manipulation.”  
* **Safety:** “Implement a **guard‑rail fallback policy** that hands control to a human operator on anomaly detection.”  
* **Privacy:** “Store user embeddings **client‑side**; only aggregate gradients are shared (federated learning).”  

Memorise 3‑4 favourites to blend into any answer.

---

### Quick GDPR References (drop these article numbers)

| Article | Tag line | When to cite |
|---------|----------|--------------|
| **Art 5** | Data minimisation & purpose limitation | Anytime you talk storage or logging |
| **Art 25** | Privacy by design & default | Bringing up early‑stage mitigation |
| **Art 35** | Data‑Protection Impact Assessment | High‑risk profiling (health, finance) |

---

### Generic Risk Table (copy to exam answer, replace examples)

| Risk| Concrete exam‑friendly example | Go‑to mitigation |
|---------------|-------------------------------|------------------------------|
| **Bias** | Chatbot mis‑identifies female names as typos | Re‑weight data, fairness whitelist |
| **Privacy leak** | Autocomplete reveals personal addresses | Encryption + anonymisation |
| **Opacity** | RL policy cannot explain move | Interpretability layer + logs |
| **Toxic Feedback Loop** | Recommender pushes extremist content → engagement spikes → more extremism | Regular retraining + diversity boosting |
| **Safety hazard** | Robot assistant bumps into child when lidar fails | Failsafe fallback + second‑human review |

(Memorise 1 concrete example per risk.)

---

### Universal Closing Sentence

> “Combining these mitigations aligns the system with **FAIR‑TAP** principles, ensuring user trust and regulatory compliance.”

Use it to tidy up any ethics sub‑part.

