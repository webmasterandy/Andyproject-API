# API Documentation for Endpoint: https://api.andyproject.de/meirl/

This API endpoint returns a random meirl from the `/r/meirl` subreddit. The endpoint is designed to fetch new memes, cache them, and return a random meme on each request. The caching mechanism ensures that the endpoint does not overwhelm the Reddit API with requests.

## Endpoint

### GET https://api.andyproject.de/meirl/

#### Optional Query Parameters

- `no-gif` (boolean): When set to true, the endpoint filters out GIFs, returning only static images (JPG, JPEG, PNG).

#### Response

The response is a JSON object containing a randomly selected response from the cache. The JSON object has the following structure:

```json
{
    "title": "Meirl title",
    "url": "URL to the meril"
}
```

#### Example Response

```json
{
    "title": "meirl",
    "url": "https://i.redd.it/cf8m7mb9jngd1.png"
}
```

## Python Usage Example

Below is a Python script demonstrating how to use the API endpoint to fetch a random meme:

```python
import requests

def get_random_meme(no_gif=False):
    url = "https://api.andyproject.de/meirl/"
    params = {}
    if no_gif:
        params['no-gif'] = 'true'
    
    response = requests.get(url, params=params)
    if response.status_code == 200:
        meme = response.json()
        return meme
    else:
        return None

# Example usage
if __name__ == "__main__":
    meme = get_random_meme(no_gif=True)
    if meme:
        print(f"Title: {meme['title']}\nURL: {meme['url']}")
    else:
        print("Failed to fetch meme.")
```

### Description of the Python Script

1. **Import the requests library**: This library is used to make HTTP requests.
2. **Define the `get_random_meme` function**: This function accepts an optional parameter `no_gif` to filter out GIF memes if set to `True`.
3. **Construct the API URL and parameters**: The base URL is `https://api.andyproject.de/meirl/`. If `no_gif` is `True`, the parameter `no-gif=true` is added to the request.
4. **Make the GET request**: The `requests.get` function sends the HTTP GET request to the API endpoint.
5. **Check the response status code**: If the status code is 200 (OK), the JSON response is parsed and returned.
6. **Example usage**: If the script is run as the main program, it fetches a random meme with the `no_gif` parameter set to `True` and prints the title and URL of the meme.
