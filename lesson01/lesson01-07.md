## MicroPython Script

#### Materials
 - Assembled circuit from previous lesson
#### Code
```Python
# led.py

from machine import Pin
from time import sleep

def blink(n):
    led_red = Pin(26, Pin.OUT)
    counter = 1
    while counter <= n:
        print(counter)
        led_red.on()
        sleep(.25)
        led_red.off()
        sleep(.25)
        counter += 1
    print('done')
```

#### Instructions
 - Using Thonny, create a new file
 - Enter the code into the editor
 - Save the file to the MicroController as led.py
 - Using the REPL, import the file
```Python
import led
```
  - Using the REPL, call the blink function
```Python
led.blink(3)
```
