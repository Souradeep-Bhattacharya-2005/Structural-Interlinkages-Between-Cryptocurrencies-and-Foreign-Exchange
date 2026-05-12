# Replication Code: Structural Interlinkages Between Cryptocurrencies and Foreign Exchange

## Overview

This repository contains the Python code and datasets required to replicate the empirical analysis presented in the paper: **"Structural Interlinkages Between Cryptocurrencies and Foreign Exchange: Evidence From Volatility and Returns Spillovers."**

The analysis investigates the transmission of returns and volatility shocks between leading cryptocurrencies (Bitcoin, Ethereum) and major foreign exchange currency pairs using EGARCH modeling and Generalized Forecast Error Variance Decomposition (FEVD) based on Vector Autoregression (VAR) models.

## Dependencies

The analysis is written in Python. To run the code, ensure you have the following libraries installed:

* **Python 3.x**
* `pandas` (Data manipulation)
* `numpy` (Numerical computations)
* `matplotlib` & `seaborn` (Data visualization)
* `statsmodels` (VAR modeling and ADF tests)
* `arch` (EGARCH volatility modeling)

You can install the dependencies via pip:

```bash
pip install pandas numpy matplotlib seaborn statsmodels arch

```

## Dataset

The code expects historical price data for the following assets. Ensure these CSV files are placed in the working directory or update the file path in the script accordingly.

* **Cryptocurrencies:**
* `Bitcoin Historical Data.csv`
* `ETH_USD Binance Historical Data.csv`


* **Fiat Currencies:**
* `EUR_USD Historical Data.csv`
* `GBP_USD Historical Data.csv`
* `AUD_USD Historical Data.csv`
* `USD_CHF Historical Data.csv`
* `USD_JPY Historical Data.csv`
* `USD_INR Historical Data.csv`



*Note: The script currently points to a local directory. Please update the `os.chdir()` path in the "Loading Datasets" section to match your local environment.*

## Workflow

The Jupyter Notebook (`.ipynb`) is structured into the following analytical steps:

1. **Data Import & Cleaning**:
* Imports raw CSV data.
* Parses dates and sets them as the index.
* Cleans price columns (removes string formatting like `$`, `,`, `%`) and converts them to numeric types.
* Merges all assets into a single time-series DataFrame.


2. **Returns Calculation**:
* Computes logarithmic returns for all currencies.


3. **Descriptive Statistics & Stationarity**:
* Generates summary statistics.
* Performs **Augmented Dickey-Fuller (ADF)** tests to ensure stationarity of log returns.


4. **Volatility Modeling (EGARCH)**:
* Fits an **EGARCH(1,1)** model to the log returns of each currency to extract conditional volatility.
* Visualizes the conditional volatility over time.


5. **Spillover Analysis**:
* **Returns Spillovers**: Estimates a **VAR(2)** model (optimal lag selected using AIC) on returns and computes the Generalized FEVD spillover matrix (H=10). Computes and plots rolling total spillover measures using a 300 day window. 
* **Volatility Spillovers**: Tests conditional volatility for stationarity, fits a **VAR(5)** model (optimal lag selected using AIC), and computes the Generalized FEVD spillover matrix for volatility. Computes and plots rolling total spillover measures using a 300 day window. 



## Usage

1. Clone this repository.
2. Ensure all data files are in the correct directory.
3. Open the Jupyter Notebook.
4. Run all cells sequentially to generate the statistical outputs and spillover heatmaps.

## License

Please refer to LICENSE.md for copyright notice and usage restrictions. 
