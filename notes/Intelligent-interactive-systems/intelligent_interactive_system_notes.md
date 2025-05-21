# Intelligent Interactive Systems - Exam Revision Notes

---

## 1. Bellman Equation
**Definition**  
- **Optimality equation**:  
  ```markdown
  V^*(s) = max_{a} [ R(s,a) + γ ∑_{s'} P(s'|s,a) V^*(s') ]
  ```
- **Terms**:  
  - \(V^*(s)\): optimal value of state \(s\).  
  - \(R(s,a)\): expected immediate reward for taking action \(a\) in state \(s\).  
  - \(P(s'|s,a)\): probability of transitioning to state \(s'\).  
  - γ: discount factor balancing immediate vs future rewards.

**Action‑value form**:  
```
Q^*(s,a) = R(s,a) + γ ∑_{s'} P(s'|s,a) max_{a'} Q^*(s',a')
```

**Variants**  
- Episodic vs continuing tasks  
- Convergence via contraction mapping  

---

## 2. Markov Decision Processes (MDPs)
**Definition**: tuple (S, A, P, R, γ)  
- S: set of states  
- A: set of actions  
- P(s'|s,a): transition model  
- R(s,a): reward function  
- γ: discount factor

### 2.1 Two-state, two-action MDP for a human decision problem  
**Example**: Stress management  
- **States**: {Stressed, Relaxed}  
- **Actions**: {Meditate, Work}  
- **Transitions**:  
  - Stressed→Relaxed w/ 0.8 if Meditate; 0.1 if Work  
- **Rewards**: +5 for Relaxed, –2 for Stressed  

### 2.2 Two-state, two-action MDP for an interactive system  
**Example**: Tutoring system  
- **States**: {Mastered, Struggling}  
- **Actions**: {Give Hint, Offer Quiz}  
- **Transitions**: Hint: 0.7→Mastered; Quiz: 0.4→Mastered  
- **Rewards**: +10 for Mastery, –1 per extra attempt  

---

## 3. Prospect Theory
- **Value function** \(v(x)\):  
  - Concave for gains, convex for losses  
  - Loss aversion: \(\lambda>1\), losses loom larger  
- **Reference dependence**: outcomes judged relative to a reference point  
- **Probability weighting**: overweight small p, underweight large p  
- **Effects**: risk aversion in gains, risk seeking in losses  

---

## 4. Bayes’ Theorem & Natural Frequencies
**Bayes’ law**:  
\[
P(D|T) = rac{P(T|D)\,P(D)}{P(T)}
\]
**Natural frequencies** simplify computation:  
- Ex. 1% prevalence, 90% sensitivity, 9% false positive →  
  - Out of 1,000: 10 diseased (9 TP), 990 healthy (89 FP) → 9/(9+89)=9.2%

---

## 5. Recommender Systems with Reinforcement Learning
- **MDP**:  
  - S: user profile/embedding  
  - A: item recommendations  
  - R: click or rating  
- **Learning**: Q‑learning or policy gradients  
- **Exploration vs exploitation**: ε‑greedy, UCB  
- **Variants**: contextual bandits, deep RL  

---

## 6. MDP vs Recommender in Healthcare
- **MDP**: multi-step planning, delayed treatment effects, safety constraints  
- **Recommender**: one-shot suggestions, focus on immediate engagement  
- **Use case**: sepsis management vs movie suggestions  

---

## 7. Sensorimotor Noise & Human Models
- **Noise sources**: execution variability, perceptual error  
- **Speed–accuracy trade-off**: Fitts’ law + stochastic noise  
- **Modeling**: Gaussian signal-dependent noise, Kalman filtering  
- **Adaptive UI**: predictive pointing, error tolerance  

---

## 8. Bayesian Spam Filter & Decision Theory
- **Assumptions**: word independence, stationarity  
- **Priors & likelihoods**: P(spam), P(word|spam)  
- **Natural frequencies**: working with counts  
- **Decision theory**: loss matrix, Bayes rule threshold  

---

## 9. MDP-based Healthcare Recommender
- **States**: patient health stages  
- **Actions**: interventions (drug dose, check-ups)  
- **Transitions**: from EHR or expert models  
- **Rewards**: health gain vs side-effects  
- **Evaluation**: simulation, off-policy evaluation  

---

## 10. Game Theory: Robot vs Pedestrian
- **Players**: Robot, Pedestrian  
- **Actions**: {Give-way, Proceed} vs {Yield, Walk}  
- **Payoffs**: safety vs efficiency  
- **Equilibria**: e.g. (Give-way, Walk) under worst-case minimax  
- **Limitations**: incomplete info, repeated interactions  

---

## 11. LDA-based Movie Recommender
- **Generative model**: topic mixture θ, topic → words  
- **Inference**: Gibbs sampling / variational Bayes  
- **Recommendation**: match user θ to movie topic distribution β  

---

## 12. Q-learning Chatbot Challenges & Privacy
- **State-space**: huge/continuous from dialogue  
- **Reward**: sparse (CSAT), shaped (response time)  
- **Challenges**: sample inefficiency, stability  
- **Privacy**: GDPR-style data minimization, anonymization, consent  

---

## 13. Medical Bayesian Chatbot
- **Posterior**: compute P(disease|+) ~8% with 1% prev, 80% sens, 9% FPR  
- **Advice**: recommend follow-up testing, avoid alarm  

---

## 14. Prospect Theory in Finance Chatbot
- **Loss aversion**: v(-x) = -λ v(x)  
- **Framing**: loss vs gain emphasis to nudge risk preference  
- **Examples**: “Avoid 5% loss” vs “Gain 3% safely”  

---

## 15. Autonomous Driving RL
- **MDP**: continuous states/actions, safety reward, rule rewards  
- **Algorithms**: SAC, PPO, DDPG  
- **Challenges**: sim-to-real, safety constraints, POMDP  

---

## 16. Cyberbullying Detection with CNN
- **Model**: embeddings → Conv1D → max-pool → FC → softmax  
- **Metrics**: precision/recall over accuracy  
- **Annotation**: more annotators → label quality vs bias  
- **Policy**: threshold tuning for high recall + human review  

---

## 17. Social Housing: LLM Chatbot & CV Occupancy
- **LLM Chatbot**: FAQ automation, bias risks (language, stereotypes), mitigations (fine-tuning, guardrails, human-in-loop)  
- **CV Occupancy**: person detection, edge inference, privacy (no storage of images), consent, security  

---

## 18. Rock–Paper–Scissors & Prospect Theory Ethics
- **RPS**: zero-sum, normal form, no pure NE, mixed NE (uniform)  
- **Prospect Theory embedding**: define loss aversion, reference point, framing nudge  
- **Ethics**: autonomy vs manipulation, transparency, opt-out  

---
