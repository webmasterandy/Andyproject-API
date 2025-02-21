# Cat API

This API provides random cat pictures from various subreddits.

## Endpoint

`https://api.andyproject.de/v1/fun/cat`

## Parameters

- `top`: Fetch top cat posts.
- `new`: Fetch new cat posts.
- `hot`: Fetch hot cat posts.
- `rising`: Fetch rising cat posts.
- `all`: Return all cat posts from the cache.

## Usage

### Fetch a Random cat post

To fetch a random cat post, simply call the endpoint without any parameters:

```
GET https://api.andyproject.de/v1/fun/cat
```

### Fetch Cat post by Category

To fetch cat post by category, add the desired parameter:

```
GET https://api.andyproject.de/v1/fun/cat?top
GET https://api.andyproject.de/v1/fun/cat?new
GET https://api.andyproject.de/v1/fun/cat?hot
GET https://api.andyproject.de/v1/fun/cat?rising
```

### Fetch All cat posts

To fetch all cat posts from the cache, use the `all` parameter:

```
GET https://api.andyproject.de/v1/fun/cat?all
```

## Response

The API returns a JSON object with the following structure:

```json
{
  "title": "Meme Title",
  "url": "https://example.com/meme.jpg"
}
```

## Example

### Request

```
GET https://api.andyproject.de/v1/fun/cat?top
```

### Response

```json
{
  "title": "Funny Cat Meme",
  "url": "https://example.com/funny-cat.jpg"
}
```
