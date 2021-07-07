## Asyncio - cancel tasks

#### Materials
 - Assembled circuit from previous lesson

#### Code
```Python
# dotstar_blink_test.py

import uasyncio as asyncio
from machine import Pin
from internal import TinyPICODotStar
from async_switch import Switch

RED = (255, 0, 0, .5)
GREEN = (0, 255, 0, .5)

def button_press(btn, color):
    dotstar_tasks.append(asyncio.create_task(dotstar.async_blink(color, .2)))

async def main():
    btn_red.close_func(button_press, (btn_red, RED))
    btn_green.close_func(button_press, (btn_green, GREEN))

    # main program loop
    while True:
        await asyncio.sleep(.01)

if __name__ == "__main__":
    btn_red = Switch( Pin(18, Pin.IN, Pin.PULL_UP) )
    btn_green = Switch( Pin(5, Pin.IN, Pin.PULL_UP) )
    dotstar = TinyPICODotStar()
    dotstar.off()
    dotstar_tasks = []
    # asyncio.run - top level entry point (should only be called once)
    try:
        asyncio.run(main())
    finally:
        dotstar.kill()
```
#### Instructions
 - Create the dotstar_blink_test script
 - Run the dotstar_blink_test script
 - Press the red button, then press the green button
 - What if we ant to stop the red blink before we start the green blink?
 - Modify the dotstar_blink_test script:  - **comments are placed above the 3 changes**
```Python
# dotstar_blink_test.py

import uasyncio as asyncio
from machine import Pin
from internal import TinyPICODotStar
from async_switch import Switch

RED = (255, 0, 0, .5)
GREEN = (0, 255, 0, .5)

def button_press(btn, color):
    # 2. Cancel running tasks before creating new tasks
    cancel_tasks()
    dotstar_tasks.append(asyncio.create_task(dotstar.async_blink(color, .2)))

# 1. Add the cancel_tasks method
def cancel_tasks():
    print('cancel ' + str(len(dotstar_tasks)) + ' task(s)')
    for task in dotstar_tasks:
        task.cancel()
    dotstar_tasks.clear()

async def main():
    btn_red.close_func(button_press, (btn_red, RED))
    btn_green.close_func(button_press, (btn_green, GREEN))

    # main program loop
    while True:
        await asyncio.sleep(.01)

if __name__ == "__main__":
    btn_red = Switch( Pin(18, Pin.IN, Pin.PULL_UP) )
    btn_green = Switch( Pin(5, Pin.IN, Pin.PULL_UP) )
    dotstar = TinyPICODotStar()
    dotstar.off()
    dotstar_tasks = []
    # asyncio.run - top level entry point (should only be called once)
    try:
        asyncio.run(main())
    finally:
        # 3. Cancel any running tasks
        cancel_tasks()
        dotstar.kill()
```
 - Run the dotstar_blink_test script
 - Press the red button, then press the green button

