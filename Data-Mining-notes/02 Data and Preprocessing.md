### Introduction: What is Data?
Data is a collection of objects and their attributes. An **attribute** is a property or characteristic of an object (e.g., eye color, temperature), also known as a variable, field, or feature. An **object** is an instance or entity that is described by these attributes.

---

## Types of Data

1. **Structured Data:** 
   - Standardized and easily transferable between systems (e.g., a student’s name, test scores).
   
2. **Unstructured Data:** 
   - Not standardized (e.g., audio recordings, doctor's notes).

3. **Semi-structured Data:**
   - Combines elements of both structured and unstructured data.

---

## Data Sets

1. **Record Data:** 
   Consists of a collection of records, each with a fixed set of attributes.
   
2. **Data Matrix:** 
   When data objects have the same set of numeric attributes, they can be represented as points in a multidimensional space. A data matrix is an $m \times n$ matrix where $m$ is the number of records and $n$ is the number of attributes.

3. **Document Data:**
   - Each document is represented as a term vector, with each term being a component (attribute). The value of each component is the number of times the term appears in the document.

4. **Transaction Data:**
   - Involves sets of items purchased together (e.g., a set of groceries in a shopping cart).

---

## Types of Attributes

1. **Nominal:** 
   - Attributes that denote distinct categories (e.g., eye color, ID numbers).
   
2. **Ordinal:** 
   - Attributes that involve order or ranking (e.g., grades, rankings).
   
3. **Interval:** 
   - Attributes with meaningful differences but no true zero point (e.g., temperature in Celsius).
   
4. **Ratio:** 
   - Attributes with meaningful differences and a true zero (e.g., height, weight).

---

## Attribute Properties

The operations applicable to different types of attributes depend on their properties:
- **Distinctness:** $=, \neq$
- **Order:** $<, >$
- **Meaningful differences:** $+, -$
- **Ratios are meaningful:** $*, /$

### Example:
For **Nominal** attributes, only distinctness ($=, \neq$) is meaningful, while for **Ratio** attributes, all operations ($+, -, *, /$) are valid.

---

## Data Quality Problems

1. **Noise and Outliers:**
   - Noise refers to random distortion in data, and outliers are data points that differ significantly from other observations.
   
2. **Missing Values:**
   - Missing values can result from various reasons, such as uncollected information or inapplicability.
   
3. **Duplicate Data:**
   - Duplicate records in a dataset often arise when merging data from multiple sources.

---

## Data Preprocessing Techniques

1. **Aggregation:**
   - Combining multiple attributes or objects into a single attribute or object. This can be used for data reduction or for more stable, aggregated data.

2. **Sampling:**
   - Selecting a subset of the data for analysis. Sampling can be done randomly or stratified based on certain characteristics.
   
3. **Discretization:**
   - Converts continuous attributes into categorical values. For example, a continuous range of temperatures can be split into intervals like "low," "medium," and "high."
   
4. **Binarization:**
   - Converts attributes into binary values, often used for categorical attributes.
   
5. **Dimensionality Reduction:**
   - Reduces the number of attributes to simplify the dataset while preserving important information. Techniques include **Principal Component Analysis (PCA)**.

---

## Attribute Transformation

This involves changing the representation or scale of attributes, such as normalizing time series data or applying transformations like **Fourier** and **wavelet analysis** to extract relevant features.

---

## The Curse of Dimensionality

As dimensionality increases, the data becomes sparse, making it difficult to calculate distances or detect patterns. **Dimensionality reduction** techniques are essential to combat this issue.

---

## Feature Selection and Creation

1. **Feature Subset Selection:** 
   - Reduces dimensionality by removing redundant or irrelevant features (e.g., removing an ID number that doesn’t affect the outcome).
   
2. **Feature Creation:** 
   - Involves creating new features that are more representative of the data (e.g., calculating density from mass and volume).

---