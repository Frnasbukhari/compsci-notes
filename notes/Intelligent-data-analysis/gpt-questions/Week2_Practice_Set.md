# Week 2 Practice Set – Coordinate Systems & Classic Decompositions (Concept‑level)

These questions focus on **ideas**, not heavy calculations.  Use them to check your qualitative grasp of bases, GLM and the “big‑picture” purpose of Fourier, wavelets and PCA.

---

## Practice questions  

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

5. **Conceptual basis change**  
   Describe how a *change of basis* turns a time‑domain audio clip into a set of frequency amplitudes, and why this is still “the same signal”.

6. **Fourier vs. Wavelet (big picture)**  
   Without equations, compare the key *strength* and *limitation* of Fourier analysis relative to wavelets for analysing a drum beat that has sharp attacks and resonant tones.

7. **Coordinate‑space thinking**  
   Explain how viewing regression lines as *points* in a “space of lines” can make certain processing tasks (e.g.\ regularisation) conceptually clearer.

---

## Brief answers  

1.
a) Dimension =3 .

b) B is a basis; its vectors are independent and span the whole space, so coordinates $(x,y,z)$ are unique.  

2. Fourier packs most image energy into a few low‑frequency coefficients → fewer numbers to save.  

3. $\text{Price}=\beta_1 \times \text{Area}+\beta_0$.  

4. Fourier → dominant frequencies; Wavelet → denoising spikes; PCA → dimension reduction; GLM → trend estimation.

5. A change of basis re-expresses a time-domain audio signal using sine waves (frequencies) instead of time points. The Fourier transform does this, showing how much each frequency contributes. It’s still the same signal—just seen from a different angle, like changing from time to pitch.

6. Fourier is great for identifying steady tones but poor at timing sharp events. Wavelets capture both when and what happens, so they handle sharp drum hits better. Trade-off: Fourier gives exact pitch, wavelets give better timing.

7. Seeing regression lines as points in a space helps us control their complexity. Regularisation becomes moving toward simpler areas of that space—more intuitive and visual.
