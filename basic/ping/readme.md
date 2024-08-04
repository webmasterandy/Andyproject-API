# API Documentation

## Endpoint: `https://api.andyproject.de/ping/`

This endpoint performs a ping request, measures CPU, RAM, and network usage, and returns the results in JSON format.

### HTTP Method

`GET`

### Response

The response is a JSON object with the following fields:

- `ping`: The average round-trip time (RTT) of the ping in milliseconds.
- `cpu_usage`: The CPU usage.
- `ram_usage`: The RAM usage in percent.
- `download_usage`: The network download consumption in kilobytes per second.
- `upload_usage`: The network upload consumption in kilobytes per second.

### Example

#### Request

```http
GET /ping/ HTTP/1.1
Host: api.andyproject.de
```

#### Response

```json
{
    "ping": 12.345,
    "cpu_usage": 0.25,
    "ram_usage": 45,
    "download_usage": 1024.5,
    "upload_usage": 512.3
}
```

### Example Python Script for Using the Endpoint

```python
import requests

url = "https://api.andyproject.de/ping/"
response = requests.get(url)

if response.status_code == 200:
    data = response.json()
    print("Ping (ms):", data['ping'])
    print("CPU Usage:", data['cpu_usage'])
    print("RAM Usage (%):", data['ram_usage'])
    print("Download Usage (KB/s):", data['download_usage'])
    print("Upload Usage (KB/s):", data['upload_usage'])
else:
    print("Request failed with status code:", response.status_code)
```

This script sends a GET request to the endpoint and prints the results to the console.
