---
title: Startegies
description: A guide on strategies
---

The `Strategy`, `TechnicalStrategy`, and `BreakoutStrategy` classes form the core of the trading strategies in your algorithmic crypto trading bot. This documentation aims to explain these classes and their key components, like RSI, EMA, and volume, in a way that is understandable even for someone new to algorithmic trading.

---

# Strategy Classes Documentation

## Overview

The strategy classes are designed to automate trading decisions based on specific rules or indicators. They analyze market data and execute trades when certain conditions are met.

## Base `Strategy` Class

### Description

The `Strategy` class is an abstract base class that provides common functionalities for different trading strategies.

### Key Methods

- **parse_trades**: Analyzes new trades and updates candle data.
- **\_check_order_status**: Regularly checks the status of a placed order.
- **\_open_position**: Opens a trading position based on a signal.
- **\_check_tp_sl**: Checks if the take profit or stop loss conditions are met.

### Attributes

- **client**: An instance of `BitmexClient` or `BinanceClient`.
- **contract**: The trading contract.
- **exchange**: The name of the exchange (e.g., 'Binance').
- **tf**: The timeframe for the strategy.
- **candles**: A list of candle data.
- **trades**: A list of ongoing trades.
- **balance_pct, take_profit, stop_loss**: Trading parameters.

## `TechnicalStrategy` Class

### Description

`TechnicalStrategy` uses technical indicators like RSI and MACD to make trading decisions.

### Key Indicators

- **RSI (Relative Strength Index)**: Measures the magnitude of recent price changes to evaluate overbought or oversold conditions. An RSI below 30 indicates oversold (potential buy signal), and above 70 indicates overbought (potential sell signal).
- **EMA (Exponential Moving Average)**: Gives more weight to recent prices, making it more responsive to new information. `ema_fast`, `ema_slow`, and `ema_signal` are different periods used to calculate EMAs for the MACD indicator.
- **MACD (Moving Average Convergence Divergence)**: A trend-following momentum indicator showing the relationship between two moving averages of an asset's price. It's calculated using EMAs.

### Key Methods

- **\_check_signal**: Computes the RSI and MACD to identify buy or sell signals.

## `BreakoutStrategy` Class

### Description

`BreakoutStrategy` focuses on identifying substantial price movements or "breakouts" in a specific direction.

### Key Attributes

- **\_min_volume**: The minimum trade volume required to consider a breakout legitimate.

### Key Methods

- **\_check_signal**: Checks for breakout conditions based on candlestick patterns and trade volume.

## General Concepts

### 1. RSI (Relative Strength Index)

- **What it is**: A momentum indicator that measures the speed and change of price movements.
- **How it's calculated**: RSI compares the magnitude of recent gains to recent losses to determine overbought and oversold conditions in the price of an asset.
- **Trading implication**: An RSI above 70 suggests an asset is overbought, while an RSI below 30 indicates it might be oversold.

### 2. EMA (Exponential Moving Average)

- **What it is**: A type of moving average that places a greater weight and significance on the most recent data points.
- **How it's calculated**: EMA gives more weight to recent prices, which tends to react more quickly to price changes than a simple moving average.
- **Trading implication**: EMAs are used to identify trend direction and potential reversal points.

### 3. MACD (Moving Average Convergence Divergence)

- **What it is**: A trend-following momentum indicator.
- **How it's calculated**: It's calculated by subtracting the 26-period EMA from the 12-period EMA. The result is the MACD line. A 9-day EMA of the MACD, called the "signal line," is then plotted on top of the MACD line.
- **Trading implication**: Traders may buy the asset when the MACD crosses above its signal line and sell, or short, the asset when the MACD crosses below the signal line.

### 4. Volume

- **What it is**: The amount of an asset that was traded over a set period.
- **Trading implication**: High volume is an indicator of market activity and liquidity, essential for assets to be sold without affecting the market price.

## Conclusion

These strategy classes allow the trading bot to analyze market data using technical indicators and execute trades based on predefined rules. Understanding these concepts is crucial for anyone interested in algorithmic trading, especially in the volatile crypto market.

---

This documentation should provide a comprehensive understanding of the technical aspects of the strategies used in your trading bot, as well as the basic principles behind key trading indicators.
