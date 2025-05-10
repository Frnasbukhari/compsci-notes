# Unsupervised Learning & Topic Modeling – Consolidated Notes

## Table of Contents
1. [Why Unsupervised?](#why-unsupervised)  
2. [Hard Clustering with K‑means](#hard-clustering-with-k-means)  
   • Algorithm  
   • Math Corner  
   • Choosing K  
3. [External Cluster Evaluation](#external-cluster-evaluation)  
4. [From Counts to Topics — Latent Dirichlet Allocation](#from-counts-to-topics--latent-dirichlet-allocation)  
5. [Inference & Hyperparameter Tuning](#inference--hyperparameter-tuning)  
6. [Minimal Python Pipeline](#minimal-python-pipeline)  
7. [Tool Selection Quick Guide](#tool-selection-quick-guide)  
8. [Common Pitfalls & Remedies](#common-pitfalls--remedies)  
9. [20‑Second Takeaway](#20-second-takeaway)

---

<a name="why-unsupervised"></a>
## 1. Why Unsupervised?
When labels are scarce or subjective, **unsupervised learning** lets the **data distribution itself** reveal structure.

* **Hard clustering** (e.g., K‑means) – each sample belongs to exactly one cluster.  
* **Soft / model‑based clustering** (e.g., Gaussian Mixtures, LDA) – samples share fractional membership across latent groups.

---

<a name="hard-clustering-with-k-means"></a>
## 2. Hard Clustering with K‑means

### 2.1 Algorithm
| Step | Action |
|------|--------|
| 1️⃣ | **Initialise**: choose *K* random centroids. |
| 2️⃣ | **Assign**: allocate each point to its nearest centroid. |
| 3️⃣ | **Update**: move each centroid to the mean of its assigned points. |
| 4️⃣ | **Repeat** steps 2–3 until convergence (assignments stop or centroids stabilise). |

### 2.2 Math Corner
*Centroid*  

\[
\mu(\omega) = \frac{1}{|\omega|} \sum_{x \in \omega} x
\]

*Residual Sum of Squares*  

\[
RSS = \sum_{k=1}^{K} \sum_{x \in \omega_k} \lVert x - \mu(\omega_k) \rVert^2
\]

### 2.3 Choosing K
* **Elbow / knee on RSS(K)** – plot RSS vs *K*; pick the first sharp bend.  
* **Silhouette score**  

\[
s = \frac{b - a}{\max(a, b)} \quad (-1 \le s \le 1)
\]  

where *a* = average distance to points in the **same** cluster, *b* = average distance to the **nearest other** cluster.

---

<a name="external-cluster-evaluation"></a>
## 3. External Cluster Evaluation

| Metric | Intuition | Formula (summary) |
|--------|-----------|-------------------|
| **Purity** | Majority label per cluster | Increases with many tiny clusters |
| **Homogeneity (h)** | “Each cluster contains one class” | \(h = 1 - \tfrac{H(C\mid K)}{H(C)}\) |
| **Completeness (c)** | “Members of a class end up in the same cluster” | \(c = 1 - \tfrac{H(K\mid C)}{H(K)}\) |
| **V‑measure** | Harmonic of *h* & *c* | \(V_\beta = \tfrac{(1+\beta)hc}{\beta h + c}\) |

---

<a name="from-counts-to-topics--latent-dirichlet-allocation"></a>
## 4. From Counts to Topics — Latent Dirichlet Allocation (LDA)

### 4.1 Generative Story
1. Draw **topic mixture** for the document: \(\theta \sim \text{Dir}(\alpha)\).  
2. For each word *n* (total *N*):  
   a. Pick topic \(z_n \sim \text{Mult}(\theta)\).  
   b. Emit word \(w_n \sim p(w\mid z_n, \beta)\).

The Dirichlet prior allows reuse of topics within a document and scoring of unseen docs.

### 4.2 Why LDA Beats Pure Clustering
* Soft, interpretable “topic–word” distributions.  
* Documents receive **fingerprints** (topic proportions) rather than hard labels.  
* Extensible (Correlated, Dynamic, Hierarchical LDA).

---

<a name="inference--hyperparameter-tuning"></a>
## 5. Inference & Hyperparameter Tuning

| Goal | Common Approach | Notes |
|------|-----------------|-------|
| Estimate hidden vars | **Variational EM** | Fast, deterministic, default in *gensim*. |
| Better accuracy | **Collapsed Gibbs sampling** | Slower but simple math. |
| Optimise \(\alpha, \eta\) | **Empirical Bayes** | Re‑estimate every few EM iterations. |

---

<a name="minimal-python-pipeline"></a>
## 6. Minimal Python Pipeline

```python
# 0. pip install gensim pyldavis
docs = [clean(t) for t in raw_texts]

# 1. Bag‑of‑Words prep
id2word = Dictionary(docs)
corpus = [id2word.doc2bow(d) for d in docs]

# 2. Search K via topic coherence
for k in range(5, 21):
    lda = LdaModel(corpus, id2word, num_topics=k, passes=10, alpha='auto')
    c_v = lda.top_topics(corpus=corpus, coherence='c_v')[0][1]
    print(k, lda.log_perplexity(corpus), c_v)
```

*Visualise topics:*  

```python
import pyLDAvis.gensim_models as gensimvis
pyldavis_html = gensimvis.prepare(lda, corpus, id2word)
```

---

<a name="tool-selection-quick-guide"></a>
## 7. Tool Selection Quick Guide

| Use‑case | Pick |
|----------|------|
| One dominant theme per item | **K‑means** (fast, scalable) |
| Mixed themes, dimensionality reduction, recommender latent factors | **LDA** |
| Non‑spherical clusters | EM‑Gaussian, Spectral, DBSCAN |

---

<a name="common-pitfalls--remedies"></a>
## 8. Common Pitfalls & Remedies

| Pitfall | Symptom | Remedy |
|---------|---------|--------|
| Too many topics | Redundant / incoherent topics | Tune *K* by coherence; merge similar topics. |
| Rare words dominate | Singleton, meaningless topics | Trim low & high‑frequency tokens; apply TF‑IDF. |
| Bag‑of‑Words limits | Missing multi‑word phrases | Add n‑grams or use phrase‑aware LDA. |
| Slow convergence | Training lags on large corpora | Use online/streaming LDA, adjust `chunksize`. |

---

<a name="20-second-takeaway"></a>
## 9. 20‑Second Takeaway
**K‑means** gives crisp buckets; **LDA** gives soft thematic fingerprints.  
Pick *K* with elbow/coherence, measure quality with **homogeneity + completeness**, and visualise topics early to keep both the model and your audience sane.

---

*Prepared May 10, 2025*
