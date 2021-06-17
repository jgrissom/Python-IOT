## PWM - Led

#### Materials
 - Assembled circuit from Lesson 3

#### Instructions
 - Using the REPL, type the following commands:
```Python
from machine import Pin, PWM
p = Pin(27, Pin.OUT)
led = PWM(p)

# set PWM frequency 500Hz
led.freq(500)

# set duty cycle to all on
led.duty(1023)
# set duty cycle to 50%
led.duty(512)
# set duty cycle to 25%
led.duty(256)
# set duty cycle to 12.5%
led.duty(128)
# set duty cycle to 6.25%
led.duty(56)
# set duty cycle to 3.125%
led.duty(28)
# set duty cycle to 1.5625%
led.duty(14)
# set duty cycle to all off
led.duty(0)
```
