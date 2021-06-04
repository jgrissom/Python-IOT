## MicroPython Script

#### Materials
 - Assembled circuit from MicroPython Functions example
#### Code
```
# led.py

from machine import Pin
from time import sleep

def blink(n):
    l = Pin(25, Pin.OUT)
    counter = 1
    while counter <= n:
        print(counter)
        l.on()
        sleep(.25)
        l.off()
        sleep(.25)
        counter += 1
    print('done')
```

#### Instructions
 - Using Thonny, create a new file
 - Enter the code into the editor
 - Save the file to the MicroController as led.py
 - Using the REPL, import the file
```
import led
```
  - Using the REPL, call the blink function
```
led.blink(3)
```
