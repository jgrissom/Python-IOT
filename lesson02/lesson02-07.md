## Advanced Asynchronous Push Button

#### Materials
 - Assembled circuit from previous lesson
 - 2.50" x 1 yellow wires
 - 2.25" x 2 blue wires
 - 1.00" x 2 black wires
 - Momentary switch x 1
 - Blue button cap x 1

[Circuit Drawing](lesson02-07.pdf)

#### Instructions
 - Assemble the circuit
 - Copy the code from github - https://github.com/tve/mpy-lib/blob/master/button/abutton.py
 - Paste the code into the async_button module
```Python
# async_switch.py

# TODO: paste code from github here and save as async_button.py
```
 - Create the advanced_asyc_button_test script
```Python
# advanced_asyc_button_test.py

import uasyncio as asyncio
from async_button import Pushbutton
from machine import Pin

def handle_event(msg):
    print(msg)

async def main():   
    btn_red.press_func(handle_event, ('red-press',))
    btn_red.release_func(handle_event, ('red-release',))
    btn_green.long_func(handle_event, ('green-long',))
    btn_blue.double_func(handle_event, ('blue-double',))

    # main program loop
    while True:
        await asyncio.sleep(.01)

if __name__ == '__main__':
    try:
        btn_red = Pushbutton( Pin(18, Pin.IN, Pin.PULL_UP) )
        btn_green = Pushbutton( Pin(5, Pin.IN, Pin.PULL_UP) )
        btn_blue = Pushbutton( Pin(22, Pin.IN, Pin.PULL_UP) )
        asyncio.run(main())
    finally:
        print("goodbye")
```
- Run the advanced_asyc_button_test script (Ctrl + c to quit)
