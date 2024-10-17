## **1. Introduction**
- The **Naive Bayes Classifier** is a probabilistic classification technique based on **Bayes Theorem**.
- It assumes independence between predictors, which simplifies computation but may not always hold in real-world cases.
- Despite its simplicity, Naive Bayes is effective and widely used in various applications such as spam detection, text classification, and medical diagnosis.

---

## **2. Bayes Theorem**
Bayes Theorem provides a way to update the probability of a hypothesis ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20h&bg=transparent) given new evidence ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20D&bg=transparent):

![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20P%28h%20%7C%20D%29%20%3D%20%5Cfrac%7BP%28D%20%7C%20h%29%20P%28h%29%7D%7BP%28D%29%7D%20&bg=transparent)

where:
- ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28h%29&bg=transparent): Prior probability of hypothesis ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20h&bg=transparent).
- ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28D%29&bg=transparent): Prior probability of the data ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20D&bg=transparent).
- ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28D%20%7C%20h%29&bg=transparent): Likelihood of observing data ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20D&bg=transparent) given that ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20h&bg=transparent) holds.
- ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28h%20%7C%20D%29&bg=transparent): Posterior probability that ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20h&bg=transparent) holds given the observed data ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20D&bg=transparent).

**Example**: 
Two bags are given:
- **Bag I**: 4 white balls, 6 black balls.
- **Bag II**: 4 white balls, 3 black balls.

If one ball is drawn at random and it is black, what is the probability that it was drawn from **Bag I**?

- Prior probabilities:
  - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28%5Ctext%7BBag%20I%7D%29%20%3D%20%5Cfrac%7B1%7D%7B2%7D&bg=transparent), ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28%5Ctext%7BBag%20II%7D%29%20%3D%20%5Cfrac%7B1%7D%7B2%7D&bg=transparent)
- Likelihoods:
  - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28%5Ctext%7BBlack%20%7C%20Bag%20I%7D%29%20%3D%20%5Cfrac%7B6%7D%7B10%7D%20%3D%200.6&bg=transparent)
  - ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28%5Ctext%7BBlack%20%7C%20Bag%20II%7D%29%20%3D%20%5Cfrac%7B3%7D%7B7%7D%20%5Capprox%200.429&bg=transparent)
- Posterior probability using Bayes:
  
![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20P%28%5Ctext%7BBag%20I%20%7C%20Black%7D%29%20%3D%20%5Cfrac%7BP%28%5Ctext%7BBlack%20%7C%20Bag%20I%7D%29%20P%28%5Ctext%7BBag%20I%7D%29%7D%7BP%28%5Ctext%7BBlack%7D%29%7D%20&bg=transparent)

---

## **3. Naive Bayes Classifier**
### **3.1 Naive Bayes Assumption**
- Assumes that the presence of a particular feature in a class is independent of the presence of any other feature.
- Given a set of features ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20X%20%3D%20%5C%7Bx_1%2C%20x_2%2C%20%5Cldots%2C%20x_n%5C%7D&bg=transparent), Naive Bayes calculates the probability of a class ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20c_j&bg=transparent) as:

![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20P%28c_j%20%7C%20X%29%20%3D%20P%28c_j%29%20%5Cprod_%7Bi%3D1%7D%5En%20P%28x_i%20%7C%20c_j%29%20&bg=transparent)

where:
- ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28c_j%29&bg=transparent) is the prior probability of class ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20c_j&bg=transparent).
- ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28x_i%20%7C%20c_j%29&bg=transparent) is the likelihood of feature ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20x_i&bg=transparent) given class ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20c_j&bg=transparent).

### **3.2 Steps for Classification**
1. Compute the prior probabilities ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28c_j%29&bg=transparent) for each class.
2. Compute the likelihood ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28x_i%20%7C%20c_j%29&bg=transparent) for each feature ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20x_i&bg=transparent) given class ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20c_j&bg=transparent).
3. Calculate the posterior probability ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28c_j%20%7C%20X%29&bg=transparent) for each class.
4. Assign the class label with the highest posterior probability to the new sample.

### **3.3 Example:**
Consider a dataset where we want to classify if a day is suitable for playing based on four features: 
**Outlook**, **Temperature**, **Humidity**, and **Wind**.

Given:
- Today’s conditions are ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%28%5Ctext%7BSunny%7D%2C%20%5Ctext%7BHot%7D%2C%20%5Ctext%7BNormal%7D%2C%20%5Ctext%7BWeak%7D%29&bg=transparent).

We need to calculate ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28%5Ctext%7BPlay%20%7C%20Today%7D%29&bg=transparent) using the Naive Bayes Classifier.

![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20P%28%5Ctext%7BPlay%20%7C%20Today%7D%29%20%3D%20P%28%5Ctext%7BPlay%7D%29%20%5Ccdot%20P%28%5Ctext%7BSunny%20%7C%20Play%7D%29%20%5Ccdot%20P%28%5Ctext%7BHot%20%7C%20Play%7D%29%20%5Ccdot%20P%28%5Ctext%7BNormal%20%7C%20Play%7D%29%20%5Ccdot%20P%28%5Ctext%7BWeak%20%7C%20Play%7D%29%20&bg=transparent)

and similarly for ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28%5Ctext%7BNo%20Play%20%7C%20Today%7D%29&bg=transparent).

---

## **4. Naive Bayes for Continuous Features**
### **4.1 Handling Continuous Data**
For continuous features, Naive Bayes assumes a **Gaussian distribution** for the values within each class. The probability density function is given by:

![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20P%28x%20%7C%20c_j%29%20%3D%20%5Cfrac%7B1%7D%7B%5Csqrt%7B2%5Cpi%5Csigma%5E2%7D%7D%20e%5E%7B-%5Cfrac%7B%28x%20-%20%5Cmu%29%5E2%7D%7B2%5Csigma%5E2%7D%7D%20&bg=transparent)

where:
- ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%5Cmu&bg=transparent) is the mean of the feature values for class ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20c_j&bg=transparent).
- ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%5Csigma&bg=transparent) is the standard deviation of the feature values for class ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20c_j&bg=transparent).


---

## **6. Conclusion**
- Naive Bayes Classifier is simple yet powerful, especially when the independence assumption holds.
- Effective in high-dimensional data, as it requires fewer parameters to estimate.
- However, it performs poorly when features are heavily correlated.

---