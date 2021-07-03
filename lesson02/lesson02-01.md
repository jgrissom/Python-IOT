## Led Class

#### Materials
 - Assembled circuit from Lesson 1
 - Green led x 1
 - 2.00" x 1 green wire
 - 1.00" x 1 green wire
 - 330 Ohm resistor x 1

[Circuit Drawing](lesson02-01.pdf)

#### Code
```Python
# output.py

class Output():
    def __init__(self, pin):
        self.pin = pin
    def on(self):
        self.pin.on()
    def off(self):
        self.pin.off()
    def toggle(self):
        self.pin.value(not self.pin.value())
```

#### Instructions
 - Assemble the circuit
 - Create python module output and save to the microcontroller
 - Using the REPL, type the following commands:
```Python
from machine import Pin
from output import Output as Led
led_red = Led(Pin(26, Pin.OUT))
led_green = Led(Pin(27, Pin.OUT))
led_red.on()
led_green.toggle()
led_green.toggle()
led_red.off()
```