
# Human‑in‑the‑Loop (HITL) & Supervised Learning – Executive Field Notes

> Condensed from:  
> – *Human‑in‑the‑Loop Machine Learning: A State of the Art* (Artificial Intelligence Review, 2023)  
> – *Machine Learning: Supervised Learning* lecture slides (University of Birmingham)  
> – Recent UK AI policy papers (BBC, Guardian)

---

## 1. Why care?

* **Data‑driven automation needs humans.** Interleaving human expertise with ML unlocks higher model quality, faster convergence, and governance readiness. citeturn1file2  
* **Board‑level KPI:** trustable predictions that scale without exploding headcount.

---

## 2. Supervised Learning Crash‑Course
### 2.1 Core idea
Train on pairs *(x, y)* where **y is known** to predict y for the next x. Two canonical tasks:

| Task | Output | Example |
|------|--------|---------|
| Classification | discrete label | SPAM / NOT SPAM |
| Regression | real value | Tomorrow’s closing price |

### 2.2 Model health dashboard

| Metric | Plain English |
|--------|---------------|
| Accuracy | Overall hit rate |
| Precision | Trust when model says **Yes** |
| Recall | Coverage of real **Yes** cases |
| F1‑Score | Balanced scorecard |

Watch for **underfitting** (too simple) and **overfitting** (memorizes noise). Hold‑out test set is non‑negotiable. citeturn0file3

### 2.3 Neural architecture cheat‑sheet
| Data type | Go‑to net | Killer feature |
|-----------|-----------|----------------|
| Images, video | CNN | Spatial filters |
| Text, audio, logs | LSTM / GRU | Long‑term context |
| Very short streams | Vanilla RNN | Ultra‑low latency |

---

## 3. Human‑in‑the‑Loop Spectrum
HITL flavours differ **by who holds the wheel**. citeturn1file16

| Approach | Control knob | Human workload | Best for |
|----------|--------------|----------------|----------|
| **Active Learning (AL)** | Model queries | Label tricky samples | Label‑scarce domains |
| **Interactive ML (IML)** | Shared | Curate, fix, steer | Rapid prototyping, data wrangling |
| **Machine Teaching (MT)** | Human teacher | Design curriculum | SME knowledge transfer |
| **Curriculum Learning (CL)** | – | Rank easy→hard | Noisy / imbalanced data |
| **Explainable AI (XAI)** | – | Consume explanations | Regulated sectors |

---

### 3.1 Active Learning quick view
1. Pool of unlabeled data  
2. Model picks most **informative** item (uncertainty or diversity sampling) citeturn1file4  
3. Human labels → retrain  
4. Stop when metric or budget met

> Tip: Batch queries reduce training overhead; sequential queries maximise immediate feedback. citeturn1file4

### 3.2 Interactive ML vs AL
* **AL** = model asks questions; user is an oracle.  
* **IML** = conversational loop; users also pick data, tweak features, merge models, etc. Faster, focused, incremental updates. citeturn1file1

---

## 4. Usable, Useful & Trustworthy AI
Usability (easy to learn & operate) + usefulness (solves the real job) sit on top of accuracy. Trust emerges from robustness, fairness, transparency and explainability. citeturn1file7

---

## 5. Trends & Strategy
* **AutoML & MLOps** shrink pipeline toil; SMEs become citizen‑data‑scientists. citeturn1file19  
* **Domain‑first framing** beats algorithm‑first hype.  
* **Policy heat**: UK 2025 AI Action Plan pledges multibillion‑pound compute and NHS data sharing—regulators demand human oversight loops. (BBC, Guardian 12‑13 Jan 2025)

---

## 6. Quick‑Start Playbook
1. Frame business metric & risk appetite  
2. Collect/label starter set (AL if scarce)  
3. Baseline simple models → sanity check features  
4. Scale with CNN/LSTM only if ROI clear  
5. Drop in IML dashboard for SME feedback  
6. Ship with XAI & monitoring hooks  
7. Refresh ethics/privacy review each release

---

## 7. Glossary
* **Oracle** – human labeler in AL  
* **Hidden state** – RNN memory vector  
* **Diversity sampling** – pick rare or novel examples  
* **Trustworthy AI** – meets accuracy, robustness, fairness, accountability, transparency, explainability and ethics criteria citeturn1file11  
