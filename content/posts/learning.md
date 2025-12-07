---
date: 2025-12-07
draft: false
title: 'Machine Learning 101: What Does "Learning" Actually Mean?'
---

We often hear buzzwords: Artificial Intelligence, Machine Learning, Deep Learning... But wait, machine is learning *what*? And exactly *how*?

Most courses and books follow the same organized curriculum: Supervised Learning, Unsupervised Learning, Gradient Descent, Learning Rate, Hyperparameter Tuning, etc. But before diving into these complex terms, we need to answer a fundamental question: **What is "learning"?**

While revisiting [*Grokking Deep Learning*](https://www.link-adresi.com) by Andrew W. Trask, I was reminded of a simple truth: *"If you can explain something in simple terms, you really understand it."* Trask explains concepts like prediction and gradient descent without drowning in technical jargon. Inspired by this, I want to explore what prediction really is and what "learning" means for a machine.

## The Anatomy of Prediction

Let’s keep it simple. Regardless of the project, we always have three components:

1. **Input:** The data we have (e.g., 2).
2. **True Value (Label):** The result we want to achieve (e.g., 0.8).
3. **Weight:** The magic number that determines the importance of the input.

To find the relationship between the Input and the True Value, we need a mechanism. This is where we encounter the **"Weight"**. We try to predict the output by processing the input through this weight. 

Simply put:

> **Prediction = Input * Weight**

## But Why Multiply?

You might ask: *"Why did we multiply the input and weight? Why didn't we add or subtract them?"* This is a crucial intuition that is often overlooked.

1. **Addition/Subtraction doesn't express "Importance":** If we just added the weight, it would only apply a constant offset, regardless of whether the input is huge or tiny. It cannot scale the effect of the input.
2. **Multiplication allows "Scaling":** Multiplication allows the weight to amplify or dampen the input signal.
    * If `w > 1`: It amplifies the input.
    * If `0 < w < 1`: It reduces (dampens) the input's effect.
    * If `w < 0`: It reverses the relationship (negative correlation).
    
This flexibility is exactly what allows a model to "learn" complex patterns.

## Defining the "Error"

If we have a *Prediction* and a *True Value*, we naturally have an **Error**. We need to measure how far off we are to improve our next guess.

Intuitively, error is: `Error = Prediction - True Value`

But wait, is it that simple? Let's say our target is **100**.
* **Guess 1:** 1100 → Error = 1000 (Too high)
* **Guess 2:** -900 → Error = -1000 (Too low)

If we sum these errors, we get **0**. It looks like we were perfect, but in reality, we missed by a huge margin twice! To prevent positive and negative errors from canceling each other out, we use the **squared error**:

> **Error = (Prediction - True Value)²**

By squaring the difference, we ensure that the error is always positive, and we punish larger mistakes more severely.

---

## So, How Do We Reduce the Error?

Now that we have an error value, what’s next? To make a better prediction, we need to minimize this error—ideally, bring it down to zero. Let’s look at our equation again:

> **Error = ((Input * Weight) - True Value)²**

Here is the critical realization:
* **Input** is fixed (it’s our data).
* **True Value** is fixed (it’s our target).

We cannot change the data or the goal. This leaves us with only one variable to optimize (or simply, to *tweak*): the **Weight**.

The model starts with a random guess. It could be 0, 0.5, or even 124. We don't know yet. Let’s simulate a manual iteration to see what happens.

### Let's try to guess the weight:
* **Input:** 2
* **True Value:** 0.8
* **Initial Weight:** 0.5

**Step 1:**
* Prediction = 2 * 0.5 = 1.0
* Error = (1.0 - 0.8)² = 0.04

We missed. The error is **0.04**. We need to change the weight to reduce this error. In the next iteration, let’s try increasing the weight. Let's say, **0.7**.

**Step 2:**
* Prediction = 2 * 0.7 = 1.4
* Error = (1.4 - 0.8)² = 0.36

**Wait!** The error increased from 0.04 to 0.36. We went in the wrong direction. Increasing the weight was a mistake. So, logic dictates we should have *decreased* it instead. Let's try **0.4**.

**Step 3:**
* Prediction = 2 * 0.4 = 0.8
* Error = (0.8 - 0.8)² = 0

**Eureka!** The error is 0. We found the perfect weight.

![Guessing Process](/images/weight_opt.png)

## The Problem with Guessing

We solved it, but we did it by guessing. We first increased the weight (wrong move), saw the error rise, and then realized we should decrease it.

In a simple example, guessing works. But imagine a model with millions of weights. We can't just guess "up or down" for all of them.

We need a way to know—**before we take a step**—whether we should increase or decrease the weight. 

This brings us to the most fundamental concept in learning: **Direction.**

We realized that guessing is inefficient. We need a compass that tells us exactly which way to move the weight and by how much. In mathematics, this compass has a name: The Derivative. In the next post, we will demystify Gradient Descent and see how machines find this 'direction' automatically, without guessing...