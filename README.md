# Time Series Forecasting of Stock Prices: ARMA, ARCH, and GARCH Models for Adani Green Energy Ltd.

## Overview
This repository contains the econometric time series analysis and volatility forecasting model for **Adani Green Energy Ltd. (AGEL)**, conducted as part of the Intermediary Econometrics coursework at Symbiosis School of Economics. 

The study analyzes daily log returns of AGEL stock to model short-term price dynamics and evaluate volatility persistence using ARMA, ARCH, and GARCH models.

---

## Abstract & Key Highlights
* **Target Asset:** Adani Green Energy Ltd. (NSE/BSE: AGEL)
* **Sample Period:** June 2018 to October 2024 ($N = 1,564$ daily observations)
* **Software Used:** EViews
* **Primary Results:**
  * **Stationarity:** The log return series exhibits stationarity at level ($p < 0.01$) based on the Augmented Dickey-Fuller (ADF) test.
  * **Autoregressive Component:** The ARMA(1,0) specification shows that approximately **22.5%** ($p = 0.0000$) of the previous day's return spills over into the current day's return.
  * **Volatility Dynamics:** The GARCH(1,1) model confirms strong volatility clustering[cite: 1]. The sum of ARCH ($\alpha_1 = 0.3547$) and GARCH ($\beta_1 = 0.4140$) parameters equals **0.7687** ($< 1$), indicating persistent yet mean-reverting volatility over time[cite: 1].

---

## Econometric Specifications & Results

### 1. ARMA(1,0) Mean Model[cite: 1]
$$Return_t = -0.002553 + 0.225136 \cdot Return_{t-1} + \epsilon_t$$

* **Constant ($c$):** $-0.002553$ ($p = 0.0258$)[cite: 1]
* **AR(1) Coefficient ($\phi_1$):** $0.225136$ ($p = 0.0000$)[cite: 1]
* **Adjusted $R^2$:** $4.94\%$[cite: 1]

### 2. ARCH(1) / GARCH(1,1) Volatility Model[cite: 1]
* **Mean Equation:**
  $$Return_t = -0.001972 + 0.174710 \cdot Return_{t-1} + \epsilon_t$$
* **Variance Equation:**
  $$\sigma_t^2 = 0.000307 + 0.354703 \cdot \epsilon_{t-1}^2 + 0.413982 \cdot \sigma_{t-1}^2$$

Where:
* $\alpha_0 = 0.000307$ ($p = 0.0000$) — Baseline long-term variance[cite: 1]
* $\alpha_1 = 0.354703$ ($p = 0.0000$) — Immediate shock reaction (ARCH effect)[cite: 1]
* $\beta_1 = 0.413982$ ($p = 0.0000$) — Volatility persistence (GARCH effect)[cite: 1]

---

## Repository Structure

```text
├── data/
│   ├── AGEL_daily_prices_2018_2024.csv    # Sourced from Investing.com
│   └── AGEL_log_returns.csv               # Calculated log-return series
├── eviews/
│   ├── ARMA_estimation.prg                # EViews script / output workfile
│   └── GARCH_volatility_forecast.wf1      # EViews workfile with variance series
├── docs/
│   └── Adani_Green_TimeSeries_Paper.pdf   # Full research paper PDF
└── README.md                              # Project documentation
