# API Documentation for https://api.andyproject.de/quotes/de/

## Overview
This API allows you to retrieve quotes from a Quote database. You can fetch a single quote by ID, get all quotes with proper authentication, or obtain quotes based on specific authors or a random selection. 

## Endpoints

### GET /quotes/de/

#### Query Parameters

- `id` (optional): Fetches a specific quote by its ID.
- `all` (optional): Fetches all quotes. Requires a valid access token.
- `token` (optional): Access token required when fetching all quotes.
- `sortby` (optional): Can be used to sort by authors or fetch quotes by a specific author.

### Responses

#### 1. Fetch a Single Quote by ID

- **Request**
  ```http
  GET /quotes/de/?id={id}
  ```
  - `id` (int): The ID of the quote to retrieve.

- **Response**
  ```json
  {
    "id": 1,
    "quote": "Example quote",
    "author": "Author Name",
    "added": "2021-01-01",
    "length": 13
  }
  ```

#### 2. Fetch All Quotes (Requires Access Token)

- **Request**
  ```http
  GET /quotes/de/?all=true&token={access_token}
  ```
  - `all` (boolean): Set to `true` to fetch all quotes.
  - `token` (string): Access token for authentication.

- **Response**
  ```json
  {
    "quotes": [
      {
        "id": 1,
        "quote": "Example quote 1",
        "author": "Author Name",
        "added": "2021-01-01",
        "length": 15
      },
      {
        "id": 2,
        "quote": "Example quote 2",
        "author": "Another Author",
        "added": "2021-02-01",
        "length": 16
      }
    ]
  }
  ```

- **Error Response (No Token Provided)**
  ```json
  {
    "error": "Es wurde kein Access Token angegeben",
    "code": 403,
    "Info": "Es ist ein Token erforderlich um auf den gesamten Datensatz zuzugreifen."
  }
  ```

- **Error Response (Invalid Token)**
  ```json
  {
    "error": "Ungültiger Access Token",
    "code": 403
  }
  ```

#### 3. Fetch Quotes by Author or Sorted by Authors

- **Request (Sorted by Authors)**
  ```http
  GET /quotes/de/?sortby=authors
  ```

- **Response (Sorted by Authors)**
  ```json
  [
    "Author One",
    "Author Two",
    "Author Three"
  ]
  ```

- **Request (Quotes by Specific Author)**
  ```http
  GET /quotes/de/?sortby=Albert Hofmann
  ```

- **Response (Quotes by Specific Author)**
  ```json
  {
    "id": 1,
    "quote": "Example quote by Albert Hofmann",
    "author": "Albert Hofmann",
    "added": "2021-03-01",
    "length": 29
  }
  ```

- **Error Response (Author Not Found)**
  ```json
  {
    "error": "Autor nicht gefunden"
  }
  ```

#### 4. Fetch a Random Quote

- **Request**
  ```http
  GET /quotes/de/
  ```

- **Response**
  ```json
  {
    "id": 1,
    "quote": "Random example quote",
    "author": "Random Author",
    "added": "2021-04-01",
    "length": 22
  }
  ```

## Example Python Script

```python
import requests

# Fetch a random quote
response = requests.get('https://api.andyproject.de/quotes/de/')
if response.status_code == 200:
    print(response.json())
else:
    print("Error:", response.status_code)

# Fetch a specific quote by ID
quote_id = 1
response = requests.get(f'https://api.andyproject.de/quotes/de/?id={quote_id}')
if response.status_code == 200:
    print(response.json())
else:
    print("Error:", response.status_code)

# Fetch all quotes (requires token)
access_token = 'your_access_token_here'
response = requests.get(f'https://api.andyproject.de/quotes/de/?all=true&token={access_token}')
if response.status_code == 200:
    print(response.json())
else:
    print("Error:", response.status_code)
```

This documentation provides details on how to use the API endpoints to retrieve quotes in various ways. For further assistance, ensure you have proper access tokens where required and adjust query parameters as necessary.
