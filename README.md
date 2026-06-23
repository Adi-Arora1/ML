# Predicting Aqueous Solubility (LogS) from Molecular Descriptors
### A Comparative Study of Linear Regression and Random Forest

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Adi-Arora1/ML/blob/main/LReg%20%26%20Randomforest%20regression.ipynb)
![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data-green.svg)

---

## Overview

Aqueous solubility is one of the most critical properties in drug discovery — a molecule that cannot dissolve in water cannot reach its biological target. This project applies two machine learning regression models to predict the **LogS** (log of aqueous solubility) of drug-like molecules using the well-known **Delaney dataset**.

The goal is to build, evaluate, and compare a **Linear Regression** and a **Random Forest Regressor**, giving insight into when a simple model suffices versus when an ensemble approach adds value.

---

## Dataset

**Source:** [Delaney Solubility with Descriptors](https://raw.githubusercontent.com/dataprofessor/data/refs/heads/master/delaney_solubility_with_descriptors.csv)

The dataset contains molecular descriptor features for a set of organic compounds along with their experimentally measured LogS values.

| Column | Description |
|---|---|
| `MolLogP` | Octanol-water partition coefficient |
| `MolWt` | Molecular weight |
| `NumRotatableBonds` | Number of rotatable bonds |
| `AromaticProportion` | Proportion of aromatic heavy atoms |
| `logS` | **Target** — log of aqueous solubility |

- **Total features (X):** 4 molecular descriptors
- **Target (Y):** `logS`
- **Train/Test split:** 80% / 20% (`random_state=100`)

---

## Project Workflow

```
Load Data → Separate X & Y → Train/Test Split → Build Models → Evaluate → Compare → Visualize
```

**1. Load Data**
The dataset is loaded directly from a public URL using `pandas`.

**2. Data Separation**
`logS` is separated as the target variable `Y`; all remaining columns form the feature matrix `X`.

**3. Train/Test Split**
An 80/20 split is applied using `train_test_split` with `random_state=100` for reproducibility.

**4. Model Building**

- **Linear Regression** — a baseline parametric model from `sklearn.linear_model`
- **Random Forest Regressor** — an ensemble tree-based model from `sklearn.ensemble`, trained with `max_depth=2` and `random_state=100`

**5. Model Evaluation**
Both models are evaluated on training and test sets using:
- **MSE** (Mean Squared Error) — measures average squared prediction error
- **R²** (R-squared) — measures proportion of variance explained by the model

**6. Model Comparison**
Results from both models are compiled into a unified comparison table using `pd.concat`.

**7. Visualization**
A scatter plot of **Predicted LogS vs Experimental LogS** is generated using `matplotlib` to visually assess model fit.

---

## Results

| Method | Training MSE | Training R² | Test MSE | Test R² |
|---|---|---|---|---|
| Linear Regression |1.007536||0.764505|1.020695|0.789162|
| Random Forest |1.028228|0.759669|1.407688|0.709223|



---

## Technologies Used

| Library | Purpose |
|---|---|
| `pandas` | Data loading and manipulation |
| `scikit-learn` | Model building and evaluation |
| `matplotlib` | Data visualization |
| `numpy` | Numerical operations |

---

## How to Run

**Option 1 — Google Colab (recommended)**

Click the badge at the top of this README. No setup required.

**Option 2 — Local**

```bash
# Clone the repository
git clone https://github.com/Adi-Arora1/ML.git
cd ML

# Install dependencies
pip install pandas scikit-learn matplotlib numpy

# Launch Jupyter
jupyter notebook "LReg & Randomforest regression.ipynb"
```

---

## Key Takeaways

- Linear Regression provides a strong, interpretable baseline for LogS prediction from molecular descriptors.
- Random Forest with a shallow depth (`max_depth=2`) is constrained here; tuning this hyperparameter could yield stronger results.
- MSE and R² together give a complete picture — R² shows explanatory power while MSE captures absolute prediction error.
- Scatter plots of predicted vs experimental values are an intuitive way to spot systematic bias in regression models.

---

## Author

**Adi Arora**
[GitHub](https://github.com/Adi-Arora1)

---

## Acknowledgements

Dataset sourced from the [Delaney (ESOL) solubility dataset](https://pubs.acs.org/doi/10.1021/ci034243x), originally published by John S. Delaney (2004). Accessed via [dataprofessor](https://github.com/dataprofessor/data).
