## Asynchronous Push Button

#### Materials
 - Assembled circuit from previous lesson

#### Instructions
 - Copy the code from github - https://github.com/tve/mpy-lib/blob/master/button/aswitch.py
 - Paste the code into the async_switch module
```Python
# async_switch.py

# TODO: paste code from github here and save as async_switch.py
```
 - Create the simple_async_button_test script
```Python
# simple_async_button_test.py

import uasyncio as asyncio
from async_switch import Switch
from machine import Pin

btn_red = Switch( Pin(18, Pin.IN, Pin.PULL_UP) )

def press():
    print('pressed')

async def main():   
    btn_red.close_func(press)

    # main program loop
    while True:
        await asyncio.sleep(.01)

if __name__ == '__main__':
    try:
        asyncio.run(main())
    finally:
        print("goodbye")
```
- Run the simple_async_button_test script (Ctrl + c to quit)
- Modify the simple_async_button_test script
```Python
# simple_async_button_test.py

import uasyncio as asyncio
from async_switch import Switch
from machine import Pin

btn_red = Switch( Pin(18, Pin.IN, Pin.PULL_UP) )

def press():
    print('pressed')
def release():
    print('released')

async def main():   
    btn_red.close_func(press)
    btn_red.open_func(release)

    # main program loop
    while True:
        await asyncio.sleep(.01)

if __name__ == '__main__':
    try:
        asyncio.run(main())
    finally:
        print("goodbye")
```
- Run the simple_async_button_test script (Ctrl + c to quit)