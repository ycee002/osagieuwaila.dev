# The Movie Database (TMDB) API Documentation

**API Version:** 3.0.0

Welcome to Version 3 of The Movie Database (TMDB) API. This documentation provides a comprehensive overview of the available methods for accessing movie, TV, actor, and image data through TMDB's services.

### Contact Information

For support or inquiries, please contact **The Movie Database Support** at [https://www.themoviedb.org/talk](https://www.themoviedb.org/talk).

### API Server

**Production Server:** [https://api.themoviedb.org/3](https://api.themoviedb.org/3)

---

## Endpoints

## GET `/movie/popular` – Popular Movies

Retrieve a list of movies sorted by popularity.

### Authentication

**Security**: `api_key` (Query parameter)

### Query Parameters

| Name | Type    | Required | Description                                    |
| ---- | ------- | -------- | ---------------------------------------------- |
| page | integer | No       | Specify the page number for paginated results. |

### Responses

#### 200 – Success

Successful response with a list of popular movies.

```json
{
  "page": 1,
  "results": [
    {
      "adult": false,
      "backdrop_path": "/x58Gk2ZGU5AEBp25MQe2nhZhd5z.jpg",
      "genre_ids": [28, 14],
      "id": 846422,
      "original_language": "en",
      "original_title": "The Old Guard 2",
      "overview": "Andy and her team of immortal warriors fight with renewed purpose as they face a powerful new foe threatening their mission to protect humanity.",
      "popularity": 617.5863,
      "poster_path": "/wqfu3bPLJaEWJVk3QOm0rKhxf1A.jpg",
      "release_date": "2025-07-01",
      "title": "The Old Guard 2",
      "video": false,
      "vote_average": 6.2,
      "vote_count": 363
    }
  ],
  "total_pages": 51345,
  "total_results": 1026899
}
```

#### 401 – Unauthorized

Invalid or missing API key.

```json
{
  "error": "Unauthorized",
  "message": "Invalid or missing API key."
}
```

#### 500 – Internal Server Error

Something went wrong on the server.

```json
{
  "error": "Internal Server Error",
  "message": "Something went wrong. Please try again later."
}
```

---

## GET `/movie/top_rated` – Top Rated Movies

Retrieve a list of movies sorted by their rating.

### Authentication

**Security**: `api_key` (Query parameter)

### Query Parameters

| Name | Type    | Required | Description                                    |
| ---- | ------- | -------- | ---------------------------------------------- |
| page | integer | No       | Specify the page number for paginated results. |

### Responses

#### 200 – Success

Successful response with a list of top rated movies.

```json
{
  "page": 1,
  "results": [
    {
      "adult": false,
      "backdrop_path": "/x58Gk2ZGU5AEBp25MQe2nhZhd5z.jpg",
      "genre_ids": [28, 14],
      "id": 846422,
      "original_language": "en",
      "original_title": "The Old Guard 2",
      "overview": "Andy and her team of immortal warriors fight with renewed purpose as they face a powerful new foe threatening their mission to protect humanity.",
      "popularity": 617.5863,
      "poster_path": "/wqfu3bPLJaEWJVk3QOm0rKhxf1A.jpg",
      "release_date": "2025-07-01",
      "title": "The Old Guard 2",
      "video": false,
      "vote_average": 6.2,
      "vote_count": 363
    }
  ],
  "total_pages": 51345,
  "total_results": 1026899
}
```

#### 401 – Unauthorized

Invalid or missing API key.

```json
{
  "error": "Unauthorized",
  "message": "Invalid or missing API key."
}
```

#### 500 – Internal Server Error

Something went wrong on the server.

```json
{
  "error": "Internal Server Error",
  "message": "Something went wrong. Please try again later."
}
```

---

## GET `/movie/upcoming` – Upcoming Movies

Retrieve a list of movies that are scheduled to be released soon.

### Authentication

**Security:** `api_key` (Query parameter)

### Query Parameters

| Name | Type    | Required | Description                                    |
| ---- | ------- | -------- | ---------------------------------------------- |
| page | integer | No       | Specify the page number for paginated results. |

### Responses

#### 200 – Success

Successful response with a list of upcoming movies.

```json
{
  "dates": {
    "maximum": "2025-08-06",
    "minimum": "2025-07-16"
  },
  "page": 1,
  "results": [
    {
      "adult": false,
      "backdrop_path": "/zViRwl3ySscZnbXZJ2Q9wq3SeUG.jpg",
      "genre_ids": [16, 878, 12, 10751],
      "id": 698687,
      "original_language": "en",
      "original_title": "Transformers One",
      "overview": "The untold origin story of Optimus Prime and Megatron, better known as sworn enemies, but once were friends bonded like brothers who changed the fate of Cybertron forever.",
      "popularity": 18.261,
      "poster_path": "/iRCgqpdVE4wyLQvGYU3ZP7pAtUc.jpg",
      "release_date": "2024-09-11",
      "title": "Transformers One",
      "video": false,
      "vote_average": 8.073,
      "vote_count": 1302
    }
  ],
  "total_pages": 43,
  "total_results": 843
}
```

#### 401 – Unauthorized

```json
{
  "error": "Unauthorized",
  "message": "Invalid or missing API key."
}
```

#### 500 – Internal Server Error

```json
{
  "error": "Internal Server Error",
  "message": "Something went wrong. Please try again later."
}
```

---

## GET `/movie/{movie_id}/changes` – Movie Changes

Retrieve the recent changes made to a specific movie.

### Authentication

**Security:** `api_key` (Query parameter)

### Path Parameters

| Name      | Type    | Required | Description                 |
| --------- | ------- | -------- | --------------------------- |
| movie\_id | integer | Yes      | The unique ID of the movie. |

### Responses

#### 200 – Success

Successful response with movie changes.

```json
{
  "changes": [
    {
      "key": "alternative_titles",
      "items": [
        {
          "id": "686e31940ad7681110ed6369",
          "action": "added",
          "time": "2025-07-09 09:08:36 UTC",
          "iso_639_1": "",
          "iso_3166_1": "UA",
          "value": {
            "title": "Глави держав",
            "type": "",
            "iso_3166_1": "UA"
          }
        }
      ]
    }
  ]
}
```

#### 401 – Unauthorized

```json
{
  "error": "Unauthorized",
  "message": "Invalid or missing API key."
}
```

#### 404 – Movie Not Found

```json
{
  "error": "Not Found",
  "message": "Movie not found."
}
```

#### 500 – Internal Server Error

```json
{
  "error": "Internal Server Error",
  "message": "Something went wrong. Please try again later."
}
```

---

## GET `/movie/{movie_id}` – Movie Details

Retrieve the top-level details of a movie by its ID.

### Authentication

**Security:** `api_key` (Query parameter)

### Path Parameters

| Name      | Type    | Required | Description                 |
| --------- | ------- | -------- | --------------------------- |
| movie\_id | integer | Yes      | The unique ID of the movie. |

### Responses

#### 200 – Success

Successful response with movie details.

```json
{
  "adult": false,
  "backdrop_path": null,
  "belongs_to_collection": null,
  "budget": 0,
  "genres": [],
  "homepage": "",
  "id": 1511648,
  "imdb_id": null,
  "origin_country": ["CN"],
  "original_language": "zh",
  "original_title": "祈愿",
  "overview": "Three years epidemic later, many villages and towns in Sichuan Province began to resume traditional cultural activities-Temple fairs.\nFor thousands of years, villagers usually thanked various gods by inviting opera troupe to sing and through asking the divinatory symbols to dream,\nmaking and returning wishes with inductive ways to interact with the gods.\nIn the clouds of incense and fire, pray for their own worldly interests to be realized, but also obtain spiritual comfort.",
  "popularity": 0.0,
  "poster_path": null,
  "production_companies": [],
  "production_countries": [],
  "release_date": "2024-01-01",
  "revenue": 0,
  "runtime": 30,
  "spoken_languages": [],
  "status": "Released",
  "tagline": "",
  "title": "Praying",
  "video": false,
  "vote_average": 0.0,
  "vote_count": 0
}
```

#### 401 – Unauthorized

```json
{
  "error": "Unauthorized",
  "message": "Invalid or missing API key."
}
```

#### 404 – Movie Not Found

```json
{
  "error": "Not Found",
  "message": "Movie not found."
}
```

#### 500 – Internal Server Error

```json
{
  "error": "Internal Server Error",
  "message": "Something went wrong. Please try again later."
}
```

---

## GET `/movie/{movie_id}/lists` – Lists Containing Movie

Retrieve the lists that a movie has been added to.

### Authentication

**Security:** `api_key` (Query parameter)

### Parameters

| Name      | In    | Type    | Required | Description                                    |
| --------- | ----- | ------- | -------- | ---------------------------------------------- |
| movie\_id | path  | integer | Yes      | The unique ID of the movie.                    |
| page      | query | integer | No       | Specify the page number for paginated results. |

### Responses

#### 200 – Success

Successful response with lists containing the movie.

```json
{
  "id": 846422,
  "page": 1,
  "results": [
    {
      "description": "",
      "favorite_count": 0,
      "id": 8530523,
      "item_count": 16,
      "iso_639_1": "en",
      "iso_3166_1": "US",
      "list_type": "movie",
      "name": "sifou3 ",
      "poster_path": null
    }
  ],
  "total_pages": 10,
  "total_results": 198
}
```

#### 401 – Unauthorized

```json
{
  "error": "Unauthorized",
  "message": "Invalid or missing API key."
}
```

#### 404 – Movie Not Found

```json
{
  "error": "Not Found",
  "message": "Movie not found."
}
```

#### 500 – Internal Server Error

```json
{
  "error": "Internal Server Error",
  "message": "Something went wrong. Please try again later."
}
```

---

## GET `/movie/latest` – Latest Movie

Retrieve the newest movie added to TMDB.

### Authentication

**Security:** `api_key` (Query parameter)

### Responses

#### 200 – Success

Successful response with details of the latest movie.

```json
{
  "adult": false,
  "backdrop_path": null,
  "belongs_to_collection": null,
  "budget": 0,
  "genres": [],
  "homepage": "",
  "id": 1511648,
  "imdb_id": null,
  "origin_country": ["CN"],
  "original_language": "zh",
  "original_title": "祈愿",
  "overview": "Three years epidemic later, many villages and towns in Sichuan Province began to resume traditional cultural activities-Temple fairs.\nFor thousands of years, villagers usually thanked various gods by inviting opera troupe to sing and through asking the divinatory symbols to dream,\nmaking and returning wishes with inductive ways to interact with the gods.\nIn the clouds of incense and fire, pray for their own worldly interests to be realized, but also obtain spiritual comfort.",
  "popularity": 0.0,
  "poster_path": null,
  "production_companies": [],
  "production_countries": [],
  "release_date": "2024-01-01",
  "revenue": 0,
  "runtime": 30,
  "spoken_languages": [],
  "status": "Released",
  "tagline": "",
  "title": "Praying",
  "video": false,
  "vote_average": 0.0,
  "vote_count": 0
}
```

#### 401 – Unauthorized

```json
{
  "error": "Unauthorized",
  "message": "Invalid or missing API key."
}
```

#### 500 – Internal Server Error

```json
{
  "error": "Internal Server Error",
  "message": "Something went wrong. Please try again later."
}
```

---

## POST `/movie/{movie_id}/rating` – Rate a Movie

Submit a rating for a movie and save it to your rated list.

### Authentication

**Security:** `bearerAuth` (Bearer token)

### Path Parameters

| Name      | Type    | Required | Description                 |
| --------- | ------- | -------- | --------------------------- |
| movie\_id | integer | Yes      | The unique ID of the movie. |

### Request Body

**Required:** Yes
**Content-Type:** `application/json`

```json
{
  "value": 8
}
```

### Responses

#### 201 – Created

Movie rated successfully.

```json
{
  "success": true,
  "status_code": 12,
  "status_message": "The item/record was updated successfully."
}
```

#### 400 – Bad Request

```json
{
  "error": "Bad Request",
  "message": "Invalid rating value or malformed request."
}
```

#### 401 – Unauthorized

```json
{
  "error": "Unauthorized",
  "message": "Invalid or missing API key."
}
```

#### 404 – Movie Not Found

```json
{
  "error": "Not Found",
  "message": "Movie not found."
}
```

#### 500 – Internal Server Error

```json
{
  "error": "Internal Server Error",
  "message": "Something went wrong. Please try again later."
}
```

---

## GET `/list/{list_id}/item_status` – Check if Item Exists in List

Check whether a specific item has already been added to a list.

### Authentication

**Security:** `api_key` (Query parameter)

### Path Parameters

| Name     | Type    | Required | Description               | Example |
| -------- | ------- | -------- | ------------------------- | ------- |
| list\_id | integer | Yes      | The unique ID of the list | 8542348 |

### Responses

#### 200 – Success

Successful response indicating whether the item is present.

```json
{
  "id": "8542348",
  "item_present": false
}
```

#### 401 – Unauthorized

```json
{
  "error": "Unauthorized",
  "message": "Invalid or missing API key."
}
```

#### 404 – List Not Found

```json
{
  "error": "Not Found",
  "message": "The list with the specified ID was not found."
}
```

#### 500 – Internal Server Error

```json
{
  "error": "Internal Server Error",
  "message": "Something went wrong. Please try again later."
}
```

---

## POST `/list` – Create a New List

Create a new list in your TMDB account to organise your favourite movies and TV shows.

### Authentication

**Security:**

* `api_key` (Query parameter)
* `session_id` (Query parameter)

### Request Body

**Content-Type:** `application/json`

```json
{
  "name": "My Favourite Shows",
  "iso_639_1": "en",
  "description": "This is a list of my favourite TV shows and movies."
}
```

### Responses

#### 201 – Created

List created successfully.

```json
{
  "success": true,
  "status_code": 1,
  "status_message": "Success.",
  "list_id": 8542396
}
```

#### 400 – Bad Request

```json
{
  "error": "Bad Request",
  "message": "Invalid input. Please check the request body."
}
```

#### 401 – Unauthorized

```json
{
  "error": "Unauthorized",
  "message": "Invalid or missing API key or session ID."
}
```

#### 500 – Internal Server Error

```json
{
  "error": "Internal Server Error",
  "message": "Something went wrong. Please try again later."
}
```

---

## POST `/list/{list_id}/add_item` – Add Movie to List

Add a movie to an existing list.

### Authentication

**Security:**

* `api_key` (Query parameter)
* `session_id` (Query parameter)

### Path Parameters

| Name     | Type    | Required | Description               | Example |
| -------- | ------- | -------- | ------------------------- | ------- |
| list\_id | integer | Yes      | The unique ID of the list | 8542348 |

### Request Body

**Content-Type:** `application/json`

```json
{
  "media_id": 551
}
```

### Responses

#### 201 – Created

Movie added to list successfully.

```json
{
  "success": true,
  "status_code": 12,
  "status_message": "The item/record was updated successfully."
}
```

#### 400 – Bad Request

```json
{
  "error": "Bad Request",
  "message": "Invalid input. Please check the request body."
}
```

#### 401 – Unauthorized

```json
{
  "error": "Unauthorized",
  "message": "Invalid or missing API key or session ID."
}
```

#### 404 – List Not Found

```json
{
  "error": "Not Found",
  "message": "The list with the specified ID was not found."
}
```

#### 500 – Internal Server Error

```json
{
  "error": "Internal Server Error",
  "message": "Something went wrong. Please try again later."
}
```

---

## component

### Security Schemes

| Name         | Type   | In    | Scheme | Bearer Format | Description                                                        |
| ------------ | ------ | ----- | ------ | ------------- | ------------------------------------------------------------------ |
| `api_key`    | apiKey | query | –      | –             | API key required as a query parameter to authenticate requests.    |
| `bearerAuth` | http   | –     | bearer | JWT           | Enter your JWT bearer token to authenticate requests.              |
| `session_id` | apiKey | query | –      | –             | Session ID required as a query parameter to authenticate requests. |

---

### schemas

## Popular Movies

### Object Properties

| Name            | Type             | Description                                                            |
| --------------- | ---------------- | ---------------------------------------------------------------------- |
| `page`          | integer          | Current page number.                                                   |
| `results`       | array of objects | List of popular movies. Each item contains detailed movie information. |
| `total_pages`   | integer          | Total number of pages available.                                       |
| `total_results` | integer          | Total number of movie results found.                                   |

### `results[]` – Movie Object

| Name                | Type    | Description                                  |
| ------------------- | ------- | -------------------------------------------- |
| `adult`             | boolean | Indicates if the movie is for adults.        |
| `backdrop_path`     | string  | Path to the backdrop image.                  |
| `genre_ids`         | array   | List of genre IDs associated with the movie. |
| `id`                | integer | Unique ID of the movie.                      |
| `original_language` | string  | ISO 639-1 code of the original language.     |
| `original_title`    | string  | Original title of the movie.                 |
| `overview`          | string  | Brief summary of the movie.                  |
| `popularity`        | number  | Popularity score of the movie.               |
| `poster_path`       | string  | Path to the movie poster image.              |
| `release_date`      | string  | Release date of the movie (`YYYY-MM-DD`).    |
| `title`             | string  | Title of the movie.                          |
| `video`             | boolean | Whether the movie has a video version.       |
| `vote_average`      | number  | Average user rating.                         |
| `vote_count`        | integer | Total number of votes received.              |

---

## Top Rated Movies

The response schema for **Top Rated Movies** is identical to the [Popular Movies](#schema--popular-movies) schema.

It includes pagination metadata (`page`, `total_pages`, `total_results`) and a `results` array containing detailed movie objects with fields such as `id`, `title`, `overview`, `genre_ids`, `vote_average`, etc.

Please refer to the [Popular Movies schema](#popular-movies) for the full structure and field descriptions.

---

## Upcoming Movies

The response schema for **Upcoming Movies** is identical to the [Popular Movies schema](#popular-movies), with one additional field at the top level:

### Additional Field

| Name    | Type   | Description                                                                                                             |
| ------- | ------ | ----------------------------------------------------------------------------------------------------------------------- |
| `dates` | object | A date range object indicating the minimum and maximum release dates for the upcoming movies in the current result set. |

### `dates` Object

| Name      | Type   | Description                          | Example        |
| --------- | ------ | ------------------------------------ | -------------- |
| `maximum` | string | Latest release date in this batch.   | `"2025-08-06"` |
| `minimum` | string | Earliest release date in this batch. | `"2025-07-16"` |

For all other fields, refer to the [Popular Movies schema](#popular-movies).

---

## Movie Changes

Returns a list of all the changes made to a movie, grouped by change type.

### Object Properties

| Name      | Type             | Description                                        |
| --------- | ---------------- | -------------------------------------------------- |
| `changes` | array of objects | List of change groups, each identified by a `key`. |

### `changes[]` – Change Group Object

| Name    | Type             | Description                                      |
| ------- | ---------------- | ------------------------------------------------ |
| `key`   | string           | The type of change (e.g., `alternative_titles`). |
| `items` | array of objects | List of change entries under this key.           |

### `items[]` – Change Detail Object

| Name         | Type   | Description                                                      |
| ------------ | ------ | ---------------------------------------------------------------- |
| `id`         | string | Unique identifier of the change record.                          |
| `action`     | string | Type of change action (e.g., `added`, `updated`, `deleted`).     |
| `time`       | string | Timestamp of when the change occurred (UTC).                     |
| `iso_639_1`  | string | ISO 639-1 language code (may be empty if not language-specific). |
| `iso_3166_1` | string | ISO 3166-1 country code.                                         |
| `value`      | object | The actual change content, structure varies depending on `key`.  |

### `value` (for `alternative_titles` key)

| Name         | Type   | Description                                         |
| ------------ | ------ | --------------------------------------------------- |
| `title`      | string | The alternative title that was added or updated.    |
| `type`       | string | Type/category of the alternative title.             |
| `iso_3166_1` | string | Country code associated with the alternative title. |

---

## Movie Details

Provides comprehensive information about a single movie.

### Object Properties

| Name                    | Type             | Description                                                        |
| ----------------------- | ---------------- | ------------------------------------------------------------------ |
| `adult`                 | boolean          | Indicates if the movie is intended for adults.                     |
| `backdrop_path`         | string \| null   | Path to the backdrop image, if available.                          |
| `belongs_to_collection` | object \| null   | Information about the collection the movie belongs to, if any.     |
| `budget`                | integer          | Production budget in USD.                                          |
| `genres`                | array of objects | List of genres associated with the movie.                          |
| `homepage`              | string           | Official homepage URL of the movie.                                |
| `id`                    | integer          | Unique TMDB ID for the movie.                                      |
| `imdb_id`               | string \| null   | IMDb ID for the movie.                                             |
| `origin_country`        | array of strings | Country codes where the movie was produced.                        |
| `original_language`     | string           | ISO 639-1 code for the original language.                          |
| `original_title`        | string           | Original title of the movie.                                       |
| `overview`              | string           | Brief summary or plot of the movie.                                |
| `popularity`            | number           | Popularity score based on user activity.                           |
| `poster_path`           | string \| null   | Path to the poster image, if available.                            |
| `production_companies`  | array of objects | List of companies involved in production.                          |
| `production_countries`  | array of objects | List of countries involved in production.                          |
| `release_date`          | string           | Release date of the movie (`YYYY-MM-DD`).                          |
| `revenue`               | integer          | Revenue generated by the movie in USD.                             |
| `runtime`               | integer          | Duration of the movie in minutes.                                  |
| `spoken_languages`      | array of objects | Languages spoken in the movie.                                     |
| `status`                | string           | Current status of the movie (e.g., `Released`, `Post Production`). |
| `tagline`               | string           | Movie tagline or slogan.                                           |
| `title`                 | string           | Localized or marketed title of the movie.                          |
| `video`                 | boolean          | Whether the movie is a video-only release.                         |
| `vote_average`          | number           | Average user rating for the movie.                                 |
| `vote_count`            | integer          | Total number of votes the movie has received.                      |

---

## Lists Containing Movie

Returns public TMDB user-created lists that contain a specific movie.

### Object Properties

| Name            | Type             | Description                                            |
| --------------- | ---------------- | ------------------------------------------------------ |
| `id`            | integer          | TMDB ID of the movie being queried.                    |
| `page`          | integer          | Current page number of the results.                    |
| `results`       | array of objects | List of public lists that include the specified movie. |
| `total_pages`   | integer          | Total number of available pages.                       |
| `total_results` | integer          | Total number of matching lists.                        |

### `results[]` – List Object

| Name             | Type           | Description                                     |
| ---------------- | -------------- | ----------------------------------------------- |
| `description`    | string         | Description of the user-created list.           |
| `favorite_count` | integer        | Number of users who have favorited the list.    |
| `id`             | integer        | Unique ID of the list.                          |
| `item_count`     | integer        | Number of items (movies/TV shows) in the list.  |
| `iso_639_1`      | string         | ISO 639-1 language code of the list content.    |
| `iso_3166_1`     | string         | ISO 3166-1 country code for the list.           |
| `list_type`      | string         | Type of list (e.g., `movie`, `tv`).             |
| `name`           | string         | Name of the list.                               |
| `poster_path`    | string \| null | Path to the list’s representative poster image. |

---

## Latest Movie

The response schema for **Latest Movie** is identical to the [Movie Details schema](#movie-details). It returns the full movie object for the most recently added movie in the database.

> **Note:** This endpoint returns a **single movie object** rather than a paginated list.

For a detailed breakdown of fields such as `title`, `overview`, `genres`, `production_companies`, and more, refer to the [Movie Details schema](#movie-details).

---

## Rate a Movie

Allows a user to submit a personal rating for a movie. The rating must be a decimal between **0.5 and 10.0**, using increments of 0.5.

### Request Body

**Content-Type:** `application/json`

| Name    | Type   | Required | Description                                             |
| ------- | ------ | -------- | ------------------------------------------------------- |
| `value` | number | Yes      | Rating value between 0.5 and 10.0 (step increment: 0.5) |

### Response Body

| Name             | Type    | Description                                      |
| ---------------- | ------- | ------------------------------------------------ |
| `success`        | boolean | Indicates whether the rating was accepted.       |
| `status_code`    | integer | TMDB status code that describes the result.      |
| `status_message` | string  | Message explaining the outcome of the operation. |

---

## Check if Item Exists in List

Checks if a particular media item (movie or TV show) exists in a specified list.

| Name           | Type    | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| `id`           | string  | The unique identifier of the list.                           |
| `item_present` | boolean | Indicates whether the specified item is present in the list. |

---

## Create a New List

### `NewList` (Request)

| Name          | Type   | Required | Description                                              |
| ------------- | ------ | -------- | -------------------------------------------------------- |
| `name`        | string | Yes      | The name of the list.                                    |
| `iso_639_1`   | string | Yes      | ISO 639-1 code representing the language (e.g., `"en"`). |
| `description` | string | Yes      | A short description of the list.                         |

### `NewListResponse`

| Name             | Type    | Description                                            |
| ---------------- | ------- | ------------------------------------------------------ |
| `success`        | boolean | Indicates if the list was created successfully.        |
| `status_code`    | integer | TMDB-specific status code indicating operation result. |
| `status_message` | string  | A message describing the outcome.                      |
| `list_id`        | integer | The unique ID of the newly created list.               |

---

## Add Movie to List

### `AddMovie` (Request)

| Name       | Type    | Required | Description                    |
| ---------- | ------- | -------- | ------------------------------ |
| `media_id` | integer | Yes      | The TMDB movie ID to be added. |

### `AddMovieResponse` 

| Name             | Type    | Description                                                |
| ---------------- | ------- | ---------------------------------------------------------- |
| `success`        | boolean | Indicates if the movie was successfully added to the list. |
| `status_code`    | integer | TMDB-specific status code indicating operation result.     |
| `status_message` | string  | A message describing the outcome.                          |

---

### `ErrorResponse`

| Name      | Type   | Description                                      |
| --------- | ------ | ------------------------------------------------ |
| `error`   | string | A short description of the error type.           |
| `message` | string | A detailed explanation of what caused the error. |