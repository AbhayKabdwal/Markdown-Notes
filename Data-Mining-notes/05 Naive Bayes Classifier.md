## **1. Introduction**
- The **Naive Bayes Classifier** is a probabilistic classification technique based on **Bayes Theorem**.
- It assumes independence between predictors, which simplifies computation but may not always hold in real-world cases.
- Despite its simplicity, Naive Bayes is effective and widely used in various applications such as spam detection, text classification, and medical diagnosis.

---

## **2. Bayes Theorem**
Bayes Theorem provides a way to update the probability of a hypothesis $h$ given new evidence $D$:

$$ P(h | D) = \frac{P(D | h) P(h)}{P(D)} $$

where:
- $P(h)$: Prior probability of hypothesis $h$.
- $P(D)$: Prior probability of the data $D$.
- $P(D | h)$: Likelihood of observing data $D$ given that $h$ holds.
- $P(h | D)$: Posterior probability that $h$ holds given the observed data $D$.

**Example**: 
Two bags are given:
- **Bag I**: 4 white balls, 6 black balls.
- **Bag II**: 4 white balls, 3 black balls.

If one ball is drawn at random and it is black, what is the probability that it was drawn from **Bag I**?

- Prior probabilities:
  - $P(\text{Bag I}) = \frac{1}{2}$, $P(\text{Bag II}) = \frac{1}{2}$
- Likelihoods:
  - $P(\text{Black | Bag I}) = \frac{6}{10} = 0.6$
  - $P(\text{Black | Bag II}) = \frac{3}{7} \approx 0.429$
- Posterior probability using Bayes:
  
$$ P(\text{Bag I | Black}) = \frac{P(\text{Black | Bag I}) P(\text{Bag I})}{P(\text{Black})} $$

---

## **3. Naive Bayes Classifier**
### **3.1 Naive Bayes Assumption**
- Assumes that the presence of a particular feature in a class is independent of the presence of any other feature.
- Given a set of features $X = \{x_1, x_2, \ldots, x_n\}$, Naive Bayes calculates the probability of a class $c_j$ as:

$$ P(c_j | X) = P(c_j) \prod_{i=1}^n P(x_i | c_j) $$

where:
- $P(c_j)$ is the prior probability of class $c_j$.
- $P(x_i | c_j)$ is the likelihood of feature $x_i$ given class $c_j$.

### **3.2 Steps for Classification**
1. Compute the prior probabilities $P(c_j)$ for each class.
2. Compute the likelihood $P(x_i | c_j)$ for each feature $x_i$ given class $c_j$.
3. Calculate the posterior probability $P(c_j | X)$ for each class.
4. Assign the class label with the highest posterior probability to the new sample.

### **3.3 Example:**
Consider a dataset where we want to classify if a day is suitable for playing based on four features: 
**Outlook**, **Temperature**, **Humidity**, and **Wind**.

Given:
- Today’s conditions are $(\text{Sunny}, \text{Hot}, \text{Normal}, \text{Weak})$.

We need to calculate $P(\text{Play | Today})$ using the Naive Bayes Classifier.

$$ P(\text{Play | Today}) = P(\text{Play}) \cdot P(\text{Sunny | Play}) \cdot P(\text{Hot | Play}) \cdot P(\text{Normal | Play}) \cdot P(\text{Weak | Play}) $$

and similarly for $P(\text{No Play | Today})$.

---

## **4. Naive Bayes for Continuous Features**
### **4.1 Handling Continuous Data**
For continuous features, Naive Bayes assumes a **Gaussian distribution** for the values within each class. The probability density function is given by:

$$ P(x | c_j) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x - \mu)^2}{2\sigma^2}} $$

where:
- $\mu$ is the mean of the feature values for class $c_j$.
- $\sigma$ is the standard deviation of the feature values for class $c_j$.


---

## **6. Conclusion**
- Naive Bayes Classifier is simple yet powerful, especially when the independence assumption holds.
- Effective in high-dimensional data, as it requires fewer parameters to estimate.
- However, it performs poorly when features are heavily correlated.

---