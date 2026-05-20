# PDAN8411 POE Part 2 — Classification Student Guide

## Overview

This guide provides the structure, expectations, and requirements for Part 2 of your POE. Your task is to build a **classification model** on a cancer-related dataset, evaluate it, and write a supporting report.

Read this guide carefully. The notebook skeleton (`PDAN8411_Part2_Guide.ipynb`) mirrors this structure — work through it section by section.

---

## The Dataset

You are working with a **cancer classification dataset** (e.g., the Wisconsin Breast Cancer Dataset or a similar well-sourced alternative). The model must predict a **categorical outcome** such as whether a tumour is malignant or benign.

**Recommended dataset:** UCI Breast Cancer Wisconsin (Diagnostic) — available on [Kaggle](https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data) and the [UCI ML Repository](https://archive.ics.uci.edu/ml/datasets/breast+cancer+wisconsin+(diagnostic)).

---

## What You Need to Submit

1. **A Jupyter Notebook (.ipynb)** — your complete analysis with code and markdown interpretation cells
2. **A PDF Report** — written for a non-technical audience, summarising your process and findings

Both must be pushed to your GitHub Classroom repository before the deadline.

---

## Notebook Structure & Requirements

### Section 1 — Introduction & Dataset Justification (Rubric: 10 Marks)

To score in the **Excellent** band (8–10 marks) you must address all of the following:

- Define classification and explain why it suits your target variable
- State and justify your dataset source (UCI, Kaggle, etc.)
- Report the Kaggle usability score if applicable, and explain what it indicates about data quality
- Assess whether the dataset is well-curated (balanced classes, no excessive noise, meaningful features)
- Identify **at least two pitfalls** in the dataset and explain how you plan to address each

> A pitfall table is an effective way to present this — see the notebook for an example.

---

### Section 2 — Analysis Plan (Rubric: 10 Marks)

To score in the **Excellent** band (8–10 marks) you must:

- Plan every major step **before writing code**
- Cover all five areas: EDA, Feature Selection, Model Training, Evaluation, and Report
- Go beyond the course material by including considerations such as class imbalance handling, metric selection rationale, or algorithm comparison strategy
- Be **succinct** — marks are deducted for excessively wordy or vague plans

A table or structured infographic is recommended. The plan should read like a roadmap a data scientist would actually follow.

---

### Section 3 — EDA & Data Cleaning (Rubric: 20 Marks)

To score in the **Excellent** band (15–20 marks) your EDA must:

- Inspect shape, data types, missing values, and duplicates
- Produce and **interpret** a class distribution plot
- Produce and **interpret** feature distribution histograms
- Produce and **interpret** a correlation heatmap
- Produce and **interpret** boxplots showing feature distributions by class

**Critical rule: every visualisation must be followed by a markdown interpretation.** Do not leave graphs uncommented. Tell the reader what the graph reveals and how it informs your next step. The only exception is basic inspection outputs like `df.describe()` — only comment on these if they reveal something statistically significant.

---

### Section 4 — Feature Engineering & Selection (Part of EDA Marks)

- Encode categorical variables (LabelEncoder for binary targets, get_dummies for multi-category features)
- Drop non-informative columns (e.g., ID columns)
- Use `SelectKBest` with `f_classif` or another justified selection method to rank features
- Apply `StandardScaler` before training — this is especially important for SVM and Logistic Regression
- Use a **stratified** train/test split (80/20) to preserve class balance

---

### Section 5 — Model Training & Comparison (Rubric: 10 Marks)

You are encouraged to train and compare **more than one algorithm**. Suitable options include:

- Logistic Regression
- Support Vector Machine (SVM)
- Naive Bayes
- K-Nearest Neighbours (optional, for additional research marks)

Use `classification_report` to evaluate each model. Print the full report for every model trained.

To score in the **Excellent** band (8–10 marks) your notebook must show evidence of additional research — for example, tuning hyperparameters, comparing kernel types in SVM, or explaining why a particular algorithm is more theoretically appropriate for your data.

---

### Section 6 — Evaluation & Interpretation (Rubric: 20 Marks)

To score in the **Excellent** band (15–20 marks) your evaluation must include:

- Classification reports for all models
- Confusion matrices for all models (with interpretation)
- ROC curves with AUC scores (with interpretation)
- A summary comparison table
- A **written justification** of your chosen best model that explains:
  - Why that model outperforms the others
  - Which metric you prioritised and why (accuracy alone is not sufficient justification)
  - What the model's limitations are

---

### Section 7 — Unseen Data Testing

To demonstrate that your model generalises, generate **3–5 synthetic data points** based on realistic feature ranges from your EDA, run them through your trained model, and interpret the predictions.

You are **not** required to fabricate data to compensate for a poor dataset — use the real dataset as-is for all training and evaluation. The synthetic samples are for demonstration purposes only.

---

### Section 8 — Report (Rubric: 20 Marks)

Your PDF report must be written for a **non-technical reader** (e.g., a hospital administrator or medical scheme manager). It should cover:

1. Executive Summary
2. Introduction & Dataset Justification
3. Analysis Plan
4. EDA Findings (include key visualisations)
5. Model Training & Comparison
6. Results & Interpretation
7. Conclusion & Recommendations
8. References (Harvard style)

To score in the **Excellent** band (15–20 marks) the report must be fully detailed, explain every step of the process, and demonstrate comprehensive additional research.

---

## Submitting to GitHub

### Using VS Code / GitHub Desktop

1. Accept the assignment link from ARC
2. If prompted about an organisation — go to your profile picture → Organisations → Accept
3. Click the green **Code** button → **Open with GitHub Desktop**
4. Copy your `.ipynb` and PDF report into the cloned folder
5. In GitHub Desktop: add a summary → **Commit to main** → **Push to origin**
6. Verify your files are visible on GitHub before the deadline

### Using Google Colab

1. Download your `.ipynb` from Colab into the cloned folder, then follow the steps above
2. Or: go to **Settings → GitHub** in Colab, link your account, and use **File → Save a copy in GitHub** to push directly to your assignment repo

---

## Common Mistakes to Avoid

| Mistake | What to do instead |
|---|---|
| Generating graphs without interpreting them | Every plot needs a markdown cell below it explaining what you observed |
| Using accuracy as the only metric | Report precision, recall, F1, and AUC — especially important with imbalanced classes |
| Not scaling features before SVM or Logistic Regression | Always apply `StandardScaler` before distance-based or gradient-based algorithms |
| Forgetting the stratified split | Use `stratify=y` in `train_test_split` to maintain class ratios |
| Planning section too vague | The plan must be specific enough that someone else could follow it |
| No justification of the chosen model | Explicitly state why your chosen model is better for this specific problem |

---

## References (Harvard Style)

List all sources used in your notebook and report. Examples:

- Pedregosa, F. et al. (2011) *Scikit-learn: Machine Learning in Python*. Available at: https://scikit-learn.org
- UCI Machine Learning Repository (1995) *Breast Cancer Wisconsin (Diagnostic) Dataset*. Available at: https://archive.ics.uci.edu/ml/datasets/breast+cancer+wisconsin+(diagnostic)
- Street, W.N., Wolberg, W.H. and Mangasarian, O.L. (1993) 'Nuclear feature extraction for breast tumour diagnosis', *SPIE Proceedings*, 1905, pp. 861–870.

If you used an AI tool (e.g., Claude, ChatGPT), reference it as:

> Anthropic (2026) *Claude AI Assistant*. Available at: https://claude.ai (Accessed: [Your date]).
