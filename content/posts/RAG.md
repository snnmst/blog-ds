---
date : 2025-06-14T22:5:+18:00
draft : false
title : ' Parametric vs Non-Parametric Models in Supervised Learning'
---

# Parametric vs Non-Parametric Models in Supervised Learning

Supervised learning models can be broadly categorized into two main types: parametric and non-parametric models. Understanding the differences between these approaches is crucial for selecting the right model for your machine learning tasks.

## Parametric Models

Parametric models make strong assumptions about the form of the function that maps inputs to outputs. They have a fixed number of parameters, regardless of the size of the training dataset.

Examples include:
- Linear Regression
- Logistic Regression
- Linear Discriminant Analysis

## Non-Parametric Models

Non-parametric models make fewer assumptions about the form of the function. The number of parameters grows with the size of the training dataset.

Examples include:
- Decision Trees
- Random Forests
- Support Vector Machines
- K-Nearest Neighbors

![Parametric vs Non-Parametric Models](/images/parametric_img.png)

*Figure 1: Comparison of parametric and non-parametric models in terms of flexibility and assumptions*

## Key Differences

1. **Model Complexity**: Parametric models are simpler and have fewer parameters, while non-parametric models can be more complex and flexible.

2. **Training Data Requirements**: Parametric models typically require less training data, while non-parametric models often need more data to perform well.

3. **Computational Efficiency**: Parametric models are generally faster to train and make predictions, while non-parametric models can be more computationally intensive.

4. **Overfitting Risk**: Parametric models are less prone to overfitting but may underfit if the assumptions are incorrect. Non-parametric models have a higher risk of overfitting but can capture more complex patterns.

