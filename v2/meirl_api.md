# Me in real API
Endpoint: https://api.andyproject.de/v2/meirl

# How to use
The API is in json format. In this example I will use Python as an example.<br>
The API also works with any other programming language. 

<b>Response:</b>
`{"title":"Meirl","url":"https:\/\/i.redd.it\/j2u32qwokcub1.jpg"}` <br>
<br>

Example in pyhton: <br>
```
import requests

def get_meirl_data():
    url = "https://api.andyproject.de/v2/meirl"
    response = requests.get(url)
    data = response.json()
    return data

def main():
    meirl_data = get_meirl_data()
    title = meirl_data["title"]
    url = meirl_data["url"]
    
    print(f"Titel: {title}")
    print(f"URL: {url}")

if __name__ == "__main__":
    main()
```

# Params
?top → Popular memes <br>
?hot → currently hyped memes <br>
?new → new memes (mostly 5 - 60 min old)<br>
?rising → Images are displayed in ascending order<br>
<br>
<b>Info:</b> please append the parameters to the endpoint URL.<br> 
For example `https://api.andyproject.de/beta/meirl/?new`
