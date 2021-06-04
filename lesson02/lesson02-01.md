## Detecting a Button Press

#### Materials
 - Assembled circuit from Lesson 1

#### Code
```
# GPIO.py

from machine import Pin

# Button class is derived from the Pin class
class Button(Pin):
    def __init__(self, pin):
        # call super class constructor
        super().__init__(pin, Pin.IN, Pin.PULL_UP)
        # save initial state of Button
        self.state = self.value()
    def pressed(self):
        # switch 0 and 1 to implement released/pressed
        # or if pin is PULLED_DOWN
        if self.state == 0 and self.value() == 1:
            self.state = self.value()
            return True
        self.state = self.value()
        return False
```
```
# GPIO_test.py

from GPIO import Button
from time import sleep

btn_red = Button(5)

while True:
    if btn_red.pressed():
        print('red pressed')
    sleep(.01)
```
```
# main.py

import GPIO_test
```
#### Instructions
 - Create python script GPIO.py and save to the microcontroller
 - Create python script GPIO_test.py and save to the microcontroller
 - Modify main.py - import GPIO_test
