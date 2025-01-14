# Nature of Data: Introduction to Intelligent Data Analysis

## Table of Contents
1. [The Nature of Data](#the-nature-of-data)
2. [From Data to Points in Space](#from-data-to-points-in-space)
3. [What is Data Analysis?](#what-is-data-analysis)
4. [Properties and Measurements](#properties-and-measurements)
5. [From Data to Variables](#from-data-to-variables)
   - [Descriptive Statistics](#descriptive-statistics)
6. [From Variables to Signals](#from-variables-to-signals)
   - [Statistical Signal Descriptors](#statistical-signal-descriptors)
7. [Final Remarks](#final-remarks)

## 1. Understanding the Nature of Data
Data representations like signals, images, videos, and text are fundamentally equivalent from a mathematical perspective. They are:
- **Points in Space**: Regardless of format, all data can be treated as points in a structured set.
- **Human-Defined Semantics**: Meaning is assigned by humans; the format influences ease of manipulation but has no inherent mathematical limitations.

![Diagram showing various data formats (e.g., image, text, video) represented as points in a 3D space.](INSERT_IMAGE_LINK_HERE)

## 2. Data as Points in Space
### Sets and Relations
- **Sets**: Collections of distinct objects, unordered by nature.
- **Relations**: Define how elements in sets interact, represented as subsets of Cartesian products.

### Cartesian Product
- Combines multiple sets into a single set of ordered tuples.
- Enables analysis of multivariate data by folding sets into one.

### Spaces and Structures
- **Spaces**: Sets combined with operations like addition or multiplication.
- **Points in Space**: Any data can be represented as points, enabling structured operations.

![Visualization of Cartesian product and its relation to data fusion.](INSERT_IMAGE_LINK_HERE)

## 3. Fundamentals of Data Analysis
### Processing vs. Analysis
- **Processing**: Enhancing data through operations like filtering.
- **Analysis**: Extracting summaries or insights (e.g., Fourier decomposition).

### Pipelines
- Sequential or combined operations form pipelines (e.g., filtering followed by statistical analysis).
- **Order Matters**: The sequence of operations affects outcomes.

![Diagram of a simple data analysis pipeline.](INSERT_IMAGE_LINK_HERE)

## 4. Properties and Measurements
### Intrinsic and Extrinsic Properties
- **Intrinsic**: Characteristics inherent to the data.
  - Cardinality, density, dimensionality.
- **Extrinsic**: Properties influenced by external factors.
  - Differentiability, continuity, separability.

### Measurement Systems and Scales
- Rules for assigning labels to data characteristics.
- Measurement Scales:
  1. **Identity**: Classification.
  2. **Magnitude**: Establishes order.
  3. **Interval**: Measures consistent differences (e.g., temperature in Celsius).
  4. **Ratio**: Includes absolute zero (e.g., weight).

![Comparison of different measurement scales with examples.](INSERT_IMAGE_LINK_HERE)

## 5. Variables and Descriptive Statistics
### Variables
- Variables describe functional relationships between data elements.
- Types of Variables:
  - **Nominal**: Categories without order.
  - **Ordinal**: Ordered categories.
  - **Interval**: Quantitative without a true zero.
  - **Ratio**: Quantitative with a true zero.

### Descriptive Statistics
- Common Measures:
  - **Central Tendency**: Mean, median, mode.
  - **Dispersion**: Variance, standard deviation.
- **Estimators**: Sample-based calculations (e.g., sample mean as an estimator of population mean).

![Graph of mean, median, and mode on a normal distribution.](INSERT_IMAGE_LINK_HERE)

## 6. Signals and Noise
### Signals
- Structured relations of observations over a lattice (ordered set).
- Signal properties depend on both the data and their ordering.

![Two signals with identical frequency distributions but different orders.](INSERT_IMAGE_LINK_HERE)

### Statistical Signal Descriptors
- **Key Metrics**:
  - Signal-to-Noise Ratio (SNR): Ratio of signal power to noise power.
  - Coefficient of Variation (CV): Ratio of dispersion to mean.
- **Noise Types**:
  - Coloured Noise: White, pink, red.
  - Distribution-Based Noise: Gaussian, Poisson.

![Visual examples of noise types (e.g., white noise, pink noise).](INSERT_IMAGE_LINK_HERE)
