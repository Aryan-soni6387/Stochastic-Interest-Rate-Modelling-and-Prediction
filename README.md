# Stochastic Interest Rate Modelling and Prediction

Finance Club, IIT Roorkee — Open Projects 2026

Implementation, calibration, and extension of the Cox–Ingersoll–Ross (CIR) model using real Treasury yield curve data.

---

## Project Overview

This project investigates whether the observed **3-Month Treasury Yield** contains sufficient information to reconstruct the remaining Treasury yield curve.

The project implements a **One-Factor CIR Model**, evaluates its predictive performance on unseen data, and extends the framework through a **Two-Factor CIR Model** to improve yield-curve reconstruction accuracy.

---

## Problem Statement

Given only the observed **3-Month Treasury Yield**, predict the remaining maturities of the Treasury yield curve:

- 6-Month Yield
- 9-Month Yield
- 1-Year Yield
- 2-Year Yield

The objective is to determine how effectively the short end of the term structure can explain the full yield curve.

---

## Models Implemented

### One-Factor CIR Model

The short rate follows:

$$
dr_t = \kappa(\theta-r_t)dt + \sigma\sqrt{r_t}\,dW_t
$$

Features:

- Mean-reverting interest-rate dynamics
- Closed-form bond-pricing solution
- Positive interest-rate property
- Yield-curve reconstruction from the observed 3M rate

### Two-Factor CIR Extension

The short rate is decomposed into:

$$
r_t = x_t + z_t
$$

where:

- $x_t$ = Long-run level factor
- $z_t$ = Short-run deviation factor

This extension captures additional yield-curve dynamics and improves predictive performance.

---

## Methodology

1. Data Cleaning and Preprocessing
2. Exploratory Data Analysis
3. CIR Theory and Bond Pricing
4. Model Calibration
5. Yield Curve Reconstruction
6. Out-of-Sample Evaluation
7. Two-Factor CIR Extension
8. Performance Comparison
9. Critical Analysis and Conclusions

---

## Results

| Model | Out-of-Sample R² |
|---------|---------|
| Base CIR | 0.9152 |
| Two-Factor CIR | 0.9158 |

### Key Findings

- The 3M Treasury Yield contains substantial information about the remaining term structure.
- The One-Factor CIR model achieves strong predictive performance.
- The Two-Factor CIR extension improves yield-curve reconstruction accuracy.
- The final model exceeds the Finance Club target of **R² > 0.85**.

---

## Repository Structure

```text
Stochastic-Interest-Rate-Modelling-and-Prediction/
│
├── data/
│   ├── train_data.csv
│   ├── test_data.csv
│   ├── test_data_3M.csv
│   └── two_factor_cir_predictions.csv
│
├── Stochastic_Interest_Rate_Modelling_and_Prediction.ipynb
├── Problem_statement.pdf
├── README.md
└── .gitignore
```

---

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- SciPy
- Scikit-Learn
- Google Colab

---

## Evaluation Metrics

Model performance is evaluated using:

- RMSE (Root Mean Squared Error)
- MAE (Mean Absolute Error)
- R² Score

All results are reported using out-of-sample test data.

---

## Author

Aryan Soni

FProject submitted as part of the Stochastic Interest Rate Modelling project — Finance Club, IIT Roorkee

