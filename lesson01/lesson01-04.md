## Blink LED Using Indefinite Repetition

#### Materials
 - Assembled circuit from MicroPython driven LED Example

#### Code
```
from machine import Pin
from time import sleep
led = Pin(25, Pin.OUT)
while True:
    led.on()
    sleep(.5)
    led.off()
    sleep(.5)
```

#### Instructions
 - Enter the code using the REPL prompt
 - Press Enter twice to run
 - Press Ctrl + C to quit
 - If needed turn the LED off
 ```
led.off()
 ```
