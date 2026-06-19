# FRC Compressive Strength Prediction

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Status](https://img.shields.io/badge/Status-Under%20Review-orange.svg)

This repository provides a public reproducibility package for predicting the compressive strength of fiber-reinforced concrete (FRC) with machine learning.

The manuscript associated with this repository is currently under review. For this reason, this release focuses on the materials needed by readers to inspect the dataset and reproduce the CatBoost downstream-reference example: the processed FRC dataset, a CatBoost notebook, a lightweight GUI notebook, and basic output CSV files. The complete multi-model benchmarking, statistical testing, interpretability, uncertainty, external-validation, and manuscript-figure pipelines are planned for release after paper acceptance.

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

## Dataset

The released dataset is a processed FRC compressive-strength dataset used for the public reproduction example.

- Main data file: `CatBoost/frc_compressive_strength.csv`
- GUI data copy: `GUI/frc_compressive_strength.csv`
- Backup copy: `Others/frc_compressive_strength.csv`
- Number of samples: 521
- Target variable: `CS`, compressive strength in MPa

The input variables include mixture-proportion, fiber-geometry, and engineered ratio descriptors:

| Column | Description |
|---|---|
| `C` | Cement content |
| `SF` | Silica fume content |
| `FA` | Fly ash content |
| `SL` | Slag content |
| `MK` | Metakaolin content |
| `Fine_Agg` | Fine aggregate content |
| `Coarse_Agg` | Coarse aggregate content |
| `W` | Water content |
| `SP` | Superplasticizer or admixture content |
| `L` | Fiber length |
| `D` | Fiber diameter |
| `Fiber_Volume_pct` | Fiber volume fraction |
| `W_C_ratio` | Water-to-cement ratio |
| `Total_Binder` | Total binder content |
| `Total_Fiber` | Total fiber volume descriptor |
| `SF_C_ratio` | Silica-fume-to-cement ratio |
| `W_Binder_ratio` | Water-to-binder ratio |
| `Fiber_Aspect_Ratio` | Fiber length-to-diameter ratio |

The CatBoost public example uses the 14-feature downstream-reference feature set retained for the released notebook:

```text
C, SF, FA, Fine_Agg, Coarse_Agg, W, SP, D,
W_C_ratio, Total_Binder, Total_Fiber, SF_C_ratio,
W_Binder_ratio, Fiber_Aspect_Ratio
```

---

## Model Role

The public notebook releases the CatBoost downstream-reference model used for reproduction and inspection.

The full manuscript reports a broader model-selection protocol:

- `ExtraTrees` achieved the best single-split internal benchmark.
- `StackingRegressor` achieved the highest repeated-holdout mean performance.
- `CatBoost` was retained as the downstream reference model from the statistically unresolved leading group and is used here for the public reproduction example.

This distinction is important: the public code is not claiming that CatBoost is the only leading model in the full study. It is the currently released reference pathway.

---

## Installation

Create a Python environment and install the core dependencies:

```bash
pip install numpy pandas scikit-learn catboost
```

The notebooks were prepared for Python 3.10+.

---

## Usage

### CatBoost Reproduction

Open and run:

```text
CatBoost/Catboost frc compressive.ipynb
```

The notebook:

1. Reads `CatBoost/frc_compressive_strength.csv`.
2. Selects the 14 public reference features.
3. Splits the dataset into training and test subsets using a fixed random seed.
4. Trains a CatBoost regressor.
5. Writes the output files under `CatBoost/outputs/`.

### GUI Example

Open and run:

```text
GUI/Gui compressive.ipynb
```

The GUI notebook trains the same CatBoost reference pathway from the released CSV file and provides a simple input interface for compressive-strength prediction.

---

## Output Files

| File | Description |
|---|---|
| `CatBoost/outputs/metrics.csv` | Training and test-set metrics for the released CatBoost example |
| `CatBoost/outputs/predictions.csv` | Test-set actual values, predictions, and errors |
| `CatBoost/outputs/feature_importance.csv` | CatBoost feature-importance ranking |

The current public CatBoost example gives the following test-set metrics:

| Metric | Test |
|---|---:|
| R2 | 0.9335 |
| RMSE | 4.4951 |
| MAE | 3.0608 |
| MAPE | 7.2092 |

---

## Currently Available

| Component | Status |
|---|---|
| Processed FRC dataset | Available |
| CatBoost downstream-reference notebook | Available |
| GUI notebook | Available |
| Basic CatBoost output CSV files | Available |

## Planned Release After Paper Acceptance

| Component | Status |
|---|---|
| Complete multi-model benchmarking code | Pending |
| Repeated-holdout statistical validation scripts | Pending |
| SHAP/ALE/LIME interpretability code | Pending |
| External-validation pipeline | Pending |
| Uncertainty-quantification modules | Pending |
| Figure-generation scripts | Pending |
| Full protocol notes and supplementary records | Pending |

---

## Citation

The associated manuscript is currently under review. Citation information will be updated after publication.
