---
date: 2025-06-14T20:30:00+03:00
draft: false
title: 'Parametric vs Non-Parametric Models in Supervised Learning'
---


Supervised learning models can be broadly categorized into two main types: parametric and non-parametric models. Understanding the differences between these approaches is crucial for selecting the right model for your machine learning tasks.

## Parametric Models

Parametric models make strong assumptions about the form of the function that maps inputs to outputs. They have a fixed number of parameters, regardless of the size of the training dataset.

Examples include:
- Linear Regression
- Logistic Regression
- Naive Bayes (Guassian / Multinomial)
- Perceptron
- Ridge / Lasso Regularization
- Neural Networks (MLP, CNN, etc.)
- SVM (Linear Kernel)

## Non-Parametric Models

Non-parametric models make fewer assumptions about the form of the function. The number of parameters grows with the size of the training dataset.

Examples include:
- Decision Trees
- Random Forests
- Support Vector Machines
- K-Nearest Neighbors
- Gradient Boosted Trees (XGBoost, Light GBM, CatBoost)
- SVM (RBF Kernel, Polynomial Kernel)

![Parametric vs Non-Parametric Models](/images/parametric_img.png)

*Figure 1: Comparison of parametric and non-parametric models in terms of flexibility and assumptions*

🤔 Question : 
A simple model like linear regression has 2 parameters y = w*x + b , parameters(w,b) (e.g. 2x + 5).
But a neural network (NN) has hundreds or even millions of weights.
How come NN is still considered “parametric”? With so many parameters?

🧠 Answer:
Parametric ≠ “with less parameters" model.

✅ Correct:
A parametric model is a fixed structure model; the number of parameters to be learned is independent of the data size.
That is, even if the data increases, the capacity of the model (number of parameters) does not increase - it remains constant.

🔍 Let's Explain with Examples:

1. Linear Regression (tek değişkenli):
y = w * x + b
Number of parameters = 2 (w, b)
→ No matter how much data you give, the model structure does not change.

2. Neural Network (e.g. 2-layer MLP):

Input: 100 dimensional → Hidden layer: 64 neurons → Output: 1 neuron
Number of parameters = (100×64 + 64) + (64×1 + 1) = 6529
→ The number of parameters is large but fixed.
→ Even if new data is added, the structure of the network does not change, the same number of weights are learned.

Therefore parametric.

![Parametric vs Non-Parametric Models](/images/img_parametric_params.png)
*Figure 2: Comparison of a simple linear regression model and a feedforward neural network in terms of parameterization. While linear regression involves only two parameters (weight and bias), the neural network consists of 6,529 parameters across multiple layers. Despite the difference in complexity, both models are considered parametric because their number of parameters remains fixed regardless of dataset size.*



## Key Differences

1. **Model Complexity**: Parametric models are simpler and have fewer parameters, while non-parametric models can be more complex and flexible.

2. **Training Data Requirements**: Parametric models typically require less training data, while non-parametric models often need more data to perform well.

3. **Computational Efficiency**: Parametric models are generally faster to train and make predictions, while non-parametric models can be more computationally intensive.

4. **Overfitting Risk**: Parametric models are less prone to overfitting but may underfit if the assumptions are incorrect. Non-parametric models have a higher risk of overfitting but can capture more complex patterns.

