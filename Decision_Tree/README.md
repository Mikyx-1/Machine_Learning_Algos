# Decision Tree Overview

## What is a Decision Tree?
A decision tree is a supervised machine learning algorithm used for classification and regression. It’s a tree-like structure where:
- **Nodes** represent decisions based on feature values.
- **Branches** represent the outcomes of those decisions.
- **Leaves** represent the final output (a class label or predicted value).

It works by splitting the data into groups that become more homogeneous with respect to the target variable.

## What is the Decision Tree Trying to Minimize?
A decision tree aims to minimize **impurity** — the amount of disorder or mixed classes in the branches. Different metrics are used to measure impurity:

- **Gini Impurity (Classification)**:


  $$Gini = 1 - \sum p_i^2$$

  Where $p_i$ is the proportion of samples in class $i$. Lower Gini means purer groups.

- **Entropy (Classification)**:

  $$Entropy = -\sum p_i \log_2(p_i)$$

  Entropy measures unpredictability, and the goal is to minimize it.

- **Mean Squared Error (Regression)**:
  Used to minimize variance in target values.

## How Does a Decision Tree Choose the Feature to Split?
The algorithm evaluates every feature and selects the one that results in the **greatest information gain** — the split that most reduces impurity.

## How Does a Decision Tree Decide Where to Split?
Once a feature is selected, the algorithm must choose the **best threshold** (value) for the split.

- **For Numerical Features:**
  1. Sort the feature values.
  2. Try possible split points between each pair of values (usually midpoints).
  3. Evaluate each split by calculating the weighted average impurity.
  4. Choose the split with the lowest impurity.

- **For Categorical Features:**
  1. Try different groupings of categories.
  2. Evaluate each grouping.
  3. Choose the grouping with the lowest impurity.

## Example
Let’s take a small example where we predict whether a person buys a product based on their age:

| Age | Buys Product? |
|-----|---------------|
| 22  | Yes           |
| 25  | No            |
| 30  | Yes           |
| 35  | Yes           |
| 40  | No            |

Possible split at `Age <= 27.5`:

- Group 1 (`Age <= 27.5`): `[22, 25] → ["Yes", "No"]`
- Group 2 (`Age > 27.5`): `[30, 35, 40] → ["Yes", "Yes", "No"]`

### Calculating Weighted Gini Impurity

**Gini Formula:**

$$
Gini = 1 - \sum p_i^2
$$

Where $p_i$ is the proportion of each class in the group.

**Group 1 (`Age <= 27.5`):**

- Values: `[22, 25]`
- Labels: `["Yes", "No"]`

Class proportions:

- `Yes`: $\frac{1}{2} = 0.5$
- `No`: $\frac{1}{2} = 0.5$

Gini impurity:

$$
Gini_1 = 1 - (0.5^2 + 0.5^2) = 1 - (0.25 + 0.25) = 1 - 0.5 = 0.5
$$

**Group 2 (`Age > 27.5`):**

- Values: `[30, 35, 40]`
- Labels: `["Yes", "Yes", "No"]`

Class proportions:

- `Yes`: $\frac{2}{3} \approx 0.67$
- `No`: $\frac{1}{3} \approx 0.33$

Gini impurity:

$$
Gini_2 = 1 - (0.67^2 + 0.33^2) = 1 - (0.4489 + 0.1089) = 1 - 0.5578 = 0.442
$$

**Weighted Gini Impurity:**

We weight each group’s impurity by its size:

- Group 1 size: 2
- Group 2 size: 3
- Total size: 5

$$
Weighted\ Gini = \frac{2}{5} \times 0.5 + \frac{3}{5} \times 0.442
$$

$$
= 0.4 \times 0.5 + 0.6 \times 0.442
$$

$$
= 0.2 + 0.2652 = 0.4652
$$

The **weighted Gini impurity for the split at `Age <= 27.5` is approximately 0.4652**.

## Advantages of Decision Trees
- Easy to understand and visualize.
- Handles numerical and categorical data.
- No need for feature scaling.

## Drawbacks of Decision Trees
- Prone to overfitting without proper tuning.
- Sensitive to small data changes.
- Sometimes less accurate than ensemble methods.



