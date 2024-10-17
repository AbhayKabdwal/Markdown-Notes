
### Classification Errors
- **Training errors**: Errors made by the model on the training dataset.
- **Test errors**: Errors made by the model on the test dataset.
- **Generalization error**: Expected error over a random selection of data points from the same distribution.

---

## Underfitting and Overfitting

- **Underfitting** occurs when the model is too simple. Both training and test errors remain high.
- **Overfitting** occurs when the model is too complex. The training error decreases, but the test error increases due to the model fitting noise or irrelevant patterns in the training data.

---

### Example: Impact of Model Complexity

As the number of nodes in a decision tree increases:
- **Simple tree**: The model may underfit, as seen in a decision tree with only 4 nodes.
- **Complex tree**: The model may overfit, as in a decision tree with 50 nodes, where the model fits noise from the training data, leading to poor generalization.

---

## Reasons for Overfitting

1. **Insufficient training data**: The model may fit noise or irrelevant patterns due to a small dataset.
2. **High model complexity**: Complex models can introduce unnecessary components, increasing overfitting. This is exacerbated by the **Multiple Comparison Procedure** where irrelevant components are added when many options are available.

---

### Example of Overfitting with Noisy Attributes

Using irrelevant attributes (e.g., 100 noisy variables from a uniform distribution) alongside relevant features leads to a highly overfitted model, as it starts capturing noise rather than true patterns in the data.

---
## Effect of Multiple Comparison Procedure
-  Many algorithms employ the following greedy strategy:
– Initial model: ![LaTeX Equation](https://latex.codecogs.com/png.latex?M)
– Alternative model: ![LaTeX Equation](https://latex.codecogs.com/png.latex?M%E2%80%99%20%3D%20M%20%E2%88%AA%20%CE%B3)
where γ is a component to be added to the model (e.g., a test condition of a decision tree)
– Keep M’ if improvement, ![LaTeX Equation](https://latex.codecogs.com/png.latex?%CE%94%28M%2CM%E2%80%99%29%20%3E%20%CE%B1)
- Often times, γ is chosen from a set of alternative components, ![LaTeX Equation](https://latex.codecogs.com/png.latex?%CE%93%20%3D%20%5C%7B%7B%CE%B3_%7B1%7D%20%2C%20%CE%B3_%7B2%7D%20%2C%20%E2%80%A6%2C%0A%CE%B3_%7Bk%7D%20%7D%5C%7D)
- If many alternatives are available, one may inadvertently add irrelevant
components to the model, resulting in model overfitting
## Addressing Overfitting: Model Selection

### 1. **Validation Set Approach**
   - Divide the training data into two subsets: a **training set** for building the model and a **validation set** for estimating generalization error. This approach reduces the amount of data available for training but helps in model selection.

### 2. **Incorporating Model Complexity (Occam’s Razor)**
   - The principle of **Occam’s Razor** states that, given two models with similar generalization errors, the simpler model should be preferred. Complex models have a higher chance of overfitting.

#### General Error Formula:
![LaTeX Equation](https://latex.codecogs.com/png.latex?%20%5Ctext%7BGen.%20Error%7D%28%5Ctext%7BModel%7D%29%20%3D%20%5Ctext%7BTrain.%20Error%7D%28%5Ctext%7BModel%2C%20Train.%20Data%7D%29%20%2B%20%5Clambda%20%5Ctimes%20%5Ctext%7BComplexity%7D%28%5Ctext%7BModel%7D%29%20)
![Image](images/image_20241017171801.png)

---

## Pruning Decision Trees

1. **Pre-Pruning** (Early Stopping):
   - Stop tree growth early if:
     - All instances belong to the same class.
     - Attribute values for all instances are identical.
     - Class distribution does not improve with further splitting (e.g., using ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Cchi%5E2) test or Gini index).

2. **Post-Pruning**:
   - Build the tree fully and then prune:
     - **Subtree Replacement**: Replace a subtree with a leaf node if the generalization error improves.
     - **Subtree Raising**: Replace a parent node with one of its subtrees if generalization error improves.




---

## Model Evaluation

1. **Holdout Method**: 
   - Reserve a portion of the dataset (e.g., ![LaTeX Equation](https://latex.codecogs.com/png.latex?k%5C%25)) for training and the rest for testing.

2. **Cross-Validation**:
   - Split the data into ![LaTeX Equation](https://latex.codecogs.com/png.latex?k) disjoint subsets. Train on ![LaTeX Equation](https://latex.codecogs.com/png.latex?k-1) subsets and test on the remaining subset. Repeat this ![LaTeX Equation](https://latex.codecogs.com/png.latex?k) times for each subset. Common values for ![LaTeX Equation](https://latex.codecogs.com/png.latex?k) include 5 and 10 (e.g., **k-fold cross-validation**).
3. **Leave-One-Out Cross-Validation (LOOCV)**:
   - A special case of cross-validation where ![LaTeX Equation](https://latex.codecogs.com/png.latex?k%20%3D%20n), where ![LaTeX Equation](https://latex.codecogs.com/png.latex?n) is the number of data points. The model is trained on all data except one point, and this is repeated for all points.

4. **Stratified Cross-Validation**:
   - Ensures that each fold has the same class distribution as the full dataset, which is especially useful for imbalanced data.

---