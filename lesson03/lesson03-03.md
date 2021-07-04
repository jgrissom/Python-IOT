## Async Wi-Fi

#### Materials
 - Assembled circuit from previous lesson

#### Code
```Python
# async_wifi.py

import uasyncio as asyncio
# default value for wifi timeout = 5000
async def connect(ssid, password, timeout=5000):
    import network, time
    wifi = network.WLAN(network.STA_IF)
    
    if not wifi.isconnected():
        print("Connecting to WiFi network...")
        wifi.active(True)
        wifi.connect(ssid, password)
        t = time.ticks_ms()
        while not wifi.isconnected():
            if time.ticks_diff(time.ticks_ms(), t) > timeout:
                wifi.disconnect()
                print("Timeout. Could not connect.")
                return False
            # async wait allows other tasks to run
            await asyncio.sleep(.05)
        print("Successfully connected to " + ssid)
        return True
    else:
        print("Already connected")
        return True
```
```Python
# async_wifi_test.py

import uasyncio as asyncio
import async_wifi
from async_output import Led
from machine import Pin

async def main():
    tasks.append(asyncio.create_task(led.blink(200)))
    print(await async_wifi.connect('ssid', 'password', 5000))
    while True:
        await asyncio.sleep(.01)

led = Led(Pin(26, Pin.OUT))
tasks = []

if __name__ == '__main__':
    try:
        asyncio.run(main())
    finally:
        print("goodbye")
```
#### Instructions
 - Modify wifi module
 - Create async_wifi_test script
 - Reboot ESP32 <ctrl + d>
 - Run async_wifi_test script - test with bad / good credentials
```
