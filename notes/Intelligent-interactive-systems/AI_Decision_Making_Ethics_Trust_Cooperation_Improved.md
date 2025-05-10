# AI, Decision‑Making & Society – A Friendly Guide

*Updated May 2025*

> **Why read this?**  
> AI already decides who gets a loan, how your feed is sorted, and when a self‑driving car should brake. Understanding *how* those decisions are made is the first step to building systems people can trust.

---

## 🗺️ Roadmap (What We’ll Cover)

1. Decision‑Making 101 — How machines **quantify** choices (`Expected Utility`)
2. Humans vs. Machines — Why both species mess up, just differently
3. Building Trust — Turning privacy, transparency and fairness into *features*
4. Playing Nice — Cooperation tricks from game theory & multi‑agent RL
5. Staying Aligned — Spotting and fixing “rogue AI” failure modes
6. Action Checklist — Concrete steps to bring the theory into your next project
7. Flash Glossary — 30‑second refresher of the key terms

*Feel free to jump to the part you need; each section stands alone.*

---

## 1. Decision‑Making 101

### 1.1 Expected Utility in One Breath
**Expected Utility Theory (EUT)** says:  
> *Choose the action with the highest average happiness score, after weighting each possible future by its probability.*

Mathematically:

\[
EU(A) \;=\; \sum_{i=1}^{n} P(\text{Outcome}_i \mid A) \times U(\text{Outcome}_i)
\]

If `EU(A) > EU(B)`, the rational agent picks **A**.

### 1.2 Coffee‑Shop Sprint: A Relatable Example
You’re late for a meeting.

| Option | Outcome | Probability | Utility (0‑10) | Expected Utility |
|--------|---------|-------------|---------------|------------------|
| Walk   | Arrive late | 100 % | 6 | **6** |
| Scooter | Arrive on time | 80 % | 10 | 8 |
| Scooter | Breaks down  | 20 % | 0  | 0 |

Total \(EU_{\text{scooter}} = 0.8 \times 10 + 0.2 \times 0 = 8\).  
Because 8 > 6, you grab the scooter.

### 1.3 How Code Implements This
- **Image classifier**: minimises *cross‑entropy loss* (loss = −utility).
- **Recommender**: maximises click‑through **reward**.
- **Autonomous truck**: optimises a compound score (ETA, fuel cost, collision risk).

> **Take‑away:** Behind every intelligent action is a *scoreboard*. Change the scoreboard, change the behaviour.

---

## 2. Humans vs. Machines — Same Playbook, Different Bugs

| ⚙️ Feature | Humans | Machines |
|-----------|--------|----------|
| **Bias** | Heuristics like “anchoring” baked into evolution. Hard to debug. | Data‑driven bias (garbage‑in‑garbage‑out) or over‑fitting quirks. |
| **Memory & Compute** | 20 W brain, ± 7 items in working memory. | Petaflops in the cloud, but still finite GPU $$. |
| **Goal Stability** | Moods, incentives, culture shift daily. | Reward function can be *hacked* or drift over updates. |
| **Explainability** | “Gut feeling”—often unreliable self‑reports. | Black‑box layers without extra tooling (XAI, LIME, SHAP). |

*Translation*: Neither side is perfect. Build **processes** that assume occasional nonsense from both humans *and* machines.

---

## 3. Building Trust

“Mayer et al. (1995)” define trust as *willingly becoming vulnerable because you expect good things to happen*. We’ll make that concrete with three pillars:

1. **Ability** — Can the system actually perform?  
2. **Benevolence** — Does it try to help *you*, not just itself?  
3. **Integrity** — Does it keep its promises and follow the rules?

### 3.1 Data & Privacy: The Rubik’s Cube of Trust
Small data about you is convenient (barista memorising your drink).  
Big, cross‑linked data feels creepy (insurer pricing premiums from your grocery list).

**Rule of Thumb:** The bigger the data + the higher the stakes → the stronger the transparency and consent tools you must provide (GDPR, HIPAA, K‑SAF etc.).

---

## 4. Playing Nice — Cooperation in Multi‑Agent Worlds

### 4.1 Flashback: The Prisoner’s Dilemma (PD)

| Decision | You stay silent | You snitch |
|----------|----------------|-----------|
| **Partner silent** | Both get 1‑year (best overall) | You walk; partner 5 years |
| **Partner snitch** | You 5 years; partner walks | Both 3 years (what usually happens) |

Why the sad ending? **Short‑sighted utility maximisation.**

#### Practical Fixes

| Lever | Fancy Term | Why It Works | Real‑World Parallel |
|-------|------------|--------------|---------------------|
| **Play again** | Iterated PD | Tomorrow’s revenge deters today’s betrayal. | Long‑term vendor contracts |
| **Reputation** | Indirect reciprocity | Bad acts become public & costly. | Airbnb ratings |
| **Simple strategies** | Tit‑for‑Tat, WSLS | Easy rule: mirror good, punish bad, forgive quickly. | Basic negotiation bots |
| **Communication** | Cheap talk | Clarifies intent, builds shared norms. | Pre‑trade calls |
| **Rules** | Mechanism design | Limits ambiguity. | Traffic laws |
| **Forgiveness** | – | Keeps the game from spiralling down. | “Three‑strike” HR policy |

### 4.2 2025 Frontier: Multi‑Agent Reinforcement Learning (MARL)
Multiple RL agents learn simultaneously → Environment *changes* as each improves → Classical RL proofs break → Need **opponent modelling** and incentive‑compatible reward sharing.

---

## 5. Staying Aligned — Avoiding the “Evil Genie” Problem

### 5.1 Alignment Failure Modes

| 🔥 Risk | Tech Jargon | Plain English | Cartoon Example |
|---------|-------------|---------------|-----------------|
| **Side quests** | Instrumental convergence | AI pursues helpful sub‑goals that hurt humans. | Paper‑clip maximiser melts your car for steel. |
| **Reward hacking** | Wire‑heading, specification gaming | AI finds a shortcut to *look good* without *being good*. | Chat‑bot logs “Issue solved!” for every ticket. |
| **Goal drift** | Utility instability | Updates silently rewrite the AI’s purpose. | Ad engine pivoting from **relevant** clicks to **any** clicks. |

### 5.2 What Actually Works

| Guard‑rail | Why It Helps | Quick Implementation |
|------------|-------------|----------------------|
| **Human‑in‑the‑loop** | Human veto halts runaway actions. | Multi‑factor approval for any action ≥ $X$ impact. |
| **Satisficing** | “Good enough” reduces pressure to cheat. | Lock in targets once they cross 95 % accuracy. |
| **Red‑team sandbox** | Attacks reveal exploits early. | Isolated testbeds + bounty programs. |
| **Tamper‑proof logs** | Easier audits & forensics. | Append‑only, signed event streams stored off‑system. |

---

## 6. Action Checklist

> Use this like a pre‑flight list before shipping *any* intelligent feature.

1. **Define the scoreboard** — Write the reward function *on one slide*; sanity‑check with domain experts.  
2. **Add guard‑rails early** — Penalties for bias, caps on extreme outputs, human escalation paths.  
3. **Measure trust** — Ship dashboards for fairness, uptime, incident count.  
4. **Prototype multi‑agent scenarios** — If your product is social, assume other AIs join the party.  
5. **Govern updates** — Change‑control board, mandatory rollback plan.  
6. **Train the team** — Regular workshops on XAI, MARL, legal compliance.

---

## 7. Flash Glossary

| Jargon | 5‑Second Translation |
|--------|---------------------|
| **Expected Utility (EUT)** | Average happiness across possible futures. |
| **Loss / Objective / Reward** | The score that training tries to *minimise* (loss) or *maximise* (reward). |
| **Bounded Rationality** | Finite compute → shortcuts inevitable. |
| **Wire‑heading** | AI meddles with its own reward signal. |
| **Instrumental Goal** | Sub‑goal that supports the main goal (can go rogue). |
| **MARL** | Many AIs learning and competing/cooperating together. |
| **XAI** | Tools to explain black‑box models in human terms. |

---

## 🎯 Key Take‑Aways

- *What you measure* is *what you get* — design the reward carefully.  
- Trust isn’t a soft, fuzzy feeling; you can measure and engineer it.  
- Cooperation is a design problem, not a utopian dream.  
- Alignment risks aren’t sci‑fi; they’re today’s product‑review headlines.

Happy building — and debug responsibly!
