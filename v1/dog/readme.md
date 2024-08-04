### Endpoint Documentation: `https://api.andyproject.de/v1/dog/`

The endpoint returns a random dog meme from the latest posts in the subreddits r/DOG and r/cutedog. Optionally, you can fetch only image posts (jpg, jpeg, png).

#### Parameters

- `img` (optional): When this parameter is set, only images are returned.

#### Response

The response is a JSON object with the following fields:
- `title`: The title of the Reddit post.
- `url`: The URL of the post.

#### Example Usage of the Endpoint

```python
import requests

# Base URL of the endpoint
url = "https://api.andyproject.de/v1/dog/"

# Optional: Parameters to fetch only images
params = {
    "img": 1
}

# Send HTTP GET request
response = requests.get(url, params=params)

# Check if the request was successful
if response.status_code == 200:
    # Parse JSON response
    data = response.json()
    print("Title:", data['title'])
    print("URL:", data['url'])
else:
    print("Request failed with status code:", response.status_code)
```

#### Example without Image Filter

```python
import requests

# Base URL of the endpoint
url = "https://api.andyproject.de/v1/dog/"

# Send HTTP GET request
response = requests.get(url)

# Check if the request was successful
if response.status_code == 200:
    # Parse JSON response
    data = response.json()
    print("Title:", data['title'])
    print("URL:", data['url'])
else:
    print("Request failed with status code:", response.status_code)
```

#### Notes

- The API caches data for 210 seconds. This means the same meme may be returned multiple times if requests are made within this time window.
- The Reddit API requires a User-Agent header to successfully complete requests.
- A repetition of the memes can be prevented by making adjustments to your own script.
