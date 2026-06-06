# Stochastic Interest Rate Modelling and Prediction

Finance Club, IIT Roorkee — Open Projects 2026

Implementation, Calibration, and Extension of the Cox–Ingersoll–Ross (CIR) Model on Real Treasury Yield Curve Data.

---

# Project Overview

This project investigates whether the observed **3-Month Treasury Yield** contains sufficient information to reconstruct the remaining Treasury yield curve.

The Cox–Ingersoll–Ross (CIR) interest-rate model is calibrated using historical Treasury yield data and evaluated on unseen observations. A Two-Factor CIR extension is then implemented to improve yield-curve reconstruction performance.

The project covers theoretical foundations, parameter calibration, out-of-sample evaluation, and model extensions within a unified CIR framework.

---

# Problem Statement

Given historical Treasury yield data, estimate the parameters of the CIR model and use them to reconstruct the yield curve using only the observed **3-Month Treasury Yield**.

Evaluate predictive performance using statistical metrics and compare the base CIR model with an extended Two-Factor CIR framework.

---

# CIR Model

The CIR short-rate process is defined as:

$$
dr_t = \kappa(\theta-r_t)dt+\sigma\sqrt{r_t}dW_t
$$

| Symbol | Meaning |
|----------|----------|
| $r_t$ | Short-term interest rate |
| $\kappa$ | Mean-reversion speed |
| $\theta$ | Long-run equilibrium rate |
| $\sigma$ | Volatility parameter |
| $dW_t$ | Brownian motion increment |

The CIR model guarantees non-negative interest rates under the Feller condition:

$$
2\kappa\theta \ge \sigma^2
$$

---

# CIR Bond Pricing Formula

The CIR model provides a closed-form solution for the price of a zero-coupon bond:

$$
P(\tau)=A(\tau)e^{-B(\tau)r_t}
$$

where

$$
\gamma=\sqrt{\kappa^2+2\sigma^2}
$$

$$
B(\tau)=
\frac{2(e^{\gamma\tau}-1)}
{(\gamma+\kappa)(e^{\gamma\tau}-1)+2\gamma}
$$

$$
A(\tau)=
\left[
\frac{
2\gamma e^{(\kappa+\gamma)\tau/2}
}{
(\gamma+\kappa)(e^{\gamma\tau}-1)+2\gamma
}
\right]^{\frac{2\kappa\theta}{\sigma^2}}
$$

The theoretical yield is then computed as:

$$
y(\tau)=\frac{-\ln(P(\tau))}{\tau}
$$

---

# Methodology

1. Load and inspect Treasury yield data.
2. Clean missing values and outliers.
3. Use the 3M Treasury Yield as the short-rate proxy.
4. Calibrate CIR parameters $(\kappa,\theta,\sigma)$.
5. Reconstruct yields for 6M, 9M, 1Y, and 2Y maturities.
6. Evaluate out-of-sample performance.
7. Extend the model using a Two-Factor CIR framework.
8. Compare performance against the base CIR model.

---

# Models Implemented

| Model | Type | Parameters |
|----------|----------|----------|
| Base CIR | One-Factor CIR | $\kappa,\theta,\sigma$ |
| Two-Factor CIR | Extended CIR | $\kappa_x,\theta_x,\sigma_x,\kappa_z,\theta_z,\sigma_z$ |

---

# Two-Factor CIR Extension

The short rate is decomposed as:

$$
r_t=x_t+z_t
$$

where:

- $x_t$ = Long-run level factor
- $z_t$ = Short-run deviation factor

The level factor is estimated using a rolling average of the observed 3M Treasury Yield, while the deviation factor captures temporary departures from the long-run trend.

This extension allows the model to capture additional yield-curve dynamics while remaining consistent with the CIR framework.

---

# Results

## Model Performance

| Model | Out-of-Sample R² |
|----------|----------|
| Base CIR | 0.9152 |
| Two-Factor CIR | 0.9158 |

## Key Findings

- The 3M Treasury Yield contains substantial information about the remaining yield curve.
- The Base CIR model achieves strong predictive performance.
- The Two-Factor CIR model improves yield-curve reconstruction accuracy.
- Both models exceed the Finance Club requirement of **R² > 0.85**.

---

# Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- SciPy
- Scikit-Learn
- Jupyter Notebook / Google Colab

---

# Repository Structure

```text
Stochastic-Interest-Rate-Modelling-and-Prediction/

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

# How to Run

1. Clone the repository:

```bash
git clone https://github.com/Aryan-soni6387/Stochastic-Interest-Rate-Modelling-and-Prediction.git
cd Stochastic-Interest-Rate-Modelling-and-Prediction
```

2. Open the notebook in Google Colab, Jupyter Notebook, or VS Code.

3. Make sure the dataset files are present inside the `data/` folder:

```text
data/
├── train_data.csv
├── test_data.csv
├── test_data_3M.csv
```

4. Run all notebook cells sequentially.

5. The notebook will:
   - Calibrate the CIR model
   - Reconstruct Treasury yields
   - Evaluate model performance
   - Train and evaluate the Two-Factor CIR model
   - Generate prediction outputs

## Output

- Calibrated model parameters
- Yield curve predictions
- Performance metrics (R², RMSE)
- `two_factor_cir_predictions.csv`

---

# References

1. Cox, Ingersoll & Ross (1985), *A Theory of the Term Structure of Interest Rates*.
2. Brigo & Mercurio, *Interest Rate Models: Theory and Practice*.
3. Steven Shreve, *Stochastic Calculus for Finance II*.

---

# Author

Aryan Soni 🎓 B.Tech Student, IIT Roorkee

GitHub: https://github.com/Aryan-soni6387
