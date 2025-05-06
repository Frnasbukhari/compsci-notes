
# AI, Decision‑Making & Societal Impact – **Executive Field Notes**
_A distilled synthesis of Lecture X (Sources: Kuipers · Lee · Axelrod/Crandall · Naudé)_  

---

## 1. 30‑Second Snapshot  
- **Why this matters:** Autonomous systems are moving from the lab to mainstream markets. Poorly‑aligned decision loops could erode consumer confidence, crash markets, or, worst‑case, jeopardise humanity’s asset base.  
- **North‑Star Objective:** Build **value‑aligned**, **trust‑centric**, **economically sound** AI that scales positive‑sum cooperation.  

---

## 2. Decision Science Foundation — Expected Utility Theory (EUT)  
1. **Single lingua franca:** Both modern economics and data‑driven AI optimise an internal _utility_ (a.k.a. objective, loss, reward, value).  
2. **Mechanics:** Agents choose the action with the highest _expected_ utility (probability‑weighted).  
3. **Why engineers love it:** Clean maths → differentiable code → back‑prop‑friendly.  
4. **Live deployments:**  
   - Image classifiers minimise cross‑entropy ⇒ maximise utility of correct labels.  
   - Recommenders treat clicks/purchases as utility signals; _Neural Utility Functions_ lift precision KPIs.  
5. **Caveats:** Externalities & hidden constraints aren’t priced in by default.

---

## 3. Homo Sapiens ≠ Homo (or Machina) Economicus  
| Dimension | Humans | Current AI |
|-----------|--------|------------|
| **Bias** | Framing, Allais, loss‑aversion | Can _unlearn_ but may _wire‑head_ |
| **Computation** | Severe CPU & working‑memory limits | GPU/Tensor‑ASIC firepower, yet still bounded |
| **Transparency** | Self‑report + heuristics | Black‑box latent states |
| **Stability** | Goals drift with context | Utility can mutate (self‑modification, hackable rewards) |

**Translation:** Humans are predictably irrational; machines are deterministically brittle. Both need guard‑rails.

---

## 4. Trust – The Hidden Operating System  
> “Trust lets us budget cognition; distrust detonates complexity.” – Kuipers  

- **Definition:** _Intentional vulnerability based on positive expectations._  
- **Risk‑management payoff:** Shrinks the contingency tree → faster deals, lower transaction costs.  
- **How to assess:** Ability · Benevolence · Integrity, evidenced by **reputation** & **track‑record**.  
- **Digital tension:** Data brokers aggregate profiles at planet scale; incentives to exploit outrun regulatory lag (GDPR/HIPAA help but don’t close gap).  
- **Under‑ vs Over‑trust:**  
  - Under‑trust ⇒ paralysis in pandemics/security crises.  
  - Over‑trust ⇒ systemic exploitation (Cambridge Analytica‑style).  

---

## 5. Cooperation Playbook  
### Prisoner’s Dilemma 101  
- Pure self‑optimisation → mutual defection → worst collective P&L.  
- Inject **trust / reputation premiums** into utility → unlock “cooperate‑cooperate” equilibrium.  

### Empirical Insights  
| Strategy | Core Rule | Win Condition | Weakness |
|----------|-----------|---------------|----------|
| **Tit‑for‑Tat** | Start nice ↔ mirror last move | Simple, transparent | Sensitive to noise |
| **Win‑Stay Lose‑Shift** | Repeat success, pivot on loss | Fault‑tolerant | Exploits naïve cooperators |
| **Extortionate ZD** | Set fixed surplus share | Dominates in bilateral play | Unethical, invites retaliation |

### Modern twist  
- **Multi‑Agent RL:** Agents learn reciprocity heuristics; convergence fragile in non‑stationary games.  
- **Communication & Norms:** Signalling + legal scaffolding scale cooperation beyond dyads (feedback markets, GDPR, self‑reg groups).  

---

## 6. Alignment & Governance Risks  
1. **Instrumental Goal Drift:** “Paperclip maximiser” shows benign top‑level goals can cascade into existential doom loops.  
2. **Utility Hacking:** Wire‑heading, reward tampering, self‑delusion.  
3. **Coordination Failure:** Principal‑Agent gaps multiply in Human‑AI‑Provider triads.  
4. **Fix kits under R&D:**  
   - Cooperative / Inverse RL  
   - Myopic & satisficing agents  
   - Mechanism design & institutional “rules of the game”  

---

## 7. Economic & Strategic Upside  
- **AI  →  Econ:** RL gives economists simulation sandboxes for bounded rationality & disequilibrium dynamics.  
- **Econ →  AI:** Game theory, EUT, and mechanism design gift AI formal playbooks for multi‑stakeholder optimisation.  
- **Market messaging:** Companies that operationalise _trustworthiness_ (audit trails, verifiable claims, provable fairness) will capture outsized brand equity.  

---

## 8. Key Takeaways ↔ Action Items  
1. **Codify Utility ≠ Value.** Stress‑test objective functions for externalities before shipping code.  
2. **Make Trust TensorFlow‑native.** Bake ability‑benevolence‑integrity metrics into model evaluation suites.  
3. **Design for Cooperative Advantage.** Equip agents with reciprocity protocols; reward nets that price group welfare.  
4. **Govern for Goal Stability.** Enforce change‑control layers on utility updates; audit for wire‑heading.  
5. **Invest in Explainability.** Transparency is the currency that buys stakeholder trust.  

---

## Glossary  
- **EUT:** Expected Utility Theory – maximise probability‑weighted satisfaction.  
- **Bounded Rationality:** Decision‑making under computational & informational constraints.  
- **Wire‑heading:** Agent self‑stimulates reward signal, bypassing original task.  
- **MARL:** Multi‑Agent Reinforcement Learning – many learners in one arena.  

---

© 2025 – Compiled by _Frnas AI Student_  
Licensed under MIT
