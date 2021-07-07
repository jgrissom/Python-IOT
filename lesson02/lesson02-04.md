## Asynchronous Flicker method

#### Materials
 - Assembled circuit from previous lesson

#### Instructions
 - Modify the output module
   - Import asyncio module
   - Create the asynchronous flicker method
```Python
# output.py

...
import uasyncio as asyncio
...
    async def async_flicker(self, delay):
        self.pin.on()
        await asyncio.sleep(delay)
        self.pin.off()
```
 - Modify the output_test script
```Python
# output_test.py

import uasyncio as asyncio
from machine import Pin
from output import Output

async def main():
    task1 = asyncio.create_task(led_red.async_flicker(2))
    task2 = asyncio.create_task(led_green.async_flicker(1))
    await task1
    await task2

if __name__ == '__main__':
    try:
        led_red = Output(Pin(26, Pin.OUT))
        led_green = Output(Pin(27, Pin.OUT))
        asyncio.run(main())
    finally:
        print('goodbye')
        led_red.off()
        led_green.off()
```
- Run the output_test script
