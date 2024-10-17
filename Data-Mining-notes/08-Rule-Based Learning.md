### Overview
A **rule-based classifier** classifies records using a collection of "if...then..." rules. Each rule is of the form:
- **Rule**: ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%28%5Ctext%7BCondition%7D%29%20%5Crightarrow%20y&bg=transparent)
   - **Condition**: A conjunction of attribute tests.
   - **![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20y&bg=transparent)**: The class label.

#### Example of Rules:
- ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%28%5Ctext%7BGive%20Birth%7D%20%3D%20%5Ctext%7Bno%7D%29%20%5Cland%20%28%5Ctext%7BCan%20Fly%7D%20%3D%20%5Ctext%7Byes%7D%29%20%5Crightarrow%20%5Ctext%7BBirds%7D&bg=transparent)
- ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%28%5Ctext%7BTaxable%20Income%7D%20%3C%2050K%29%20%5Cland%20%28%5Ctext%7BRefund%7D%20%3D%20%5Ctext%7BYes%7D%29%20%5Crightarrow%20%5Ctext%7BEvade%7D%20%3D%20%5Ctext%7BNo%7D&bg=transparent)

---

## Rule Characteristics

1. **Coverage**: The fraction of records that satisfy the condition of the rule.
   - Example: For the rule ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%28%5Ctext%7BStatus%7D%20%3D%20%5Ctext%7BSingle%7D%29%20%5Crightarrow%20%5Ctext%7BNo%7D&bg=transparent), coverage could be ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%2040%5C%25&bg=transparent).
   
2. **Accuracy**: The fraction of records satisfying the condition that also satisfy the conclusion.
   - Example: Accuracy of ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%2050%5C%25&bg=transparent) means half of the records meeting the condition also match the class label.
![Image](images/image_20241017160414.png)
---

## Mutually Exclusive and Exhaustive Rules

1. **Mutually Exclusive Rules**:
   - Rules are independent, and each record is covered by at most one rule.

2. **Exhaustive Rules**:
   - The rule set accounts for all possible combinations of attribute values, meaning every record is covered by at least one rule.

---

## Handling Non-Mutually Exclusive or Non-Exhaustive Rules

1. If rules are **not mutually exclusive**:
   - A record may trigger multiple rules. This can be handled by:
     - **Ordered Rule Set**: Rank rules by priority and assign the class label of the highest-ranked rule.
     - **Unordered Rule Set**: Use a voting scheme.

2. If rules are **not exhaustive**:
   - A record may trigger no rules, in which case a **default class** is assigned.

---

## Rule Ordering Schemes

1. **Rule-based ordering**: Rules are ranked based on quality.
2. **Class-based ordering**: Rules with the same class labels are grouped together.
![Image](images/image_20241017160658.png)

---

## Rule Construction Methods

1. **Direct Method**:
   - Rules are extracted directly from the data.
   - Examples: RIPPER, CN2, Holte’s 1R.
   
2. **Indirect Method**:
   - Rules are extracted from other classification models, such as decision trees.
   - Example: **C4.5rules**, which generates rules from a decision tree.

---
## Rule Growing

![Image](images/image_20241017160819.png)

---
## Rule Evaluation
![Image](images/image_20241017160927.png)

---
## RIPPER Algorithm (Direct Method)

For a two-class problem, one class is treated as positive, and the other as negative. RIPPER builds the rule set for the positive class first:
1. **Rule Growing**: Start with an empty rule and add conditions as long as they improve FOIL’s information gain.
2. **Pruning**: Remove unnecessary conditions using **incremental reduced error pruning**. The pruning criterion is:
   ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20%20v%20%3D%20%5Cfrac%7Bp%20-%20n%7D%7Bp%20%2B%20n%7D%20&bg=transparent)
   where ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20p&bg=transparent) is the number of positive examples and ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20n&bg=transparent) is the number of negative examples covered by the rule.
- **Pruning method**: delete any final sequence of conditions that maximizes v
![Image](images/image_20241017161316.png)

---

## Indirect Method: C4.5rules

This method extracts rules from an unpruned decision tree. For each rule ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20r%3A%20A%20%5Crightarrow%20y&bg=transparent), alternative rules ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20r%27%3A%20A%27%20%5Crightarrow%20y&bg=transparent) are considered, where ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20A%27&bg=transparent) removes one conjunct from ![LaTeX Equation](https://latex.codecogs.com/png.latex?%5Ccolor%7Bwhite%7D%20A&bg=transparent). The rule with the lowest pessimistic error is selected.

---

## Advantages of Rule-Based Classifiers

- Rule-based classifiers are expressive and easy to interpret, similar to decision trees.
- They perform well with imbalanced classes and can handle redundant or irrelevant attributes.
- However, they may struggle with variable interactions and missing values in the test set.

---
