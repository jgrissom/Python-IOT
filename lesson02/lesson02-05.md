## Asynchronous Blink method

#### Materials
 - Assembled circuit from previous lesson

#### Instructions
 - Modify the output module - create the "blink" method
```Python
# output.py

...
    async def async_blink(self, delay, end_count=0):
        # end_count determines the umber of iterations
        # default value of 0 will blink forever
        count = 0
        while True:
            if end_count > 0:
                count += 1
                if count > end_count:
                    break
            self.pin.on()
            await asyncio.sleep(delay)
            self.pin.off()
            await asyncio.sleep(delay)
```
 - Modify the output_test script
```Python
# output_test.py

import uasyncio as asyncio
from machine import Pin
from output import Output

async def main():
    task1 = asyncio.create_task(led_red.async_blink(.4, 3))
    task2 = asyncio.create_task(led_green.async_blink(.2))
    await task1
    await task2

if __name__ == "__main__":
    # asyncio.run - top level entry point (should only be called once)
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
