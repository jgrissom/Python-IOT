## Create a ONE_SHOT Timer

#### Materials
 - Assembled circuit from LED class - toggle method example

#### Code
```Python
# timer_test.py

from machine import Timer
from GPIO import Led

led_red = Led(25)
led_red.on()

# initialize a software timer (-1)
timer = Timer(-1)
# define a function to be called as the timer callback
def turn_off_led(timer):
    led_red.off()
# inialize the timer to excecute the callback after 1.5 seconds
timer.init(period=1500, mode=Timer.ONE_SHOT, callback=turn_off_led)
```
```Python
# main.py

import timer_test
```
#### Instructions
 - Create the timer_test module and save it to the microcontroller
 - Modify the main module to import the timer_test module
