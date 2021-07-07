## Battery Management

#### Materials
 - Assembled circuit from previous lesson

#### Code
```Python
# battery_test.py

import tinypico as TinyPICO
from output import Output
import uasyncio as asyncio
from machine import Pin

def leds_off():
    led_red.off()
    led_yellow.off()
    led_green.off()
def led_on(led, charge_status):
    cancel_tasks(led_tasks)
    leds_off()
    if charge_status:
        led_tasks.append(asyncio.create_task(led.async_blink(.2)))
    else:
        led.on()
def cancel_tasks(tasks):
    print('cancel ' + str(len(tasks)) + ' task(s)')
    for task in tasks:
        task.cancel()
    tasks.clear()
    
async def check_battery_status():
    while True:
        battery_voltage = TinyPICO.get_battery_voltage()
        charge_status = TinyPICO.get_battery_charging()
        
        print("\nBattery Voltage is {}V".format( battery_voltage ) )
        print("Battery Charge State is {}\n".format( charge_status ) )
        
        if battery_voltage > 3.5:
            led_on(led_green, charge_status)
        elif battery_voltage <= 3.5 and bv > 3.1:
            led_on(led_yellow, charge_status)
        else:
            led_on(led_red, charge_status)
        await asyncio.sleep(3)

async def main():
    system_tasks.append(asyncio.create_task(check_battery_status()))
    
    while True:
        print('doing other stuff')
        await asyncio.sleep(.5)
    

if __name__ == '__main__':
    try:
        led_green = Output(Pin(27, Pin.OUT))
        led_yellow = Output(Pin(14, Pin.OUT))
        led_red = Output(Pin(26, Pin.OUT))
        led_tasks = []
        system_tasks = []
        asyncio.run(main())
    finally:
        cancel_tasks(system_tasks)
        cancel_tasks(led_tasks)
        leds_off()
        print('goodbye')
```
#### Instructions
 - Create the battery_test script
 - Run the battery_test script
