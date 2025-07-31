# OpenLibrary Subjects API

This API allows you to search for books and other works based on **subject tags**. You can refine your search using options like `details` (for more information), `ebooks` (to find only digital books), and `published_in` (to filter by publication year).

**Base URL:** `https://openlibrary.org`

---

## **GET /subjects/{subject}.json**

### Summary

Get books and works related to a specific subject.

### Description

Find a list of books and other content associated with a chosen subject. You can also narrow down results using optional filters like including more details, showing only ebooks, or specifying a publication year or range.

### **Parameters**

#### **Path Parameters**

| Name    | In   | Type   | Required | Description                                                                 |
| ------- | ---- | ------ | -------- | --------------------------------------------------------------------------- |
| subject | path | string | Yes      | The main subject you're interested in (e.g., "science fiction", "cooking"). |

#### **Query Parameters**

| Name          | In    | Type    | Required | Default | Description                                                                                                          |
| ------------- | ----- | ------- | -------- | ------- | -------------------------------------------------------------------------------------------------------------------- |
| details       | query | boolean | No       | false   | Set to true to get more extensive information for each work listed.                                                  |
| ebooks        | query | boolean | No       | false   | Set to true to display only works that have an ebook version available.                                              |
| published\_in | query | string  | No       | -       | Filter works by their publication date. You can provide a single year (e.g., "2000") or a range (e.g., "1950-1960"). |

### **Responses**

#### **200 – Success**

Returns a list of subjects and related works.

##### **Response Example**

```json
{
  "key": "/subjects/love",
  "name": "love",
  "subject_type": "subject",
  "work_count": 17822,
  "works": [
    {
      "key": "/works/OL21177W",
      "title": "Wuthering Heights",
      "edition_count": 2850,
      "cover_id": 12818862,
      "cover_edition_key": "OL38586477M",
      "subject": [
        "British and irish fiction (fictional works by one author)",
        "Drama",
        "Fiction",
        "Love stories",
        "Triangles (Interpersonal relations)",
        "Romance fiction",
        "Heathcliff (Fictitious character : Brontë)"
      ]
    }
  ]
}
```

#### **404 – Not Found**

The requested subject was not found.

##### **Response Example**

```json
{
  "status": 404,
  "message": "Subject not found in the database."
}
```

#### **500 – Internal Server Error**

An unexpected server error occurred.

##### **Response Example**

```json
{
  "status": 500,
  "message": "An unexpected error occurred. Please try again later."
}
```

---

## Components

### Schemas

### **SubjectList**

| Property      | Type    | Description                                                       |
| ------------- | ------- | ----------------------------------------------------------------- |
| key           | string  | The unique identifier for the subject. Example: /subjects/love.   |
| name          | string  | The name of the subject. Example: love.                           |
| subject\_type | string  | The type of entry (always 'subject' for this endpoint).           |
| work\_count   | integer | The total number of works found for this subject. Example: 17822. |
| works         | array   | A list of individual works related to the subject.                |

#### **Work Object (inside works array)**

| Property            | Type    | Description                                                              |
| ------------------- | ------- | ------------------------------------------------------------------------ |
| key                 | string  | The unique identifier for the work. Example: /works/OL21177W.            |
| title               | string  | The title of the work. Example: Wuthering Heights.                       |
| edition\_count      | integer | The number of different editions available for this work. Example: 2850. |
| cover\_id           | integer | The ID for the work's cover image. Example: 12818862.                    |
| cover\_edition\_key | string  | The key for the specific edition's cover image. Example: OL38586477M.    |
| subject             | array   | A list of subjects or tags associated with this work.                    |

---

### **ErrorResponse**

| Property | Type    | Description                                               |
| -------- | ------- | --------------------------------------------------------- |
| status   | integer | The HTTP status code of the error. Example: 404.          |
| message  | string  | A clear message describing the error. Example: Not found. |