## PWM - Buzzer

#### Materials
 - Assembled circuit from PWM Led example

#### Code
```Python
# keyboard.py

from machine import Pin, PWM
from time import sleep

red = Pin(5, Pin.IN, Pin.PULL_UP)

p = Pin(15, Pin.OUT)
buzzer = PWM(p)
buzzer.duty(0)
    
try:
    while True:
        r1 = red.value()
        
        sleep(0.01)
        
        r2 = red.value()
        
        if r1 and not r2:
            buzzer.freq(262)
            buzzer.duty(10)
        elif not r1 and r2:
            buzzer.duty(0)
except KeyboardInterrupt:
    print('goodbye')
    buzzer.deinit()
```
#### Instructions
 - Create the keyboard module
 - Using the REPL, imoport the module and test the red button - the buzzer should play C (octave 4)
