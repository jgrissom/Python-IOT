## Read/Write JSON Data to File

#### Materials
 - Assembled circuit from previous lesson

#### Code
```Python
# json_test.py

import ujson as json

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

def main():
    write_data()
    read_data()

if __name__ == "__main__":
    main()
```

#### Instructions
 - Create the json_test script and save it to the microcontroller
 - Run the json_test script
 - Examine the created file: color.json

