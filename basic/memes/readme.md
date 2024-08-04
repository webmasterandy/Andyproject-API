# API Documentation: Meme Endpoint

This document explains how to use the Meme Endpoint available at `https://api.andyproject.de/memes/`. This endpoint returns a random meme from the latest posts in the `r/dankmemes` and `r/memes` subreddits.

## Endpoint

`GET https://api.andyproject.de/memes/`

### Optional Query Parameters

- `no-gif` (boolean): When set, the endpoint will exclude GIF memes from the results.

## Example Request

### Basic Request

To get a random meme:

```bash
curl -X GET "https://api.andyproject.de/memes/"
```

### Request without GIFs

To get a random meme excluding GIFs:

```bash
curl -X GET "https://api.andyproject.de/memes/?no-gif=true"
```

## Example Response

```json
{
    "title": "Funny Meme Title",
    "url": "https://i.redd.it/funnymeme.jpg"
}
```

## Example Python Script

Below is a simple Python script that demonstrates how to use this endpoint.

```python
import requests

def get_random_meme(no_gif=False):
    base_url = "https://api.andyproject.de/memes/"
    params = {'no-gif': 'true'} if no_gif else {}
    
    response = requests.get(base_url, params=params)
    
    if response.status_code == 200:
        meme = response.json()
        return meme
    else:
        raise Exception(f"Failed to fetch meme: {response.status_code}")

# Example usage:
if __name__ == "__main__":
    try:
        random_meme = get_random_meme(no_gif=True)
        print(f"Title: {random_meme['title']}")
        print(f"URL: {random_meme['url']}")
    except Exception as e:
        print(e)
```

### Explanation of the PHP Script

The provided PHP script does the following:

1. **Fetches New Memes**:
   - It retrieves new posts from the `r/dankmemes` and `r/memes` subreddits.
   - It uses a custom user-agent to avoid being blocked by Reddit.
2. **Caching**:
   - It caches the memes in a `cache.json` file for 210 seconds to reduce the number of API requests to Reddit.
3. **Filtering**:
   - If the `no-gif` parameter is set, it filters out GIF memes.
4. **Random Selection**:
   - It selects a random meme from the cached memes.
5. **Response**:
   - It returns the selected meme in JSON format.

This PHP script is called every time the endpoint is accessed, ensuring that the response is quick and efficient by using cached data when available.
