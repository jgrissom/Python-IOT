## MicroPython Functions

#### Materials
 - Assembled circuit from previous lesson
#### Code
```Python
from machine import Pin
from time import sleep
led_red = Pin(26, Pin.OUT)
def blink(n):
    counter = 1
    while counter <= n:
        print(counter)
        led_red.on()
        sleep(.5)
        led_red.off()
        sleep(.5)
        counter += 1
    print('done')
blink(5)
```

#### Instructions
 - Enter the code using the REPL prompt
