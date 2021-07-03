## Deep Sleep
This example was adapted from [https://RandomNerdTutorials.com](https://RandomNerdTutorials.com)

#### Materials
 - Assembled circuit from Lesson 02-14
 - 3.50" x 1 black wire
 - 2.00" x 1 black wire
 - Small momemtary switch x 1
 - White, black or gray button cap x 1

[Circuit Drawing](lesson02-15.pdf)

#### Code
```Python
# deep_sleep_test.py

import machine
import esp32
from machine import Pin
from time import sleep

wake1 = Pin(33, Pin.IN, Pin.PULL_UP)

#level parameter can be: esp32.WAKEUP_ANY_HIGH or esp32.WAKEUP_ALL_LOW
esp32.wake_on_ext0(pin = wake1, level = esp32.WAKEUP_ALL_LOW)

#your main code goes here to perform a task

print('Im awake. Going to sleep in 10 seconds')
sleep(10)
print('Going to sleep now')
machine.deepsleep()
```

#### Instructions
 - Assemble the circuit
 - Create the deep_sleep_test script
 - Run the deep_sleep_test script
 - When the microcontroller goes to deep sleep, you can wake it by pressing the button attached to pin 33
