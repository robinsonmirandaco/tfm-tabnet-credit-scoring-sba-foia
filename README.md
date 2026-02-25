# Interpretable Tabular Deep Learning for SME Credit Scoring  
### Comparative Benchmark: TabNet vs XGBoost vs Logistic Regression

Master’s Thesis – MSc in Artificial Intelligence  
Universidad Internacional de La Rioja (UNIR)  
Author: Robinson José Miranda Pérez

Year: 2026  

---

## 📌 Overview

This repository contains the full reproducible experimental pipeline for evaluating the viability of interpretable deep learning in SME credit scoring.

The study compares:

- Logistic Regression (baseline statistical model)
- XGBoost (industry-standard gradient boosting)
- TabNet (interpretable tabular deep learning)

using SBA FOIA 7(a) public data.

The evaluation focuses on:

- Discrimination (ROC-AUC, PR-AUC, KS)
- Calibration (Brier Score, reliability curves)
- Stability (inter-fold variability)
- Interpretability (coefficients, SHAP, attention masks)
- Robustness under temporal distribution shift (pre-COVID vs post-COVID stress test)

---

## 🎯 Research Objective

To evaluate whether TabNet achieves non-inferiority relative to XGBoost (Δ ≤ 0.02 in ROC-AUC) while maintaining comparable calibration and interpretability under a controlled and reproducible protocol.

---

## 📊 Dataset

Source: U.S. Small Business Administration (SBA)  
Program: FOIA 7(a) Loan Data  

This repository **does not redistribute the original data**.

Data must be obtained from:
https://data.sba.gov

Preprocessing scripts are provided to reproduce the dataset used in the experiments.

---

## 🧪 Experimental Design

- Temporal split:
  - Base: Pre-COVID period
  - Stress: Post-COVID period
- Stratified 5-fold cross-validation (base period)
- Identical preprocessing and splits across models
- Hyperparameter optimization using ROC-AUC
- Paired statistical testing (95% confidence intervals)
- Non-inferiority margin: Δ = 0.02 (ROC-AUC)

---

## 📈 Evaluation Metrics

Primary:
- ROC-AUC

Secondary:
- PR-AUC
- KS statistic
- F1-score
- Confusion matrix

Calibration:
- Brier Score
- Reliability curves

Interpretability:
- Logistic coefficients
- SHAP values (XGBoost)
- Feature attention masks (TabNet)

---

## 🔁 Reproducibility

- Python version: [e.g., 3.11]
- Fixed random seed (SEED = 42)
- Full environment specification included
- Deterministic cross-validation splits

---

## 📂 Repository Structure

See project structure below.

<img width="365" height="695" alt="image" src="https://github.com/user-attachments/assets/7d5ea1ef-515a-4f10-aebe-6ffc2dcf716b" />


---

## 📜 License

This project is licensed under the Apache License 2.0.

---

## 📚 Citation

If you use this work, please cite:

Miranda R. (2026).  
Interpretable Tabular Deep Learning for SME Credit Scoring.  
Master’s Thesis, UNIR.

---

## ⚠ Disclaimer

This repository is intended for academic research purposes only.  
No financial or credit decisions should be based on this implementation.
