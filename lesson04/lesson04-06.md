## PWMBuzzer - GPIO

#### Materials
 - Assembled circuit from PWM Buzzer example

#### Code
```Python
# GPIO.py

from machine import PWM
...
class PWMBuzzer(PWM):
    def __init__(self, p):
        super().__init__(Pin(p, Pin.OUT), 550, 0)
    def flicker(self, duty, freq, delay):
        self.duty(duty)
        self.freq(freq)
        self.flicker_timer = Timer(-6)
        self.flicker_timer.init(period=delay, mode=Timer.ONE_SHOT, callback=lambda t : self.duty(0))
```
```Python
# main.py

import pymon
```
```Python
# pymon.py

from GPIO import Button, Led, TinyPICODotStar, PWMBuzzer
from time import sleep
import machine

COLOR_RED = (255, 0, 0, .5)
COLOR_GREEN = (0, 255, 0, .5)
COLOR_BLUE = (0, 0, 255, .5)
COLOR_YELLOW = (255, 255, 0, .5)
colors = [ COLOR_RED, COLOR_GREEN, COLOR_BLUE, COLOR_YELLOW ]

NOTE_RED = 440     # a  (4th octave)
NOTE_GREEN = 165   # e  (3rd octave)
NOTE_BLUE = 330    # e  (4th octave)
NOTE_YELLOW = 277  # c# (4th octave)
notes = [ NOTE_RED, NOTE_GREEN, NOTE_BLUE, NOTE_YELLOW ]

BTN_RED_PIN = 18
BTN_GREEN_PIN = 5
BTN_BLUE_PIN = 22
BTN_YELLOW_PIN = 21
btns = [ Button(BTN_RED_PIN), Button(BTN_GREEN_PIN), Button(BTN_BLUE_PIN), Button(BTN_YELLOW_PIN) ]

LED_RED_PIN = 25
LED_GREEN_PIN = 26
LED_BLUE_PIN = 27
LED_YELLOW_PIN = 15
leds = [ Led(LED_RED_PIN), Led(LED_GREEN_PIN), Led(LED_BLUE_PIN), Led(LED_YELLOW_PIN) ]
# turn off all leds by default
for i in range(len(leds)):
    leds[i].off()

dotstar = TinyPICODotStar()
dotstar.off()
buzzer = PWMBuzzer(33)
buzzer_duty = 50
restart_button = Button(32)

try:
    while True:
        for i in range(len(btns)):
            if btns[i].pressed():
                dotstar.flicker(colors[i], 200)
                leds[i].flicker(200);
                buzzer.flicker(buzzer_duty, notes[i], 200)
            elif restart_button.pressed():
                print('restart game')
            
        sleep(.01)
except KeyboardInterrupt:
    print('goodbye')
    buzzer.deinit()
```
#### Instructions
 - Modify thge GPIO module - add the PWMBuzzer class
 - Modify the main module - import the pymon module
 - Create the pymon module

