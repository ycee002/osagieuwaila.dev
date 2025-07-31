# API Documentation Portfolio – Osagie Uwaila (Ycee)

Welcome to my API documentation portfolio. This repository contains real-world API documentation samples written using industry-standard formats: OpenAPI 3.x, Postman collections, and Markdown. All samples are structured for clarity, testing, and developer usability.

## Folder Structure

Each API project is organized within a single folder for clarity and easy navigation. For example:

[api-name]/
├── README.md            # Human-readable Markdown documentation
├── openapi.yaml         # OpenAPI 3.x spec in YAML format
└── postman_collection.json  # Postman collection file (.json)

> All folder names are lowercase for cross-platform consistency.

## Authentication Methods Used

| API Name         | Auth Method(s)           |
|------------------|--------------------------|
| TMDB             | Bearer Token, Query Key  |
| OpenWeatherMap   | Query Key                |
| CoinGecko        | No Auth                  |
| OpenLibrary      | No Auth                  |
| GitHub (Public)  | Optional Token (Bearer)  |

## Included Projects

| API | Description |
|-----|-------------|
| TMDB | A rich movie database API with support for bearer and query key authentication. |
| OpenWeatherMap | Real-time weather data API using query-based API keys. |
| CoinGecko | Cryptocurrency data API with public access (no authentication). |
| OpenLibrary | Open-source book and author database with easy public access. |
| GitHub Public API | User and repo data via GitHub’s REST API (token optional). |

## Contents of Each Folder

- `README.md` – A human-readable Markdown document for developers or product teams, including examples and error handling guides.
- `openapi.yaml` – The OpenAPI 3.0.3 spec, defining each endpoint, parameters, responses, error models, and security requirements.
- `postman_collection.json` – A Postman collection file ready to import to test all endpoints manually.

## Usage Instructions

1. Clone or download this repository.
2. Explore each API project folder.
3. Open the files directly:
   - `README.md` for human-readable instructions
   - `openapi.yaml` in Swagger Editor or Redoc
   - `postman_collection.json` in Postman for hands-on testing

## Author

**Osagie Uwaila (Ycee)**  
- GitHub: [github.com/ycee002](https://github.com/ycee002)  
- LinkedIn: [linkedin.com/in/osagie-uwaila-86b413374](https://www.linkedin.com/in/osagie-uwaila-86b413374/)  
- Email: Osagieuwaila31@gmail.com

## Contributing

I welcome collaborations, improvements, or feedback.  
Feel free to fork this repository or open a pull request.

> The OpenAPI specifications in this portfolio follow the 3.0.x versions (3.0.0 and 3.0.3) of the specification, and all documentation follows API writing best practices.
