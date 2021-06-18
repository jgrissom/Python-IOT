## PWM - Buzzer GPIO

#### Materials
 - Assembled circuit from PWM Buzzer example

#### Code
```Python
# GPIO.py

...
from machine import PWM
...
class PWMBuzzer(PWM):
    def __init__(self, pin):
        super().__init__(Pin(pin, Pin.OUT))
        self.duty(0)
    def flicker(self, duty, freq, delay):
        self.freq(freq)
        self.duty(duty)
        self.flicker_timer = Timer(-5)
        self.flicker_timer.init(period=delay, mode=Timer.ONE_SHOT, callback=lambda t : self.duty(0))
```

```Python
# keyboard.py

from GPIO import Button, PWMBuzzer
from time import sleep

red_btn = Button(5)
green_btn = Button(22)
blue_btn = Button(21)
yellow_btn = Button(32)

buzzer = PWMBuzzer(4)
    
try:
    while True:
        if (red_btn.pressed()):
            # C (octave 4)
            buzzer.flicker(10, 262, 200)
        elif (green_btn.pressed()):
            # D (octave 4)
            buzzer.flicker(10, 294, 200)
        elif (blue_btn.pressed()):
            # E (octave 4)
            buzzer.flicker(10, 330, 200)
        sleep(.01)
            
except KeyboardInterrupt:
    print('goodbye')
    buzzer.duty(0)
except:
    print("error")
    buzzer.duty(0)
```

#### Instructions
 - Modify the GPIO module - add the PWMBuzzer class and flicker method
 - Create the keyboard module
 - Using the REPL, type the following commands
```Python
import keyboard
```
**Mary Had A Little Lamb**:
 
##### blue, green, red, green, blue, blue, blue

##### green, green, green

##### blue, blue, blue
##### blue, green, red, green, blue, blue, blue, red, green, green, blue, green, red
 
