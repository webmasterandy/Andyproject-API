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
# NFSW API
This API outputs random NFSW content from various Reddit platforms. <br>
<a style=“color:red“>Attention! content. These resources are from Reddit. I, as the operator of the API, assume no liability for illegal content.</a>
<br><br>
<b>Source of API Content</b>
  - `https://www.reddit.com/r/harrypotterporn/`
  - `https://www.reddit.com/r/PadmeNFSW/`
  - `https://www.reddit.com/r/NFSW_Cuties/`
  - `https://www.reddit.com/r/LegalTeens/`
  - `https://www.reddit.com/r/Nudes/`
  - `https://www.reddit.com/r/nsfw/`
<br>
Endpoint: `https://api.andyproject.de/nfsw`
<br><br>
<b>Parameters:</b><br><br>
- `?padme` → NFSW Content of Padme Admidala <br>
- `?nudes` → Nudes <br>
- `?harry-potter` → Diffrent NFSW Content of the Harry Potter World (Mostly Content of Hermione and Ginny) <br>
- `?legal-teens` → Just Nudes, but of Young Girls <br>
- `?nfsw-cuties` → Also some NFSW Content
- `?nfsw2` → NFSW Content
Follow Parameters can be used in combination with the parameters above. To seperate use "&".
- `?no-gif` → Only jpg', 'jpeg', 'png'
- `?only-media` → 'jpg', 'jpeg', 'png', 'gif', 'bmp', 'tiff', 'ico' and 'mp4', 'webm', 'ogg', 'avi', 'mov', 'wmv', 'flv','img','png','jpeg'
<br>
<br>
If you use only „https://api.andyproject.de/nfsw“ you will see nfws content from all categories.
<br>
Please use the API conscientiously. Thanks
<br><br>
<b>Response:</b><br>

```
{
"title":"Can Vader handle all this?",
"url":"https:\/\/i.redd.it\/g93dl3ytxaza1.jpg",
"warning":"Attention! content. These resources are from Reddit. I, as the operator of the API, assume no liability for illegal content."
}
```
<br>
<b>Example:</b><br>

```
import requests

#API-URL
url = "https://api.andyproject.de/nfsw?padme"

#GET-Anfrage an die API senden
response = requests.get(url)

#JSON-Daten aus der Antwort extrahieren
data = response.json()

#Titel, URL des Bildes und Warnung aus den JSON-Daten ausgeben
print("Titel: " + data["title"])
print("URL des Bildes: " + data["url"])
print("Warnung: " + data["warning"])
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
