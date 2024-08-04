# WeatherAPI Documentation

This documentation provides information on how to use the WeatherAPI endpoint available at `https://api.andyproject.de/v1/weather/`. The API retrieves weather data based on location headers provided in the request.

## Endpoint

### Get Weather by Location
Fetch weather data by specifying a city, state code, and country code through HTTP headers.

**URL:** `https://api.andyproject.de/v1/weather/`

**Method:** `GET`

**Headers:**
- `X-City`: Name of the city (e.g., "Berlin")
- `X-State-Code`: State code (e.g., "BE")
- `X-Country-Code`: Country code (e.g., "DE")

**Response:**
- Returns weather data in JSON format.
- If location data is not found, returns an error message.

## Example Python Script

Below is a simple Python script demonstrating how to use the WeatherAPI endpoint to fetch weather data by specifying location headers.

```python
import requests

# Define the API endpoint
url = "https://api.andyproject.de/v1/weather/"

# Define the headers with location information
headers = {
    'X-City': 'Berlin',
    'X-State-Code': 'BE',
    'X-Country-Code': 'DE'
}

# Send the GET request to the API endpoint
response = requests.get(url, headers=headers)

# Print the response from the API
print(response.json())
```

## Possible State Codes
Below is a list of possible state codes for Germany:

- `BW`: Baden-Württemberg
- `BY`: Bayern (Bavaria)
- `BE`: Berlin
- `BB`: Brandenburg
- `HB`: Bremen
- `HH`: Hamburg
- `HE`: Hessen (Hesse)
- `MV`: Mecklenburg-Vorpommern
- `NI`: Niedersachsen (Lower Saxony)
- `NW`: Nordrhein-Westfalen (North Rhine-Westphalia)
- `RP`: Rheinland-Pfalz (Rhineland-Palatinate)
- `SL`: Saarland
- `SN`: Sachsen (Saxony)
- `ST`: Sachsen-Anhalt (Saxony-Anhalt)
- `SH`: Schleswig-Holstein
- `TH`: Thüringen (Thuringia)

## Error Handling
The API returns appropriate error messages in the following scenarios:
- **No location data found:**
  ```json
  {
    "error": "No location data found.",
    "info": "Please visit https://github.com/webmasterandy/Andyproject-API/tree/main/v1/weather for more information."
  }
  ```
- **No weather data found:**
  ```json
  {
    "error": "No weather data found."
  }
  ```

## Note
Ensure that you have the correct headers set with valid location information to get the desired weather data. For more detailed information, please visit the [GitHub repository](https://github.com/webmasterandy/Andyproject-API/tree/main/v1/weather).
