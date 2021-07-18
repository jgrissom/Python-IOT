## Relay Switch

#### Instructions AC Devices
 - Plug relay into wall AC outlet
 - Connect black wire to ESP32 ground
 - Connect red wire to ESP32 5V
 - Connect yellow wire to ESP32 pin 26
 - Plug AC powered device(s) into relay outlet
```Python
from machine import Pin
p26 = Pin(26, Pin.OUT)
p26.on()
p26.off()
```
```Python
from machine import Pin
from time import sleep
p26 = Pin(26, Pin.OUT)
def fun(n):
    while True:
        p26.on()
        sleep(n)
        p26.off()
        sleep(n)
fun(4)
```
 - Press <ctrl> + C to quit having fun

#### Instructions DC Devices
 - Plug relay into wall AC outlet
 - Examine circuit (including 12V rectifier)
 - Connect black wire to ESP32 ground
 - Connect red wire to ESP32 5V
 - Connect yellow wire to ESP32 pin 26
 - Connect multimeter to positive / negative wires from rectifier
```Python
from machine import Pin
p26 = Pin(26, Pin.OUT)
p26.on()
```
 - Examine multimeter (@12.2V)
```Python
p26.off()
```
 - Connect lock to positive / negative wires from rectifier
```Python
from machine import Pin
p26 = Pin(26, Pin.OUT)
p26.on()
```
 - Examine lock
```Python
p26.off()
```