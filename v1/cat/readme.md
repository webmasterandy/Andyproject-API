# API Endpoint Documentation

## Endpoint URL

```
https://api.andyproject.de/v1/cat/
```

## Description

This API endpoint fetches new posts from the Reddit subreddits `/r/cats` and `/r/CatSlaps`, caches them, and returns a random post. If the `img` query parameter is provided, only image posts (`.jpg`, `.jpeg`, `.png`) are considered.

## Request

### Optional Query Parameters

- `img` (optional): When this parameter is present, the API will only return image posts.

### Example Request

To fetch a random post:

```
https://api.andyproject.de/v1/cat/
```

To fetch a random image post:

```
https://api.andyproject.de/v1/cat/?img=true
```

## Response

### JSON Object

The response will be a JSON object with the following fields:

- `title`: The title of the Reddit post.
- `url`: The URL of the Reddit post.

### Example Response

```json
{
  "title": "Cute cat sleeping",
  "url": "https://i.redd.it/cute_cat.jpg"
}
```

## Python Example

Below is a simple Python script to demonstrate how to use this API endpoint.

```python
import requests

def get_random_cat_post(img=False):
    url = 'https://api.andyproject.de/v1/cat/'
    params = {}
    if img:
        params['img'] = 'true'
    
    response = requests.get(url, params=params)
    if response.status_code == 200:
        return response.json()
    else:
        return None

# Fetch a random post
random_post = get_random_cat_post()
print("Random Post:", random_post)

# Fetch a random image post
random_image_post = get_random_cat_post(img=True)
print("Random Image Post:", random_image_post)
```

### Usage

1. Import the `requests` module.
2. Define the `get_random_cat_post` function with an optional `img` parameter.
3. Make a GET request to the endpoint.
4. Check the status code and return the JSON response if successful.
5. Call the function and print the results.

This script demonstrates how to interact with the API and fetch random cat posts or image posts based on the provided parameter.
