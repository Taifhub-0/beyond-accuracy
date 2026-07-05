# Beyond Accuracy: A Deep Investigation into Failure Mechanisms of Classification Models

## Overview
This project investigates why accuracy alone is not enough to evaluate machine learning classification models. Through a practical case study on disease prediction, we show how a model can score 100% accuracy while being fundamentally broken.

## The Problem
Accuracy is the most commonly used metric to judge a model, but a model can score 99–100% and still fail completely in the real world. High accuracy can hide serious issues such as data leakage, label noise, memorization, and bias — problems that only surface after deployment, when the cost of failure is highest.

## Key Finding: Data Leakage Case Study
We trained KNN, SVM, and Random Forest models to predict 41 diseases from patient symptoms using a Kaggle dataset (4,920 records). All three models achieved a perfect 100% accuracy — which immediately raised a red flag.

Investigation revealed the real cause: **4,616 out of 4,920 records (93.8%) were exact duplicates**, leaving only 304 unique patterns. Because the train-test split was done *after* this duplication, the same patient records appeared in both the training and test sets. The models weren't learning to diagnose disease — they were memorizing answers they had already seen.

The confusion matrix confirmed this: a perfect diagonal across all 41 disease classes, a classic sign of memorization rather than genuine learning.

## Six Hidden Failure Modes Covered
1. **Baseline Illusion** — when a simple/dumb model matches a complex one
2. **Data Leakage** — target leakage and train-test contamination
3. **Label Noise** — incorrect labels degrading model quality
4. **Memorization vs. Learning** — perfect training scores that don't generalize
5. **Adversarial Examples** — small input changes that fool models
6. **Algorithmic Bias** — high accuracy masking unfair outcomes across groups (COMPAS, Amazon hiring, healthcare allocation)

## Tech Stack
- Python
- pandas, numpy
- scikit-learn (KNN, SVM, Random Forest)
- matplotlib, seaborn
- Google Colab

## Files in This Repo
- `notebook.ipynb` — full analysis: preprocessing, model training, duplicate detection, evaluation
- `report.pdf` — full project report
- `presentation.pdf` — project slides

## Practical Checklist (from our conclusions)
Before trusting any model, ask:
- Was the train-test split done *before* preprocessing?
- Are there duplicate records that crossed the split boundary?
- Was the model compared against a simple baseline?
- Were F1, precision, and recall checked — not just accuracy?
- Was performance tested on independent, unseen data?

## Team
- Malath Al-Harthy — 442006687
- Taif Alzahrani — 443038092
- Hadeel Al-Zahrani — 444022117

## Supervisor
Dr. Saad Algithami

## Course
Machine Learning — Faculty of Computing and Information, Al-Baha University — 2026
