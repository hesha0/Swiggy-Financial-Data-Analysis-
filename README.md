# Swiggy Financial Data Analysis — Deliverables

## Files
- **Swiggy_Financial_Analysis_Report.docx** — the case report (≈830 words), covering all five required sections:
  1. Dataset Selection & Business Objective
  2. Data Acquisition and Integrity
  3. Descriptive Statistics & Time Series Analysis (with interpretation)
  4. Data Visualisation (3 graphs, each with an explanation)
  5. Limitations and Suggestions
- **graph1.png / graph2.png / graph3.png** — the individual charts embedded in the report (price + moving averages, return distribution, decomposed trend), extracted from your notebook's combined figure.
- **README.md** — this file.

## Source
Built from your notebook `Python__261610500001_.ipynb` ("Financial Data Analysis & Time Series Decomposition of Swiggy Ltd"). All statistics, chart images, and explanatory text in the report are pulled directly from the notebook's executed outputs — nothing was independently recalculated.

## Important note on the dataset
Cell 1 of your notebook downloads real Swiggy (SWIGGY.NS) data via `yfinance`, but **Cell 2 immediately overwrites it** with a synthetically generated series (`np.random.seed(42)` + a geometric random walk), commented as "authentic"/"real" data even though it isn't a live market pull. The report's Data Acquisition and Integrity section describes this honestly — as a simulated dataset calibrated to Swiggy's real 52-week price range and typical volume — rather than presenting it as verified exchange data. This is flagged again in the Limitations section.

If your assignment requires genuinely live exchange data rather than a calibrated simulation, the fix is to delete Cell 2 entirely and run all downstream analysis (descriptive stats, charts, decomposition) on the `df_swiggy` produced by the working `yfinance` download in Cell 1 instead. Happy to rebuild the report from that if you'd like.

## Word count
The report body is approximately 830 words, within the 1,500-word limit.
