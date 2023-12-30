# t-SNE implementation

## 1. What is t-SNE?
  In short, t-SNE is a dimentionality reduction algorithm like PCA. However, it is designed specifically for non-linear data.
  
## 2. How does it work in words?
  Step 1: t-SNE first create probability distributions based of distances between one point and other points.
  
  Step 2: Initialise points in a lower dimensional space.
  
  Step 3: Create probability distributions based on distances between one point and other points in that space.
  
  Step 4: Use Kullback-Leibler Divergence to calculate distance between distribution of every single point in the original space and the lower dimensional space.
  
  Step 5: Use gradient descent to update the points in the lower dimensional space.

## 3. How does it work in mathematics ?
![Screenshot from 2023-12-30 10-18-35](https://github.com/Mikyx-1/Machine_Learning_Algos/assets/92131994/99ab4b15-981b-4358-9a9e-a65a7ee78358)


  
