# Nature of Data: Introduction to Intelligent Data Analysis

## The Nature of Data
- **Universality of Data Representations**: Data formats (e.g., signal, image, video, text) are equivalent as mathematical points in space.
- **Key Insight**: Semantics are added by humans; mathematical representation is independent of meaning.
- **Convenience vs. Limitations**: The format affects ease of manipulation but does not impose mathematical constraints.

---

## From Data to Points in Space
### Sets and Relations
- **Sets**: Collections of distinct objects without inherent order.
- **Relations**: Subsets of Cartesian products, serving as the "verbs" or actions in mathematical operations.

### Cartesian Product
- Combines multiple sets into a single set of ordered tuples.
- Supports multivariate analysis by folding sets into one.

### Key Concepts
- **Spaces**: Sets equipped with operations (e.g., addition, multiplication).
- **Points in Space**: All data can be viewed as points within a space.

---

## What is Data Analysis?
### Processing vs. Analysis
- **Processing**: Internal operations that enhance data (e.g., filtering).
- **Analysis**: External operations extracting summaries (e.g., Fourier analysis).
- **Pipelines**: Chains of processing/analysis steps combined into a single operation for convenience.

### Important Considerations
- Order of operations matters.
- Overprocessing can distort insights; just because an operation is possible doesn't mean it should be used.

---

## Properties and Measurements
### Intrinsic Properties
- **Cardinality**: Size of the set.
- **Density**: Discrete vs. continuous.
- **Dimensionality**: Number of basis elements in a vector space.
- **Countability**: Countable vs. uncountable sets.

### Extrinsic Properties
- **Differentiability**: Smoothness.
- **Continuity**: Presence of abrupt changes.
- **Separability**: Ability to distinguish elements.

### Measurement Systems
- Define rules for assigning labels to data characteristics.
- Scales:
  - **Identity**: Classifies objects.
  - **Magnitude**: Establishes order.
  - **Interval**: Measures consistent differences.
  - **Ratio**: Includes absolute zero for proportional comparisons.

---

## From Data to Variables
- **Variables as Relations**: Functions that describe associations between sets.
- **Types of Variables**:
  - **Nominal**: Categories (e.g., colors).
  - **Ordinal**: Ordered categories (e.g., rankings).
  - **Interval**: Quantitative data without a true zero (e.g., temperature in Celsius).
  - **Ratio**: Quantitative data with a true zero (e.g., weight).

### Descriptive Statistics
- **Common Measures**:
  - Central tendency: Mean, median, mode.
  - Dispersion: Variance, standard deviation.
- **Estimators**: Sample-based statistics (e.g., average as an estimator of the mean).

---

## From Variables to Signals
### Signals
- Defined as structured relations of observations over a lattice (ordered set).
- Importance of order and position of observations.

### Statistical Signal Descriptors
- **Key Metrics**:
  - Signal-to-Noise Ratio (SNR): Ratio of signal power to noise power.
  - Coefficient of Variation (CV): Ratio of signal dispersion to mean.
- **Noise Types**:
  - White, pink, red (coloured noises).
  - Gaussian, Poisson (distribution-based noises).

---

## Final Remarks
- **Assumptions in Data Analysis**:
  - Assumptions should be made cautiously.
  - Stick to mathematical rigor when in doubt.
- **Mathematical Correctness**:
  - Mathematics is always correct; errors arise from incorrect assumptions or interpretations.
