# Week 1 Practice Set – Nature of Data

This practice set mirrors the tone, depth and notation style of the Week 1 lecture materials.

---

## Practice questions  
*(Mini ≈ 10 min each  •  Extended ≈ 25‑30 min each)*

### Mini questions  

1. **Sets & cardinality**  
   Let $A=\{\texttt{red},\texttt{blue},\texttt{green}\}$.  
   1. State the cardinality $|A|$.  
   2. Explain (one sentence) why the tuple $(\texttt{green},\texttt{red})$ is *not* an element of $A$.  

2. **Cartesian product**  
   Given $B=\{1,2\}$ and $C=\{x,y,z\}$, list every element of $B \times C$.

3. **Relation spotting**  
   For each relation on $\mathbb N$ decide whether it is an **order**, an **equivalence**, or **neither**.  
   a) $xRy \iff x<y$ b) $xRy \iff x \equiv y~(\text{mod }5)$.

4. **Variable types & admissible statistics**  
   Classify each variable and name **one statistic** that is valid for it.  
   a) Shirt size \{S,M,L,XL\}.  
   b) Temperature in °C.  
   c) Annual income in £.  

5. **Intrinsic vs. extrinsic**  
   Put each property in the correct bucket. Choose from {cardinality, differentiability, countability, continuity}.  

6. **Frequency table sketch**  
   You observe the values `[2,2,3,5,2,5,3]`. Draw a two‑column frequency table (value / count).

7. **Noise characterisation**  
   A microphone captures $x(t)=f(t)+\varepsilon(t)$ where $\varepsilon(t)$ is *white* noise.  
   1. State one defining spectral property of white noise.  

8. **SNR quick check**  
   A signal segment has sample mean $\mu=0.8\,\text{V}$ and (biased) standard deviation $\sigma=0.2\,\text{V}$.  
   Compute an estimator of the SNR using $\mathrm{SNR}\approx \mu/\sigma$.

---

### Extended questions  

9. **Descriptive‑statistics workout**  
   Dataset: $D=[4,7,7,8,10,12,13,13,13,18]$.  
   1. Compute **mean, median, mode, variance (biased), SD**.  
   2. Draw a histogram with sensible binning and comment on skew.  
   3. Give the coefficient of variation (CV) and interpret its magnitude.  

10. **From sets to spaces**  
    Consider the grayscale image matrix  

    ```text
    I = [[  0, 128],
         [255, 128]]
    ```  

    1. Treating each pixel as a point in $\mathbb R$, give the set representation of \(I\).  
    2. Specify one **operation** that turns this set into a *space* suitable for linear filtering.  
    3. Explain in ≤100 words why “image” vs “signal” is semantically irrelevant for this operation.

11. **Measurement‑scale design**  
    You are measuring *perceived softness* of fabrics on a 1–7 Likert scale.  
    1. Identify the measurement scale.  
    2. A colleague wants to average the scores and compute SD. Discuss whether each is permissible and justify.  

12. **Over‑processing scenario**  
    A student applies the pipeline  

    ```
    raw EEG → high‑pass 1 Hz → ICA artefact removal → adaptive notch → 30 Hz low‑pass
    ```  

    to look for slow cortical potentials (< 0.5 Hz).  
    1. Point out the *specific* step that risks eliminating the desired signal.  

---

## Solutions  

### Mini  

1. **Answer**  
   a) $|A| = 3$.  
   b) $A$ is *unordered* and its elements are singletons, not ordered pairs.

2. **Answer**  
   $B\times C = \{(1,x),(1,y),(1,z),(2,x),(2,y),(2,z)\}$.

3. **Answer**  
   a) Order (strict). b) Equivalence (reflexive, symmetric, transitive).

4. **Answer**  
   a) **Ordinal** – median is valid.  
   b) **Interval** – mean is valid.  
   c) **Ratio** – coefficient of variation is valid.

5. **Answer**  
   *Intrinsic*: cardinality, countability. *Extrinsic*: differentiability, continuity.

6. **Answer**

    | value | count |
    |-------|-------|
    | 2     | 3     |
    | 3     | 2     |
    | 5     | 2     |

7. **Answer**  
   1) Flat power spectral density across all frequencies.  

8. **Answer**  
   $\text{SNR} \approx 0.8 / 0.2 = 4$.

---

### Extended  

9. **Answer**

   *Mean*: 10.5  
   *Median*: 11  
   *Mode*: 13  

   *Variance* (biased): $s^{2}=\frac{\sum(x_i-\mu)^2}{n}=20.45$

   *SD*: $s \approx 4.52$  

   *Histogram*: three bins 0‑6, 6‑12, 12‑18 → unimodal, slight right skew.  

   *CV*: $4.52/10.5 \approx 0.43$ → moderate dispersion.

10. **Answer**

      1. $I=\{(0,0,0),(0,1,128),(1,0,255),(1,1,128)\}$.  
      2. Define pixel‑wise addition and scalar multiplication (vector space $\mathbb R^{4}$).  
      3. Filtering is a linear operator on that space; the data’s label (“image” vs “signal”) does not affect the algebraic action.

11. **Answer**

      1. Ordinal.  
      2. Mean & SD assume equal intervals—invalid here. Use median or mode.

12. **Answer**

      1. The **1 Hz high‑pass** filter.  
