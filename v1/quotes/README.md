# Quotes API

## Endpoint: `https://api.andyproject.de/v1/quotes/`

This endpoint provides the count of quotes available in different languages.

### HTTP Method
`GET`

### Response
The response is a JSON object containing the count of quotes for each language.

#### Example Response
```json
{
    "German Quotes": 10,
    "English Quotes": 15,
    "Russian Quotes": 5
}
```

### Notes
- The counts are retrieved from endpoints located at `./de`, `./en`, and `./ru`.
- If a file does not exist, the count for that language will be `0`.

### Usage
To use this endpoint, simply send a `GET` request to the URL and you will receive the counts of quotes in the response.
