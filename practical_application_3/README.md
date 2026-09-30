# Comparing Classifiers: Bank Marketing Campaign

## Overview
This project compares four classification algorithms — **K-Nearest Neighbors, Logistic
Regression, Decision Trees, and Support Vector Machines** — on a dataset of ~41,000 direct
marketing (telephone) contacts from a Portuguese bank. The goal is to predict whether a
client will subscribe to a term deposit, so the bank can target its calling effort more
efficiently. The work follows the **CRISP-DM** framework.

## Link to Notebook
[View the full analysis notebook →](./prompt_III.ipynb)

## Business Problem
Calling every client is expensive and most contacts don't convert (only ~11% subscribe).
A model that reliably identifies the clients most likely to say "yes" lets the bank call
fewer people while winning about the same number of subscriptions.

## Evaluation Metric
Because the classes are heavily imbalanced (~89% "no"), **accuracy is misleading** — a model
that predicts "no" for everyone scores ~89%. We evaluate primarily with **ROC-AUC**, which
measures how well the model ranks likely subscribers above unlikely ones regardless of the
imbalance.

## Summary of Findings
- All four models beat the majority-class baseline on ROC-AUC.
- The strongest predictors of subscription were the **outcome of a previous campaign**,
  the **contact method** (cellular beat landline), the **time of year**, and broader
  **economic indicators** (interest-rate and employment measures).
- `duration` (call length) was **dropped** — it is only known after a call ends and would
  leak the outcome into the model.

## Recommendations
1. Prioritize clients whose previous campaign ended in success.
2. Prefer cellular contact over landline.
3. Time campaigns with the calendar and economic conditions.
4. Use the model to rank the call list and call highest-probability clients first.

## Next Steps
- Handle class imbalance (class weights, SMOTE, threshold tuning) to improve recall on "yes".
- Add tree-based ensembles (Random Forest, Gradient Boosting).
- Fold in per-call cost and per-subscription revenue to set a profit-maximizing threshold.

## Repository Structure
```
practical_application_3/
├── README.md            # this file
├── prompt_III.ipynb     # full CRISP-DM analysis notebook
└── data/
    └── bank-additional-full.csv   # dataset (semicolon-separated; from UCI)
```

## How to Run
1. Download the data from the [UCI Bank Marketing repository](https://archive.ics.uci.edu/dataset/222/bank+marketing)
   and place `bank-additional-full.csv` in the `data/` folder.
2. Open `prompt_III.ipynb` and run all cells top to bottom.

Requires: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`.
