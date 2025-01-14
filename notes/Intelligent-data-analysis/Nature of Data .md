# Nature of Data: Introduction to Intelligent Data Analysis

[Listen to the AI-generated overview podcast on this lecture!](https://notebooklm.google.com/notebook/414c1910-4899-4f7e-b8fe-b1f280274d39/audio)

---

## 1. Understanding the Nature of Data

<img src="../../images/nature_of_data.png" alt="Nature of Data" width="800">

Data representations—signals, images, videos, or text—are fundamentally equivalent from a mathematical perspective:
- **Points in Space**: All data can be treated as points in a structured set, regardless of format.
- **Human-Defined Semantics**: Meaning is assigned by humans, while format primarily affects ease of manipulation.
- **Representation Matters**: Formats impose no mathematical limitations but impact convenience.

---

## 2. Data as Points in Space

### 2.1 Sets and Elements
A **set** is a finite or infinite collection of distinct objects (elements), where order does not matter. Data in any format (e.g., text, images, videos) can be represented as sets.

### 2.2 Manipulating Sets
- Knowledge is extracted by applying operations to sets.
- **Relations as Actions**: Relations describe how elements interact:
  - Example: "2 plus 2 equals 4" or "The dog is green."

### 2.3 Cartesian Product
- **Definition**: Combines multiple sets into one by creating ordered tuples:
  - \( A = \{1, 2\}, B = \{x, y\} \)
  - \( A \times B = \{(1, x), (1, y), (2, x), (2, y)\} \)
- **Implications**:
  - Enables multivariate data analysis by folding dimensions into one.
  - Multimodal data fusion is essentially higher-level Cartesian product usage.

<img src="https://i.ytimg.com/vi/l4j4XgVbuxc/hq720.jpg" alt="Cartesian Example" width="800">

### 2.4 Types of Relations
Relations (subsets of Cartesian products) can have constraints:
1. **Functions**: One element in the domain maps to at most one in the range.
2. **Orders**: Reflexive, transitive, and anti-symmetric.
3. **Equivalences**: Reflexive, transitive, and symmetric.
4. **Functors**: Domains that are functions.
5. **Operations**: Relations applied to set powers.

---

### 2.5 Representations of Relations
Relations can be expressed as:
- Explicit sets, adjacency tables, graphs, tables of tuples, or graphical depictions.

<img src="https://cdn1.byjus.com/wp-content/uploads/2020/10/Relations-and-Functions-1.png" alt="Relations Visualization" width="800">

### 2.6 From Sets to Spaces
- A **space** is a set equipped with operations (e.g., vector spaces).
- Data elements are treated as **points** in these spaces, enabling structured operations.

---

## 3. Fundamentals of Data Analysis

### 3.1 Processing vs. Analysis
1. **Processing**: Internal operations enhancing data (e.g., filtering).
2. **Analysis**: External operations extracting insights (e.g., Fourier decomposition).

### 3.2 Pipelines
Chains of processing and analysis steps applied sequentially:
- **Key Considerations**:
  - **Order Matters**: Operations are rarely commutative.
  - **Overprocessing**: Too many transformations can distort insights.

<img src="../../images/pipeline.png" alt="Pipeline Example" width="800">

---

## 4. Properties and Measurements

### 4.1 Properties, Characteristics, and Measurements
- **Characteristic**: A quantity or quality of an object.
- **Measurement**: Assigns a label to a characteristic (numeric or otherwise).
- **Property**: A measurable characteristic connecting data and labels.

**Key Insight**: Properties are relationships between characteristics of a space and assigned labels.

---

### 4.2 Intrinsic and Extrinsic Properties
#### Intrinsic Properties:
- **Cardinality**: The size of a set.
- **Density**: Discrete (points) vs. dense (continuous).
- **Dimensionality**: Number of basis elements.
- **Countability**: Finite, countably infinite, or uncountable.

#### Extrinsic Properties:
- **Differentiability**: Smoothness of data.
- **Continuity**: Presence or absence of gaps.
- **Separability**: Ability to distinguish elements.

---

### 4.3 Measurement Systems and Scales
#### Components:
1. **Type of Object**: Qualitative or quantitative.
2. **Unit**: Standard for comparison (e.g., kilograms).
3. **Magnitude**: Multiplicity of the unit.
4. **Uncertainty**: Bias or stochastic variability.

#### Properties:
- **Identity**: Objects in the same class have the same label.
- **Magnitude**: Establishes ranking.
- **Interval**: Consistent differences; invariant under addition.
- **Ratio**: Absolute zero; invariant under scaling.

---

### 4.4 Measurement Scales
- **Nominal**: Categorization only.
- **Ordinal**: Ranking or order.
- **Interval**: Allows addition and subtraction but lacks true zero.
- **Ratio**: All arithmetic operations valid with an absolute zero.

---

## 5. Variables and Descriptive Statistics

### 5.1 Variables
- **Definition**: Functional relationships between data elements.
- **Types**:
  - **Nominal**: Categories (e.g., colors).
  - **Ordinal**: Ordered categories (e.g., rankings).
  - **Interval**: Quantitative without a true zero.
  - **Ratio**: Quantitative with a true zero.

---

### 5.2 Descriptive Statistics
- **Central Tendency**: Mean, median, mode.
- **Dispersion**: Variance, standard deviation.
- **Estimators**: Sample-based statistics for population values.

<img src="INSERT_IMAGE_LINK_HERE" alt="Descriptive Statistics" width="800">

---

## 6. Signals and Noise

### 6.1 Signals
- Structured relationships over a lattice.
- The **order** of observations impacts interpretation.

---

### 6.2 Noise and Descriptors
- **Key Metrics**:
  - **Signal-to-Noise Ratio (SNR)**: Signal power vs. noise power.
  - **Coefficient of Variation (CV)**: Dispersion to mean ratio.
- **Types of Noise**:
  - Coloured Noise: White, pink, red.
  - Distribution-Based Noise: Gaussian, Poisson.

<img src="INSERT_IMAGE_LINK_HERE" alt="Noise Examples" width="800">
