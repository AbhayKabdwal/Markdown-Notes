# Classification and Decision Trees

**Classification:**  
Classification is a supervised learning task where the goal is to assign predefined labels (classes) to data based on their features.

**Examples of Classification Tasks:**
- **Email categorization:** Spam or non-spam
- **Tumor identification:** Malignant or benign
- **Galaxy classification:** Elliptical, spiral, or irregular-shaped galaxies

---

## General Approach for Classification Models

1. **Training Phase:**
   - A model is trained on labeled data, where the attribute set ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%5Cmathbf%7Bx%7D&bg=transparent) is used to predict the class label ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20y&bg=transparent).
2. **Prediction Phase:**
   - The model is applied to unseen data to predict class labels.

---

## Classification Techniques

1. **Base Classifiers**  
   - Decision Trees  
   - Rule-based Methods  
   - Nearest-Neighbor  
   - Naïve Bayes  
   - Support Vector Machines (SVM)  
   - Neural Networks

2. **Ensemble Classifiers**  
   - Bagging  
   - Boosting  
   - Random Forests

---

## Decision Trees

Decision trees are a popular classification technique where data is split recursively based on attribute values. Each internal node represents a "test" on an attribute, and each leaf node represents a class label.

### Example of a Decision Tree:
For a simple dataset, the attributes could be:

- ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%5Ctext%7BHomeOwner%7D%20%5Cin%20%5C%7BYes%2C%20No%5C%7D&bg=transparent)
- ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%5Ctext%7BMaritalStatus%7D%20%5Cin%20%5C%7BSingle%2C%20Married%2C%20Divorced%5C%7D&bg=transparent)
- ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%5Ctext%7BIncome%7D%20%5Cin%20%5C%7B%3C%2080K%2C%20%3E%2080K%5C%7D&bg=transparent)

The decision tree splits the data based on these attributes to classify a target variable, such as whether a person will default on a loan.

---

## Decision Tre Induction

Decision tree algorithms include:

- **CART** (Classification and Regression Trees)
- **ID3**, **C4.5** (Developed by Ross Quinlan)
- **Hunt’s Algorithm**
- **SLIQ,SPRINT**

### Hunt’s Algorithm
At each node ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20t&bg=transparent), the following procedure is applied:
- If all records in ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20t&bg=transparent) belong to the same class ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20y_t&bg=transparent), make it a leaf node.
- Otherwise, select an attribute to split the data and recursively apply the procedure.

---

## Splitting Criteria

To determine the "best" attribute for splitting, impurity measures are used.

### Gini Index

The Gini Index measures node impurity. For a node ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20t&bg=transparent), where ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20p_i&bg=transparent) is the proportion of class ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20i&bg=transparent) in node ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20t&bg=transparent), the Gini Index is defined as:

![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%0A%5Ctext%7BGini%7D%28t%29%20%3D%201%20-%20%5Csum_%7Bi%3D1%7D%5E%7Bc%7D%20p_i%5E2%0A&bg=transparent)

For a binary classification problem, the Gini Index can be simplified to:

![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%0A%5Ctext%7BGini%7D%28t%29%20%3D%202p%281%20-%20p%29%0A&bg=transparent)
![Image](images/image_20241017175436.png)

#### Example:
- For a node with class distribution ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28C1%29%20%3D%200.5&bg=transparent) and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28C2%29%20%3D%200.5&bg=transparent), the Gini Index is:
![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%0A%5Ctext%7BGini%7D%20%3D%201%20-%20%280.5%5E2%20%2B%200.5%5E2%29%20%3D%200.5%0A&bg=transparent)

- For a pure node where ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28C1%29%20%3D%201&bg=transparent) and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28C2%29%20%3D%200&bg=transparent), the Gini Index is:
![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%0A%5Ctext%7BGini%7D%20%3D%201%20-%20%281%5E2%20%2B%200%5E2%29%20%3D%200%0A&bg=transparent)

---

### Entropy

Entropy is another measure of impurity, given by:

![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%0A%5Ctext%7BEntropy%7D%28t%29%20%3D%20-%20%5Csum_%7Bi%3D1%7D%5E%7Bc%7D%20p_i%20%5Clog_2%28p_i%29%0A&bg=transparent)

#### Example:
- For a node with ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28C1%29%20%3D%200.5&bg=transparent) and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28C2%29%20%3D%200.5&bg=transparent), the entropy is:
![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%0A%5Ctext%7BEntropy%7D%20%3D%20-%20%280.5%20%5Clog_2%280.5%29%20%2B%200.5%20%5Clog_2%280.5%29%29%20%3D%201%0A&bg=transparent)

- For a pure node where ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28C1%29%20%3D%201&bg=transparent) and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20P%28C2%29%20%3D%200&bg=transparent), the entropy is:
![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%0A%5Ctext%7BEntropy%7D%20%3D%20-%20%281%20%5Clog_2%281%29%29%20%3D%200%0A&bg=transparent)

---

### Information Gain

Information Gain is used to select the attribute that best splits the data. It is calculated as the reduction in entropy after a split:

![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%0A%5Ctext%7BGain%7D%28A%29%20%3D%20%5Ctext%7BEntropy%7D%28%5Ctext%7Bparent%7D%29%20-%20%5Csum_%7Bi%3D1%7D%5E%7Bk%7D%20%5Cfrac%7B%7CD_i%7C%7D%7B%7CD%7C%7D%20%5Ctext%7BEntropy%7D%28D_i%29%0A&bg=transparent)

where ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20D_i&bg=transparent) is a partition of the data after the split.

---

### Misclassification Error

Misclassification Error is another impurity measure, defined as:

![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%0A%5Ctext%7BError%7D%28t%29%20%3D%201%20-%20%5Cmax%28p_1%2C%20p_2%2C%20%5Cdots%2C%20p_c%29%0A&bg=transparent)

---

## Handling Continuous Attributes

For continuous attributes like "income," decision trees often use binary splits of the form ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20A%20%3C%20v&bg=transparent) or ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20A%20%5Cgeq%20v&bg=transparent), where ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20v&bg=transparent) is a threshold value. To find the optimal split:

1. Sort the attribute values.
2. Evaluate potential splits based on Gini Index, Entropy, or other criteria.

---

## Advantages of Decision Trees

- Simple to understand and interpret.
- Fast classification of unknown records.
- Can handle both numerical and categorical data.
- Handles irrelevant and redundant attributes well.
- Robust to noise when proper pruning techniques are applied.

---

## Disadvantages of Decision Trees

- Greedy nature of decision tree algorithms may overlook interactions between attributes.
- Can overfit the data if not pruned properly.
- Decision boundaries are axis-parallel, meaning they may not work well for complex data structures.
