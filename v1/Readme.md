# Andyproject API
Here I would like a list of useful API endpoints. The Andyproject API offers several <br>
endpoints for free for projects. Of course a donation would be appreciated <a href="https://www.buymeacoffee.com/andyproject">Buy me a coffee</a>.
# Meme API
This API outputs a random meme from the subreddits <a href="https://www.reddit.com/r/dankmemes/">Dankmemes</a> and <a href="https://www.reddit.com/r/memes/">Memes</a>.
<br>
<br>
<b>Endpoint:</b>
<br>
`https://api.andyproject.de/memes/`
<br><br>
<b>Parameter:</b>
- `?no-gif` → Show only Memes with extensions: jpg, jpeg, png
<br>
<b>Response:</b>
  
```
  {
  "title":"I want to be excused from the dinner table help me\u2026",
  "url":"https:\/\/i.redd.it\/x3aiybfvz7za1.jpg"
  }
``` 
<br>
<b>Example:</b>
  
```
import requests

response = requests.get("https://api.andyproject.de/memes/")
data = response.json()

print("Title:", data["title"])
print("URL:", data["url"])
```
# Drachenlord API
Dieser API-Endpunkt ist für deutsche Entwickler. Dieser Endpunkt gibt zufällige Drachenlord Zitate aus, zusammen mit einer seiner Spitznamen xD.
<br><br>
<b>Endpoint:</b>
  <br>
`https://api.andyproject.de/drache`
<br><br>
<b>Parameters:</b>
<br>
- No parameter 
<br>
<b>Response:</b><br>

```
{
"author":"Kotmidas",
"data":"Also im Prinzip will ich Dich hier jetzt live fragen… ob Du mich heiraten willst."
}
```
<br>
<b>Example:</b><br>
  
```
import requests

response = requests.get("https://api.andyproject.de/drache/")
data = response.json()

print("Author:", data["author"])
print("Data:", data["data"])
```
# Me in real
This API outputs „Me in real“ memes from Reddit.
<br><br>
Endpoint: `https://api.andyproject.de/meirl/`
<br>
Parameters: `None`
<br><br>
<b>Response:</b><br>

```
{
"title":"Meirl",
"url":"https:\/\/i.redd.it\/iz7t3g9lgg0b1.jpg"
}
```
<b>Example:</b><br>

```
import requests

# API-URL
url = "https://api.andyproject.de/meirl/"

# GET-Anfrage an die API senden
response = requests.get(url)

# JSON-Daten aus der Antwort extrahieren
data = response.json()

# Titel und URL aus den JSON-Daten ausgeben
print("Title: " + data["title"])
print("URL: " + data["url"])
```
# Quote API
A collection of German and English quotes. Over 6000 quotes. Free and fast forever.

# Documentation
The API can be reached via `https://api.andyproject.de/quotes/`.<br>
Backup API: `http://data.andyproject.de/quotes/`. <br>
Notice: The Backup API have no SSL certificat also not working vor Images.
<br>This will output random quotes in any language. 
<br>
<br>
<b>German</b>
<br>
To get German quotes the URL `https://api.andyproject.de/quotes/de` can be used.
<br>
<br>
<b>English</b><br>
To get English quotes the URL `https://api.andyproject.de/quotes/de` can be used.
<br>
<br>
<b>Parameters and options</b><br>
- List all authors with `?sortby=authors`
- Search quote by author `?sortby=[name of author]`
- Search quote by ID `?id=[ID]`
- Show all quotes (token required) `?all&token=[token]`
<br>
Note: These parameters and options are only available for the url `/de` and `/en`.<br><br>

<b> Example:</b>
```
import requests

response = requests.get('https://api.andyproject.de/quotes/de/?id=54')

if response.status_code == 200:
    data = response.json()
    print(f'"{data["quote"]}" - {data["author"]}')
else:
    print(f'Error {response.status_code}: {response.text}')
```

# Image API
You can also use ready-made images with German quotes. 
<br>These are also uploaded on instagram at <a href="https://instagram.com/dailywords4u">@dailywords4u</a>.
<br>Pictures with English quotes will follow. 
<br>Please note that the rights and licenses of the images in this API are held by <a href="https://prexels.com">Prexels</a>. So you are obligated to cite Prexels as source.<br><br>
URL: `https://api.andyproject.de/quotes/img/dailywords4u`
<br>
Note: There are no parameters or options for this URL.
<br><br>

<b>Reponse:</b>
``` 
{"bild":
{
"link":"https:\/\/img.andyproject.de\/dailywords4u?link=dailywords4u_581.png",
"date":"2023-05-04 15:19:34",
"size":3598217,
"extension":"png"
}} 
```
# Weather API
This endpoint spits out current weather information. Unlike before, you have to specify headers and not parameters in the URL, as I usually like to do.<br>
Endpoint: `https://api.andyproject.de/v1/weather/`
<br>
Headers: ```headers = {
    "X-CITY": city,
    "X-STATE_CODE": state_code,  
    "X-COUNTRY_CODE": country_code
}```

Response:
```
{
  "coord": {
    "lon": 10.0007,
    "lat": 53.5503
  },
  "weather": [
    {
      "id": 801,
      "main": "Clouds",
      "description": "Ein paar Wolken",
      "icon": "02d"
    }
  ],
  "base": "stations",
  "main": {
    "temp": 15.35,
    "feels_like": 15.19,
    "temp_min": 14.33,
    "temp_max": 17.16,
    "pressure": 1012,
    "humidity": 86
  },
  "visibility": 10000,
  "wind": {
    "speed": 1.54,
    "deg": 230
  },
  "clouds": {
    "all": 20
  },
  "dt": 1688496623,
  "sys": {
    "type": 1,
    "id": 1263,
    "country": "DE",
    "sunrise": 1688439426,
    "sunset": 1688500273
  },
  "timezone": 7200,
  "id": 2911298,
  "name": "Hamburg",
  "cod": 200
}
```

Example in Python:<br>
```
import requests

def get_weather_information(city, state_code, country_code):
    endpoint = "https://api.andyproject.de/v1/weather/"
    headers = {
        "X-CITY": city,
        "X-STATE_CODE": state_code,
        "X-COUNTRY_CODE": country_code
    }
    
    response = requests.get(endpoint, headers=headers)
    data = response.json()
    
    # Koordinaten
    lon = data['coord']['lon']
    lat = data['coord']['lat']
    print(f"Koordinaten: Längengrad {lon}, Breitengrad {lat}")
    
    # Wetterbeschreibung
    weather_description = data['weather'][0]['description']
    print(f"Wetter: {weather_description}")
    
    # Temperatur
    temperature = data['main']['temp']
    print(f"Temperatur: {temperature}°C")
    
    # Luftfeuchtigkeit
    humidity = data['main']['humidity']
    print(f"Luftfeuchtigkeit: {humidity}%")
    
    # Windgeschwindigkeit
    wind_speed = data['wind']['speed']
    print(f"Windgeschwindigkeit: {wind_speed} m/s")
    
    # Wolkenbedeckung
    cloudiness = data['clouds']['all']
    print(f"Wolkenbedeckung: {cloudiness}%")
    
    # Sichtbarkeit
    visibility = data['visibility']
    print(f"Sichtbarkeit: {visibility} m")
    
    # Zeitzone
    timezone = data['timezone']
    print(f"Zeitzone: GMT{timezone / 3600}")
    
    # Stadtname
    city_name = data['name']
    print(f"Stadt: {city_name}")

    #Variable befüllen
    stadt=input("Stadt: ")
    bnd=input("Bundeslandcode: ")
    land=input("Ländercode: ")
    # Beispielaufruf
get_weather_information(stadt, bnd, land)

```

Have fun developing your application. Please note that this API can not be used for commercial purposes, because this API is not vulnerable. It is a hobby project.

