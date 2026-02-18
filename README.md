# Stock Price Time-Series Analysis

## Overview

This project explores stock price movements over time using time-series analysis techniques. The goal is to understand the underlying drivers of price changes — long-term trends, repeating patterns, and random fluctuations rather than just visualizing raw data.

By applying decomposition and smoothing methods, complex price behaviors are broken into interpretable components for analysis and decision-making.

## Objectives

Visualize stock price changes over time

Detect trends and volatility

Separate trend, seasonality, and irregular components

Smooth short-term noise to highlight meaningful patterns

## Tools & Libraries

Python

pandas – for data preparation and time indexing

matplotlib – for visualizations

statsmodels – for time-series decomposition

## Data Preparation

The dataset was structured with dates properly recognized as a time index. Correct chronological ordering is critical for accurate time-series analysis.

import pandas as pd

# Load data and set date as index
df = pd.read_csv("stock_prices.csv", parse_dates=['Date'], index_col='Date')

## Visualization

Stock prices were plotted to observe general behavior such as trends, stability, and periods of high volatility.

import matplotlib.pyplot as plt

plt.figure(figsize=(12,6))
plt.plot(df['Close'], label='Stock Price')
plt.title('Stock Price Over Time')
plt.xlabel('Date')
plt.ylabel('Price')
plt.legend()
plt.show()

## Decomposition

The time series was split into three components:

Trend: Long-term price movement

Seasonality: Repeating cycles or periodic behavior

Residuals: Random fluctuations not explained by trend or seasonality

from statsmodels.tsa.seasonal import seasonal_decompose

result = seasonal_decompose(df['Close'], model='additive', period=30)
result.plot()
plt.show()

## Moving Average Smoothing

Moving averages were calculated to reduce daily market noise and reveal the underlying trend.

df['MA_30'] = df['Close'].rolling(window=30).mean()
plt.figure(figsize=(12,6))
plt.plot(df['Close'], label='Stock Price')
plt.plot(df['MA_30'], label='30-Day MA', color='red')
plt.title('Stock Price with 30-Day Moving Average')
plt.xlabel('Date')
plt.ylabel('Price')
plt.legend()
plt.show()

## Key Takeaways

Structured analysis can uncover meaningful patterns in seemingly chaotic stock data.

Decomposition helps distinguish genuine movement from short-term fluctuations.

Smoothing techniques make trends easier to identify and communicate.

## Skills Strengthened

Time-series visualization

Financial data interpretation

Statistical decomposition

Understanding sequential features
