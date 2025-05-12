# Reinforcement Learning

> **Roadmap for this lecture:**  
> 1. **Intuition** – grasp what RL is and why we bother.  
> 2. **Building blocks** – meet the cast: states, actions, rewards, policies.  
> 3. **Mathematics** – see how Markov Decision Processes (MDPs) and Bellman equations price the future.  
> 4. **Algorithms** – dive into Q‑Learning as a flagship example.  
> 5. **Deployment** – where RL already adds value and how to tune it for the real world.  
>     
> By the end you should be able to glance at a new RL research paper or product pitch and immediately understand the moving parts.

---

## 1. What Is Reinforcement Learning?
> *Why start here?* Every term, formula, and diagram that follows builds on this single idea: an **agent** improves by experimenting, observing feedback, and repeating. Nail the concept now and the rest will feel natural.

**Reinforcement Learning (RL)** is a branch of machine learning in which a software **agent** learns a **behavior policy** by **trial‑and‑error** within an **environment**.  
- The agent chooses an **action** (e.g., steer left).  
- The environment responds with a **new state** and a **numerical reward**.  
- Over many episodes the agent discovers a strategy that **maximizes the long‑term sum of rewards**.

Think of teaching a puppy: sit, treat; jump on the couch, scold. The puppy’s “policy” is whatever sequence of moves now yields the most snacks over its lifetime.

---

## 2. Why the Enterprise Needs RL
> *Connecting the dots:* once we know **what** RL is, the next natural question is **why** organisations pour money into it.

| Business Reality | Why Classical Software Struggles | RL Advantage |
|------------------|----------------------------------|--------------|
| **Complex, high‑dimensional worlds** (autonomous driving, 3D robotics) | Enumerating every rule is impossible. | RL **learns rules** instead of hard‑coding them. |
| **Non‑stationary markets** (finance, ads, energy) | Hand‑tuned heuristics become stale. | RL **updates its policy on‑line** as the world shifts. |
| **Sparse feedback** (long games, supply‑chain cycles) | Supervised labels are scarce or delayed. | RL optimizes for **delayed, aggregate rewards**. |

Bottom line: RL turns volatility into algorithmic competitive advantage.

---

## 3. Core Ingredients — A Shared Vocabulary
> *Building the language:* before we juggle equations, let’s agree on names for the pieces we’ll keep rearranging.

| Symbol / Term | Technical Definition | Everyday Analogy |
|---------------|----------------------|------------------|
| **Agent** | Algorithm that acts | You playing chess |
| **Environment** | Everything outside agent control | The chess board + opponent |
| **State (s)** | Snapshot of the environment | Current board layout |
| **Action (a)** | Choice available to the agent | Move a knight |
| **Reward (r)** | Scalar feedback | +1 for checkmate, −1 for blunder |
| **Policy (π)** | Rule mapping states → actions | “If early‑game & center open → develop knights.” |
| **Episode** | Sequence from start to terminal state | One full chess game |

The last three columns form a dialogue: the agent **acts**, the environment **reacts**, the agent **learns**. Everything else in RL is plumbing around that loop.

---

## 4. The RL Feedback Loop
> *From nouns to verbs:* now that we know the pieces, let’s see them dance.

1. **Observe** the current state *s*.  
2. **Select** an action *a* (usually a mix of “best‑known” and “try something new”).  
3. **Execute** *a* and obtain reward *r* plus next state *s′*.  
4. **Update** internal value estimates or policy parameters.  
5. **Repeat** until an episode ends, then start over.

```text
┌────────────┐      action a       ┌─────────────────┐
│   Agent    │ ──────────────────► │  Environment    │
│            │ ◄────────────────── │  state s′, reward r
└────────────┘   observation
```

That one‑line diagram is the mental model to keep on a sticky note.

---

## 5. Markov Decision Process (MDP) — The Formal Playground
> *Why formalize?* Mathematics lets us **prove** optimality instead of guessing.

An **MDP** is the 5‑tuple $$\langle S, A, P, R, \gamma \rangle$$

| Component | Description | Note |
|-----------|-------------|------|
| **S** | Set of states | Finite or continuous |
| **A** | Set of actions | May depend on state |
| **P(s′ \| s,a)** | Transition probability | “Loaded dice” of the world |
| **R(s,a)** | Immediate reward distribution | Could be noisy |
| **γ (0–1)** | Discount factor | How much tomorrow matters |

“Markov” says **the future depends only on now**, not the whole past. That makes planning tractable.

---

## 6. The Bellman Equations — Pricing the Future
> *Why we need them:* to **evaluate** how good a state or action is we must account for **all future rewards**. Bellman gives a recursive shortcut.

### State‑Value Form
$$V^{\*}(s)=\max_{a} \big[R(s,a)+\gamma \sum_{s′}P(s′\|s,a)\,V^{\*}(s′)\big]$$

### Action‑Value Form
$$Q^{\*}(s,a)=R(s,a)+\gamma \sum_{s′}P(s′\|s,a)\max_{a′}Q^{\*}(s′,a′)$$

Interpretation: present value = immediate gain + best discounted future.  
If **γ → 0**, the agent is myopic; if **γ → 1**, it plans like a pension fund.

---

## 7. Q‑Learning — Learning Values Without a Map
> *Escaping the model:* what if **P** and **R** are unknown or huge? Learn value estimates directly from data.

### Update Rule
$$Q(s,a) \leftarrow (1-\alpha)\,Q(s,a) + \alpha\big[r + \gamma\max_{a′}Q(s′,a′)\big]$$

| Symbol | Meaning | Typical Range |
|--------|---------|---------------|
| **α** | Learning rate | 0.1 → 0.001 (often decayed) |
| **γ** | Discount factor | 0.9 → 0.99 |
| **ε** | Exploration rate (for ε‑greedy) | 1 → 0.05 |

```python
# Minimal pseudo‑code
for episode in episodes:
    s = env.reset()
    done = False
    while not done:
        a = ε_greedy(Q[s])
        s′, r, done = env.step(a)
        Q[s,a] = (1-α)*Q[s,a] + α*(r + γ*max_a′ Q[s′,a′])
        s = s′
```

#### 7.1 Grid‑World Toy Example  

| From State | To State | Reward | Updated Q |
|-----------:|---------:|-------:|----------:|
| 1 | 5 | +100 | 100 |
| 3 | 1 | 0 | 80 |

Even a zero‑reward move gains value if it reliably leads to the 100‑point goal.

---

## 8. Applications — Where RL Earns Its Keep
> *Stepping outside the classroom:* here’s where RL is already paying bills.

| Sector | RL Task | Strategic Pay‑off |
|--------|---------|-------------------|
| **Autonomous Vehicles** | Lane‑keeping, merge decisions | Safety & fuel efficiency |
| **Robotics** | Grasping, locomotion | Lower programming overhead |
| **Finance** | Portfolio balancing | Adaptive risk/reward |
| **Healthcare** | Dynamic treatment planning | Better patient outcomes |
| **Supply Chain** | Inventory & routing | Cost reduction |
| **Recommender Systems** | Session‑based ranking | Engagement lift |

---

## 9. Hyper‑Parameters — Tuning Knobs That Matter
> *From prototype to product:* small dials steer large systems. Treat them like first‑class citizens.

| Parameter | Role | Practical Tip |
|-----------|------|---------------|
| **α** learning rate | How fast new info overwrites old | Start high, decay gradually |
| **γ** discount | Short‑ vs long‑term focus | 0.95+ for strategic play |
| **ε** exploration | % random actions | Anneal exponentially |
| **Batch size** | Updates per step (in DQN, etc.) | Power of 2 (32–256) |
| **Episodes** | Training loops | 10³–10⁶+ depending on domain |

A/B‑test one knob at a time; interactions can be non‑linear.

---

## 10. Key Takeaways
> *Bringing it all together:*

1. **RL operationalizes curiosity** — systems self‑improve without labeled data.  
2. **MDP is the ledger** — states, actions, rewards, probabilities in one book.  
3. **Bellman equations price tomorrow today.**  
4. **Q‑Learning democratizes RL** — model‑free, simple to code, surprisingly powerful.  
5. Deploy RL where environments are **complex, uncertain, or fast‑changing**.

---

## Further Reading & Next Steps
- **“Reinforcement Learning: An Introduction”** – Sutton & Barto (free online)  
- **Spinning Up in Deep RL** – OpenAI educational repo  
- **RL Adventure Series** – clean PyTorch examples  
- **MORL (Multi‑Objective RL)** – for when one reward isn’t enough  
- **Safe RL** – constraints & risk management

Happy learning – may your returns be ever‑increasing!
