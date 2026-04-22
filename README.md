# ACC102-Individual-Assignment-Track-2
This project is a Python-based financial data product that uses WRDS/CRSP data to analyse the risk, return, and portfolio performance of selected US technology stocks from 2016 to 2021.
# ACC102 Data Product: Risk and Return Analysis of US Technology Stocks

**Module:** ACC102  
**Assessment:** Python Data Product Track 2  
**Project Type:** Financial data product using Python and WRDS/CRSP  
**Period Covered:** 2016–2021

---

## 1. Project Overview

This project develops a Python-based data product to analyse the risk and return characteristics of selected US technology stocks using historical market data from WRDS/CRSP. The notebook is designed to move beyond a simple one-off analysis by presenting a structured, reproducible workflow that can be understood and reused by students and beginner users.

The project compares major technology stocks across multiple dimensions, including price performance, cumulative returns, volatility, downside risk, correlation, and portfolio behaviour. It also includes a comparison with the broader market benchmark to provide additional context for interpreting stock performance.

The final product is intended for users who want an accessible but academically grounded stock analysis tool, especially business students learning how Python can be used for financial data extraction, cleaning, visualisation, and interpretation.

---

## 2. Analytical Problem

The main analytical problem addressed in this project is:

**How do selected US technology stocks differ in terms of return, risk, and diversification benefits over the period 2016–2021?**

This question is important because investors and students often focus only on raw returns, while ignoring risk. A stock with very high growth may also have high volatility and large drawdowns. Therefore, this project evaluates both return and risk-adjusted performance, and also explores whether combining stocks into a simple equal-weight portfolio produces more stable results.

More specifically, the notebook aims to answer the following questions:

- Which of the selected stocks achieved the strongest cumulative growth?
- Which stocks showed the highest volatility and downside risk?
- How strongly are the selected stocks correlated with each other?
- Does an equal-weight portfolio reduce risk compared with holding individual stocks?
- How does the performance of the selected stocks compare with the general market benchmark?

---

## 3. Target Users

This notebook is mainly designed for:

- Business and finance students who want a reproducible stock analysis example
- Beginner users interested in comparing stock return and risk
- Users with WRDS access who want a simple workflow that can be extended to other stocks

The notebook prioritises clarity and interpretability over advanced quantitative modelling, making it suitable for educational use.

---

## 4. Data Source and Justification

The analysis uses data from **WRDS (Wharton Research Data Services)**, primarily from the **CRSP** database. The following tables are used:

- `crsp.dsf` – daily stock prices and returns
- `crsp.dsenames` – company identifiers and ticker linking information
- `crsp.dsi` – daily stock market index data used as a benchmark

### Why this dataset was chosen
WRDS/CRSP was chosen for three main reasons:

1. **Reliability**  
   CRSP is a well-established academic financial database widely used in research and teaching.

2. **Data quality**  
   It provides standardised historical stock return data, which is more suitable for academic analysis than many free online sources.

3. **Reproducibility**  
   The use of database queries makes the workflow more transparent and reproducible for users with WRDS access.

### Selected stocks
The notebook uses the following default companies:

- AAPL
- MSFT
- AMZN
- GOOGL
- TSLA

These stocks were selected because they are large, highly recognisable technology firms with different patterns of growth, risk, and market behaviour. This makes them appropriate for comparison in a classroom-based financial analysis project.

---

## 5. Project Logic and Workflow

The notebook follows a complete analytical pipeline from raw data extraction to final interpretation. The logic of the project can be summarised in the following stages:

### Stage 1: User input and setup
The notebook defines the sample period and selected stock tickers. In the improved section, the workflow is made more reusable by allowing users to provide their own WRDS username and a custom ticker list.

### Stage 2: Data extraction
Daily stock data are queried from WRDS/CRSP using SQL through the `wrds` Python package. Company identifiers are matched using `crsp.dsenames`, and return series are extracted from `crsp.dsf`. Market benchmark data are obtained from `crsp.dsi`.

### Stage 3: Data cleaning and preparation
The raw data are cleaned and transformed using `pandas` and `numpy`. This includes:
- converting date fields into datetime format
- ensuring numeric variables are correctly typed
- handling missing values
- reshaping long-format data into wide tables for multi-stock comparison
- aligning stock return series across the same dates

### Stage 4: Descriptive analysis
The notebook explores stock behaviour through:
- price evolution
- normalised price comparison
- daily return calculation
- cumulative return calculation

This stage provides a first view of how different stocks performed through time.

### Stage 5: Risk and performance measurement
The notebook calculates key financial indicators, including:
- annual return
- annual volatility
- Sharpe ratio
- Sortino ratio
- maximum drawdown
- Value at Risk (VaR)

These indicators are used to compare stocks not only by return, but also by the risk taken to achieve those returns.

### Stage 6: Correlation and portfolio analysis
The notebook examines the relationship between stocks using return correlations and visualises them with a heatmap. It then constructs an equal-weight portfolio to test whether diversification leads to a smoother return profile and lower overall risk than individual stocks.

### Stage 7: Benchmark comparison
An additional improvement compares selected stocks and the portfolio against the broader market benchmark from CRSP. This adds context by showing whether observed stock performance simply follows the market or meaningfully differs from it.

### Stage 8: Output and interpretation
The notebook presents results through tables and charts, then interprets the findings in a way suitable for student users and non-specialist audiences.

---

## 6. Python Tools and Libraries

The following Python libraries are used in the project:

- `wrds` – to connect to WRDS and query CRSP data
- `pandas` – for data cleaning, transformation, and tabular analysis
- `numpy` – for numerical calculations
- `matplotlib` – for plotting
- `seaborn` – for clearer statistical visualisations

These libraries were selected because they are standard tools for financial data analysis in Python and are appropriate for an academic data product.

---

## 7. Main Visualisations and Their Purpose

The notebook includes several visual outputs. Each one supports a different part of the analysis:

### 1. Normalised price trend chart
This chart compares stock price movements after scaling them to a common starting value. It helps users compare growth paths visually, even when stock prices have very different absolute levels.

### 2. Cumulative return plot
This plot shows how a hypothetical investment would grow over time for each stock. It makes long-run performance easier to interpret than daily return tables.

### 3. Correlation heatmap
The heatmap visualises the correlation between stock returns. This is useful for understanding which stocks move similarly and whether diversification is likely to reduce risk.

### 4. Rolling volatility chart
This chart shows how stock risk changes over time rather than treating volatility as constant. It helps identify periods of instability or unusually high uncertainty.

### 5. Return distribution plot
This visualisation shows the shape and spread of returns, helping users understand whether a stock experiences more extreme positive or negative movements.

### 6. Portfolio and benchmark comparison charts
These outputs compare the equal-weight portfolio and individual stocks against the broader market, helping users evaluate relative rather than absolute performance.

---

## 8. Key Findings

The main findings of the project can be summarised as follows:

1. **The selected stocks show very different return profiles**  
   Some stocks achieved much stronger cumulative growth than others over the sample period.

2. **Higher return was often associated with higher risk**  
   The strongest-performing stocks were not always the most attractive on a risk-adjusted basis, because they also showed higher volatility or deeper drawdowns.

3. **Risk-adjusted indicators improved interpretation**  
   Measures such as the Sharpe ratio and Sortino ratio provided a more balanced comparison than return alone.

4. **Diversification improved stability**  
   The equal-weight portfolio generally appeared less extreme than the most volatile individual stocks, suggesting that diversification can reduce overall risk.

5. **Benchmark comparison added context**  
   Comparing stock performance with the broader market helped distinguish between general market growth and stock-specific outperformance.

Overall, the project shows that evaluating stocks requires a combination of return, risk, correlation, and benchmark comparison rather than a single performance number.

---

## 9. Reusability as a Data Product

A key aim of this assignment was not just to produce analysis, but to create a **data product**. This means the notebook should be useful beyond one fixed run.

To support this, the project includes an improvement section that demonstrates how the workflow can be made more reusable. Instead of hard-coding all inputs, users can adapt the notebook by changing:

- WRDS username
- ticker list
- sample dates
- output focus

This improves the notebook’s practical value and makes it more aligned with the idea of a reusable analytical tool.

---

## 10. Limitations

Although the project provides a structured and useful financial analysis workflow, it has several limitations:

- It only covers a small number of technology stocks
- The time period is limited to 2016–2021
- The portfolio analysis uses equal weights rather than formal optimisation
- Full reproducibility depends on access to WRDS
- The notebook is designed for clarity and teaching purposes rather than professional investment modelling

These limitations mean that the project should be viewed as an educational data product rather than a complete investment decision system.

---

## 11. Future Improvements

Possible future extensions include:

- adding more sectors and a larger stock universe
- allowing fully interactive user input
- introducing portfolio optimisation methods
- exporting outputs automatically into a dashboard or report
- adding more benchmark indices and factor-based comparisons
- improving automation for repeated analysis

---

## 12. How to Run the Project

### Requirements
To run this notebook successfully, users need:

- Python installed
- Jupyter Notebook or VS Code
- WRDS access credentials
- The following Python packages:
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `seaborn`
  - `wrds`

### Basic steps
1. Open the notebook file in Jupyter Notebook or VS Code  
2. Install any missing Python libraries  
3. Run the setup/import cells  
4. Enter WRDS credentials when prompted  
5. Run the notebook cells in order  
6. Review the generated charts, tables, and summary outputs  

### Important note
Because the project depends on WRDS, users without valid WRDS access may not be able to reproduce the full data extraction stage.
### Conclusion
This project demonstrates how Python can be used to build a clear and reproducible financial data product using academic market data. By combining WRDS extraction, data cleaning, statistical analysis, visualisation, and interpretation, the notebook provides a practical example of how stock risk and return can be analysed in a structured way.

The project also highlights an important lesson from financial analysis: strong returns should always be interpreted alongside volatility, drawdowns, and diversification effects. In this sense, the notebook is not only a technical exercise, but also a decision-support tool for comparing stocks in a more balanced and informed way.
