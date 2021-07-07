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

def press():
    print('pressed')

async def main():   
    btn_red.close_func(press)

    # main program loop
    while True:
        await asyncio.sleep(.01)

if __name__ == "__main__":
    # asyncio.run - top level entry point (should only be called once)
    try:
        btn_red = Switch( Pin(18, Pin.IN, Pin.PULL_UP) )
        asyncio.run(main())
    finally:
        print('goodbye')
```
- Run the simple_async_button_test script (Ctrl + c to quit)
- Modify the simple_async_button_test script - **comments are placed above the 2 changes**
```Python
# simple_async_button_test.py

import uasyncio as asyncio
from async_switch import Switch
from machine import Pin

def press():
    print('pressed')
# 1. Add release method
def release():
    print('released')

async def main():   
    btn_red.close_func(press)
    # 2. Attach event listener to switch open_func
    btn_red.open_func(release)

    # main program loop
    while True:
        await asyncio.sleep(.01)

if __name__ == "__main__":
    # asyncio.run - top level entry point (should only be called once)
    try:
        btn_red = Switch( Pin(18, Pin.IN, Pin.PULL_UP) )
        asyncio.run(main())
    finally:
        print('goodbye')
```
- Run the simple_async_button_test script (Ctrl + c to quit)