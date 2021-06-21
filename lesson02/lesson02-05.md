## Create a PERIODIC timer

#### Materials
 - Assembled circuit from the Lambda as callback example
 - Green led x 1
 - 2.00" x 1 green wire
 - 1.00" x 1 green wire
 - 330 Ohm resistor x 1

[Circuit Drawing](lesson02-05.pdf)

#### Code
```Python
# timer_test.py

from machine import Timer
from GPIO import Led
from time import sleep

led_red = Led(25)
led_green = Led(26)
led_red.on()

# initialize a software timer
timer1 = Timer(-1)
# initialize a software timer
timer2 = Timer(-2)

# inialize the timer to execute the callback after 1.5 seconds
timer1.init(period=1500, mode=Timer.ONE_SHOT, callback=lambda t : led_red.off())
# inialize the timer to excecute the callback every 200 ms
timer2.init(period=200, mode=Timer.PERIODIC, callback=lambda t : led_green.toggle())

try:
    while True:
        sleep(.01)
except KeyboardInterrupt:
    led_red.off()
    led_green.off()
    # deinitialize the ONE_SHOT timer
    timer1.deinit()
    # deinitialize the ONE_SHOT timer
    timer2.deinit()
```
#### Instructions
 - Assemble the circuit
 - Modify the timer_test module - add a PERIODIC timer to toggle the green led every 200 ms
