# Practical Application III — Comparing Classifiers (Bank Marketing)

## Executive Summary
This project builds and compares multiple classification models to predict whether a client will subscribe to a term deposit (`y`) based on client attributes, prior contact history, and macro-economic context variables from the UCI Bank Marketing dataset

- **Goal:** predict whether a client will subscribe to a term deposit (`y`) so the bank can prioritize outbound calls and reduce wasted contacts.  
- **Primary metric:** **ROC-AUC** (class imbalance ~11% "yes").  
- **Approach:** standardized numeric features + one-hot encoded categoricals; compared **Logistic Regression, KNN, Decision Tree, and SVM** with default settings and 5-fold stratified CV; then performed **grid search** per model.  
- **Outcome:** Logistic Regression provides the strongest ROC-AUC on the hold-out test set and can be used as a **ranking score** for call prioritization.  
- **Recommendation:** deploy batch scoring before campaigns, choose a threshold aligned to campaign goals (efficiency vs. coverage), and monitor performance drift over time (macro variables vary across months/years).

## Key Findings (summarized from final notebook results)

- Notebook runtime is ~6 minutes end-to-end on standard hardware while still including cross-validation and grid search for fair model comparison.
- The default model comparison results are reported in the notebook (`results_df`).
- Cross-validated performance is summarized in `cv_df`.
- Tuned model performance (grid search) is summarized in `grid_df`, with final hold-out test performance in `tuned_test_df`.

## Model Results Summary

Four classification models were compared to predict customer subscription to a term deposit. **Logistic Regression** achieved the strongest overall performance, with the highest ROC-AUC on both cross-validation (0.936) and the test set (0.944). Although KNN produced higher accuracy, ROC-AUC was prioritized due to class imbalance and the business objective of ranking customers for call prioritization. Based on performance, interpretability, and efficiency, **Logistic Regression was selected as the recommended model.**

By ranking customers based on predicted likelihood of subscription, the bank can focus outbound calls on higher-probability clients, improving campaign efficiency while reducing unnecessary contacts.

## Notebook

- [Practical_Assignment_3_Comparing_Classifiers_FINAL.ipynb](Practical_Assignment_3_Comparing_Classifiers_FINAL.ipynb)

## How to Run

1. Open the notebook in Jupyter.
2. Ensure `bank-additional-full.csv` is available in the appropriate data directory.
3. Run all cells top-to-bottom.

## Repo Hygiene

- Keep only the notebook, README, and (optionally) exported images/CSVs.
- Avoid committing large intermediate artifacts or temporary diagnostic files.
