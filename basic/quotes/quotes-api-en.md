# API Documentation: Quotes Endpoint in English

## Endpoint URL

`https://api.andyproject.de/quotes/en/`

## HTTP Methods

- `GET`

## Headers

```php
header('Access-Control-Allow-Origin: *');
header('Access-Control-Allow-Methods: GET, POST, OPTIONS');
header('Access-Control-Allow-Headers: Content-Type, Authorization');
header('Content-Type: application/json; charset=utf-8');
```

## Parameters

### Query Parameters

- `id` (optional): An integer representing the ID of a specific quote.
- `all` (optional): If set, retrieves all quotes. Requires a valid access token.
- `token` (optional): Access token required when using the `all` parameter.
- `sortby` (optional): String parameter used for sorting. Can be:
  - `authors`: Returns a list of authors sorted alphabetically.
  - `author_name`: Returns all quotes by the specified author.

## Responses

### Success Response

#### 200 OK

When fetching a specific quote by `id`:

```json
{
  "id": 1,
  "quote": "Your Quote Here",
  "author": "Author Name",
  "added": "Date Added",
  "length": 18
}
```

When fetching all quotes (with valid `token`):

```json
{
  "quotes": [
    {
      "id": 1,
      "quote": "Your Quote Here",
      "author": "Author Name",
      "added": "Date Added",
      "length": 18
    },
  ]
}
```

When fetching sorted authors:

```json
[
  "Author Name 1",
  "Author Name 2",
]
```

When fetching quotes by a specific author:

```json
{
  "id": 1,
  "quote": "Your Quote Here",
  "author": "Author Name",
  "added": "Date Added",
  "length": 18
}
```

### Error Responses

#### 403 Forbidden

- Missing or invalid access token when using the `all` parameter:

```json
{
  "error": "Es wurde kein Access Token angegeben",
  "code": 403,
  "Info": "Es ist ein Token erforderlich um auf den gesamten Datensatz zuzugreifen."
}
```

- Invalid token:

```json
{
  "error": "Ungültiger Access Token",
  "code": 403
}
```

#### 404 Not Found

- Quote not found by ID:

```json
{
  "error": "Zitat nicht gefunden"
}
```

- Author not found:

```json
{
  "error": "Autor nicht gefunden"
}
```

## Example Usage

### Python Script

```python
import requests

# Fetch a random quote
response = requests.get('https://api.andyproject.de/quotes/en/')
print(response.json())

# Fetch a specific quote by ID
quote_id = 1
response = requests.get(f'https://api.andyproject.de/quotes/en/?id={quote_id}')
print(response.json())

# Fetch all quotes (requires access token)
access_token = 'your_access_token'
response = requests.get(f'https://api.andyproject.de/quotes/en/?all&token={access_token}')
print(response.json())

# Fetch authors sorted alphabetically
response = requests.get('https://api.andyproject.de/quotes/en/?sortby=authors')
print(response.json())

# Fetch quotes by a specific author
author_name = 'Albert Hofmann'
response = requests.get(f'https://api.andyproject.de/quotes/en/?sortby={author_name}')
print(response.json())
```

## Notes

- Ensure you have the correct access token when using the `all` parameter.
- Use appropriate error handling in your scripts to manage API responses effectively.
- Access tokens can be requested by sending an e-mail to info@andyproject.de. Please provide a reason.
