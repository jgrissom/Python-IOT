## Connect ESP32 to Wi-Fi

#### Materials
 - Assembled circuit from previous lesson

#### Code
```Python
# wifi.py

def connect(ssid, password):
    import network
    wifi = network.WLAN(network.STA_IF)
    
    if not wifi.isconnected():
        print("Connecting to WiFi network...")
        wifi.active(True)
        wifi.connect(ssid, password)
        while not wifi.isconnected():
            pass
        print("Successfully connected to " + ssid)
    else:
        print("Already connected")
    print('network config:', wifi.ifconfig())
```
#### Instructions
 - Create wifi module, connect() method - using the REPL, type (use guest network if on WCTC campus):
```Python
import wifi
wifi.connect('<ssid>', '<password>')
```
