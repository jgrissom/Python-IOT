## PWM - Buzzer

#### Materials
 - Assembled circuit from PWM Led example

#### Instructions
 - Using the REPL, type the following commands - if needed, type buzzer.deinit()
```Python
from machine import Pin, PWM
p = Pin(4, Pin.OUT)
pwm = PWM(p, duty=0)
pwm.freq(262) # C (octave 4)
pwm.duty(10)
pwm.duty(0)
pwm.duty(20)
pwm.duty(0)
pwm.freq(523) # C (octave 5)
pwm.duty(10)
pwm.duty(0)
pwm.deinit()
```
