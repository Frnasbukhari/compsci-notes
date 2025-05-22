# **Pocket Examples – Intelligent Interactive Systems**


## 1 · Markov Decision Process (MDP) “Two‑State Health” Template

> **Scenario placeholder:** *[Replace with chatbot coaching users on exercise]*

| Element            | State H *(Healthy)* | State S *(Sick)* |
|--------------------|---------------------|------------------|
| **Actions**        | Exercise (E) / Rest (R) | Medicate (M) / Ignore (I) |
| **Rewards**        | +1 (E) / 0 (R) | −1 (M) / −2 (I) |
| **Transitions**    | P(H→H|E)=0.9, H→S=0.1 | P(S→H|M)=0.6, S→S=0.4 |

*Bellman optimality sketch*  

\[
\begin{aligned}
V(H) &= \max\bigl\{1+0.9V(H)+0.1V(S), \, 0+V(H)\bigr\}\\
V(S) &= \max\bigl\{-1+0.6V(H)+0.4V(S), \, -2+V(S)\bigr\}
\end{aligned}
\]

Solve quickly:
1. Assume optimal actions *E* in **H**, *M* in **S**.
2. Substitute and solve 2 linear equations →  
   \(V(H)=\tfrac{1+0.9·V(H)+0.1·V(S)}{1}\) etc.  
3. Get **policy** π\* = {H:E, S:M}.

> **Fast customisation:** swap “Healthy/Sick” for any binary state (e.g. *Battery Full/Low*, *Happy/Frustrated*).

---

## 2 · Q‑Learning One‑Pass Update Cheat

*Given episode (H, E) → reward +1 → next H*

\[
Q_{new}(H,E)=Q_{old}(H,E)+α\,[1 + γ·\underbrace{\max_{a'}Q(H,a')}_{Q(H,E)} - Q_{old}(H,E)]
\]

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

\[
P(Disease\,|\,+) = \frac{8}{97} \approx 8.2\,\%
\]

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

