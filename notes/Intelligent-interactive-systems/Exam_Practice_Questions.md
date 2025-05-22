# Practice Questions for Intelligent Interactive Systems

Use these questions to practice under exam conditions. Write full answers, include equations, diagrams, and critical commentary.

---

## 1. MDPs & Reinforcement Learning

1. **Bellman Equation**  
   - Derive the Bellman optimality equation for $V^*(s)$. Explain each term and sketch a short proof of convergence under contraction mapping.

2. **Two-State Human MDP**  
   - Design a two-state, two-action MDP modelling a person’s choice between “exercise” and “rest” to manage mood. Specify $S, A, P, R, \gamma$.

3. **Interactive System MDP**  
   - Construct a two-state, two-action MDP for an intelligent tutoring system predicting student success in a pointing task. Define transitions and rewards.

4. **Healthcare MDP Recommender**  
   - Propose an MDP-based recommender for personalized dosing of a chronic-disease medication. Describe how you’d estimate $P$ from EHR data and test the policy offline.

5. **Autonomous Driving MDP**  
   - Formulate an RL agent for urban driving as an MDP. List state variables, actions (continuous or discrete), reward components (safety vs efficiency) and discuss $\gamma$ selection.

6. **Training Challenges**  
   - Outline the pipeline for training that driving agent (data collection, preprocessing, algorithm choice). Identify three core challenges (e.g. sim-to-real, safety) and mitigation strategies.

---

## 2. Decision Making & Prospect Theory

7. **Prospect Theory Fundamentals**  
   - Define the Prospect-Theory value function $v(x)$ and probability-weighting function $\pi(p)$. Illustrate with a plotted value curve.

8. **Risk Framing**  
   - Show with a numerical example how framing an investment as “avoiding a loss” vs “securing a gain” shifts preferences for a user with $\lambda=2$.

9. **Prospect vs Expected Utility**  
   - Compare Prospect Theory with Expected Utility Theory. Under what conditions do they predict identical choices? When do they diverge?

10. **Chatbot Framing**  
    - Design two different message framings for a finance chatbot (loss-minimizing vs gain-maximizing). Explain how each would nudge user behavior.

11. **Ethics of Nudging**  
    - Critically evaluate the ethics of embedding Prospect-Theory-based nudges in an AI recommender. Discuss autonomy, transparency, and possible regulatory safeguards.

---

## 3. Bayesian Reasoning & Natural Frequencies

12. **Bayes’ Theorem**  
    - State Bayes’ law. Using a disease with 1% prevalence, 80% sensitivity, and 9% false-positive rate, compute $P(\text{disease}\mid +)$ both in probability form and as a natural-frequency tree.

13. **Decision Threshold**  
    - Given losses $L_{FP}$ and $L_{FN}$, derive the Bayes-optimal threshold for classifying “positive” vs “negative” tests.

14. **Spam Filter Assumptions**  
    - List the “naive” assumptions behind a Bayesian spam filter. Give one real-world scenario where these break down.

15. **Illustration with Frequencies**  
    - Create a tiny corpus (e.g., 10 spam, 20 ham with word counts) and manually compute $P(\text{spam}\mid\text{“win”})$ using natural frequencies.

16. **Loss-Sensitive Labelling**  
    - Extend the spam filter to include a loss matrix (high cost for false positives). Show how this shifts the classification boundary.

---

## 4. Recommender Systems & LDA

17. **RL-Based Recommender**  
    - Model a movie recommender as an MDP: define $S$ (user embedding), $A$ (item list), $R$ (click/rating). Write the Q-learning update and discuss exploration strategies.

18. **Matrix-Factorization vs RL**  
    - Compare MF-based recommendation to RL-based approaches. When is each better? Cite one application where RL is essential.

19. **LDA Generative Explanation**  
    - Explain why LDA is a generative model. Walk through the “θ→z→w” sampling process and the role of Dirichlet priors.

20. **Topic-Based Recommendations**  
    - Given an LDA model with $K$ topics, describe how to map user-topic proportions $\theta$ and movie-topic profiles $\beta$ into a ranked list of top-N movies.

---

## 5. Human Factors & Sensorimotor Noise

21. **Sensorimotor Noise Effects**  
    - Describe two ways sensorimotor noise impacts pointing tasks (e.g., endpoint scatter; speed–accuracy trade-off).

22. **Human-Aware Interface**  
    - Propose an interface that uses a Kalman filter to infer user intent under noisy cursor movements. Sketch the observation model and adaptation mechanism.

23. **Critique Human Models**  
    - Analyse the pros/cons of embedding detailed human motion models in interactive systems (e.g., personalization vs overfitting).

---

## 6. Game Theory & Interaction

24. **Rock–Paper–Scissors**  
    - Draw the RPS payoff matrix for two players (win=+1, loss=–1, draw=0). Show there is no pure Nash equilibrium and derive the mixed NE.

25. **Robot vs Pedestrian**  
    - Formulate a one-shot game between a food-delivery robot and a pedestrian (actions: Proceed/Give-way vs Walk/Yield). Build a payoff matrix, find Nash equilibrium(s), and critique modeling assumptions.

---

## 7. Ethics, Privacy & Responsible AI

26. **AI in Recruitment**  
    - Critically analyse the ethics of AI screening in hiring: privacy of applicant data, algorithmic bias, fairness definitions, need for human oversight, and regulatory remedies.

27. **Chatbot Privacy**  
    - List the key GDPR principles relevant to storing chatbot logs. Propose a data-minimization and anonymization pipeline.

28. **CV Occupancy Monitoring**  
    - Debate the use of real-time video analytics for social-housing energy control. Identify privacy, security, and fairness risks—and propose technical mitigations.

29. **Bias in LLM Chatbots**  
    - For a tenant-service LLM chatbot, identify three potential biases (language, socioeconomic) and outline how you’d detect and correct them.

---

> **Tip**: Select 5–7 questions, set a 90‑minute timer, and answer as if in an exam. Good luck!
