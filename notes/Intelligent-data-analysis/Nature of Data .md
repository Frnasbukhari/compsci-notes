# Nature of Data: Introduction to Intelligent Data Analysis

[Listen to the AI generated overview podcast on this lecture!](https://notebooklm.google.com/notebook/414c1910-4899-4f7e-b8fe-b1f280274d39/audio)


## 1. Understanding the Nature of Data

<img src="../../images/nature_of_data.png" alt="Nature of Data" width="800">

Data representations, whether signals, images, videos, or text, are fundamentally equivalent from a mathematical perspective. Key insights include:
- **Points in Space**: All data can be treated as points in a structured set, regardless of its format.
- **Human-Defined Semantics**: The meaning of data is assigned by humans, while the format primarily affects ease of manipulation, not mathematical properties.
- **Representation Matters**: While the format does not impose mathematical limitations, it impacts the convenience of data manipulation.

---

## 2. Data as Points in Space
Data can be understood and analyzed through fundamental mathematical constructs.

### Sets and Elements
- **Definition**: A set is a finite or infinite collection of distinct objects, called elements or members, where order does not matter.
- **Key Point**: Data in any format (e.g., text, images, videos) can be represented as sets.

### Manipulating Sets
- **Operations on Sets**: Knowledge is extracted by applying operations to sets.
- **Relations as Actions**: Relations describe how elements in sets interact. For example:
  - "2 plus 2 equals 4" is a relation.
  - "The dog is green" is another relation.

### Cartesian Product
- **Definition**: Combines multiple sets into one by creating ordered tuples. For example:
  - \( A = \{1, 2\}, B = \{x, y\} \)
  - \( A x B = \{(1, x), (1, y), (2, x), (2, y)\} \).
- **Implications**:
  - Multivariate data analysis often uses Cartesian products to combine dimensions into one.
  - Complex data structures like multimodal data fusion leverage Cartesian products at higher abstraction levels.

<img src="https://i.ytimg.com/vi/l4j4XgVbuxc/hq720.jpg?sqp=-oaymwEhCK4FEIIDSFryq4qpAxMIARUAAAAAGAElAADIQj0AgKJD&rs=AOn4CLCXsi22xXVMFFoLOtBnczKHoIYX2Q" alt="Cartesian" width="800">

---

### Types of Relations
Relations, as subsets of Cartesian products, can have specific constraints:
1. **Functions**: Each element in the domain maps to at most one image (e.g., variables).
2. **Orders**: Relations that are reflexive, transitive, and anti-symmetric.
3. **Equivalences**: Relations that are reflexive, transitive, and symmetric.
4. **Functors**: Relations where domains are themselves functions.
5. **Operations**: Relations applied to powers of a set.

### Representations of Relations
Relations can be represented in various ways:
1. Explicit sets.
2. Adjacency tables.
3. Graphs.
4. Tables of tuples.
5. Graphical depictions.

<img src="https://cdn1.byjus.com/wp-content/uploads/2020/10/Relations-and-Functions-1.png" alt="Relations" width="800">

### From Sets to Spaces
- **Spaces**: A set becomes a space when operations are defined on it (e.g., vector spaces, groups, rings).
- **Points in Spaces**: Data elements can be treated as points in mathematical spaces, enabling structured operations.

---

## 3. Fundamentals of Data Analysis
Data analysis can be broken into two key activities:
1. **Processing**: Internal operations that enhance input data (e.g., filtering).
2. **Analysis**: External operations that extract summary statistics or insights (e.g., Fourier analysis).

### Pipelines
- **Definition**: Chains of processing and analysis steps applied sequentially to data.
- **Key Considerations**:
  - **Order Matters**: Most operations are not commutative.
  - **Overprocessing**: Applying excessive operations can distort insights.

<img src="../../images/pipeline.png" alt="Pipeline" width="800">

---

## 4. Properties and Measurements
Understanding the properties of data and how they are measured is essential in selecting the right analysis techniques. Data properties can be classified as **intrinsic** or **extrinsic**, while measurements involve assigning labels to characteristics.

### Properties, Characteristics, and Measurements
1. **Characteristic**: A quantity or quality of an object that can be observed or analyzed.
2. **Measurement**: The assignment of a label to a characteristic of an object, often to enable comparisons.
   - This involves defining a **functional relation** between elements of a set and a set of labels.
   - Labels may or may not be numeric.
3. **Property**: A measurable characteristic, representing the relationship between a characteristic and its label.

**Key Insight**: Properties are relations between the characteristics of a space and the assigned labels.

### Intrinsic and Extrinsic Properties
#### Intrinsic Properties
Intrinsic properties are inherent to the data and do not depend on external factors. Key intrinsic properties include:
- **Cardinality**: The size of a set, which can be finite or infinite.
- **Density**: Determines whether the data is discrete (individual points) or dense (continuous).
- **Dimensionality**: Refers to the number of basis elements in a space. 
  - *Implicit Dimensionality*: Cardinality of the basis for the space.
  - *Explicit Dimensionality*: May differ from implicit dimensionality in certain spaces.
- **Countability**: Defines whether the set is countable (finite or countably infinite) or uncountable (e.g., real numbers).

#### Extrinsic Properties
Extrinsic properties depend on the environment or context of the data. Examples include:
- **Differentiability**: Indicates whether the data is smooth or has abrupt changes.
- **Continuity**: Reflects the presence or absence of gaps in the data.
- **Separability**: Related to countability and whether elements in a space can be distinctly identified.

### Measurement Systems and Scales
Measurement involves assigning labels to the characteristics of data. This process defines a **functional relationship** between elements in a set and a set of labels.

#### Components of Measurement Systems
- **Type of Object**: The nature of the data being measured (e.g., qualitative or quantitative).
- **Unit of Measurement**: The standard or constant used for comparison (e.g., kilograms, seconds).
- **Magnitude**: The value or multiplicity of the unit.
- **Uncertainty**: Represents biases, variability, or deterministic/stochastic differences in measurement.

#### Properties of Measurement Systems
Measurement systems are characterized by the following properties:
1. **Identity**: Ensures that the same label is used for objects in the same category or class.
   - *Example*: Labeling cars as "Sedan" or "SUV."
2. **Magnitude or Order**: Establishes a ranking or order among objects.
   - *Example*: Speeds labeled as "Slow (1)" and "Fast (2)," where slow precedes fast.
3. **Interval**: Labels represent consistent differences and are invariant to addition.
   - *Example*: Temperatures in Celsius, where the difference between 10°C and 20°C is the same as between 30°C and 40°C.
4. **Ratio**: Incorporates an absolute zero point and labels are invariant to scaling.
   - *Example*: Weight measurements, where 0 kg represents no weight.

![Comparison of different measurement scales with examples.](INSERT_IMAGE_LINK_HERE)

### Measurement Scales and Their Operations
Measurement systems are further classified into scales, which define the permissible operations:
- **Nominal Scale**: Categorization only (e.g., colors).
- **Ordinal Scale**: Order or ranking (e.g., Likert scales: Agree, Neutral, Disagree).
- **Interval Scale**: Allows addition/subtraction but lacks a true zero (e.g., temperature in Celsius).
- **Ratio Scale**: Includes all arithmetic operations and an absolute zero (e.g., height, weight).

#### Examples of Valid Operations by Scale
| Scale        | Operations Allowed                    |
|--------------|---------------------------------------|
| Nominal      | Classification, counting.            |
| Ordinal      | Classification, ranking, comparisons.|
| Interval     | Add, subtract, measure differences.  |
| Ratio        | All arithmetic operations.           |

### Measuring Uncertainty and Reproducibility
- Measurements must be **reproducible** despite uncertainty.
- Uncertainty can arise from:
  - Bias: Systematic error in measurement.
  - Variability: Stochastic changes across observations.

### Practical Example of Measurement Scales
1. **Identity**:
   - *Example*: Assigning numeric labels to car types: 1 = Sedan, 2 = SUV.
2. **Magnitude**:
   - *Example*: Ranking speeds of cars: 1 = Slow, 2 = Medium, 3 = Fast.
3. **Interval**:
   - *Example*: Temperature in Celsius: Differences are meaningful, but 0°C doesn’t indicate the absence of temperature.
4. **Ratio**:
   - *Example*: Weight in kilograms: 0 kg represents no weight, and ratios (e.g., 4 kg is twice 2 kg) are meaningful.

### Summary
- Intrinsic properties provide the foundation for understanding data's nature.
- Extrinsic properties consider external factors affecting analysis.
- Measurement systems and scales define how data characteristics are quantified, labeled, and interpreted.
- Proper selection of scales and understanding uncertainty is crucial for reliable data analysis.

![Illustration summarizing intrinsic vs. extrinsic properties and scales.](INSERT_IMAGE_LINK_HERE)


---

## 5. Variables and Descriptive Statistics
### Variables
- **Definition**: Describe relationships between data elements.
- **Types**:
  - Nominal: Categories without order.
  - Ordinal: Ordered categories.
  - Interval: Quantitative without a true zero.
  - Ratio: Quantitative with a true zero.

### Descriptive Statistics
- **Central Tendency**: Mean, median, mode.
- **Dispersion**: Variance, standard deviation.
- **Estimators**: Sample-based calculations for population statistics.

![Graph of mean, median, and mode on a normal distribution.](INSERT_IMAGE_LINK_HERE)

---

## 6. Signals and Noise
### Signals
- **Definition**: Structured relationships of observations over a lattice.
- **Order Importance**: The sequence of observations can affect interpretation.

![Two signals with identical frequency distributions but different orders.](INSERT_IMAGE_LINK_HERE)

### Noise and Descriptors
- **Key Metrics**:
  - Signal-to-Noise Ratio (SNR): Ratio of signal power to noise power.
  - Coefficient of Variation (CV): Ratio of dispersion to mean.
- **Types of Noise**:
  - Coloured Noise: White, pink, red.
  - Distribution-Based Noise: Gaussian, Poisson.

![Visual examples of noise types (e.g., white noise, pink noise).](INSERT_IMAGE_LINK_HERE)
