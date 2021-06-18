## Led Class - flicker Method

#### Materials
 - Assembled circuit from the PERIODIC timer example

#### Code
```Python
# GPIO.py

...
from machine import Timer
...
    def flicker(self, delay):
        self.on()
        # create software timer - runs once
        self.flicker_timer = Timer(-1)
        self.flicker_timer.init(period=delay, mode=Timer.ONE_SHOT, callback=lambda t : self.off())
    def off(self):
        super().off()
        try:
            self.flicker_timer.deinit()
        except:
            pass
```
```Python
# GPIO_test.py

from GPIO import Button, Led
from time import sleep

btn_red = Button(5)
led_red = Led(25)

try:
    while True:
        if btn_red.pressed():
            led_red.flicker(200)
        sleep(.01)
except KeyboardInterrupt:
    led_red.off()
```
#### Instructions
 - Add the flicker method to the Led class
 - Override the super class's off method to ensure that the timer is deinitialized
 - Modify the GPIO_test module to flicker the red led when the red button is pressed
