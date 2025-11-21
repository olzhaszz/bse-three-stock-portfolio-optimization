# BSE Three-Stock Portfolio Optimization

This repository contains an empirical portfolio analysis based on three
Hungarian stocks traded on the Budapest Stock Exchange (BSE):  
**MASTERPLAST, MOL, and MTELEKOM**.

The goal is to estimate risk, evaluate the probability of a negative daily
return, construct a minimum-variance portfolio from two of the stocks, and
build an efficient frontier using all three assets.

## Description

The project covers three main tasks:

1. **Single-stock risk and probability of loss**

   - Use publicly available daily close prices over a period of at least
     three months for the three stocks.
   - Compute daily returns and their sample mean and standard deviation.
   - Identify the **highest-risk** stock based on the standard deviation
     of daily returns.
   - Under the assumption that daily returns are approximately **normally
     distributed**, calculate the probability that the daily return of
     this highest-risk stock is **negative** (i.e. \( P(R < 0) \)).

2. **Minimum-variance portfolio of the two lower-risk stocks**

   - Take the two stocks with **lower risk** than the highest-risk stock.
   - Estimate their standard deviations and **correlation**.
   - Compute the weights \( w_2, w_3 \) that minimize the portfolio
     standard deviation, subject to:
     - \( w_2 + w_3 = 1 \)
     - \( w_2 \ge 0, \; w_3 \ge 0 \)
   - Optionally verify the solution using a numerical optimizer (e.g.
     Excel Solver or a Python optimization routine).
   - Report the **minimum portfolio risk** (standard deviation) and the
     corresponding weights.

3. **Efficient frontier with three stocks**

   - Consider portfolios consisting of all **three** stocks
     (MASTERPLAST, MOL, MTELEKOM).
   - Generate a set of portfolios with different weight combinations that
     satisfy:
     - \( w_1 + w_2 + w_3 = 1 \),
     - \( w_i \ge 0 \) for all i (no short selling).
   - For each portfolio, compute the **expected return** and **risk**
     (standard deviation).
   - Identify and plot (or tabulate) the **efficient frontier**:
     portfolios that provide the **maximum expected return** for a given
     level of risk.
   - Provide at least **five** portfolio points on the frontier, including
     the **minimum-variance portfolio**.

## Data

- **Market**: Budapest Stock Exchange (BSE)
- **Instruments**: MASTERPLAST, MOL, MTELEKOM
- **Frequency**: Daily closing prices
- **Period**: At least three months of data (e.g. 2025-06-12 to 2025-11-12)

Place the raw or cleaned data in a `data/` folder, such as:

- `data/raw_prices.xlsx` or `data/daily_prices.csv`

Document your exact date range and tickers in the notebook or script.

## Methods

The analysis uses standard portfolio theory and basic statistics:

- Daily return calculation (simple or log returns, consistently applied)
- Sample mean and standard deviation of returns
- Normal approximation for:
  \[
  P(R < 0) = \Phi\left( \frac{0 - \mu}{\sigma} \right)
  \]
- Two-asset **minimum-variance portfolio** formula with correlation
- Three-asset portfolio variance and expected return:
  \[
  \sigma_p^2 = \mathbf{w}^\top \Sigma \mathbf{w}, \quad
  \mu_p = \mathbf{w}^\top \boldsymbol{\mu}
  \]
- Efficient frontier construction via grid search over weights or by using
  an optimizer with constraints.

## Repository Structure

A suggested structure is:

- `data/` – Input data (daily prices for the three stocks)
- `notebooks/` – Jupyter notebook(s) with calculations and commentary  
  - e.g. `bse_three_stock_portfolio.ipynb`
- `src/` – Python scripts for:
  - Loading and cleaning data
  - Computing returns, risk, and correlations
  - Optimizing portfolio weights and generating frontier points
- `figures/` – Plots of:
  - Return distributions
  - Efficient frontier (risk–return diagram)
- `README.md` – Project overview (this file)

##Results

The final output should document:

Which stock has the highest daily risk and its probability of a
negative daily return under normality.

The minimum-variance portfolio built from the two lower-risk stocks
(weights and resulting standard deviation).

A set of at least five efficient portfolios using all three stocks,
with their weights, expected returns, and risks, and a clear plot of the
efficient frontier.
