## Flicker method

#### Materials
 - Assembled circuit from previous lesson

#### Instructions
 - Modify the output module - add the flicker method
```Python
# output.py

...
    def flicker(self, delay):
        from time import sleep
        self.pin.on()
        sleep(delay)
        self.pin.off()
```
 - Modify the output_test script
```Python
# output_test.py

from time import sleep
from machine import Pin
from output import Output

def main():
    led_red.flicker(2)

led_red = Output(Pin(26, Pin.OUT))

if __name__ == "__main__":
    main()
```
 - Run the output_test script
 - This works perfectly fine for 1 led/buzzer
 - What if we want to flicker 2 leds/buzzers at the same time?
 - Modify the output_test script
```Python
# output_test.py

from time import sleep
from machine import Pin
from output import Output

def main():
    led_red.flicker(2)
    led_green.flicker(1.5)
    

led_red = Output(Pin(26, Pin.OUT))
led_green = Output(Pin(27, Pin.OUT))

if __name__ == "__main__":
    main()
```
- Run the output_test script
