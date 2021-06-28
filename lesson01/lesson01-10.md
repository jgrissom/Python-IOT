## Momentary Switch Driven LED

#### Materials
 - Assembled circuit from Momentary switch example

#### Code
```Python
from machine import Pin
from time import sleep
btn_red = Pin(18, Pin.IN, Pin.PULL_UP)
led_red = Pin(26, Pin.OUT)
while True:
    led_red.value(btn_red.value())
    sleep(.01)
```

#### Instructions
 - Enter the code using the REPL prompt
 - PRACTICE: Alter the code so the LED lights up when the button is pressed and turns off when the button is released
