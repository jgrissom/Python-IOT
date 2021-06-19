## PWM - Buzzer GPIO

#### Materials
 - Assembled circuit from PWM Buzzer example

#### Code
```Python
# keyboard.py

from GPIO import Button
from time import sleep
from machine import Pin, PWM

red_btn = Button(5)
green_btn = Button(22)
blue_btn = Button(21)
yellow_btn = Button(32)

buzzer = PWM(Pin(4, Pin.OUT), duty=0)

def buzz(duty, freq, duration):
    buzzer.duty(duty)
    buzzer.freq(freq)
    sleep(duration)
    buzzer.duty(0)
    
try:
    while True:
        if (red_btn.pressed()):
            # C (octave 4)
            buzz(10, 262, .2)
        elif (green_btn.pressed()):
            # D (octave 4)
            buzz(10, 294, .2)
        elif (blue_btn.pressed()):
            # E (octave 4)
            buzz(10, 330, .2)
        sleep(.01)
            
except KeyboardInterrupt:
    print('goodbye')
    buzzer.deinit()
except:
    print("error")
    buzzer.deinit()
```

#### Instructions
 - Create the keyboard module
 - Using the REPL, type the following commands
```Python
import keyboard
```
**Mary Had a Little Lamb**:
 
*blue, green, red, green, blue, blue, blue*

*green, green, green*

*blue, blue, blue*

*blue, green, red, green, blue, blue, blue, red, green, green, blue, green, red*
 
