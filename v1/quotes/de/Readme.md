# Quotes API Documentation

This API provides access to a collection of quotes in German. The base URL for the API is `https://api.andyproject.de/v1/quotes/de`.

## Endpoints

### 1. Get a Random Quote

**Endpoint:** `/`

**Description:** Returns a random quote from the collection.

**Method:** `GET`

**Parameters:** None

**Example Request:**
```bash
curl https://api.andyproject.de/v1/quotes/de
```

**Example Response:**
```json
{
  "id": 1,
  "quote": "Das Leben ist wie Fahrrad fahren. Um die Balance zu halten, musst du in Bewegung bleiben.",
  "author": "Albert Einstein"
}
```

### 2. Get a Quote by ID

**Endpoint:** `/?id={id}`

**Description:** Returns a quote by its ID.

**Method:** `GET`

**Parameters:**
- `id` (required): The ID of the quote.

**Example Request:**
```bash
curl https://api.andyproject.de/v1/quotes/de?id=1
```

**Example Response:**
```json
{
  "id": 1,
  "quote": "Das Leben ist wie Fahrrad fahren. Um die Balance zu halten, musst du in Bewegung bleiben.",
  "author": "Albert Einstein"
}
```

### 3. Get All Quotes (Requires Access Token)

**Endpoint:** `/?all&token={token}`

**Description:** Returns all quotes in the collection. Requires an access token.

**Method:** `GET`

**Parameters:**
- `all` (required): Indicates that all quotes should be returned.
- `token` (required): The access token to authorize the request.

**Example Request:**
```bash
curl https://api.andyproject.de/v1/quotes/de?all&token=your_access_token
```

**Example Response:**
```json
{
  "quotes": [
    {
      "id": 1,
      "quote": "Das Leben ist wie Fahrrad fahren. Um die Balance zu halten, musst du in Bewegung bleiben.",
      "author": "Albert Einstein"
    },
    {
      "id": 2,
      "quote": "Der einzige Weg, großartige Arbeit zu leisten, ist zu lieben, was man tut.",
      "author": "Steve Jobs"
    }
    // ...more quotes...
  ]
}
```

### 4. Get Quotes by Author

**Endpoint:** `/?sortby={author}`

**Description:** Returns a random quote by the specified author.

**Method:** `GET`

**Parameters:**
- `sortby` (required): The name of the author.

**Example Request:**
```bash
curl https://api.andyproject.de/v1/quotes/de?sortby=Albert%20Einstein
```

**Example Response:**
```json
{
  "id": 1,
  "quote": "Das Leben ist wie Fahrrad fahren. Um die Balance zu halten, musst du in Bewegung bleiben.",
  "author": "Albert Einstein"
}
```

### 5. Get List of Authors

**Endpoint:** `/?sortby=authors`

**Description:** Returns a list of all authors in the collection.

**Method:** `GET`

**Parameters:**
- `sortby` (required): Must be set to `authors`.

**Example Request:**
```bash
curl https://api.andyproject.de/v1/quotes/de?sortby=authors
```

**Example Response:**
```json
[
  "Albert Einstein",
  "Steve Jobs",
  // ...more authors...
]
```

## Error Handling

The API returns appropriate error messages and HTTP status codes for various error conditions.

### Example Error Response (Invalid Access Token)

**Response:**
```json
{
  "error": "Ungültiger Access Token",
  "code": 403
}
```

### Example Error Response (Quote Not Found)

**Response:**
```json
{
  "error": "Zitat nicht gefunden"
}
```

## Notes

- All responses are in JSON format.
- The API supports CORS (Cross-Origin Resource Sharing) by allowing requests from any origin.
- The character encoding for all responses is UTF-8.

For further assistance, please contact the API support team.
