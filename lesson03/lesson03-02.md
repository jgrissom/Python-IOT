## Wi-Fi Timeout

#### Materials
 - Assembled circuit from Connect ESP32 to Wi-Fi example

#### Code
```Python
# wifi.py

def connect(ssid, password, timeout):
    import network, time
    wifi = network.WLAN(network.STA_IF)
    
    if not wifi.isconnected():
        print("Connecting to WiFi network...")
        wifi.active(True)
        wifi.connect(ssid, password)
        # Wait until connected
        t = time.ticks_ms()
        while not wifi.isconnected():
            if time.ticks_diff(time.ticks_ms(), t) > timeout:
                wifi.disconnect()
                print("Timeout. Could not connect.")
                return False
        print("Successfully connected to " + ssid)
        return True
    else:
        print("Already connected")
        return True
```
#### Instructions
 - Modify wifi module
 - Reboot ESP32 <ctrl + d>
 - Using the REPL, type:
```Python
import wifi
wifi.connect('<ssid>', '<password>')
```
