## MicroPython Functions

#### Materials
 - Assembled circuit from Blink LED using definite repetition example
#### Code
```
from machine import Pin
from time import sleep
led = Pin(25, Pin.OUT)
def blink(n):
    counter = 1
    while counter <= n:
        print(counter)
        led.on()
        sleep(.5)
        led.off()
        sleep(.5)
        counter += 1
    print('done')
blink(5)
```

#### Instructions
 - Enter the code using the REPL prompt
