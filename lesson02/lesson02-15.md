## Deep Sleep
This example was adapted from [https://RandomNerdTutorials.com](https://RandomNerdTutorials.com)

#### Materials
 - Assembled circuit from the Garbage Collection example

#### Code
```Python
# deep_sleep_test.py

import machine
import esp32
from machine import Pin
from time import sleep

wake1 = Pin(32, Pin.IN, Pin.PULL_UP)

#level parameter can be: esp32.WAKEUP_ANY_HIGH or esp32.WAKEUP_ALL_LOW
esp32.wake_on_ext0(pin = wake1, level = esp32.WAKEUP_ALL_LOW)

#your main code goes here to perform a task

print('Im awake. Going to sleep in 10 seconds')
sleep(10)
print('Going to sleep now')
machine.deepsleep()
```

#### Instructions
 - Create the deep_sleep_test module
 - Using the REPL, import the deep_sleep_test module
 - When the microcontroller goes to deep sleep, you can wake it by pressing the yellow button
