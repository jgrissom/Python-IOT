## TinyPICODotStar Class - toggle, flicker and blink methods

#### Materials
 - Assembled circuit from previous lesson

#### Code
```Python
# internal.py

...
    def toggle(self, color):
        # if dotstar is already set to color, set dotstar to black
        if self[0][0] == color[0] and self[0][1] == color[1] and self[0][2] == color[2]:
            self[0] = self.BLACK
        else:
            self[0] = color      
    async def async_flicker(self, color, delay):
        self.on(color)
        await asyncio.sleep(delay)
        self.off()
    async def async_blink(self, color, delay, end_count=0):
        count = 0
        while True:
            if end_count > 0:
                count += 1
                if count > end_count:
                    break
            self.on(color)
            await asyncio.sleep(delay)
            self.off()
            await asyncio.sleep(delay)
```
```Python
# dotstar_test.py

import uasyncio as asyncio
from machine import Pin
from internal import TinyPICODotStar

RED = (255, 0, 0, .5)
GREEN = (0, 255, 0, .5)


async def main():
    await asyncio.create_task(dotstar.async_flicker(RED, 1))
    await asyncio.create_task(dotstar.async_blink(GREEN, .2, 5))

if __name__ == "__main__":
    dotstar = TinyPICODotStar()
    dotstar.off()
    # asyncio.run - top level entry point (should only be called once)
    try:
        asyncio.run(main())
    finally:
        dotstar.kill()
```
#### Instructions
 - Modify the internal module
 - Add the toggle, flicker and blink methods
 - Create the dotstar_test script
 - Run the dotstar_test script
