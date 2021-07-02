## MicroPython Boot Scripts

#### Materials
 - Assembled circuit from MicroPython Scripts example

#### Instructions
 - Using Thonny, create a new file
 - Enter the code into the editor:
```Python
# main.py

import led
led.blink(7)
```
 - Save the file to the MicroController as main.py
 - Press Ctrl + D (to soft reboot the MicroController)
 - Modify the main.py:
```Python
# main.py

import led

if __name__ == '__main__':
    try:
        led.blink(7)
    finally:
        print('goodbye')
```
