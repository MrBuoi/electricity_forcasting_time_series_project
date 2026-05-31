## electricity_forcasting_time_series_project
Forecasting Hourly Electricity Consumption in the PJM East Region Using a Two-Stage Hybrid ARIMAX - GARCH Model Integrated with Temporal Structural Variables.
## 📝 Project Overview
This repository contains the complete implementation of a **two-stage hybrid ARIMAX-GARCH forecasting framework** designed to predict high-frequency hourly electricity consumption in the **PJM East Region (PJME)** power grid. 

Hourly energy data poses two massive econometrics challenges:
1. **Multiple Seasonality:** Overlapping daily (24h), weekly (168h), and monthly cycles driven by human behavior and climate variations.
2. **Volatility Clustering:** Continuous blocks of massive forecasting errors occurring during severe weather shocks or sudden demand peaks, which violate classical homoskedastic errors assumptions.

To solve this, our pipeline leverages a decoupled hybrid approach combining **linear time-series tracking (ARIMAX)** and **conditional variance modeling (GARCH)**.

---

## ⚡ Key Methodology & Pipeline Stages

```mermaid
graph TD
    A[1. Raw Data Ingestion: PJME Hourly Data] --> B[2. Data Preprocessing & Linear Imputation]
    B --> C[3. Exogenous Feature Engineering: One-Hot Categories]
    C --> D[4. Stationarity Verification via Augmented Dickey-Fuller Test]
    D --> E[5. Stage 1: Fit Global Optimized ARIMAX 2,1,5 Model]
    E --> F[6. Residual Extraction & ARCH-LM Diagnostic Test]
    F --> G[7. Stage 2: Fit Parsimonious GARCH 1,1 Volatility Model]
    G --> H[8. Final Operational Forecast Benchmarking: 24h Multi-Step vs 1-Step Rolling]
