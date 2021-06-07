## Connect ESP32 to WiFi

#### Materials
 - Assembled circuit from Lesson 2

#### Code
```Python
# wifi.py

def connect():
    import network
    sta_if = network.WLAN(network.STA_IF)
    if not sta_if.isconnected():
        print('connecting to network...')
        sta_if.active(True)
        sta_if.connect('<essid>', '<password>')
        while not sta_if.isconnected():
            pass
    print('network config:', sta_if.ifconfig())
```
```Python
# main.py

import wifi
wifi.connect()
```
#### Instructions
 - Create wifi module, connect() method
 - import wifi module into main module - call connect() method
