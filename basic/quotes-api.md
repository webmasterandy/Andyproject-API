# API Documentation for `https://api.andyproject.de/quotes/`

This API endpoint provides random quotes from a predefined list. The quotes are returned in JSON format with UTF-8 encoding.

## Endpoint

### URL

`https://api.andyproject.de/quotes/`

### Method

`GET`

### Response

The response is a JSON object containing a random quote, along with additional metadata.

#### Response Example

```json
{
    "quote": "Life is what happens when you're busy making other plans.",
    "author": "John Lennon",
    "length": 54
}
```

#### Response Parameters

- `quote` (string): The text of the quote.
- `author` (string): The author of the quote.
- `length` (integer): The length of the quote in characters.

## Usage

### Python Example

The following Python example demonstrates how to retrieve a random quote from the API and display it.

```import requests

# Define the API endpoint
url = 'https://api.andyproject.de/quotes/'

# Send a GET request to the API
response = requests.get(url)

# Check if the request was successful
if response.status_code == 200:
    # Parse the JSON response
    random_quote = response.json()
    
    # Display the quote
    print("Quote:", random_quote['quote'])
    print("Author:", random_quote['author'])
    print("Length:", random_quote['length'])
else:
    # Handle the error
    print(f"Error: Unable to fetch quote (Status code: {response.status_code})")

```

## Error Handling

The API may return standard HTTP status codes to indicate the success or failure of a request:

- `200 OK`: The request was successful, and the quote is returned in the response.
- `404 Not Found`: The endpoint could not be found.
- `500 Internal Server Error`: The server encountered an unexpected condition that prevented it from fulfilling the request.

## Notes

- Ensure that your application correctly handles UTF-8 encoded JSON responses.
- The quotes are selected randomly, so multiple requests may yield different quotes each time.

## Additional Information

For any questions or further assistance, please open a ticket.

This documentation provides a comprehensive guide on how to use the `https://api.andyproject.de/quotes/` endpoint, including an example of how to implement it in PHP. The response structure and error handling information help users integrate the API into their applications effectively.
