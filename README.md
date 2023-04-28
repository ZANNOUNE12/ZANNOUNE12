import requests

CHUNK_SIZE = 1024
url = "https://api.elevenlabs.io/v1/text-to-speech/<p2x8792QjwEYLAziNVNp>"

headers = {
  "Accept": "audio/mpeg",
  "Content-Type": "application/json",
  "xi-api-key": "<b6e99437497b342238657ae485b49551>"
}

data = {
  "text": "Some very long text to be read by the voice",
  "voice_settings": {
    "stability": 0,
    "similarity_boost": 0
  }
}

response = requests.post(url, json=data, headers=headers)
with open('output.mp3', 'wb') as f:
    for chunk in response.iter_content(chunk_size=CHUNK_SIZE):
        if chunk:
            f.write(chunk)
