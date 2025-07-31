## CoinGecko API Documentation

### Version

3.1.1

### Base URL

`https://api.coingecko.com/api/v3`

### Description

CoinGecko provides comprehensive crypto market data from over 1,000 exchanges and 17,000+ coins via RESTful JSON APIs.

---

## Endpoints

### GET `/ping`

**Summary:** Check API Server Status
**Description:** Verify CoinGecko API server is operational.

**Responses:**

* `200 OK`: API server is running.

  ```json
  {
    "gecko_says": "(V3) To the Moon!"
  }
  ```
* `500 Internal Server Error`

  ```json
  {
    "error": "Internal server error"
  }
  ```

---

### GET `/coins/list`

**Summary:** Get List of Supported Coins
**Description:** Retrieve a list of all supported coins (ID, symbol, name).

**Responses:**

* `200 OK`

  ```json
  [
    {
      "id": "ethereum",
      "symbol": "eth",
      "name": "Ethereum"
    },
    {
      "id": "bitcoin",
      "symbol": "btc",
      "name": "Bitcoin"
    }
  ]
  ```
* `500 Internal Server Error`

  ```json
  {
    "error": "Internal server error"
  }
  ```

---

### GET `/coins/{id}`

**Summary:** Get Metadata for a Specific Coin
**Description:** Retrieve detailed metadata for a coin using its unique CoinGecko ID.

**Path Parameters:**

| Name | Type   | Required | Description                                 |
| ---- | ------ | -------- | ------------------------------------------- |
| id   | string | Yes      | The unique ID of the coin (e.g., `bitcoin`) |

**Responses:**

* `200 OK`

  ```json
  {
    "id": "bitcoin",
    "symbol": "btc",
    "name": "Bitcoin"
  }
  ```
* `404 Not Found`

  ```json
  {
    "error": "Coin ID not found"
  }
  ```
* `500 Internal Server Error`

  ```json
  {
    "error": "Internal server error"
  }
  ```

---

### GET `/coins/markets`

**Summary:** Get Market Data for Coins
**Description:** Returns market data (price, market cap, 24h volume) for specified coins in a target currency.

**Query Parameters:**

| Name         | Type   | Required | Description                                                            |
| ------------ | ------ | -------- | ---------------------------------------------------------------------- |
| vs\_currency | string | Yes      | The target currency for market data (e.g., `usd`, `eur`, `jpy`).       |
| ids          | string | No       | Comma-separated list of coin IDs to filter (e.g., `bitcoin,ethereum`). |

**Responses:**

* `200 OK`

  ```json
  [
    {
      "id": "bitcoin",
      "symbol": "btc",
      "name": "Bitcoin",
      "current_price": 107824,
      "market_cap": 2145170791593
    }
  ]
  ```
* `400 Bad Request`

  ```json
  {
    "error": "Missing or invalid query parameter: vs_currency"
  }
  ```
* `404 Not Found`

  ```json
  {
    "error": "Coin not found"
  }
  ```
* `500 Internal Server Error`

  ```json
  {
    "error": "Internal server error"
  }
  ```

---

### GET `/simple/price`

**Summary:** Get Current Price for Coins
**Description:** Returns the current price for specified coins in target currencies.

**Query Parameters:**

| Name           | Type   | Required | Description                                                                |
| -------------- | ------ | -------- | -------------------------------------------------------------------------- |
| vs\_currencies | string | Yes      | Comma-separated list of target currency codes (e.g., `usd`, `eur`, `jpy`). |
| ids            | string | No       | Comma-separated list of coin IDs (e.g., `bitcoin,ethereum`).               |

**Responses:**

* `200 OK`

  ```json
  {
    "bitcoin": {
      "usd": 107893
    }
  }
  ```
* `400 Bad Request`

  ```json
  {
    "error": "Missing required parameter: vs_currencies"
  }
  ```
* `404 Not Found`

  ```json
  {
    "error": "Coin ID not found"
  }
  ```
* `500 Internal Server Error`

  ```json
  {
    "error": "Internal server error"
  }
  ```

---

## Component 

### Schemas

### Ping

| Field       | Type   | Example             | Description          |
| ----------- | ------ | ------------------- | -------------------- |
| gecko\_says | string | (V3) To the Moon!   | Message from the API. |

### CoinItem

|  Field    |  Type    |  Example    |    Description         |
| --------- | -------- | ----------- | ---------------------- |
| id        | string   | ethereum    | CoinGecko coin ID.     |
| symbol    | string   | eth         | Coin ticker symbol.    |
| name      | string   | Ethereum    | Full name of the coin. |

Usage

Type: Array of CoinItem

### CoinMetadata

| Field  | Type   | Example   | Description        |
| ------ | ------ | --------- | ------------------ |
| id     | string |  bitcoin  | CoinGecko coin ID.  |
| symbol | string |  btc      | Coin ticker symbol. |
| name   | string |  Bitcoin  | Coin full name.     |

### CoinMarketData

| Field          | Type    | Example       | Description               |
| -------------- | ------- | ------------- | ------------------------- |
| id             | string  |  bitcoin      | CoinGecko coin ID.         |
| symbol         | string  |  btc          | Coin ticker symbol.        |
| name           | string  |  Bitcoin      | Coin full name.            |
| current\_price | number   | 107824        | Current price in currency. |
| market\_cap    | integer | 2145170791593 | Market capitalization.     |

Usage

Type: Array of CoinMarketData

### SimplePrice

| Field  | Type   | Description                      |
| ------ | ------ | -------------------------------- |
| <coin> | object | Maps coin ID to currency prices. |

Nested coin object

| Field      | Type   | Description                     |
| ---------- | ------ | ------------------------------- |
| <currency> | number | Current price in that currency. |

### Error

| Field | Type   | Example                 | Description               |
| ----- | ------ | ----------------------- | ------------------------- |
| error | string | "Internal server error" | Error message description. |
