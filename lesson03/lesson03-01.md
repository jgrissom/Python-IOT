## Connect ESP32 to Wi-Fi

#### Materials
 - Assembled circuit from Lesson 2

#### Code
```Python
# wifi.py

def connect(ssid, password):
    import network
    sta_if = network.WLAN(network.STA_IF)
    if not sta_if.isconnected():
        print('connecting to network...')
        sta_if.active(True)
        sta_if.connect(ssid, password)
        while not sta_if.isconnected():
            pass
    print('network config:', sta_if.ifconfig())
```
#### Instructions
 - Create wifi module, connect() method - using the REPL, type:
```Python
import wifi
wifi.connect('<ssid>', '<password>')
```
