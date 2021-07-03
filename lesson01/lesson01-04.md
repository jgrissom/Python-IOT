## Blink LED Using Indefinite Repetition

#### Materials
 - Assembled circuit from previous lesson

#### Code
```Python
from machine import Pin
from time import sleep
led_red = Pin(26, Pin.OUT)
while True:
    led_red.on()
    sleep(.5)
    led_red.off()
    sleep(.5)
```

#### Instructions
 - Enter the code using the REPL prompt
 - Press Enter twice to run
 - Press Ctrl + C to quit
 - If needed turn the LED off
 ```Python
led.off()
 ```
