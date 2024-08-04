# API-Dokumentation

## Endpoint: `https://api.andyproject.de/ping/`

Dieser Endpoint führt eine Ping-Anfrage, CPU-, RAM- und Netzwerk-Auslastungsmessungen durch und gibt die Ergebnisse in JSON-Format zurück.

### HTTP Methode

`GET`

### Antwort

Die Antwort ist ein JSON-Objekt mit den folgenden Feldern:

- `ping`: Die durchschnittliche Round-Trip-Zeit (RTT) des Ping in Millisekunden.
- `cpu_usage`: Die CPU-Auslastung.
- `ram_usage`: Die RAM-Auslastung in Prozent.
- `download_usage`: Der Netzwerk-Download-Verbrauch in Kilobyte pro Sekunde.
- `upload_usage`: Der Netzwerk-Upload-Verbrauch in Kilobyte pro Sekunde.

### Beispiel

#### Anfrage

```http
GET /ping/ HTTP/1.1
Host: api.andyproject.de
```

#### Antwort

```json
{
    "ping": 12.345,
    "cpu_usage": 0.25,
    "ram_usage": 45,
    "download_usage": 1024.5,
    "upload_usage": 512.3
}
```

### Beispiel-Python-Skript zur Verwendung des Endpoints

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
    print("Fehler bei der Anfrage:", response.status_code)
```

Dieses Skript sendet eine GET-Anfrage an den Endpoint und gibt die Ergebnisse in der Konsole aus.
