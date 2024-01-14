---
title: Binance connector
description: A guide on the binance connector
---

The `BinanceClient` class serves as a comprehensive connector for interacting with both the spot and futures markets on the Binance platform, supporting both live and test endpoints. Below is an extensive documentation for this class.

---

# BinanceClient Class Documentation

The `BinanceClient` class provides a robust interface for interacting with the Binance exchange. It supports operations on both futures and spot markets and can be configured for either testnet or live trading environments.

## Constructor

### Parameters

- **public_key** (`str`): The user's public API key.
- **secret_key** (`str`): The user's secret API key.
- **testnet** (`bool`): Flag to indicate whether to use Binance's testnet.
- **futures** (`bool`): If `False`, the client will operate in spot market mode.

### Description

Initializes the BinanceClient instance, setting up URLs and WebSocket connections based on the specified market type (futures or spot) and whether the testnet is being used. It also initializes various instance attributes, including contracts, balances, strategies, and WebSocket parameters.

## Methods

### \_add_log

#### Parameters

- **msg** (`str`): Message to be logged.

#### Description

Adds a log message to the internal log list, also logging it through the standard logger.

### \_generate_signature

#### Parameters

- **data** (`Dict`): Dictionary of parameters to be signed.

#### Description

Generates a HMAC SHA256 signature for the provided data.

### \_make_request

#### Parameters

- **method** (`str`): HTTP method ('GET', 'POST', 'DELETE').
- **endpoint** (`str`): API endpoint.
- **data** (`Dict`): Request parameters.

#### Description

A wrapper for making HTTP requests to the Binance API, handling errors and logging.

### get_contracts

#### Returns

- A dictionary of `Contract` objects.

#### Description

Retrieves a list of available contracts/symbols from the exchange and sorts them.

### get_historical_candles

#### Parameters

- **contract** (`Contract`): Contract object.
- **interval** (`str`): Time interval for candles.

#### Returns

- A list of `Candle` objects.

#### Description

Fetches historical candle data for a given contract and interval.

### get_bid_ask

#### Parameters

- **contract** (`Contract`): Contract object.

#### Returns

- Dictionary with 'bid' and 'ask' prices.

#### Description

Retrieves the current bid and ask prices for a given contract.

### get_balances

#### Returns

- A dictionary of `Balance` objects.

#### Description

Fetches the current balances from the account.

### place_order

#### Parameters

- **contract** (`Contract`): Contract object.
- **order_type** (`str`): Type of the order (e.g., 'LIMIT', 'MARKET').
- **quantity** (`float`): Order quantity.
- **side** (`str`): Order side ('buy' or 'sell').
- **price** (`float`, optional): Order price.
- **tif** (`str`, optional): Time in force for the order.

#### Returns

- `OrderStatus` object.

#### Description

Places an order on the Binance exchange.

### cancel_order

#### Parameters

- **contract** (`Contract`): Contract object.
- **order_id** (`int`): Order ID.

#### Returns

- `OrderStatus` object.

#### Description

Cancels an existing order.

### \_get_execution_price

#### Parameters

- **contract** (`Contract`): Contract object.
- **order_id** (`int`): Order ID.

#### Returns

- Average execution price (`float`).

#### Description

Calculates the average execution price for an order. Only applicable for spot trading.

### get_order_status

#### Parameters

- **contract** (`Contract`): Contract object.
- **order_id** (`int`): Order ID.

#### Returns

- `OrderStatus` object.

#### Description

Retrieves the status of a specified order.

### \_start_ws

#### Description

Starts the WebSocket connection and manages reconnection attempts.

### \_on_open

#### Parameters

- **ws** (`websocket.WebSocketApp`): WebSocket instance.

#### Description

Callback for when the WebSocket connection is opened.

### \_on_close

#### Parameters

- **ws** (`websocket.WebSocketApp`): WebSocket instance.

#### Description

Callback for when the WebSocket connection is closed.

### \_on_error

#### Parameters

- **ws** (`websocket.WebSocketApp`): WebSocket instance.
- **msg** (`str`): Error message.

#### Description

Callback for handling errors in the WebSocket connection.

### \_on_message

#### Parameters

- **ws** (`websocket.WebSocketApp`): WebSocket instance.
- **msg** (`str`): Message received.

#### Description

Callback for handling incoming messages through the WebSocket connection

.

### subscribe_channel

#### Parameters

- **contracts** (`List[Contract]`): List of contract objects.
- **channel** (`str`): Channel to subscribe to.
- **reconnection** (`bool`): Flag to force subscription during reconnection.

#### Description

Subscribes to a specific channel for updates on given contracts.

### get_trade_size

#### Parameters

- **contract** (`Contract`): Contract object.
- **price** (`float`): Current price of the asset.
- **balance_pct** (`float`): Percentage of the balance to use.

#### Returns

- Computed trade size (`float`).

#### Description

Computes the trade size based on the user's balance and the desired percentage to invest.

---

This documentation outlines the functionality and usage of the `BinanceClient` class within the Astro - Starlight crypto bot. It should serve as a reference for developers and users to understand and utilize the various features provided by this connector.
