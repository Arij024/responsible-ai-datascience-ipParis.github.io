---
title: "A Groupe Fairness"
date: 2025-03-01T22:29:01+01:00
draft: false
---

# FRAPPÉ: Making AI Fair Without Retraining

## Introduction 


Fairness in predictive models has become a crucial issue in the rapidly developing field of machine learning. Reducing bias in these systems is crucial to preventing the continuation of social injustices as machine learning algorithms are increasingly used in high-stakes applications including criminal justice, lending, and employment.  
Consider creating a machine learning model to predict student outcomes, loan approvals, or job performance. On the whole, the model performs well, but on closer inspection, you find that it treats several demographic groups unfairly. It is often necessary to retrain the entire model to correct this bias in typical machine learning pipelines, which can be costly, time-consuming, or even impossible if you don't have access to the learning pipeline.

## FRAPPÉ is here 

FRAPPÉ (Fairness Framework for Post-Processing Everything) offers a revolutionary method and is building the roadmap to the way we think about fairness in machine learning. In this blog, we’ll try to go through the key ideas, contributions, and implications of this innovative work.


## Why Fairness in AI Matters

(AI) algorithms are increasingly  affecting people's lives, from loan applications to job decisions to medical diagnoses.  If there's a chance that these processes can be compromised by bias, they are likely to promote systemic discrimination. 

Consequently, one of the key issues in the ethical development of AI is **group fairness**, i.e. ensuring that different demographic groups (e.g. based on race, gender or age) receive fair treatment.
Ensuring that algorithms do not disproportionately harm or help certain groups, particularly those identified by sensitive characteristics such as age, gender or race, is the goal of fairness in artificial intelligence.  Achieving fairness, however, is no simple matter.  Each of the thousands of definitions of fairness (such as equal opportunity, statistical parity and equalization of opportunity) involves trade-offs between predictive accuracy and fairness.

Traditionally, there are three types of fairness mitigation strategies:

- **Pre-processing**: Removing bias from training data.
- **In-processing**: Incorporating fairness constraints or regularizers during training.
- **Post-processing**: Adjusting the outputs to achieve fairness.


 On one hand, in-processing are highly effective ,they often require retraining of the entire model, which is known to be computationally expensive and impractical in many real-life situations.  On the other hand, post-processing offers more flexibility, it has been limited to particular contexts and fairness standards.



---


## Why FRAPPÉ is a Game-Changer ?

### 1. Works with Any Model

FRAPPÉ is **model-agnostic** — meaning thay it can is well functional with deep neural networks, decision trees, or even black-box models . We can put it as the following if your model produces scores or logits, FRAPPÉ can enhance its fairness.

 ### 2. Broad applicability: 
 FRAPPÉ can be used with any quantitative concept of fairness, unlike previous post-processing techniques which are tailored to particular definitions of fairness (such as statistical parity) or problematic situations (such as binary sensitive attributes).  This makes it possible to take into account parameters incompatible with previous post-processing techniques due to continuous sensitive qualities (e.g. age, income).
 FRAPPÉ can enforce different notions of fairness, including:

- **Statistical Parity** (ensuring similar outcomes across groups)
- **Equal Opportunity** (ensuring equal true positive rates across groups)
- **Equalized Odds** (balancing both true and false positive rates across groups)

 ### 3.Absence of sensitive attributes during inference: 
 Many post-processing techniques require knowledge of sensitive attributes (such as gender or race) at the time of inference, which is sometimes impractical or morally dubious.  By simulating the post-hoc transformation as a function of all covariates, not just the sensitive characteristic, FRAPPÉ gets around this problem.

 
### 4.Efficient and modular: 
The modular design of FRAPPÉ' makes it easier to adapt to different definitions of fairness and speeds up calculations since only the post-hoc module needs to be modified, rather than the entire model.

### 5.Handling Partial Group Labels: 
In most real-life scenarios, only a small part of the data has sensitive attributes. In this case FRAPPÉ outperforms in-processing methods , as it avoids over-adjusting the fairness regularizer and keeps a good trade-off between fairness and accuracy.



---

## How FRAPPÉ Works
Here's how it works:

 Base model: Predictions are made using a pre-trained model, such as logistic regression, random forest or neural network.

 Post hoc module: The results of the basic model go through direct additive alternations. Like processing techniques, this module is trained using a fairness regularizer, but during inference, it does not need the access to sensitive attributes or the training pipeline .

 The concept is  **applying a fairness adjustment layer after model predictions**.  To decrease bias, this layer, called `TPP(x)`, changes each prediction.  The updated prediction is as follows:

 Base_prediction + TPP(x) = Fair_prediction


 - `base_prediction` : the prediction of the first model.
 - `TPP(x)` : the fairness correction based on input characteristics.

### Key Advantages

The authors of the article use comprehensive trials on a number of datasets, including Adult, COMPAS, HSLS, ENEM and Communities & Crime, to show the effectiveness of FRAPPÉ.  The key findings are as follows:

 - FRAPPÉ is more computationally efficient than in-house processing techniques, while offering comparable or better fairness-error trade-offs.

 - It outperforms current post-processing methods such as FairProjection, particularly in the presence of continuous sensitive features or partial group labels.

 - Due to its modular nature, FRAPPÉ is very useful for real-world applications, and can be quickly adapted to a variety of fairness definitions or trade-offs.

## Real-World Example

Let's take in mind a hiring algorithm ,it basically scores applicants based on their resumes. An exemple of historical bias means female applicants womm receive lower scores on average. Traditionally, we’d need to retrain the whole model to correct this.

Using FRAPPÉ, we can leave the original model untouched — we just add a **fairness correction layer** that adjusts scores to ensure fair treatment across genders. This is faster, cheaper, and works even if we didn’t train the original model.

## How Well Does FRAPPÉ Work?

### As Good as In-Processing

Experimenting with datasets such as **Adult Income**, **COMPAS**, and **HSLS**, FRAPPÉ scored **similar fairness-accuracy trade-offs** as traditional in-processing moduls without retraining.

### Better Than Other Post-Processing Methods

Compared to **FairProjection**, a leading post-processing method, FRAPPÉ consistently achieved **better fairness with lower accuracy loss** across datasets.

### Even works with Partial Group Labels

When even only a small percentage of the training data includes group labels (e.g., race or gender), FRAPPÉ keeps a strong performance — a great positive point compared to traditional methods, which often overfit when group labels are sparse.

## Why FRAPPÉ Matters

### Efficiency: 
FRAPPÉ can **decrease training costs upto 90%** compared to in-processing approaches, as it only learns a small **layer of correction** and not the entire model.
 ### Flexibility: 
 Is **statistical parity** required instead of **equal opportunity**?  Just relearn the correction layer to solve the problem.
 ### Privacy: 
 For FRAPPÉ the storage or extraction of sensitive demographic data is not crucial or obigatory, as it works without group labels at the time of prediction.

## Final Thoughts

When retraining is not an option, FRAPPÉ provides a useful, adaptable and efficient method for ensuring fairness in machine learning systems.

 FRAPPÉ can make the usage of responsible AI in practical applications by **separating model learning from fairness correction**.




 For those interested in ethical AI, data science or policy-making, FRAPPÉ presents a promising new tool for developing fairer technologies faster and with fewer limitations.

## What do you think about FRAPPÉ? 
Could this framework be the key to making fairness mitigation more practical and scalable? We are curious for you to share your thoughts !
## References

- Alexandru Țifrea, Preethi Lahoti, Ben Packer, Yoni Halpern, Ahmad Beirami, Flavien Prost. *FRAPPÉ: A Group Fairness Framework for Post-Processing Everything*. ICML 2024. [arXiv Link](https://arxiv.org/abs/2312.02592)

- [Responsible AI Blog Guidelines - Télécom Paris](https://responsible-ai-datascience-ipparis.github.io/tutorial/)

## About the Author

**Arij Hajji** 

*M2 Data Science, Institut Polytechnique de Paris*  
*arij.hajji@telecom-paris.fr*

