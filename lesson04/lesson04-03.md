## PWM - Buzzer GPIO

#### Materials
 - Assembled circuit from PWM Buzzer example

#### Code
```Python
# GPIO.py

...
from machine import PWM
...
class Buzzer(PWM):
    def __init__(self, pin):
        super().__init__(Pin(pin, Pin.OUT))
        self.duty(0)
    def flicker(self, duty, freq, delay):
        self.freq(freq)
        self.duty(duty)
        self.flicker_timer = Timer(-5)
        self.flicker_timer.init(period=delay, mode=Timer.ONE_SHOT, callback=lambda t : self.duty(0))
```

#### Instructions
 - Modify the GPIO module - add the Buzzer class and flicker method
 - Using the keyboard module created in the PWM Buzzer example as your guide, play D (octave 4) when the green button is pressed and play E (octave 4) when the blue button is pressed
 - [Note Frequency Chart](NoteFrequencyChart.pdf)
 - When you are finished, you can play **Mary Had A Little Lamb**:
 
##### blue, green, red, green, blue, blue, blue

##### green, green, green

##### blue, blue, blue
##### blue, green, red, green, blue, blue, blue, red, green, green, blue, green, red
 
