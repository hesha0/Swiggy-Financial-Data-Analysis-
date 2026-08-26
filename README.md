# Swiggy Ltd (SWIGGY) — Financial Data Analysis & Time Series Study

Financial data analysis case study on Swiggy Limited (NSE: SWIGGY) daily trading
data, covering dataset acquisition, descriptive statistics, time series
decomposition, visualisation, and a discussion of limitations — submitted as a
Word report generated from the accompanying Jupyter notebook.

## 1. Project Overview

| | |
|---|---|
| **Company analysed** | Swiggy Limited (NSE: SWIGGY) |
| **Period** | 25 Aug 2025 – 25 Aug 2026 (261 trading days) |
| **Author** | Hesha Jadhav (261610500001) |
| **Notebook** | `Python__261610500001_.ipynb` |
| **Report** | `Swiggy_Financial_Analysis_Report.docx` (~830 words) |

**Business objective:** quantify Swiggy's price volatility, directional trend,
and trading-volume dynamics over the past year, and translate the patterns
into insights useful to equity analysts and risk managers assessing the
stock's short- and medium-term risk profile.

## 2. Repository / Folder Contents

```
.
├── Python__261610500001_.ipynb        # Source notebook (analysis code + outputs)
├── Swiggy_Financial_Analysis_Report.docx  # Final Word report (deliverable)
├── graph1.png                         # Price + 20/50-day SMA crossover chart
├── graph2.png                         # Daily return distribution (histogram + KDE)
├── graph3.png                         # Seasonal-decomposition trend chart
└── README.md                          # This file
```

## 3. Requirements

Built and run in Google Colab / Jupyter with Python 3. Dependencies:

```
pandas
numpy
matplotlib
seaborn
statsmodels
yfinance
```

Install locally with:

```bash
pip install pandas numpy matplotlib seaborn statsmodels yfinance
```

## 4. How to Run

1. Open `Python__261610500001_.ipynb` in Jupyter or Google Colab.
2. Run all cells top to bottom:
   - **Cell 1** — pulls live Swiggy (`SWIGGY.NS`) daily data via `yfinance`.
   - **Cell 2** — builds the working dataset used for the rest of the analysis (see note below).
   - **Cell 3** — computes descriptive statistics (mean, std, skew, kurtosis, IQR).
   - **Cell 4** — markdown interpretation of the statistics.
   - **Cell 5** — generates the three charts (price/SMA, return distribution, trend decomposition).
   - **Cells 6–7** — visual explanations and limitations/suggestions.
3. The Word report was built separately from the notebook's outputs; regenerate it by re-running the report-build script if the underlying data or charts change.

## 5. Methodology

- **Data structuring:** OHLCV data indexed by trading date; `Daily_Return` (pct change) and `Log_Return` (log of price ratio) added as derived columns.
- **Descriptive statistics:** mean, standard deviation, min/median/max, skewness, kurtosis, and interquartile range for Close, Daily Return, and Volume.
- **Time series analysis:** additive seasonal decomposition (`statsmodels.tsa.seasonal.seasonal_decompose`, period = 20 trading days) to separate the long-term trend from short-term noise.
- **Visualisation:** 20-day and 50-day simple moving averages overlaid on closing price; histogram + KDE of daily returns; extracted trend component from decomposition.

## 6. ⚠️ Important Note on Data Source

Cell 1 downloads **real** Swiggy data via `yfinance`. Cell 2, however,
**overwrites it with a synthetically generated series** (`np.random.seed(42)`
+ a geometric random walk calibrated to Swiggy's real 52-week range of
₹235–₹474), even though it is commented as "authentic" data. This is
disclosed transparently in the report's Data Acquisition and Integrity
section and repeated in Limitations — treat the figures and charts as a
calibrated simulation, not verified exchange ticks.

**To use genuine live data instead:** delete Cell 2 and run all downstream
analysis (Cells 3–7) directly on the `df_swiggy` produced by Cell 1.

## 7. Key Results Summary

| Metric | Close (₹) | Daily Return | Volume |
|---|---|---|---|
| Mean | 270.58 | 0.0245% | 16,191,570 |
| Std. Dev. | 28.85 | 2.1497% | 7,557,422 |
| Min | 229.85 | -5.6025% | 5,199,824 |
| Median | 260.64 | 0.1250% | 14,598,250 |
| Max | 342.24 | 8.8421% | 58,556,130 |
| Skewness | 0.673 | 0.382 | 1.525 |
| Kurtosis | -0.742 | 0.678 | 3.860 |

The decomposed trend shows a decline from ~₹310 (Sep 2025) to a trough near
~₹245 (Mar 2026), followed by recovery to ~₹305–310 by Aug 2026.

## 8. Limitations

- Short (1-year) historical horizon
- Simulated rather than live tick data (see Section 6)
- No fundamental/exogenous variables (AOV, GOV, competitor pricing)
- Linear-trend assumption in moving averages

## 9. Suggested Extensions

- Re-run on verified live exchange data before drawing investment conclusions
- GARCH-family models for volatility clustering
- Multi-factor regression with competitor prices, input costs, sentiment
- LSTM / Prophet forecasting with rolling cross-validation

## 10. Word Count

Report body: ≈830 words (limit: 1,500 words).
