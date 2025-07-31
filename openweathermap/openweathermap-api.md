# OpenWeatherMap API Documentation

## Overview

**Version:** 1.0.0
**Base URL:** `https://api.openweathermap.org`
**Description:**
Access weather, air pollution, and geocoding data using OpenWeatherMap's reliable APIs.

---

## Endpoint: GET /data/2.5/weather

### Summary

Get Current Weather by Location

### Description

This endpoint provides the current weather conditions for any given geographical coordinates (latitude and longitude).

### Security

* ApiKeyAuth (query parameter: `appid`)

### Parameters

| Name | In    | Type   | Required | Description               |
| ---- | ----- | ------ | -------- | ------------------------- |
| lat  | query | number | Yes      | Latitude of the location  |
| lon  | query | number | Yes      | Longitude of the location |

### Responses

#### 200 OK – Successfully retrieved current weather data

```json
{
  "coord": {"lon": 3.3792, "lat": 6.5244},
  "weather": [{"id": 211, "main": "Thunderstorm", "description": "thunderstorm", "icon": "11n"}],
  "base": "stations",
  "main": {"temp": 298.27, "feels_like": 299.29, "pressure": 1011, "humidity": 94},
  "visibility": 8000,
  "wind": {"speed": 1.54, "deg": 220},
  "clouds": {"all": 20},
  "dt": 1750790921,
  "sys": {"type": 1, "id": 1185, "country": "NG", "sunrise": 1750743231, "sunset": 1750788231},
  "timezone": 3600,
  "id": 2566677,
  "name": "Shogunle",
  "cod": 200
}
```

#### 400 Bad Request

```json
{ "error": "Latitude and longitude are required" }
```

#### 401 Unauthorized

```json
{ "error": "API key is invalid or missing" }
```

#### 500 Internal Server Error

```json
{ "error": "Unexpected server error" }
```

---

## Endpoint: GET /map/{layer}/{z}/{x}/{y}.png

### Summary

Get Weather Map Tile

### Description

This endpoint delivers a PNG image representing a specific weather layer (like clouds or wind) for a given map tile.

### Security

* ApiKeyAuth (query parameter: `appid`)

### Path Parameters

| Name  | Type    | Required | Description                                         |
| ----- | ------- | -------- | --------------------------------------------------- |
| layer | string  | Yes      | Type of weather layer (e.g. clouds\_new, wind\_new) |
| z     | integer | Yes      | Zoom level (0–18)                                   |
| x     | integer | Yes      | X-coordinate of the tile grid                       |
| y     | integer | Yes      | Y-coordinate of the tile grid                       |

### Responses

#### 200 OK – Returns a PNG image

* Content-Type: image/png

#### 401 Unauthorized

```json
{ "error": "API key is invalid or missing" }
```

#### 404 Not Found

```json
{ "error": "Tile not found" }
```

#### 500 Internal Server Error

```json
{ "error": "Unexpected server error" }
```

---

## Endpoint: GET /data/2.5/air\_pollution

### Summary

Get Air Pollution Data by Location

### Description

This endpoint provides current air pollution and AQI data for a specified geographical location.

### Security

* ApiKeyAuth (query parameter: `appid`)

### Parameters

| Name | In    | Type   | Required | Description               |
| ---- | ----- | ------ | -------- | ------------------------- |
| lat  | query | number | Yes      | Latitude of the location  |
| lon  | query | number | Yes      | Longitude of the location |

### Responses

#### 200 OK

```json
{
  "coord": {"lon": 3.3792, "lat": 6.5244},
  "list": [{
    "main": {"aqi": 1},
    "components": {"co": 107.89, "no": 0, "no2": 0.07, "nh3": 0.01},
    "dt": 1750798781
  }]
}
```

#### 400 Bad Request

```json
{ "error": "Latitude and longitude are required" }
```

#### 401 Unauthorized

```json
{ "error": "API key is invalid or missing" }
```

#### 500 Internal Server Error

```json
{ "error": "Unexpected server error" }
```

---

## Endpoint: GET /geo/1.0/direct

### Summary

Convert Location Name to Coordinates (Geocoding)

### Description

This endpoint translates a location name into its geographical coordinates. Optionally include state and country.

### Security

* ApiKeyAuth (query parameter: `appid`)

### Parameters

| Name  | In    | Type    | Required | Description                              |
| ----- | ----- | ------- | -------- | ---------------------------------------- |
| q     | query | string  | Yes      | Location name (e.g., city,state,country) |
| limit | query | integer | No       | Max number of results to return (1–5)    |

### Responses

#### 200 OK

```json
[
  {
    "name": "London",
    "local_names": {"sv": "London"},
    "lat": 51.5073219,
    "lon": -0.1276474,
    "country": "GB",
    "state": "England"
  }
]
```

#### 400 Bad Request

```json
{ "error": "Query parameter 'q' is required" }
```

#### 401 Unauthorized

```json
{ "error": "API key is invalid or missing" }
```

#### 500 Internal Server Error

```json
{ "error": "Unexpected server error" }
```

---

## Components

### Security Schemes

| Scheme     | Type   | In    | Name  | Description         |
| ---------- | ------ | ----- | ----- | ------------------- |
| ApiKeyAuth | apiKey | query | appid | Your unique API key |

### Parameters

| Name | In    | Type           | Required | Description             |
| ---- | ----- | -------------- | -------- | ----------------------- |
| lat  | query | number (float) | Yes      | Latitude (-90 to 90)    |
| lon  | query | number (float) | Yes      | Longitude (-180 to 180) |

### Schemas

#### Weather

| Property         | Type    | Description                     |
| ---------------- | ------- | ------------------------------- |
| coord.lat        | number  | Latitude of the location        |
| coord.lon        | number  | Longitude of the location       |
| weather\[]       | array   | List of weather conditions      |
| base             | string  | Internal parameter              |
| main.temp        | number  | Temperature (Kelvin)            |
| main.feels\_like | number  | Feels like temperature (Kelvin) |
| main.pressure    | integer | Pressure in hPa                 |
| main.humidity    | integer | Humidity in %                   |
| visibility       | integer | Visibility in meters            |
| wind.speed       | number  | Wind speed (m/s)                |
| wind.deg         | integer | Wind direction (degrees)        |
| clouds.all       | integer | Cloudiness in %                 |
| dt               | integer | Data timestamp (Unix)           |
| sys.country      | string  | Country code                    |
| sys.sunrise      | integer | Sunrise time (Unix)             |
| sys.sunset       | integer | Sunset time (Unix)              |
| timezone         | integer | Shift from UTC (seconds)        |
| id               | integer | City ID                         |
| name             | string  | City name                       |
| cod              | integer | Internal parameter              |

#### AirPollution

| Property                  | Type    | Description                 |
| ------------------------- | ------- | --------------------------- |
| coord.lat                 | number  | Latitude of the location    |
| coord.lon                 | number  | Longitude of the location   |
| list\[].main.aqi          | integer | AQI index (1–5)             |
| list\[].components.co     | number  | CO concentration (μg/m³)    |
| list\[].components.no     | number  | NO concentration (μg/m³)    |
| list\[].components.no2    | number  | NO₂ concentration (μg/m³)   |
| list\[].components.o3     | number  | O₃ concentration (μg/m³)    |
| list\[].components.so2    | number  | SO₂ concentration (μg/m³)   |
| list\[].components.pm2\_5 | number  | PM2.5 concentration (μg/m³) |
| list\[].components.pm10   | number  | PM10 concentration (μg/m³)  |
| list\[].components.nh3    | number  | NH₃ concentration (μg/m³)   |
| list\[].dt                | integer | Timestamp (Unix)            |

#### Geocoding

| Property     | Type   | Description                 |
| ------------ | ------ | --------------------------- |
| name         | string | Location name               |
| local\_names | object | Names in multiple languages |
| lat          | number | Latitude                    |
| lon          | number | Longitude                   |
| country      | string | Country code                |
| state        | string | State (if applicable)       |

#### Error

| Property | Type   | Description   |
| -------- | ------ | ------------- |
| error    | string | Error message |
