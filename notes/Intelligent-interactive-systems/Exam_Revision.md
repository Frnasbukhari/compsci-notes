# Intelligent Interactive Systems – **Deep‑Dive Study Guide**



## 1 · Core technical theories

### 1.1 Markov Decision Processes (MDPs)

> **Intuition:** imagine coaching a user through a fitness app.  The coach doesn’t just care about today’s calorie burn; it cares about the user’s *long‑term health trajectory*.  The MDP is simply a **mathematical diary** of *where* the user can be (states), *what* the coach can say or do (actions), and *how* those choices ripple into tomorrow (transition + reward).

* **States (S)** – snapshots of the world.  Must be **Markovian**: knowing “today” is enough to predict “tomorrow” given an action.  
* **Actions (A)** – levers you can pull.  
* **Transition $P$** – nature’s response table: “If I pull this lever in state H, I land in H again 90 % of the time.”  
* **Reward (R)** – immediate score; positive for desirable outcomes, negative for pain/cost.  
* **Discount γ** – human (and algorithm) *impatience*.  A reward next week feels smaller today.  γ close to 1 = long‑term thinker; γ near 0 = short‑sighted.

#### Bellman equation — what’s the big deal?

It says **“Value of a state = today’s reward + tomorrow’s value, properly folded in.”**  That self‑referential loop lets us solve for *optimal* behaviour by dynamic programming instead of brute‑force search.

#### Worked micro‑MDP (Healthy/Sick)

| Element   | Healthy (H)                                          | Sick (S)                              |
|-----------|------------------------------------------------------|---------------------------------------|
| Actions   | Exercise (costs effort, boosts health) / Rest        | Medicate (costly) / Ignore            |
| Reward    | +1 for *Exercise* (endorphins!) / 0 for *Rest*       | −1 for *Medicate* / −2 for *Ignore*   |
| P( next ) | Exercise → H 0.9, S 0.1 · Rest → H 1.0               | Medicate → H 0.6, S 0.4 · Ignore → S 1.0 |

*Key pedagogical twist*: The reward on *Medicate* is **negative** even though it helps – mirroring *side‑effects* and encouraging foresight via γ.

---

### 1.2 Reinforcement Learning (Q‑learning)

> **Think: toddler + hot stove.**  Touch → pain → don’t do again.  Q‑learning formalises that trial‑and‑error into a table of “action quality” $Q(s,a)$.

* Learning rate $α$ – how quickly to overwrite old beliefs.  High α learns fast but forgets fast.  
* Discount γ – same impatience as before.  
* Exploration – occasionally trying “bad‑looking” actions prevents getting stuck in local optima (the toddler eventually tries broccoli).

---

### 1.3 Bayesian reasoning & natural frequencies

> **The brain is bad with percentages but great with people.**  Saying “1 % prevalence” is abstract; saying “10 out of 1000 patients” lights up intuition.

Bayes’ rule in *frequency* form:

> **Target events / Test‑positive population**.

Why used in interactive systems?  
Chatbots often present diagnostics or fraud alerts.  Explicitly walking the user through the frequency table counteracts **base‑rate neglect**, building trust.

---

### 1.4 Prospect Theory

> **Classical economics: humans are calculators. Reality: humans hate losing \$5 more than they love gaining \$5.**

Components:

* **Value curve** – steep in the loss domain, shallow in gains.  Explains risk‑seeking in losses (lotteries) but risk‑averse in gains (insurance).
* **Probability weighting** – we buy lottery tickets (overweight 1 %) but ignore seat belts (underweight 99 % accident‑free).  
Design tip: **frame outcomes** to nudge safer choices, but remember ethics.

---

### 1.5 Game Theory essentials

> **From single‑agent to multi‑agent drama.**  When your recommender competes for user attention against TikTok, payoffs depend on both sides.

* **Payoff matrix** encodes “if I do X and you do Y, we each get something”.  
* **Nash equilibrium** – nobody regrets their move *given* the other’s.  Not necessarily optimal globally (cf. Prisoner’s Dilemma).

Why in IIS?  
Chatbots may negotiate delivery slots or mediate between two users; understanding equilibria prevents unintended manipulation.

---

### 1.6 Classification metrics

> **Precision asks: of all the *fire alarms* you rang, how many real fires?**  
> **Recall asks: of all the fires, how many did you ring the alarm for?**

Trade‑off knob: raise threshold ⇒ fewer alarms (**high precision**, low recall).  
Crucial when false positives annoy users (spam filter) or false negatives endanger them (medical triage).

---

### 1.7 Sensorimotor noise & human models

> **Humans are squishy sensors and actuators.**  Clicks drift, eyes lag.  Systems that respect Fitts’ Law (bigger buttons for faster hits) feel *magically easier*.

---

### 1.8 Topic Modelling (LDA)

> **Reverse‑engineer hidden themes.**  LDA imagines each document as a smoothie of topics; each topic is a sprinkle of words.  By unsupervised inference we uncover “Action‑adventure”, “Rom‑com” etc., powering cold‑start recommendations.

---

## 2 · Ethics & Responsible AI (deeper sense‑making)

| Risk | Why it matters in IIS | Concrete safeguard (intuition) |
|------|-----------------------|--------------------------------|
| **Privacy** | Chat logs reveal mental‑health secrets. | *Differential privacy* adds calibrated noise so one user’s secret barely nudges model weights. |
| **Bias** | Training data mirrors historical prejudice. | Re‑weight minority examples → model sees balanced picture. |
| **Opacity** | Users can’t contest wrong advice. | *Model cards* translate dev jargon into user‑facing FAQs. |
| **Autonomy** | Loss‑framed nudges can coerce. | Offer explicit *cancel/opt‑out* button – restoring agency. |
| **Accountability** | When a trading bot loses \$1M, who pays? | Immutable *audit logs* chain who approved what and when. |

*Mnemonic **“P‑B‑O‑A‑A”** eaten as “Peanut Butter On A Apple” keeps the five risks in order.*

---

## 3 · Signature application scenarios – *and why each theory fits*

| Scenario | What’s happening under the hood | Theory lenses |
|----------|---------------------------------|---------------|
| **Medical chatbot** | Probabilistic triage; high‑stakes framing. | Bayes (diagnostic) + Prospect (risk communication) + Ethics |
| **Financial advisor bot** | Sequential portfolio suggestions. | MDP / RL + Prospect (loss aversion) |
| **Recommender system** | Long‑term user engagement loop. | MDP (session model) + LDA (content) |
| **Spam filter** | Class imbalance, changing adversary. | Bayesian classifier + Prec/Rec trade‑off |
| **Cyber‑bullying detector** | NLP classification + user reporting loop. | Precision/Recall + Ethics (false positives ≈ censorship) |
| **Autonomous vehicle** | Interactive multi‑agent road game. | Game theory + RL safety |

---

## 4 · Walk‑through mini‑problems

<details>
<summary>Bayes medical test – *why each number appears*</summary>

1. **Prior** 1 % → imagine *10 infected* in a crowd of 1000.  
2. **Sensitivity** 80 % → test catches 80 % of those → 8 TP.  
3. **False‑positive rate** 9 % → out of 990 healthy, 89 scream *positive*.  
4. **Posterior** 8 / 97 = 8.2 %.  *Despite a scary “positive”, odds of actually being sick are still low.*  
5. **UX insight:** Always pair result with “Next steps” to avoid panic.
</details>

<details>
<summary>Two‑state MDP diet choice – *policy intuition*</summary>

*States* Hungry (H), Full (F).  
*Actions* Eat (E), Skip (S).  
Rewards: E when H = +3 (satisfaction), S when H = −2 (hangry), etc.

> **γ effect:** High γ encourages occasional fasting (long‑term weight loss), low γ chases immediate satiety.

Compute $V$ quickly, then explain *why* the greedy policy alternates E and S.
</details>

<details>
<summary>Prospect framing dialogue – *ethics reflection*</summary>

Explain how switching from “85 % chance to keep £100” to “15 % chance to lose £100” flips user choice *because* of the steeper loss slope.  Then ask: **Should we do this?**  Ethical critique scores marks.
</details>

