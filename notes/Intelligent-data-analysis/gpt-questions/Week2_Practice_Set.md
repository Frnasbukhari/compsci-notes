# Week 2 Practice Set – Coordinate Systems & Classic Decompositions (Concept‑level)

These questions focus on **ideas**, not heavy calculations.  Use them to check your qualitative grasp of bases, GLM and the “big‑picture” purpose of Fourier, wavelets and PCA.

---

## Practice questions  
*(Mini ≈ 5–8 min each  •  Short Essay ≈ 15 min each)*

### Mini questions  

1. **Spot the dimension**  
   The set $B=\{(1,0,0),(0,1,0),(0,0,1)\}$ lives in $\mathbb R^3$.  
   1. What is the *dimension* of the space spanned by $B$?  
   2. Why can every vector in $\mathbb R^3$ be written uniquely with this $B$?

2. **Why change basis?**  
   Give *one* concrete reason why switching from the pixel basis of an image (each pixel is a coordinate) to a Fourier basis might be helpful for image compression.

3. **GLM in plain words**  
   Rewrite the statement “house price is a linear function of floor area” as a one‑line General Linear Model using symbols for slope and intercept.

4. **Technique‑to‑task match**  
   Match each method to the most *typical* task:  
   - Fourier series  
   - Wavelet transform  
   - PCA  
   - GLM  
   Tasks: {trend estimation, denoising localised spikes, finding dominant frequencies, reducing dimensions of survey responses}.

5. **Impulse intuition**  
   Explain in two sentences what the discrete delta $\delta[n-k]$ does when used inside a sum representing a signal.

---

### Short‑essay / discussion questions  

6. **Conceptual basis change**  
   Describe (≈ 120 words) how a *change of basis* turns a time‑domain audio clip into a set of frequency amplitudes, and why this is still “the same signal”.

7. **Fourier vs. Wavelet (big picture)**  
   Without equations, compare the key *strength* and *limitation* of Fourier analysis relative to wavelets for analysing a drum beat that has sharp attacks and resonant tones.

8. **Coordinate‑space thinking**  
   In your own words (≤ 100 words) explain how viewing regression lines as *points* in a “space of lines” can make certain processing tasks (e.g.\ regularisation) conceptually clearer.

---

## Brief answers  

1. a) Dimension =3 . b) B is a basis; its vectors are independent and span the whole space, so coordinates $(x,y,z)$ are unique.  

2. Fourier packs most image energy into a few low‑frequency coefficients → fewer numbers to save.  

3. $\text{Price}=\beta_1 \times \text{Area}+\beta_0$.  

4. Fourier → dominant frequencies; Wavelet → denoising spikes; PCA → dimension reduction; GLM → trend estimation.  

5. $\delta[n-k]$ is zero everywhere except $n=k$, so it “picks out” the $k$‑th sample’s amplitude inside a sum.  

6.–8. (Any coherent explanation earning the key ideas: same information in new coordinates; Fourier global vs. wavelet local; coefficient‑space view simplifies operations.)

---

*Use these prompts to solidify **concepts** before diving into computations in later weeks.*
