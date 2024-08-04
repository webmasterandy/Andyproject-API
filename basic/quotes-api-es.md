# Documentation for the Endpoint: https://api.andyproject.de/quotes/es/

This endpoint provides random quotes in Spanish. The response is in JSON format and includes the quote along with additional metadata.

## Usage

### HTTP Method

`GET`

### Request URL

```
https://api.andyproject.de/quotes/es/
```

### Response

The response is a JSON object with the following fields:

- `quote`: The quote in Spanish.
- `author`: The author of the quote.
- `length`: The length of the quote in characters.

### Example Response

```json
{
  "quote": "La vida es sueño, y los sueños, sueños son.",
  "author": "Pedro Calderón de la Barca",
  "length": 43
}
```

## Example Usage in Python

The following Python script demonstrates how to call the endpoint and process the response:

```python
import requests

def get_random_quote():
    url = "https://api.andyproject.de/quotes/es/"
    response = requests.get(url)
    
    if response.status_code == 200:
        quote_data = response.json()
        print(f"Quote: {quote_data['quote']}")
        print(f"Author: {quote_data['author']}")
        print(f"Length: {quote_data['length']} characters")
    else:
        print(f"Error: {response.status_code}")

if __name__ == "__main__":
    get_random_quote()
```

This script uses the `requests` library to send a GET request to the endpoint. If the response is successful (status code 200), the quote and its metadata are printed. Otherwise, an error message is displayed.

### Prerequisites

Ensure that the `requests` library is installed. You can install it using the following command:

```sh
pip install requests
```

## Notes

- The endpoint provides random quotes, so each call will return a different quote.
- The response encoding is UTF-8.
