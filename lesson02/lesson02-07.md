## Led Class - blink Method

#### Materials
 - Assembled circuit from the Led flicker example

#### Code
```Python
# GPIO.py

...
    def off(self):
        super().off()
        try:
            self.flicker_timer.deinit()
        except:
            pass
        try:
            self.blink_timer.deinit()
        except:
            pass
    def blink(self, delay, end_count):
        # set end_count = -1 for infinite blink
        self.off()
        self.blink_count = 0
        self.end_count = end_count
        self.blink_timer = Timer(-2)
        # create software timer - runs periodically
        self.blink_timer.init(period=delay, mode=Timer.PERIODIC, callback=self.__toggle_blink)
    def __toggle_blink(self, timer):
        if (self.blink_count < (self.end_count * 2)) or self.end_count == -1:
            self.toggle()
            self.blink_count += 1
        else:
            self.blink_timer.deinit()
```
```Python
# GPIO_test.py

from GPIO import Button, Led
from time import sleep

btn_red = Button(5)
btn_green = Button(22)
led_red = Led(26)
led_green = Led(27)

try:
    while True:
        if btn_red.pressed():
            led_red.flicker(200)
        if btn_green.pressed():
            led_green.blink(500, 5)
        sleep(.01)
except KeyboardInterrupt:
    led_red.off()
    led_green.off()
```
#### Instructions
 - Add the blink and __toggle_blink methods to the Led class
 - Modify Led class off method
 - Modify the GPIO_test module to blink the green led 5 times when the green button is pressed
