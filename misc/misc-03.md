## Neopixels

#### Materials 
 - Neopixel strip

#### Code
```Python
# async_neopixel.py

import neopixel
from machine import Pin

class NP():
    def __init__(self, p, n):
        self.np = neopixel.NeoPixel(p, n)
        self.n = n
    def clear(self):
        for i in range(self.n):
            self.np[i] = (0, 0, 0)
        self.np.write()
    def on(self, color):
        for i in range(self.n):
            self.np[i] = color
        self.np.write()
```

### Instructions
 - Create the async_neopixel module
 - Enter the following code using the REPL prompt
 
#### Code
```Python
from async_neopixel import NP
from machine import Pin
# replace n with correct pin
# replace z with number of neopixels
np = NP(Pin(n), z)
np.on((255,0,0))
np.clear()
```

### Instructions
 - Modify the async_neopixel module
 - Import the uasyncio module
 - Add the async_flicker method to the NP class
 - Add the main method to test the module
 - Run the code

#### Code
```Python
import uasyncio as asyncio
...
    async def async_flicker(self, color, delay):
        self.on(color)
        await asyncio.sleep(delay)
        self.clear()

async def main():
    # replace n with correct pin
    # replace z with number of neopixels
    np = NP(Pin(n), z)

    await np.async_flicker((0,0,255), .5)

if __name__ == '__main__':
    try:
        asyncio.run(main())
    finally:
        print("goodbye")
```

### Instructions
 - Modify the async_neopixel module
 - Add the async_cycle method to the NP class
 - Mopdule the main method to test the new method
 - Run the code

#### Code
```Python
...
    async def async_cycle(self, color, num=4):
        for i in range(num * self.n):
            for j in range(self.n):
                self.np[j] = (0,0,0)
            self.np[i % self.n] = color
            self.np.write()
            await asyncio.sleep(.02)
        self.clear()
...
async def main():
    ...
    await asyncio.sleep(.2)
    await np.async_cycle((0, 255, 0), 3)
```
