---
title: "A Groupe Fairness"
date: 2025-03-01T22:29:01+01:00
draft: false
---

# FRAPPÉ: Making AI Fair Without Retraining

## Introduction

Imagine developing a machine learning model to predict job performance, loan approvals, or student success. The model performs well overall — but when you dig deeper, you realize it treats certain demographic groups unfairly. In traditional machine learning pipelines, fixing this bias would often require **retraining the entire model**, which can be costly, slow, or even impossible if you don't have access to the training pipeline.

### Enter FRAPPÉ

**FRAPPÉ** (Fairness Framework for Post-Processing Everything) introduces a smarter approach. It **corrects unfairness after training**, applying fairness fixes directly to the model’s predictions — no need to retrain or even access the model’s internal code. This makes fair AI more accessible to teams working with pre-trained models or limited computational resources.

---

## Why Fairness in AI Matters

AI models increasingly make decisions that affect people’s lives — from loan applications to hiring decisions and medical diagnoses. If these systems are biased, they can perpetuate systemic discrimination. 

That’s why **group fairness** — ensuring that different demographic groups (e.g., based on race, gender, or age) receive equitable treatment — is a core concern in responsible AI development.

---

## Traditional Fairness Fixes — Why They Fall Short

Fairness methods usually fall into two categories:

- **In-Processing**: Modifies the model’s training process to add fairness constraints.
- **Post-Processing**: Adjusts the model’s predictions after training to improve fairness.

**In-processing methods are powerful but impractical when you don’t have access to the training pipeline or raw data.** That’s why post-processing methods like FRAPPÉ are so appealing.

---

## What Makes FRAPPÉ Unique?

FRAPPÉ brings several key benefits:

### 1. Works with Any Model

FRAPPÉ is **model-agnostic** — it works with deep neural networks, decision trees, or even black-box models from AutoML platforms. If your model produces scores or logits, FRAPPÉ can enhance its fairness.

### 2. Supports Different Fairness Definitions

FRAPPÉ can enforce different notions of fairness, including:

- **Statistical Parity** (ensuring similar outcomes across groups)
- **Equal Opportunity** (ensuring equal true positive rates across groups)
- **Equalized Odds** (balancing both true and false positive rates across groups)

### 3. No Sensitive Attributes at Prediction Time

Most fairness approaches rely on knowing demographic attributes (like race or gender) when making predictions. FRAPPÉ doesn’t. It learns how to correct unfairness using **all available features**, removing the need to collect sensitive data at prediction time.

---

## How FRAPPÉ Works

The core idea is to **add a fairness correction layer after the model’s predictions**. This layer, called `TPP(x)`, adjusts each prediction to reduce bias. The corrected prediction looks like:

fair_prediction = base_prediction + TPP(x)


- `base_prediction`: the original model’s prediction.
- `TPP(x)`: the fairness correction, based on the input features.

### Key Advantages

- **Modular**: The fairness correction is independent of the original model.
- **Flexible**: You can change the fairness definition (e.g., from statistical parity to equal opportunity) without touching the base model — just retrain the correction layer.

---

## Real-World Example

Imagine a hiring algorithm that scores applicants based on their resumes. Historical bias means female applicants receive lower scores on average. Traditionally, you’d need to retrain the whole model to correct this.

With FRAPPÉ, you leave the original model untouched — you just add a **fairness correction layer** that adjusts scores to ensure fair treatment across genders. This is faster, cheaper, and works even if you didn’t train the original model.

---

## Visual Summary

             +----------------------+
             |  Pre-trained Model   |
             +----------------------+
                        |
                        v
            +-------------------------+
            |  Fairness Correction    |
            |    (FRAPPÉ TPP)         |
            +-------------------------+
                        |
                        v
            +-------------------------+
            |   Fair Predictions      |
            +-------------------------+

---

## How Well Does FRAPPÉ Work?

### As Good as In-Processing

In experiments on datasets like **Adult Income**, **COMPAS**, and **HSLS**, FRAPPÉ achieved **similar fairness-accuracy trade-offs** as traditional in-processing methods — without the need for retraining.

### Better Than Other Post-Processing Methods

Compared to **FairProjection**, a leading post-processing method, FRAPPÉ consistently achieved **better fairness with lower accuracy loss** across datasets.

### Works Even with Partial Group Labels

Even when only a small portion of the training data includes group labels (e.g., race or gender), FRAPPÉ maintains strong performance — a major advantage over traditional methods, which often overfit when group labels are sparse.

---

## Why FRAPPÉ Matters

### Efficiency

- FRAPPÉ only trains a small **correction layer**, not the full model.
- This can **reduce training costs by over 90%** compared to in-processing methods.

### Flexibility

- Need to change from **equal opportunity** to **statistical parity**? No problem — just retrain the correction layer.

### Privacy-Friendly

- Because FRAPPÉ works without group labels at prediction time, it avoids the need to store or request sensitive demographic data.

---

## Final Thoughts

**FRAPPÉ offers a practical, flexible, and efficient way to ensure fairness in machine learning systems — even when retraining isn’t an option.**

By **decoupling fairness correction from model training**, FRAPPÉ makes responsible AI more accessible for real-world applications.

Whether you’re a data scientist, a policy maker, or someone interested in ethical AI, FRAPPÉ offers a promising new tool to build fairer technology — faster and with fewer constraints.

---

## References

- Alexandru Țifrea, Preethi Lahoti, Ben Packer, Yoni Halpern, Ahmad Beirami, Flavien Prost. *FRAPPÉ: A Group Fairness Framework for Post-Processing Everything*. ICML 2024. [arXiv Link](https://arxiv.org/abs/2312.02592)

- [Responsible AI Blog Guidelines - Télécom Paris](https://responsible-ai-datascience-ipparis.github.io/tutorial/)

---

## About the Author

**Arij Hajji**  
*M2 Data Science, Institut Polytechnique de Paris*  
*arij.hajji@telecom-paris.fr*

