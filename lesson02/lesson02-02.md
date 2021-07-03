## Buzzer Class

#### Materials
 - Assembled circuit from Lesson 02-01

#### Code
```Python
# output_test.py

from time import sleep
from machine import Pin
from output import Output as Buzzer

def main():
    buzzer.on()
    sleep(.2)
    buzzer.off()

buzzer = Buzzer(Pin(25, Pin.OUT))

if __name__ == "__main__":
    main()
```
#### Instructions
 - Create the output_test script
 - Run the output_test script
