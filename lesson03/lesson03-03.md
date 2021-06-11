## Read/Write JSON Data to File

#### Materials
 - Assembled circuit from Connect ESP32 to Wi-Fi example

#### Code
```Python
# json_test.py

import json

def write_data():
    out_data = {"word": "jeff", "color": "green"}
    out_file = open("color.json", "w")
    json.dump(out_data, out_file)
    out_file.close()

def read_data():
    in_file = open("color.json")
    in_data = json.load(in_file)
    print(in_data["word"])
    print(in_data["color"])
```
```Python
# main.py

import json_test
json_test.write_data()
json_test.read_data()
```

#### Instructions
 - Create the json_test module and save it to the microcontroller
 - Import the json_test module into the main module and call the write_data() & read_data() methods
 - Examine the created file: color.json

