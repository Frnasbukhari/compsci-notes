
# Latent Dirichlet Allocation (LDA) — A Friendly Guide 📚

> **Bottom line first:** LDA automatically discovers the *“topics”* that run through a collection of documents.  
> Each document ends up as a *smooth mix* of those topics, which is way more informative than a raw bag‑of‑words.

---

## 🚀 Roadmap

1. [Why Bother With “Topics”?](#1-why-bother-with-topics)
2. [From Bag‑of‑Words to Smarter Counts](#2-from-bag-of-words-to-smarter-counts)
3. [From Counts to Probabilistic Topic Models](#3-from-counts-to-probabilistic-topic-models)
4. [LDA’s Generative Story, Step by Step](#4-ldas-generative-story-step-by-step)
5. [How We *Actually* Learn an LDA Model](#5-how-we-actually-learn-an-lda-model)
6. [A Python Pipeline You Can Copy‑Paste](#6-a-python-pipeline-you-can-copy-paste)
7. [What LDA Is Good — and Not So Good — For](#7-what-lda-is-good--and-not-so-good--for)
8. [Clustering Refresher — Hard vs Soft](#8-clustering-refresher--hard-vs-soft)
9. [How to Evaluate Your Topics](#9-how-to-evaluate-your-topics)
10. [Extensions & Practical Gotchas](#10-extensions--practical-gotchas)
11. [Glossary — 20‑Second Recap](#11-glossary--20second-recap)

*(Click any item to jump straight there.)*

---

## 1. Why Bother With “Topics”?

**How this section fits:** Before inventing fancy math, we’d better be crystal‑clear on *why* we care.  
If you can already explain this to a colleague, skip ahead.

### 1.1 The Intuition

* Documents rarely talk about exactly one thing. A news article on climate policy also mentions politics, economics, maybe even energy tech.
* Pure bag‑of‑words = every word is an independent feature. That’s thousands of dimensions and zero structure.
* **Topics compress** that chaos into a handful of *themes* (“climate”, “politics”, “economics”) you can reason about.

### 1.2 Concrete Pay‑Offs

| Use‑Case | Why Topics Help |
| --- | --- |
| **Search & Retrieval** | Rank by *idea* similarity instead of exact words. |
| **Recommendation** | Serve articles/movies/products that share latent themes the user liked. |
| **Downstream ML** | γ‑vectors (doc‑topic weights) are low‑dim/features for classifiers. |
| **Exploratory Analysis** | Inspect topics to see what your corpus is *actually* about. |

---

## 2. From Bag‑of‑Words to Smarter Counts

**Bridge from §1 → §2:** Now that we agree structure is needed, let’s discuss the first attempts to add it *without* full‑blown probabilistic models.

### 2.1 TF‑IDF — The Classic Re‑Weighting

* `tf` = term frequency in a document.  
* `idf` = inverse document frequency = ✔ high if the term is *rare* in the corpus.  
* **Product** dampens stop‑words like “the”, boosts domain terms like “polymerase”.

### 2.2 Latent Semantic Indexing (LSI)

1. Build the **tf‑idf matrix** (docs × terms).
2. Apply **Singular Value Decomposition (SVD)**.  
   *Keep only the top `k` singular vectors → a low‑rank approximation.*
3. Result: each document lives in a dense `k`‑dim space that *roughly* captures synonymy/polysemy.

> **Limitation:** LSI is *linear algebra, not probability* — no generative story, no principled way to handle unseen docs.

---

## 3. From Counts to Probabilistic Topic Models

**Why this leap matters:** Probabilistic models let us *reason about uncertainty* and *extend to new documents*. Three milestones:

| Model | One‑Line Pitch | Strength | Weakness |
| --- | --- | --- | --- |
| **Mixture of Unigrams** | Each doc picks *one* topic. | Simple maths. | Unrealistic for mixed‑topic docs. |
| **pLSI** | Each word picks a topic; docs are mixtures. | Handles multi‑topic docs. | No prior → can’t score unseen docs. |
| **LDA** | Adds a Dirichlet prior over topic mixtures. | Full generative story; handles new docs. | Needs approximate inference.|

---

## 4. LDA’s Generative Story ― Step by Step

**Connection:** We’re zooming into the winning model from §3.

1. **Pick document proportions**  
   *θ* ∼ Dirichlet(α)   ← `α` tunes how many topics a doc tends to mix.
2. **For each word slot `n` in the doc**  
   a. Draw a **topic label** *zₙ* ∼ Multinomial(θ).  
   b. Draw the **word** *wₙ* from that topic’s distribution β<sub>zₙ</sub>.
3. **Exchangeability assumption:** order of words doesn’t matter; only counts.

⮕ *After the fact*, we only observe words; θ and z’s are *hidden*.

---

## 5. How We *Actually* Learn an LDA Model

**Bridge:** The generative story is nice, but how do we go from data to learnt topics?

| Concept | Plain English | Used In |
| --- | --- | --- |
| **Variational Inference** | Replace nasty posterior with a simpler one, optimize. | Gensim, Spark‑MLlib. |
| **Gibbs Sampling** | Monte‑Carlo: repeatedly resample each zₙ given others. | MALLET. |
| **γ (gamma)** | Doc‑level Dirichlet parameters ≈ topic weights. | Features for classifiers. |
| **φ (phi)** | Probabilities of each topic for each word token. | Internal; rarely stored. |
| **Perplexity** | Lower = better predictive power on held‑out text. | Model selection. |
| **Topic Coherence** | Human‑proxy metric: do top words *fit together*? | `gensim.models.CoherenceModel`.

> **Rule of thumb:** Optimize coherence first; perplexity can mislead if interpretability matters.

---

## 6. A Python Pipeline You Can Copy‑Paste

**Why this section now?** You’ve met the theory; here’s how to run it end‑to‑end.

```python
import gensim
from gensim.utils import simple_preprocess
from gensim.corpora import Dictionary
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer

# 1️⃣  Pre‑process
lemmatizer = WordNetLemmatizer()
stop_set = set(stopwords.words("english"))

def clean(doc):
    tokens = [lemmatizer.lemmatize(w) for w in simple_preprocess(doc) if w not in stop_set]
    return tokens

docs = [clean(d) for d in raw_documents]

# 2️⃣  Build dictionary & BoW corpus
id2word = Dictionary(docs)
corpus   = [id2word.doc2bow(d) for d in docs]

# 3️⃣  Train LDA
lda = gensim.models.LdaModel(corpus=corpus,
                             id2word=id2word,
                             num_topics=10,
                             passes=10,
                             alpha="auto",
                             eta="auto")

# 4️⃣  Inspect
for idx, topic in lda.show_topics(formatted=False):
    print("Topic", idx, "→", [w for w, _ in topic])
```

*Visualization tip:* `pyLDAvis.gensim_models.prepare(lda, corpus, id2word)` opens an interactive topic explorer.

---

## 7. What LDA Is Good — and Not So Good — For

| ✅ Shines At | 🚫 Falls Short When |
| --- | --- |
| Corpus exploration / dashboards. | You need *exact* phrase structures. |
| Feature reduction before classification. | The corpus is very small (data‑hungry). |
| Soft clustering of users/items (e.g., recsys). | You need real‑time training (slow). |
| Handling mixed‑theme documents. | Topics must be fully interpretable by laypeople. |

---

## 8. Clustering Refresher — Hard vs Soft

* Hard clustering (**k‑means**): each doc → one cluster; minimizes residual sum of squares (RSS).
* Soft clustering (**Gaussian/Bernoulli Mixture, LDA**): a doc has fractional membership across clusters/topics; learns via EM or Gibbs.

> **Take‑away:** LDA is basically *soft clustering in word space*.

---

## 9. How to Evaluate Your Topics

| Metric | Measures | Watch‑Out |
| --- | --- | --- |
| **Purity** | % of docs whose majority class matches their cluster. | Inflated by many tiny clusters. |
| **Rand Index** | Pairwise agreement. | Sensitive to imbalance. |
| **F‑measure** | Harmonic mean of P & R. | Needs class weights. |
| **NMI** | Mutual information between clusters & labels. | 0 – 1 scale. |
| **V‑measure** | Harmonic mean of Homogeneity & Completeness. | Robust to cluster count. |
| **Topic Coherence** | Semantic relatedness of top words. | Needs a reference corpus (usually). |

---

## 10. Extensions & Practical Gotchas

* **Correlated LDA** – lets topics co‑vary (e.g., “sports” & “fitness”).  
* **Dynamic LDA** – adds a time axis to track topic drift.  
* **Hierarchical LDA** – discovers topic trees (broad → narrow).  
* **Choosing *K*** – grid‑search over coherence scores; balance interpretability.  
* **Beyond Bag‑of‑Words** – inject n‑grams, embeddings, or syntax for richer topics.  
* **Interpretability Hacks** – name topics via top‑word ± point‑wise mutual‑information (PMI).

---

## 11. Glossary — 20‑Second Recap

| Term | Plain‑English Meaning |
| --- | --- |
| **Topic** | A probability distribution over words. |
| **Dirichlet** | A distribution over distributions (vectors that sum to 1). |
| **Multinomial** | Multi‑sided dice for discrete outcomes. |
| **θ (theta)** | Vector of topic weights for a document. |
| **β (beta)** | Matrix of word probabilities per topic. |
| **γ (gamma)** | Variational estimate of θ. |
| **φ (phi)** | Per‑word topic assignment probabilities. |
| **Exchangeability** | We ignore word order; only counts matter. |
| **Soft clustering** | Items can belong to multiple groups simultaneously. |

---

### 🎯 30‑Second Summary

> **LDA = Soft, probabilistic clustering of words + documents.**  
> It gives you *interpretable*, low‑dimensional features (θ) that power search, classification, and insight dashboards.  
> Tweak preprocessing & `K`, trust coherence over perplexity, and visualize early.

---

*These notes were rebuilt from the original draft for clarity and teaching flow.*  © 2025
