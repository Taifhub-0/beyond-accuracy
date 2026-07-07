# Beyond Accuracy: A Deep Investigation into Failure Mechanisms of Classification Models

## Overview
This project investigates why accuracy alone is not enough to evaluate machine learning classification models. Through a practical case study on disease prediction, we show how a model can score 100% accuracy while being fundamentally broken.

## Key Finding: Data Leakage Case Study
We trained KNN, SVM, and Random Forest models to predict 41 diseases from patient symptoms using a Kaggle dataset (4,920 records). All three models achieved a perfect 100% accuracy — an immediate red flag.

Investigation revealed the real cause: 4,616 out of 4,920 records (93.8%) were exact duplicates, leaving only 304 unique patterns. Because the train-test split was done after this duplication, the same patient records appeared in both the training and test sets. The models weren't learning to diagnose disease — they were memorizing answers they had already seen.

The confusion matrix confirmed this: a perfect diagonal across all 41 disease classes, a classic sign of memorization rather than genuine learning.

## Other Hidden Failure Modes Covered
- Baseline Illusion — when a simple/dumb model matches a complex one
- Label Noise — incorrect labels degrading model quality
- Memorization vs. Learning — perfect training scores that don't generalize
- Adversarial Examples — small input changes that fool models
- Algorithmic Bias — high accuracy masking unfair outcomes across groups (COMPAS, Amazon hiring, healthcare allocation)

(Full explanations and analysis for each are in report.pdf.)

## Tech Stack
Python · pandas · numpy · scikit-learn (KNN, SVM, Random Forest) · matplotlib · seaborn · Google Colab

## Files in This Repo
- notebook.ipynb — full analysis: preprocessing, model training, duplicate detection, evaluation
- report.pdf — full project report
- presentation.pdf — project slides


## How to Run
- Open notebook.ipynb in Google Colab or Jupyter.
- Install dependencies: pip install pandas numpy scikit-learn matplotlib seaborn
- Run all cells in order.


## Practical Checklist (from our conclusions)
- Before trusting any model, ask:
- Was the train-test split done before preprocessing?
- Are there duplicate records that crossed the split boundary?
- Was the model compared against a simple baseline?
- Were F1, precision, and recall checked — not just accuracy?
- Was performance tested on independent, unseen data?


## Team & Contributions
This project was completed collaboratively by a team of three students as part of the Machine Learning course at Al-Baha University.

### My Contribution
- Sections written: Data Leakage Case Study, Algorithmic Bias, Conclusion & Recommendations
- Responsibilities: Report structure, document formatting, analysis write-up


## Supervisor
Dr. Saad Algithami
Faculty of Computing and Information, Al-Baha University — 2026

# License
MIT License - Feel free to use this for educational purposes.
