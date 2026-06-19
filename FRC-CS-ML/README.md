# FRC Compressive Strength Prediction

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Under%20Review-orange.svg)

A machine learning framework for predicting the compressive strength of fiber-reinforced concrete (FRC) using CatBoost.

This repository is a public reproducibility package released while the manuscript is under review. It follows the same public-release boundary as `hollisterwong/UHPC-FS-ML`: primary dataset files, a CatBoost notebook, a GUI notebook, and basic output CSV files are available. Full manuscript materials and internal analysis pipelines will be released after publication.

---

## Repository Structure

```text
FRC-CS-ML/
├── README.md
├── CatBoost/
│   ├── Catboost frc compressive.ipynb
│   ├── frc_compressive_strength.csv
│   └── outputs/
│       ├── feature_importance.csv
│       ├── metrics.csv
│       └── predictions.csv
├── GUI/
│   ├── Gui compressive.ipynb
│   └── frc_compressive_strength.csv
└── Others/
    └── frc_compressive_strength.csv
```

---

## Currently Available

| Component | Status |
|---|---|
| CatBoost prediction notebook | Available |
| GUI notebook | Available |
| Primary training dataset | Available |
| Basic output CSV files | Available |

## Upon Paper Acceptance

| Component | Status |
|---|---|
| Complete multi-model benchmarking code | Pending |
| Statistical validation scripts | Pending |
| SHAP/ALE/LIME interpretability code | Pending |
| External-validation pipeline | Pending |
| Uncertainty quantification modules | Pending |
| Figure generation scripts | Pending |
| Full protocol notes and supplementary records | Pending |

---

## Usage

Open and run:

- `CatBoost/Catboost frc compressive.ipynb`
- `GUI/Gui compressive.ipynb`

The CatBoost notebook reads `frc_compressive_strength.csv` and writes the basic output files under `CatBoost/outputs/`.
