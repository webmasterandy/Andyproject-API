# MeIRL API Endpoint

This API endpoint provides random post from the subreddit r/meirl. The endpoint fetches the latest posts and caches them for a specified duration to reduce load on the Reddit API.

## Endpoint

`https://api.andyproject.de/v1/fun/meirl`

## Parameters

- `no-gif` (optional): If set, the API will filter out GIFs and only return images with extensions `jpg`, `jpeg`, or `png`.

## Example Request

To get a random meme:

```
GET https://api.andyproject.de/v1/fun/meirl
```

To get a random meme without GIFs:

```
GET https://api.andyproject.de/v1/fun/meirl?no-gif=true
```

## Example Response

```json
{
    "title": "Funny meme title",
    "url": "https://i.redd.it/example.jpg"
}
```

## Caching

The API caches the results for 210 seconds to reduce the number of requests to Reddit. If the cache is older than 210 seconds, it will fetch new data from Reddit.
