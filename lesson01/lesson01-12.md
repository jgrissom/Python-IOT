## Momentary Switch Debouncing

#### Materials
 - Assembled circuit from previous lesson

#### Code
```Python
# button.py

from machine import Pin
from time import sleep

def main():
    while True:
        first = btn_green.value()
        sleep(0.01)
        second = btn_green.value()
        if first and not second:
            print('Button pressed!')
        elif not first and second:
            print('Button released!')

if __name__ == '__main__':
    try:
        btn_green = Pin(5, Pin.IN, Pin.PULL_UP)
        main()
    finally:
        print('goodbye')
```

#### Instructions
 - Create python script button.py and save to the Microcontroller
 - Test the script button.py
