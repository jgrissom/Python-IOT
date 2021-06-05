## Use a Lambda as the Timer Callback

#### Materials
 - Assembled circuit from the Lambda as callback example
 - Yellow led x 1
 - Green led x 1
 - 2.00" x 1 green wire
 - 1.75" x 1 yellow wire
 - 1.25" x 1 green wire
 - 1.25" x 1 yellow wire
 - 330 Ohm resistor x 2

 #### Circuit
[LED Circuit Drawing](lesson02-05.pdf)

#### Code
```
# timer_test.py

from machine import Timer
from GPIO import Led
from time import sleep

red_led = Led(25)
green_led = Led(27)
red_led.on()

# initialize a software timer
timer1 = Timer(-1)
timer2 = Timer(-2)

# inialize the timer to excecute the callback after 1.5 seconds
timer1.init(period=1500, mode=Timer.ONE_SHOT, callback=lambda t : red_led.off())
# inialize the timer to excecute the callback every 200 ms
timer2.init(period=200, mode=Timer.PERIODIC, callback=lambda t : green_led.toggle())

try:
    while True:
        sleep(.01)
except KeyboardInterrupt:
    red_led.off()
    green_led.off()
    timer1.deinit()
    timer2.deinit()
```
#### Instructions
 - Assemble the circuit
 - Modify the timer_test module - add a PERIODIC timer to toggle the green led every 200 ms
