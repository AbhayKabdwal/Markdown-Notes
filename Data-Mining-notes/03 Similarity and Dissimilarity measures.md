## **1. Similarity and Dissimilarity Definitions**
- **Similarity Measure**:
  - A numerical measure of how alike two data objects are.
  - Higher values indicate more similarity.
  - Typically falls within the range `[0, 1]`.

- **Dissimilarity Measure**:
  - A numerical measure of how different two data objects are.
  - Lower values indicate more similarity.
  - Minimum dissimilarity is often 0, with the upper limit varying depending on the context.

- **Proximity** refers to either a similarity or dissimilarity measure.

---

## **2. Similarity/Dissimilarity for Simple Attributes**
- Let `x` and `y` be two data objects with simple attributes. The proximity between them can be computed using various distance metrics, each suited for different attribute types.

## **3. Euclidean Distance**
- For `n`-dimensional data objects `x` and `y`, the Euclidean distance is defined as:
  
  ```math
 d(x, y) = \sqrt{sum of_{k=1}^n (x_k - y_k)^2} 
```

  where `x_k` and `y_k` are the `k`-th components (attributes) of `x` and `y`. Standardization may be necessary if scales differ.

## **4. Minkowski Distance**
- Generalization of the Euclidean distance:

  ```math
 d(x, y) = ( sum of_{k=1}^n |x_k - y_k|^r )^{1/r} 
```

  - **Examples**:
    - `r = 1`: City Block (Manhattan, L1 norm) distance.
    - `r = 2`: Euclidean distance.
    - `r \to ∞`: Supremum (L`_∞`) distance.

## **5. Mahalanobis Distance**
- Takes into account the correlations of the data by using the covariance matrix `\Sigma`:
  
  ```math
 d(x, y) = \sqrt{(x - y)^T \Sigma^{-1} (x - y)} 
```

  This distance is effective for multivariate data and considers the spread of the data.

---

## **6. Similarity Measures for Binary Vectors**
- Binary vectors `x` and `y` are compared using four counts:
  - `f_{11}`: Count of 1-1 matches.
  - `f_{00}`: Count of 0-0 matches.
  - `f_{01}`: Count of 0-1 mismatches.
  - `f_{10}`: Count of 1-0 mismatches.

- **Simple Matching Coefficient (SMC)**:
  
  ```math
 SMC = \frac{f_{11} + f_{00}}{f_{11} + f_{00} + f_{01} + f_{10}} 
```

- **Jaccard Coefficient**:

  ```math
 J = \frac{f_{11}}{f_{11} + f_{01} + f_{10}} 
```

  Jaccard considers only 1-1 matches, making it more appropriate when 0-0 matches are not meaningful.

---

## **7. Cosine Similarity**
- Measures the cosine of the angle between two vectors `d_1` and `d_2`:

  ```math
 \cos(d_1, d_2) = (\langle d_1, d_2 \rangle / ||d_1|| * ||d_2||) 
```

  - Example:
    - `d_1 = [3, 2, 0, 5, 0, 0, 0, 2, 0, 0]`
    - `d_2 = [1, 0, 0, 0, 0, 0, 0, 1, 0, 2]`
  
    Calculation:

    ```math
 \langle d_1, d_2 \rangle = 3 x 1 + 2 x 0 + 5 x 0 + 2 x 1 = 5 
```

    ```math
 ||d_1|| = sqrt(3^2 + 2^2 + 5^2 + 2^2) = 6.481 
```

    ```math
 ||d_2|| = sqrt(1^2 + 1^2 + 2^2) = 2.449 
```

    ```math
 \cos(d_1, d_2) = (5 / 6.481 x 2.449) = 0.315 
```

---

## **8. Correlation Coefficient**
- Measures the linear relationship between data objects `x` and `y`:

  ```math
 \text{corr}(x, y) = \frac{sum of_{k=1}^n (x_k - \bar{x})(y_k - \bar{y})}{(n-1) * s_x * s_y} 
```

  where `\bar{x}` and `\bar{y}` are the means, and `s_x`, `s_y` are the standard deviations of `x` and `y`.

- **Drawback**: Cannot capture non-linear relationships.

---

## **9. Information-Based Measures**
- **Entropy** (`H`): Measures the uncertainty of a variable.

  ```math
 H(X) = -sum of_{i=1}^n p(x_i) \log_2 p(x_i) 
```

- **Mutual Information** (`MI`): Measures the amount of information obtained about one variable through another.

  ```math
 MI(X, Y) = H(X) + H(Y) - H(X, Y) 
```

  - Example (Student Status vs. Grade):

    - `H(\text{Student Status}) = 0.9928`
    - `H(\text{Grade}) = 1.4406`
    - `H(\text{Combined}) = 2.2710`

    ```math
 MI = 0.9928 + 1.4406 - 2.2710 = 0.1624 
```

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
