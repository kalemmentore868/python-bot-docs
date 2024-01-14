---
title: Models
description: A guide on python models
---

Creating extensive documentation for your crypto bot's models will help in understanding and maintaining the code. Below is a detailed documentation for each class in your code.

---

# Python trading Bot Models Documentation

This documentation provides a detailed overview of the models used in the connectors to the exchange for the Astro - Starlight crypto bot. These models are designed to streamline the code and reduce the likelihood of errors.

## 1. `Balance` Class

### Description

The `Balance` class is used to represent the balance information for different types of exchanges, including Binance Futures, Binance Spot, and Bitmex.

### Attributes

- **initial_margin**: The initial margin requirement.
- **maintenance_margin**: The maintenance margin requirement.
- **margin_balance**: The total margin balance.
- **wallet_balance**: The total wallet balance.
- **unrealized_pnl**: The unrealized profit and loss.
- **free** (Binance Spot only): The free balance available.
- **locked** (Binance Spot only): The locked balance.

### Constructor Parameters

- `info`: A dictionary containing balance information.
- `exchange`: A string specifying the exchange type.

## 2. `Candle` Class

### Description

The `Candle` class represents a single candlestick in a market chart for various exchanges.

### Attributes

- **timestamp**: The timestamp of the candle.
- **open**: The opening price.
- **high**: The highest price in the candle.
- **low**: The lowest price in the candle.
- **close**: The closing price.
- **volume**: The trading volume.

### Constructor Parameters

- `candle_info`: A dictionary or list containing candlestick information.
- `timeframe`: The timeframe of the candlestick data.
- `exchange`: The exchange from which the data is sourced.

## 3. `Contract` Class

### Description

The `Contract` class encapsulates contract details for different exchanges.

### Attributes

- **symbol**: The symbol of the contract.
- **base_asset**: The base asset of the contract.
- **quote_asset**: The quote asset of the contract.
- **price_decimals**: The number of decimal places for the price.
- **quantity_decimals**: The number of decimal places for the quantity.
- **tick_size**: The minimum price movement.
- **lot_size**: The minimum quantity movement.
- **quanto** (Bitmex only): Indicates if the contract is a quanto derivative.
- **inverse** (Bitmex only): Indicates if the contract is an inverse derivative.
- **multiplier** (Bitmex only): The contract multiplier.

### Constructor Parameters

- `contract_info`: A dictionary containing contract details.
- `exchange`: The exchange to which the contract belongs.

## 4. `OrderStatus` Class

### Description

The `OrderStatus` class holds information about the status of an order on different exchanges.

### Attributes

- **order_id**: The unique identifier of the order.
- **status**: The current status of the order.
- **avg_price**: The average price at which the order is executed.
- **executed_qty**: The quantity of the order that has been executed.

### Constructor Parameters

- `order_info`: A dictionary containing order details.
- `exchange`: The exchange on which the order was placed.

## 5. `Trade` Class

### Description

The `Trade` class represents a trade executed by the bot.

### Attributes

- **time**: The timestamp of the trade.
- **contract**: The contract associated with the trade.
- **strategy**: The strategy used for the trade.
- **side**: The side of the trade (buy/sell).
- **entry_price**: The entry price of the trade.
- **status**: The current status of the trade.
- **pnl**: The profit or loss of the trade.
- **quantity**: The quantity involved in the trade.
- **entry_id**: A unique identifier for the trade entry.

### Constructor Parameters

- `trade_info`: A dictionary containing trade information.

## Utility Functions

### `tick_to_decimals`

A function to convert a tick size to the number of decimal places.

#### Parameters

- `tick_size`: The tick size to convert.

#### Returns

The number of decimal places for the given tick size.

---

This documentation should be used as a reference for understanding and working with the various models in the Astro - Starlight crypto bot. It is crucial for ensuring code clarity and ease of maintenance.
