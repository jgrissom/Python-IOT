## Use a Lambda as the Timer Callback

#### Materials
 - Assembled circuit from the ONE_SHOT timer example

#### Code
```Python
# timer_test.py

from machine import Timer
from GPIO import Led

red_led = Led(25)
red_led.on()

# initialize a software timer (-1)
timer = Timer(-1)

# inialize the timer to excecute the callback after 1.5 seconds
timer.init(period=1500, mode=Timer.ONE_SHOT, callback=lambda t : red_led.off())
```
#### Instructions
 - Modify the timer_test module to use a lambda function
