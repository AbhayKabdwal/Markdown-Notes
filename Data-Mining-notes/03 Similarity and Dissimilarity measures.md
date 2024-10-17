## **1. Similarity and Dissimilarity Definitions**
- **Similarity Measure**:
  - A numerical measure of how alike two data objects are.
  - Higher values indicate more similarity.
  - Typically falls within the range ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%5B0%2C%201%5D&bg=transparent).

- **Dissimilarity Measure**:
  - A numerical measure of how different two data objects are.
  - Lower values indicate more similarity.
  - Minimum dissimilarity is often 0, with the upper limit varying depending on the context.

- **Proximity** refers to either a similarity or dissimilarity measure.

---

## **2. Similarity/Dissimilarity for Simple Attributes**
- Let ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20x&bg=transparent) and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20y&bg=transparent) be two data objects with simple attributes. The proximity between them can be computed using various distance metrics, each suited for different attribute types.

## **3. Euclidean Distance**
- For ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20n&bg=transparent)-dimensional data objects ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20x&bg=transparent) and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20y&bg=transparent), the Euclidean distance is defined as:
  
  ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20d%28x%2C%20y%29%20%3D%20%5Csqrt%7B%5Csum_%7Bk%3D1%7D%5En%20%28x_k%20-%20y_k%29%5E2%7D%20&bg=transparent)

  where ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20x_k&bg=transparent) and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20y_k&bg=transparent) are the ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20k&bg=transparent)-th components (attributes) of ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20x&bg=transparent) and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20y&bg=transparent). Standardization may be necessary if scales differ.

## **4. Minkowski Distance**
- Generalization of the Euclidean distance:

  ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20d%28x%2C%20y%29%20%3D%20%5Cleft%28%20%5Csum_%7Bk%3D1%7D%5En%20%7Cx_k%20-%20y_k%7C%5Er%20%5Cright%29%5E%7B1/r%7D%20&bg=transparent)

  - **Examples**:
    - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20r%20%3D%201&bg=transparent): City Block (Manhattan, L1 norm) distance.
    - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20r%20%3D%202&bg=transparent): Euclidean distance.
    - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20r%20%5Cto%20%5Cinfty&bg=transparent): Supremum (L![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20_%5Cinfty&bg=transparent)) distance.

## **5. Mahalanobis Distance**
- Takes into account the correlations of the data by using the covariance matrix ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%5CSigma&bg=transparent):
  
  ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20d%28x%2C%20y%29%20%3D%20%5Csqrt%7B%28x%20-%20y%29%5ET%20%5CSigma%5E%7B-1%7D%20%28x%20-%20y%29%7D%20&bg=transparent)

  This distance is effective for multivariate data and considers the spread of the data.

---

## **6. Similarity Measures for Binary Vectors**
- Binary vectors ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20x&bg=transparent) and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20y&bg=transparent) are compared using four counts:
  - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20f_%7B11%7D&bg=transparent): Count of 1-1 matches.
  - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20f_%7B00%7D&bg=transparent): Count of 0-0 matches.
  - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20f_%7B01%7D&bg=transparent): Count of 0-1 mismatches.
  - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20f_%7B10%7D&bg=transparent): Count of 1-0 mismatches.

- **Simple Matching Coefficient (SMC)**:
  
  ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20SMC%20%3D%20%5Cfrac%7Bf_%7B11%7D%20%2B%20f_%7B00%7D%7D%7Bf_%7B11%7D%20%2B%20f_%7B00%7D%20%2B%20f_%7B01%7D%20%2B%20f_%7B10%7D%7D%20&bg=transparent)

- **Jaccard Coefficient**:

  ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20J%20%3D%20%5Cfrac%7Bf_%7B11%7D%7D%7Bf_%7B11%7D%20%2B%20f_%7B01%7D%20%2B%20f_%7B10%7D%7D%20&bg=transparent)

  Jaccard considers only 1-1 matches, making it more appropriate when 0-0 matches are not meaningful.

---

## **7. Cosine Similarity**
- Measures the cosine of the angle between two vectors ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20d_1&bg=transparent) and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20d_2&bg=transparent):

  ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20%5Ccos%28d_1%2C%20d_2%29%20%3D%20%5Cfrac%7B%5Clangle%20d_1%2C%20d_2%20%5Crangle%7D%7B%7C%7Cd_1%7C%7C%20%5Ccdot%20%7C%7Cd_2%7C%7C%7D%20&bg=transparent)

  - Example:
    - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20d_1%20%3D%20%5B3%2C%202%2C%200%2C%205%2C%200%2C%200%2C%200%2C%202%2C%200%2C%200%5D&bg=transparent)
    - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20d_2%20%3D%20%5B1%2C%200%2C%200%2C%200%2C%200%2C%200%2C%200%2C%201%2C%200%2C%202%5D&bg=transparent)
  
    Calculation:

    ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20%5Clangle%20d_1%2C%20d_2%20%5Crangle%20%3D%203%20%5Ctimes%201%20%2B%202%20%5Ctimes%200%20%2B%205%20%5Ctimes%200%20%2B%202%20%5Ctimes%201%20%3D%205%20&bg=transparent)

    ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20%7C%7Cd_1%7C%7C%20%3D%20%5Csqrt%7B3%5E2%20%2B%202%5E2%20%2B%205%5E2%20%2B%202%5E2%7D%20%3D%206.481%20&bg=transparent)

    ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20%7C%7Cd_2%7C%7C%20%3D%20%5Csqrt%7B1%5E2%20%2B%201%5E2%20%2B%202%5E2%7D%20%3D%202.449%20&bg=transparent)

    ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20%5Ccos%28d_1%2C%20d_2%29%20%3D%20%5Cfrac%7B5%7D%7B6.481%20%5Ctimes%202.449%7D%20%3D%200.315%20&bg=transparent)

---

## **8. Correlation Coefficient**
- Measures the linear relationship between data objects ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20x&bg=transparent) and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20y&bg=transparent):

  ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20%5Ctext%7Bcorr%7D%28x%2C%20y%29%20%3D%20%5Cfrac%7B%5Csum_%7Bk%3D1%7D%5En%20%28x_k%20-%20%5Cbar%7Bx%7D%29%28y_k%20-%20%5Cbar%7By%7D%29%7D%7B%28n-1%29%20%5Ccdot%20s_x%20%5Ccdot%20s_y%7D%20&bg=transparent)

  where ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%5Cbar%7Bx%7D&bg=transparent) and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%5Cbar%7By%7D&bg=transparent) are the means, and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20s_x&bg=transparent), ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20s_y&bg=transparent) are the standard deviations of ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20x&bg=transparent) and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20y&bg=transparent).

- **Drawback**: Cannot capture non-linear relationships.

---

## **9. Information-Based Measures**
- **Entropy** (![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20H&bg=transparent)): Measures the uncertainty of a variable.

  ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20H%28X%29%20%3D%20-%5Csum_%7Bi%3D1%7D%5En%20p%28x_i%29%20%5Clog_2%20p%28x_i%29%20&bg=transparent)

- **Mutual Information** (![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20MI&bg=transparent)): Measures the amount of information obtained about one variable through another.

  ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20MI%28X%2C%20Y%29%20%3D%20H%28X%29%20%2B%20H%28Y%29%20-%20H%28X%2C%20Y%29%20&bg=transparent)

  - Example (Student Status vs. Grade):

    - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20H%28%5Ctext%7BStudent%20Status%7D%29%20%3D%200.9928&bg=transparent)
    - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20H%28%5Ctext%7BGrade%7D%29%20%3D%201.4406&bg=transparent)
    - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20H%28%5Ctext%7BCombined%7D%29%20%3D%202.2710&bg=transparent)

    ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20MI%20%3D%200.9928%20%2B%201.4406%20-%202.2710%20%3D%200.1624%20&bg=transparent)

## **10. Maximal Information Coefficient (MIC)**
- Detects both linear and non-linear relationships in large datasets. Normalized mutual information computed across different binnings.

---

## **11. Choosing Proximity Measures**
- Depends on the data domain:
  - **Documents**: Cosine similarity is often suitable.
  - **Temperature**: Euclidean distance for magnitude comparison.
  - **Time series**: Correlation captures similarity in temporal patterns.

- Considerations:
  - Symmetry.
  - Noise tolerance.
  - Domain knowledge alignment.
