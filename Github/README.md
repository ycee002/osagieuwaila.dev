# GitHub API Documentation

## Overview

GitHub's REST API helps you manage your GitHub resources like repositories, users, and organizations. You can automate tasks, integrate with other systems, and extend GitHub's features to fit your development needs.

### Version

**2022-11-28**

### Base URL

```
https://api.github.com
```

### Contact

* **Name:** GitHub API Support
* **Website:** [GitHub Support](https://support.github.com/)
* **Email:** [api-support@github.com](mailto:api-support@github.com)

---

## Endpoints

### GET `/orgs/{org}/repos`

#### Summary

Get Organization Repositories

#### Description

This endpoint retrieves a list of all repositories belonging to a specific GitHub organization.

#### Parameters

| Name | In   | Type   | Required | Description                          |
| ---- | ---- | ------ | -------- | ------------------------------------ |
| org  | path | string | true     | The name of the GitHub organization. |

#### Responses

##### 200 OK

A list of repositories for the specified organization.

**Content Type:** `application/json`

Example Response:

```json
[
  {
    "id": 15929,
    "node_id": "MDEwOlJlcG9zaXRvcnkxNTkyOQ==",
    "name": "albino",
    "full_name": "github/albino",
    "private": false,
    "owner": {
      "login": "github",
      "id": 9919,
      "node_id": "MDEyOk9yZ2FuaXphdGlvbjk5MTk=",
      "type": "Organization",
      "user_view_type": "public",
      "site_admin": false
    }
  }
]
```

##### 404 Not Found

Organization not found.

##### 500 Internal Server Error

Internal server error.

---

### POST `/orgs/{org}/repos`

#### Summary

Create Repository in Organization

#### Description

Use this endpoint to create a brand new repository within a specified organization on GitHub.

#### Security

Authentication required: Bearer Token (JWT)

#### Parameters

| Name | In   | Type   | Required | Description                          |
| ---- | ---- | ------ | -------- | ------------------------------------ |
| org  | path | string | true     | The name of the GitHub organization. |

#### Request Body

**Required:** Yes

**Content Type:** `application/json`

Example Request:

```json
{
  "name": "Ehizzymonie-programmer",
  "description": "API integration project to document Ehizzymonie programmer",
  "homepage": "https://github.com/myfashionhub/Ehizzy-programmer",
  "private": false,
  "has_issues": true,
  "has_projects": true,
  "has_wiki": false
}
```

#### Responses

##### 201 Created

Repository created successfully.

Example Response:

```json
{
  "id": 1011333072,
  "name": "Ehizzymonie-programmer",
  "full_name": "myfashionhub1234/Ehizzymonie-programmer",
  "private": false,
  "owner": {
    "login": "myfashionhub1234",
    "id": 218431065,
    "type": "Organization",
    "user_view_type": "public"
  }
}
```

##### 400 Bad Request

Invalid input data.

##### 401 Unauthorized

Authentication required.

##### 404 Not Found

Organization not found.

##### 500 Internal Server Error

Internal server error.

---

### GET `/repos/{owner}/{repo}`

#### Summary

Get Repository Details

#### Description

This endpoint fetches detailed information about a specific repository on GitHub.

#### Parameters

| Name  | In   | Type   | Required | Description                                                 |
| ----- | ---- | ------ | -------- | ----------------------------------------------------------- |
| owner | path | string | true     | The username or organization name that owns the repository. |
| repo  | path | string | true     | The name of the repository.                                 |

#### Responses

##### 200 OK

Repository details retrieved successfully.

Example Response:

```json
{
  "id": 1010657333,
  "name": "Ycee-tech-writer",
  "full_name": "myfashionhub1234/Ycee-tech-writer",
  "private": false,
  "owner": {
    "login": "myfashionhub1234",
    "id": 218431065,
    "type": "Organization",
    "user_view_type": "public",
    "site_admin": false
  }
}
```

##### 404 Not Found

Repository not found.

##### 500 Internal Server Error

Internal server error.

---

### PATCH `/repos/{owner}/{repo}`

#### Summary

Update Repository

#### Description

Use this endpoint to modify the details of an existing repository on GitHub.

#### Security

Authentication required: Bearer Token (JWT)

#### Parameters

| Name  | In   | Type   | Required | Description                                                 |
| ----- | ---- | ------ | -------- | ----------------------------------------------------------- |
| owner | path | string | true     | The username or organization name that owns the repository. |
| repo  | path | string | true     | The name of the repository.                                 |

#### Request Body

**Required:** Yes

**Content Type:** `application/json`

Example Request:

```json
{
  "name": "Zolando-fashion",
  "description": "This is an updated description for the repository.",
  "private": true
}
```

#### Responses

##### 200 OK

Repository updated successfully.

Example Response:

```json
{
  "id": 1011387773,
  "name": "Zolando-fashion",
  "full_name": "myfashionhub1234/Zolando-fashion",
  "private": false,
  "owner": {
    "login": "myfashionhub1234",
    "id": 218431065,
    "type": "Organization",
    "user_view_type": "public"
  }
}
```

##### 400 Bad Request

Invalid input data.

##### 401 Unauthorized

Authentication required.

##### 404 Not Found

Repository not found.

##### 500 Internal Server Error

Internal server error.

---

### GET `/users`

#### Summary

Get All Users

#### Description

This endpoint returns a comprehensive list of all publicly available users on GitHub.

#### Responses

##### 200 OK

Example Response:

```json
[
  {
    "login": "mojombo",
    "id": 1,
    "node_id": "MDQ6VXNlcjE=",
    "type": "User",
    "user_view_type": "public"
  }
]
```

##### 500 Internal Server Error

Internal server error.

---

### GET `/users/{username}`

#### Summary

Get User Profile

#### Description

Use this endpoint to retrieve the public profile information for any specific GitHub user.

#### Parameters

| Name     | In   | Type   | Required | Description                      |
| -------- | ---- | ------ | -------- | -------------------------------- |
| username | path | string | true     | The username of the GitHub user. |

#### Responses

##### 200 OK

Example Response:

```json
{
  "login": "ycee002",
  "id": 199307583,
  "node_id": "U_kgDOC-ExPw",
  "created_at": "2025-02-14T22:55:02Z",
  "updated_at": "2025-06-10T20:13:54Z"
}
```

##### 404 Not Found

User not found.

##### 500 Internal Server Error

Internal server error.

---

### GET `/rate_limit`

#### Summary

Get API Rate Limit Status

#### Description

This endpoint shows your current API rate limit status, including how many requests you have remaining and when the limit resets.

#### Responses

##### 200 OK

Example Response:

```json
{
  "resources": {
    "core": {
      "limit": 60,
      "remaining": 59,
      "reset": 1751319801,
      "used": 1,
      "resource": "core"
    }
  },
  "rate": {
    "limit": 60,
    "remaining": 59,
    "reset": 1751319801,
    "used": 1,
    "resource": "core"
  }
}
```

##### 500 Internal Server Error

Internal server error.

---

## Components

### Security Schemes

#### BearerAuth

| Type | Scheme | Bearer Format | Description                                             |
| ---- | ------ | ------------- | ------------------------------------------------------- |
| http | bearer | JWT           | Enter your Bearer token in the format `Bearer <token>`. |

### Schemas

### `Repository`

| Field      | Type    | Description                                                                                    |
| ---------- | ------- | ---------------------------------------------------------------------------------------------- |
| id         | integer | The unique identification number of the repository.                                            |
| node\_id   | string  | GitHub's global ID for the repository (used in GraphQL).                                       |
| name       | string  | The name of the repository.                                                                    |
| full\_name | string  | The complete name of the repository, including the owner's username (e.g., `owner/repo-name`). |
| private    | boolean | Indicates whether the repository is private (`true`) or public (`false`).                      |
| owner      | object  | Information about the repository owner. See [Owner Object](#owner-object).                     |

### Owner Object

| Field            | Type    | Description                                                           |
| ---------------- | ------- | --------------------------------------------------------------------- |
| login            | string  | The username of the repository owner.                                 |
| id               | integer | The unique identification number of the owner.                        |
| node\_id         | string  | GitHub's global ID for the owner.                                     |
| type             | string  | The type of the owner (e.g., `User`, `Organization`).                 |
| user\_view\_type | string  | The visibility type of the user profile (e.g., `public`).             |
| site\_admin      | boolean | `true` if the user is a GitHub site administrator, `false` otherwise. |

---

### `NewRepository` (Request)

| Field         | Type    | Description                                                                            |
| ------------- | ------- | -------------------------------------------------------------------------------------- |
| name          | string  | The desired name for the new repository. **(Required)**                                |
| description   | string  | A brief summary or description of the repository.                                      |
| homepage      | string  | A URL for a website related to the repository.                                         |
| private       | boolean | Set to `true` to make the repository private, `false` for public. Defaults to `false`. |
| has\_issues   | boolean | Set to `true` to enable the issues feature for the repository. Defaults to `true`.     |
| has\_projects | boolean | Set to `true` to enable the projects feature for the repository. Defaults to `true`.   |
| has\_wiki     | boolean | Set to `true` to enable the wiki feature for the repository. Defaults to `true`.       |

### `NewRepositoryResponse`

The response returned after creating a new repository conforms to the [`Repository`](#schema-repository) schema.

This means all fields and their structure in `NewRepositoryResponse` are identical to the existing `Repository` schema, including:

* `id`
* `name`
* `full_name`
* `private`
* `owner` (with nested fields)

For reference, see the complete [Repository Schema](#schema-repository) for detailed field descriptions.

---

### `OwnerRepositoryResponse`

The response returned when retrieving a repository owned by a specific user or organization conforms to the [`Repository`](#schema-repository) schema.

This means all fields in `OwnerRepositoryResponse` are identical to those in the `Repository` schema, including:

* `id`
* `node_id`
* `name`
* `full_name`
* `private`
* `owner` (with nested fields such as `login`, `id`, `type`, `site_admin`, etc.)

For a complete overview of the structure and field definitions, refer to the [Repository Schema](#schema-repository).

---

### `UpdateRepository` (Request)

| Field       | Type    | Description                                                             |
| ----------- | ------- | ----------------------------------------------------------------------- |
| name        | string  | The new name you want to give the repository.                           |
| description | string  | A new description for the repository.                                   |
| private     | boolean | Change to `true` to make the repository private, or `false` for public. |

### `UpdateRepositoryResponse`

The response returned after successfully updating a repository follows the same structure as the [`Repository`](#schema-repository) schema.

All fields in `UpdateRepositoryResponse` are identical to those in the `Repository` schema, including:

* `id`
* `name`
* `full_name`
* `private`
* `owner` (with nested fields)

For a complete breakdown of the response structure and field descriptions, refer to the [Repository Schema](#schema-repository).

---

### `Users`

| Field            | Type    | Description                                                |
| ---------------- | ------- | ---------------------------------------------------------- |
| login            | string  | The user's GitHub username.                                |
| id               | integer | The unique identification number for the user.             |
| node\_id         | string  | GitHub's global ID for the user.                           |
| type             | string  | The type of GitHub account (e.g., `User`, `Organization`). |
| user\_view\_type | string  | The visibility of the user's profile (e.g., `public`).     |

---

### `UserByUsername`

| Field       | Type               | Description                                       |
| ----------- | ------------------ | ------------------------------------------------- |
| login       | string             | The username of the user.                         |
| id          | integer            | The unique identification number for the user.    |
| node\_id    | string             | GitHub's global ID for the user.                  |
| created\_at | string (date-time) | Timestamp of when the user account was created.   |
| updated\_at | string (date-time) | Timestamp of the last update to the user account. |

---

### `RateLimit`

| Field     | Type   | Description                                                                                               |
| --------- | ------ | --------------------------------------------------------------------------------------------------------- |
| resources | object | Contains rate limit data for specific API resource categories. See [Resources Object](#resources-object). |
| rate      | object | Contains the global rate limit data. See [Rate Object](#rate-object).                                     |

### Resources Object

This object holds individual rate limits for specific resource groups like `core`, `integration_manifest`, and `search`.

#### `resources.core`

| Field     | Type    | Description                                           |
| --------- | ------- | ----------------------------------------------------- |
| limit     | integer | Total allowed requests for the `core` resource group. |
| remaining | integer | Number of remaining requests.                         |
| reset     | integer | The UTC epoch seconds when the rate limit resets.     |
| used      | integer | Number of used requests.                              |
| resource  | string  | Resource group name (`core`).                         |

#### `resources.integration_manifest`

| Field     | Type    | Description                                                  |
| --------- | ------- | ------------------------------------------------------------ |
| limit     | integer | Total allowed requests for the `integration_manifest` group. |
| remaining | integer | Number of remaining requests.                                |
| reset     | integer | The UTC epoch seconds when the rate limit resets.            |
| used      | integer | Number of used requests.                                     |
| resource  | string  | Resource group name (`integration_manifest`).                |

#### `resources.search`

| Field     | Type    | Description                                             |
| --------- | ------- | ------------------------------------------------------- |
| limit     | integer | Total allowed requests for the `search` resource group. |
| remaining | integer | Number of remaining requests.                           |
| reset     | integer | The UTC epoch seconds when the rate limit resets.       |
| used      | integer | Number of used requests.                                |
| resource  | string  | Resource group name (`search`).                         |

### Rate Object (Top-level Global Rate Limit)

| Field     | Type    | Description                                              |
| --------- | ------- | -------------------------------------------------------- |
| limit     | integer | Total number of allowed global requests.                 |
| remaining | integer | Number of remaining global requests.                     |
| reset     | integer | The UTC epoch seconds when the global rate limit resets. |
| used      | integer | Number of global requests already used.                  |
| resource  | string  | Resource group name (`rate`).                            |

---

### `Error`

| Field | Type   | Description                                               |
| ----- | ------ | --------------------------------------------------------- |
| error | string | A clear, easy-to-understand error message. **(Required)** |
