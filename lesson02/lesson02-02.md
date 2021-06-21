## LED Class - Toggle Method

#### Materials
 - Assembled circuit from Button class example

#### Code
```Python
# GPIO.py
...
class Led(Pin):
    def __init__(self, pin):
        super().__init__(pin, Pin.OUT)
    def toggle(self):
        self.value(not self.value())
```
```Python
# GPIO_test.py

from GPIO import Button, Led
from time import sleep

btn_red = Button(18)
led_red = Led(25)

while True:
    if btn_red.pressed():
        led_red.toggle()
    sleep(.01)
```
#### Instructions
 - Add the LED class to the GPIO.py module
 - Modify the GPIO_test.py module to toggle the red led when the button is pressed
