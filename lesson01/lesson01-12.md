## Momentary Switch Debouncing

#### Materials
 - Assembled circuit from Momentary switch driven buzzer example

#### Code
```
# button.py

from machine import Pin
from time import sleep

btn = Pin(22, Pin.IN, Pin.PULL_UP)

try:
    while True:
        first = btn.value()
        sleep(0.01)
        second = btn.value()
        if first and not second:
            print('Button pressed!')
        elif not first and second:
            print('Button released!')
except KeyboardInterrupt:
    print('goodbye')
```

#### Instructions
 - Create python script button.py and save to the Microcontroller
 - Import the module into main.py and test
