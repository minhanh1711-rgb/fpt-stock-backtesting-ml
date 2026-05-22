# fpt-stock-backtesting-ml
Independent quantitative trading research project using SMA, XGBoost, and LSTM models for financial time-series prediction, backtesting, and strategy performance comparison with risk-adjusted evaluation metrics.
# FPT Stock Backtesting & Machine Learning Trading Strategy

## Overview

This project is an independent quantitative trading research project focused on FPT stock using historical market data from 2010 to 2024.

The project develops, tests, and compares multiple trading strategies, including traditional technical indicator strategies, machine learning models, and deep learning models. The main objective is to evaluate which approach performs better under historical market conditions through backtesting and performance metrics.

## Objectives

- Collect and preprocess historical stock data for FPT
- Explore price trends, trading volume, returns, correlations, and stationarity
- Build rule-based trading strategies using technical indicators
- Optimize strategy parameters using Hyperopt
- Apply walk-forward optimization to reduce overfitting risk
- Train machine learning and deep learning models for next-day price direction prediction
- Backtest all strategies and compare their risk-return performance

## Data

- Stock ticker: FPT
- Period: 2010–2024
- Data source: vnstock
- Main variables: Open, High, Low, Close, Volume

## Methods

### 1. Exploratory Data Analysis

The project includes exploratory analysis of:

- Stock price trend
- Trading volume dynamics
- Return distribution
- Correlation matrix
- Missing values and outliers
- Stationarity testing using the Augmented Dickey-Fuller test

The original closing price series was found to be non-stationary, while the return series became stationary after transformation.

### 2. Rule-Based Trading Strategies

Three technical indicator strategies were implemented:

- SMA Crossover Strategy
- RSI Strategy
- Bollinger Bands Strategy

Each strategy generates trading positions based on technical signals and is backtested using `backtesting.py`.

### 3. Parameter Optimization

The SMA strategy was optimized using Hyperopt to search for better moving average parameters.

The optimized SMA strategy achieved strong historical performance, but it generated only one major trade, meaning the result may largely reflect the long-term upward trend of FPT stock.

### 4. Walk-Forward Optimization

Walk-forward optimization was applied to evaluate strategy robustness across different time periods.

This helps reduce overfitting by repeatedly training on past periods and testing on future unseen periods.

### 5. Machine Learning Strategy: XGBoost

An XGBoost classifier was trained to predict next-day price direction.

Features used include:

- Daily return
- SMA20
- SMA50
- Volatility
- Momentum
- Volume change
- RSI
- MACD
- MACD signal

The XGBoost model achieved around 50% test accuracy, showing the difficulty of predicting short-term stock price direction using technical indicators alone.

### 6. Deep Learning Strategy: LSTM

An LSTM model was built using PyTorch to capture sequential patterns in financial time series.

The model used 30-day sequences and 9 technical features to predict next-day price direction.

Although prediction accuracy was also around 50%, the LSTM-based trading strategy performed better than XGBoost in backtesting.

## Final Strategy Comparison

| Strategy | Return [%] | Sharpe Ratio | Max Drawdown [%] | Win Rate [%] | Trades | Profit Factor |
|---|---:|---:|---:|---:|---:|---:|
| SMA | 2493.12 | 0.8370 | -36.90 | 100.00 | 1 | NaN |
| XGBoost | 45.10 | 0.2366 | -30.33 | 59.06 | 149 | 1.3214 |
| LSTM | 282.26 | 0.6202 | -30.98 | 63.64 | 55 | 2.8337 |

## Key Findings

- The optimized SMA strategy achieved the highest total return and Sharpe Ratio.
- However, SMA generated only one major trade, so its strong performance mainly captured the long-term upward trend of FPT stock.
- XGBoost showed weak predictive performance, with accuracy close to random guessing.
- LSTM performed better than XGBoost in backtesting, with higher return, Sharpe Ratio, win rate, and profit factor.
- Financial time-series prediction remains challenging due to market noise, non-stationarity, and overfitting risk.

## Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- vnstock
- ta
- backtesting.py
- Hyperopt
- Scikit-learn
- XGBoost
- PyTorch
- Statsmodels

## Project Structure

```text
New_project_FPT.ipynb
README.md
