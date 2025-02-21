# API Documentation

## Endpoint

`https://api.andyproject.de/v1/fun/drache`

## Description

This API endpoint returns a random quote from the "Drachenlord" along with the author information. The response is in JSON format and encoded in UTF-8.

## Request

### Method

`GET`

### URL

`https://api.andyproject.de/v1/fun/drache`

## Response

### Content-Type

`application/json; charset=utf-8`

### Example Response

```json
{
    "author": "Random Author",
    "data": "Random Quote"
}
```

### Response Fields

- `author`: A string representing the name of the author.
- `data`: A string containing the random quote.

## Usage

To use this API, simply send a `GET` request to the endpoint URL. The response will contain a JSON object with a random quote and the corresponding author.

## Example Request

```bash
curl -X GET "https://api.andyproject.de/v1/fun/drache"
```

## Example Response

```json
{
    "author": "Drachenlord",
    "data": "Random Quote"
}
```
