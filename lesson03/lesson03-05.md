## MicroPython urequests

#### Materials
 - Assembled circuit from Install MicroPython urequests example

#### Instructions
 - Create a get request - using the REPL, type:
```Python
import urequests as requests
base_url = 'https://nugatory.azurewebsites.net'
r = requests.get(base_url + '/api/word')
r.status_code
r.text
```
 - Create a post request - using the REPL, type:
```Python
import ujson as json
payload = { 'word': 'jeff', 'color': 'green' }
hdr = { 'Content-Type': 'application/json' }
r = requests.post(base_url + '/api/word', headers = hdr, data = json.dumps(payload))
r.status_code
r.text
```
 - Recreate the get request from the previous step
 - Create a get request to return a single object - using the REPL, type:
```Python
r = requests.get(base_url + '/api/word/2')
r.status_code
r.text
```
