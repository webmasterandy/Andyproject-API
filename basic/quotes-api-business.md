# API Documentation for `https://api.andyproject.de/quotes/busi/`

## Description
This API provides access to a collection of business-related quotes. It supports several query parameters to retrieve quotes based on specific criteria.

## Base URL
```
https://api.andyproject.de/quotes/busi/
```

## Endpoints

### Retrieve All Quotes
**Endpoint:**
```
GET /?all&token={access_token}
```

**Description:**
Retrieves all quotes from the database. Requires an access token.

**Parameters:**
- `all`: Required to retrieve all quotes.
- `token`: Required. The access token to authenticate the request.

**Example Request:**
```sh
curl -X GET "https://api.andyproject.de/quotes/busi/?all&token=your_access_token"
```

**Example Response:**
```json
{
  "quotes": [
    {
      "id": 1,
      "quote": "The best way to predict the future is to create it.",
      "author": "Peter Drucker",
      "added": "2021-01-01",
      "length": 42
    },
    ...
  ]
}
```

### Retrieve Quote by ID
**Endpoint:**
```
GET /?id={quote_id}
```

**Description:**
Retrieves a specific quote based on its ID.

**Parameters:**
- `id`: Required. The ID of the quote.

**Example Request:**
```sh
curl -X GET "https://api.andyproject.de/quotes/busi/?id=1"
```

**Example Response:**
```json
{
  "id": 1,
  "quote": "The best way to predict the future is to create it.",
  "author": "Peter Drucker",
  "added": "2021-01-01",
  "length": 42
}
```

### Retrieve Quotes Sorted by Authors
**Endpoint:**
```
GET /?sortby=authors
```

**Description:**
Retrieves a list of authors sorted alphabetically.

**Parameters:**
- `sortby`: Required. Must be set to `authors`.

**Example Request:**
```sh
curl -X GET "https://api.andyproject.de/quotes/busi/?sortby=authors"
```

**Example Response:**
```json
[
  "Albert Einstein",
  "Peter Drucker",
  "Steve Jobs",
  ...
]
```

### Retrieve Quotes by Author
**Endpoint:**
```
GET /?sortby={author_name}
```

**Description:**
Retrieves all quotes by a specific author.

**Parameters:**
- `sortby`: Required. The name of the author.

**Example Request:**
```sh
curl -X GET "https://api.andyproject.de/quotes/busi/?sortby=Peter Drucker"
```

**Example Response:**
```json
{
  "id": 1,
  "quote": "The best way to predict the future is to create it.",
  "author": "Peter Drucker",
  "added": "2021-01-01",
  "length": 42
}
```

### Retrieve a Random Quote
**Endpoint:**
```
GET /
```

**Description:**
Retrieves a random quote from the database.

**Example Request:**
```sh
curl -X GET "https://api.andyproject.de/quotes/busi/"
```

**Example Response:**
```json
{
  "id": 2,
  "quote": "Innovation distinguishes between a leader and a follower.",
  "author": "Steve Jobs",
  "added": "2021-01-02",
  "length": 49
}
```

## Error Responses

### Missing or Invalid Token
**Response:**
```json
{
  "error": "Es wurde kein Access Token angegeben",
  "code": 403,
  "Info": "Es ist ein Token erforderlich um auf den gesamten Datensatz zuzugreifen."
}
```

### Invalid Author
**Response:**
```json
{
  "error": "Autor nicht gefunden"
}
```

## Example Python Script

```python
import requests

# Set the base URL
base_url = 'https://api.andyproject.de/quotes/busi/'

# Example: Retrieve all quotes (requires access token)
def get_all_quotes(token):
    response = requests.get(f"{base_url}?all&token={token}")
    return response.json()

# Example: Retrieve a quote by ID
def get_quote_by_id(quote_id):
    response = requests.get(f"{base_url}?id={quote_id}")
    return response.json()

# Example: Retrieve quotes sorted by authors
def get_authors():
    response = requests.get(f"{base_url}?sortby=authors")
    return response.json()

# Example: Retrieve quotes by author
def get_quotes_by_author(author_name):
    response = requests.get(f"{base_url}?sortby={author_name}")
    return response.json()

# Example: Retrieve a random quote
def get_random_quote():
    response = requests.get(base_url)
    return response.json()

# Example usage
if __name__ == "__main__":
    token = 'your_access_token'
    print(get_all_quotes(token))
    print(get_quote_by_id(1))
    print(get_authors())
    print(get_quotes_by_author('Peter Drucker'))
    print(get_random_quote())
```
