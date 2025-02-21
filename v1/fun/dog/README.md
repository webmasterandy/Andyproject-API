# Dog Image API

This API provides random dog images from various subreddits. The endpoint fetches data from Reddit and caches it to improve performance.

## Endpoint

`https://api.andyproject.de/v1/fun/dog`

## Parameters

- `top`: Fetches the top posts.
- `new`: Fetches the newest posts.
- `hot`: Fetches the hot posts.
- `rising`: Fetches the rising posts.
- `all`: Returns the entire cache content.

## Usage

### Fetch a Random Dog Image

To fetch a random dog image, simply make a GET request to the endpoint without any parameters:

```
GET https://api.andyproject.de/v1/fun/dog
```

### Fetch Specific Types of Posts

To fetch specific types of posts, add the corresponding parameter to the query string:

```
GET https://api.andyproject.de/v1/fun/dog?top
GET https://api.andyproject.de/v1/fun/dog?new
GET https://api.andyproject.de/v1/fun/dog?hot
GET https://api.andyproject.de/v1/fun/dog?rising
```

### Fetch All Cached Dog Images

To fetch the entire cache content, use the `all` parameter:

```
GET https://api.andyproject.de/v1/fun/dog?all
```

## Response

The API returns a JSON object containing the dog image data. For a random dog image, the response will look like this:

```json
{
    "title": "Cute Dog",
    "url": "https://example.com/dog_image.jpg"
}
```

For the `all` parameter, the response will be an array of dog image objects:

```json
[
    {
        "title": "Cute Dog 1",
        "url": "https://example.com/dog_image1.jpg"
    },
    {
        "title": "Cute Dog 2",
        "url": "https://example.com/dog_image2.jpg"
    }
]
```

## Example

### Fetch a Random Dog Image

```bash
curl https://api.andyproject.de/v1/fun/dog
```

### Fetch Top Dog Posts

```bash
curl https://api.andyproject.de/v1/fun/dog?top
```

### Fetch All Cached Dog Images

```bash
curl https://api.andyproject.de/v1/fun/dog?all
```

## Notes

- The cache is refreshed every 10 minutes.
- Only image posts (jpg, jpeg, png, gif) are included in the response.
