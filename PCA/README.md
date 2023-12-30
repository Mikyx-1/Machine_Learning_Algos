# Principle Component Analysis Implementation

## 1. What is PCA ?
Principle component analysis is a unsupervised learning technique aiming at reducing data dimensionality. Its main objective is to maximise the variance within that data in the new plane.

## 2. How does it works ?
Assume that: $x \in \mathbb{R}^{N*d1}$

Step 1: Initialise a matrix $W \in \mathbb{R}^{d1*d2}$

Step 2: Project the new data points to new plane: $x_{new} = W \cdot x$

Step 3: Minimise ${\sigma^2}_{x_n}$ by using Gradient Descent or Lagrangian method


**Updating**
