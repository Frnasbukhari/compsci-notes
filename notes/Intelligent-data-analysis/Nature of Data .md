# Nature of Data: Introduction to Intelligent Data Analysis

[Listen to the AI-generated overview podcast on this lecture!](https://notebooklm.google.com/notebook/414c1910-4899-4f7e-b8fe-b1f280274d39/audio)

---

## 1. Understanding the Nature of Data

<img src="../../images/nature_of_data.png" alt="Nature of Data" width="800">

Data comes in many forms—signals, images, videos, text, etc.—but from a mathematical perspective, all data can be represented as **points in space**. This abstraction enables us to apply consistent mathematical techniques across different data types.

### Key Insights:
- **Points in Space**: Regardless of format, all data can be treated as points in a structured set or space. For example, an image can be represented as a matrix of pixel values, and a video as a sequence of such matrices over time.
- **Human-Defined Semantics**: The meaning (semantics) of the data is determined by humans. For example, the same numeric data might represent temperature in Celsius, income in dollars, or votes in an election.
- **Representation Matters**: The way data is stored and manipulated (its representation) affects convenience but not its mathematical properties. Choosing the right representation is crucial for efficient analysis.

---

## 2. Data as Points in Space

### 2.1 Sets and Elements
A **set** is a collection of distinct objects, called elements. Sets are fundamental because they form the basis for organizing data:
- **Finite Sets**: Contain a limited number of elements (e.g., a set of colors: `{red, green, blue}`).
- **Infinite Sets**: Contain an unlimited number of elements (e.g., the set of all integers).

In data analysis, we can represent almost any type of data as a set:
- Text: A set of words in a document.
- Image: A set of pixel values arranged spatially.
- Video: A set of images (frames) ordered in time.

---

### 2.2 Manipulating Sets
Manipulating sets allows us to extract relationships and insights:
- **Operations**: Include union, intersection, and difference. For example, combining datasets is a union, while finding common entries is an intersection.
- **Relations**: Describe connections between elements. These are the "verbs" in mathematics:
  - Example: "2 plus 2 equals 4" relates numbers in a mathematical operation.
  - Example: "Alice owns a cat" relates a person and an animal in a logical sense.

---

### 2.3 Cartesian Product
The Cartesian product combines sets into a single set of ordered pairs (or tuples):
- **Definition**: If \( A = \{1, 2\} \) and \( B = \{x, y\} \), then:
  \[
  A x B = \{(1, x), (1, y), (2, x), (2, y)\}
  \]
- **Application**:
  - In multivariate data, a Cartesian product helps represent combinations of variables like height and weight.
  - In machine learning, feature spaces are often Cartesian products of multiple input dimensions.

<img src="https://i.ytimg.com/vi/l4j4XgVbuxc/hq720.jpg" alt="Cartesian Example" width="800">

---

### 2.4 Types of Relations

Relations are fundamental concepts in data analysis and mathematics, describing how elements of sets interact. These relations are subsets of Cartesian products and can have specific constraints. There are **five key types of relations**:

1. **Functions**:
   - **Definition**: A relation where each input (element from the domain) maps to **at most one output** (element from the range).
   - **Example**: \( f(x) = x^2 \), where every input \( x \) has exactly one output \( x^2 \).
   - **Application**: Functions are used in modeling relationships between variables, such as predicting house prices based on square footage.

   <img src="https://cdn1.byjus.com/wp-content/uploads/2021/06/Functions-and-Types-of-Functions-01.png" alt="Function" width="400">

2. **Orders**:
   - **Definition**: A relation that is **reflexive, transitive, and anti-symmetric**
   - **Application**: Orders are useful for sorting and ranking tasks, such as prioritizing items in a queue.

3. **Equivalences**:
   - **Definition**: A relation that is **reflexive, transitive, and symmetric**
   - **Application**: Equivalences are used to group data into **equivalence classes**, such as clustering items based on similarity.

4. **Functors**:
   - **Definition**: A higher-level relation where the domain and codomain themselves consist of functions or mappings. Functors preserve structure between spaces.
   - **Example**: Mapping functions from one vector space to another while preserving linearity.
   - **Application**: Common in fields like machine learning and graph theory, where transformations between spaces or datasets need to maintain relationships.

5. **Operations**:
   - **Definition**: A relation applied to powers of a set, often combining multiple elements into one.
   - **Example**: Addition (\( + \)) is an operation on the set of numbers, combining two numbers to produce a third (\( a + b = c \)).
   - **Application**: Operations form the foundation of algebraic structures like groups, rings, and fields, enabling arithmetic and matrix computations.


---

### 2.5 Representations of Relations
Relations can be visualized in multiple ways:
- **Graph**: Nodes and edges depict relationships.
- **Adjacency Matrix**: A table shows whether elements are related.
- **Tuples**: Explicitly list related pairs.
and more...

<img src="https://cdn1.byjus.com/wp-content/uploads/2020/10/Relations-and-Functions-1.png" alt="Relations" width="800">

These representations are key to data modeling in applications like social networks (graphs) or machine learning (feature matrices).

---

### 2.6 From Sets to Spaces
- **Spaces**: A space is a set where specific operations (e.g., addition, multiplication) are defined. For example:
  - A 2D plane is a space where points can be added or scaled.
  - A vector space supports advanced operations like projection and rotation.
- **Data as Points**: Data points in spaces allow us to compute distances, find clusters, or reduce dimensions.

---

## 3. Fundamentals of Data Analysis

### 3.1 Processing vs. Analysis
1. **Processing**:
   - Enhances or cleans data before analysis.
   - Example: Noise removal in a video or filtering missing values in a dataset.
2. **Analysis**:
   - Extracts summaries, patterns, or insights.
   - Example: Computing statistical metrics like averages or performing clustering.


### 3.2 Pipelines
A **pipeline** combines processing and analysis steps in sequence:
- Example: In text processing, a pipeline might involve tokenizing text, removing stop words, and applying sentiment analysis.
- **Key Rules**:
  - **Order Matters**: A step depends on the output of the previous one.
  - **Overprocessing Risks**: Excessive steps can remove useful data or distort results.

---

## 4. Properties of Sets

### 4.1 Key Definitions
- **Characteristic**: A trait or quality of an object (e.g., "red" is a characteristic of an apple).
- **Measurement**: Assigning labels to characteristics to enable comparison (e.g., height measured in centimeters).
- **Property**: A measurable characteristic (e.g., weight is a property of an object).

**Key Insight**: Properties connect data to their mathematical representation, forming the basis for analysis.

---

### 4.2 Intrinsic and Extrinsic Properties


#### 4.2.1 Intrinsic Properties
Intrinsic properties are built-in features of the data, independent of external context:
- **Cardinality**: How many elements are in a set.
  - Example: A set of colors like \{red, blue, green\} has a cardinality of 3.
- **Density**: Whether the data is discrete (individual points) or continuous (a smooth range).
  - Example: Whole numbers are discrete; real numbers are continuous.
- **Dimensionality**: The number of "axes" needed to describe the data.
  - Example: A 2D space requires length and width, while a 3D space also includes height.
- **Countability**: Whether you can list all elements in the set.
  - Example: The set of integers is countable, but the set of real numbers is uncountable.

#### 4.2.2 Extrinsic Properties
Extrinsic properties depend on **context or environment**:
- **Differentiability**: Whether the data changes smoothly.
  - Example: A curve is differentiable if it has no sharp edges.
- **Continuity**: Whether the data has gaps.
  - Example: A line with missing sections is not continuous.
- **Separability**: Whether you can distinguish groups in the data.
  - Example: Distinguishing cats and dogs in an image dataset depends on resolution and clarity.

While extrinsic properties seem tied to the data, their realization or perception depends on external factors like:
1. Measurement tools (e.g., sensor precision, noise levels).
2. Sampling processes (e.g., gaps from missing observations).
3. Context of analysis (e.g., resolution or algorithm choices).

---

### 4.3 Measurement Systems

#### 4.3.1 Labels themselves are characterised by:
1. **Type**: Qualitative (e.g., categories) or quantitative (e.g., numbers).
2. **Unit**: A standard for comparison (e.g., kilograms for weight).
3. **Magnitude**: The specific value (e.g., 5 kg).
4. **Uncertainty**: Variability or error in measurement.

---

#### 4.3.2 Properties of the measurement system
1. **Nominal**: Categorical (e.g., colors, names).
2. **Ordinal**: Ordered categories (e.g., rankings like "small, medium, large").
3. **Interval**: Numeric, but no true zero (e.g., temperature in Celsius).
4. **Ratio**: Numeric with a true zero (e.g., weight in kilograms).

---

## 5. Variables and Descriptive Statistics

### 5.1 From Data to Variables
Data can be analyzed using **variables**, which define functional relationships between inputs (elements of a set) and their associated outputs. These relationships may be deterministic or stochastic.

#### Variables as Functions
A variable can be represented as a function:

- **Notation**: $f : X \to Y$, where:
  - $X$: Domain (set of inputs).
  - $Y$: Range (set of outputs).
  - $y = f(x) + \epsilon$:
  - The output $y$ is determined by the input $x$, with $\epsilon$ representing uncertainty.

#### Types of Functions
1. **Deterministic Function**:
   - No uncertainty ($\epsilon = 0$).
   - Example: $y = 2x$, where every input $x$ has a precise and predictable output.
2. **Random Function**:
   - Includes uncertainty ($\epsilon \neq 0$).
   - Example: $y = x^2 + \epsilon$, where the output varies due to random noise.

---

#### Random Variables
A **random variable** maps elements from a sample space $S$ to a range $T$, with associated uncertainty:

- **Notation**: $X : S \to T$
- Example: For a coin toss, the sample space $S = \{\text{Heads}, \text{ Tails}\}$, and the random variable maps these outcomes to numeric labels (e.g., Heads = 1, Tails = 0).

---

# Key Concepts: Variables as Functions and Their Relation to Probabilistic Events

## Variables as Functions

- **Function Notation**:
  - A variable can be described as a function:  
    `f : X -> Y,   y = f(x) + ε`
    - **Domain (X)**: The set of inputs.
    - **Range (Y)**: The set of outputs.
    - **Uncertainty (ε)**: Captures the variability or randomness in the association.

### Types of Functions
1. **Deterministic Function**:
   - No uncertainty (`ε = 0`).
   - Example: `y = 2x`, where each input `x` has a precise, predictable output.

2. **Random Function**:
   - Includes uncertainty (`ε != 0`).
   - Example: `y = x^2 + ε`, where the output varies due to randomness.

---

## Random Variables and Their Relationship to Probabilistic Events

- A **random variable** is a function that maps elements from a **sample space** (`S`) to a range (`T`):  
  `X : S -> T`
  - Example: A coin toss has a sample space `S = {Heads, Tails}`, and a random variable `X` assigns labels like "Heads" or "Tails."

### Observing Random Variables
- When a statistical experiment is performed, an outcome `s` in `S` occurs, and the random variable outputs `X(s)` with some uncertainty:  
  `X(s) + ε`

---

## Frequency Tables and Distributions

### Frequency Table
- A **frequency table** enumerates the number of times each outcome occurs in a dataset.
  - Example format:

    | Value/Interval | # Observations |
    |----------------|----------------|
    | {}            | 0              |
    | {x}           | 4              |
    | {y}           | 1              |

### Frequency Distribution
- A **frequency distribution** adds probabilities to the frequency table by normalizing the counts:
  `P(X = x) = (# Observations for x) / (Total Observations)`

  - Example format:

    | Value/Interval | # Observations | Probability |
    |----------------|----------------|-------------|
    | {}            | 0              | 0/10        |
    | {x}           | 4              | 4/10        |
    | {y}           | 1              | 1/10        |

### Histograms
- A **histogram** visually represents the frequency table or distribution using a bar plot:
  - X-axis: Observation values.
  - Y-axis: Frequency or probability.

---

## From Events to Probabilities

- Probabilities quantify the likelihood of each event occurring:
  `P(X = x) ∈ [0, 1]`
- This connects random variables to statistical events, enabling the study of patterns and relationships in data.

---

### 5.2 Descriptive Statistics
Descriptive statistics summarize data to provide insight into its key properties. They are divided into measures of **central tendency** and **dispersion**.

#### Central Tendency
Central tendency metrics describe the "center" or typical value of a dataset:

1. **Mean**: The arithmetic average.
   - Formula: $\text{Mean} = \frac{\sum x_i}{n}$
   - Example: For the dataset $[2, 4, 6]$, $\text{Mean} = \frac{2 + 4 + 6}{3} = 4$.
2. **Median**: The middle value when sorted.
   - Example: For $[1, 3, 5]$, $\text{Median} = 3$.
3. **Mode**: The most frequently occurring value.
   - Example: For $[1, 2, 2, 3]$, $\text{Mode} = 2$.

---

#### Dispersion
Dispersion metrics describe how spread out the data is:

1. **Range**: The difference between the maximum and minimum values.
   - Example: For $[1, 4, 9]$, $\text{Range} = 9 - 1 = 8$.
2. **Variance**: Measures the average squared deviation from the mean.
   - Formula: $\text{Variance} = \frac{\sum (x_i - \mu)^2}{n}$
3. **Standard Deviation (SD)**: The square root of the variance.
   - Indicates how much data typically deviates from the mean.

---

### Types of Variables
Variables are classified based on their properties, influencing what types of descriptive statistics are valid:

| Variable Type | Description                      | Examples                    | Valid Statistics                  |
|---------------|----------------------------------|----------------------------|-----------------------------------|
| **Nominal**   | Categories without order         | Colors (red, blue, green)  | Frequency, Mode                   |
| **Ordinal**   | Ordered categories              | Ranks (gold, silver, bronze) | Median, Range                    |
| **Interval**  | Quantitative, no true zero       | Temperature (°C, °F)       | Mean, Median, Standard Deviation  |
| **Ratio**     | Quantitative, true zero exists   | Weight, height             | All descriptive statistics        |

---

## 6. Signals and Noise

### 6.1 From Variables to Signals
When the location (loci) of observations matters, we treat data as **signals**. A signal is a structured relationship between observations and their positions in a lattice.

#### Definition of a Signal
A **signal** is a set of observations ($Y$) collected over a lattice ($X, \preceq$), where:
- $X$: Represents positions (e.g., time or space).
- $\preceq$: Defines a partial order (topology) over these positions.

#### Examples of Signals
1. **1D Signals**: Amplitude of sound over time (e.g., audio waveform).
2. **2D Signals**: Pixel intensity values over spatial coordinates (e.g., grayscale image).
3. **Multidimensional Signals**: Video, where 2D images evolve over time.

---

### 6.2 Statistical Signal Descriptors
Statistical descriptors characterize signals based on their range of values. These include:

1. **Mean**: Represents the central value of the signal.
   - Caution: In nonstationary signals (e.g., trends), the mean may not be meaningful.
2. **Standard Deviation (SD)**: Describes the signal's variability around its mean.
   - Example: A sine wave has a consistent standard deviation, even with periodic oscillations.
3. **Histogram**: Shows the frequency distribution of signal values.
   - Example: For a grayscale image, a histogram shows the number of pixels for each intensity level.

---

### 6.3 Noise in Signals
Noise refers to unwanted variation or random disturbances within a signal.

#### Types of Noise
1. **Coloured Noise**:
   - **White Noise**: Equal power across all frequencies (e.g., static on a radio).
   - **Pink Noise**: More power at lower frequencies, common in natural systems.
   - **Red Noise (Brownian Noise)**: Strong low-frequency components, resembling random walks.
2. **Distribution-Based Noise**:
   - **Gaussian Noise**: Follows a normal distribution, common in measurement errors.
   - **Poisson Noise**: Associated with count data and low-light imaging.
3. **Algorithmic Noise**:
   - **Brownian Noise**: Random-walk behavior.
   - **Fractal Noise**: Self-similar patterns over scales.

---

### 6.4 Quantifying Noise
Noise is quantified using metrics that compare its impact on the signal.

1. **Signal-to-Noise Ratio (SNR)**:
   - Measures the strength of the signal relative to noise.
   - Formula: 
     $\text{SNR} = \frac{P_{\text{signal}}}{P_{\text{noise}}}$
   - Example: High SNR means the signal is clear, while low SNR indicates significant noise.

2. **Coefficient of Variation (CV)**:
   - Measures relative variability of the signal.
   - Formula:
     $\text{CV} = \frac{\sigma_x}{\mu_x}$
   - Useful for comparing variability across datasets with different units or scales.
