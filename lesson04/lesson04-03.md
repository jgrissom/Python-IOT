## PWM - Buzzer Keyboard

#### Materials
 - Assembled circuit from PWM Buzzer example

#### Code
```Python
# keyboard.py

from GPIO import Button
from time import sleep
from machine import Pin, PWM

btn_red = Button(18)
btn_green = Button(5)
btn_blue = Button(22)

buzzer = PWM(Pin(33, Pin.OUT), duty=0)

def buzz(duty, freq, duration):
    buzzer.duty(duty)
    buzzer.freq(freq)
    sleep(duration)
    buzzer.duty(0)
    
try:
    while True:
        if (btn_red.pressed()):
            # C (octave 4)
            buzz(10, 262, .2)
        elif (btn_green.pressed()):
            # D (octave 4)
            buzz(10, 294, .2)
        elif (btn_blue.pressed()):
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
 
