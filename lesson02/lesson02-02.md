## Buzzer

#### Materials
 - Assembled circuit from previous lesson

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

if __name__ == '__main__':
    try:
        buzzer = Buzzer(Pin(25, Pin.OUT))
        main()
    finally:
        print('goodbye')
        buzzer.off()
```
#### Instructions
 - Create the output_test script
 - Run the output_test script
