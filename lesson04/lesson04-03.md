## PWM - Buzzer Keyboard

#### Materials
 - Assembled circuit from previous lesson

#### Code
```Python
# keyboard.py

import uasyncio as asyncio
from async_switch import Switch
from machine import Pin, PWM

async def buzz(duty, freq, duration):
    print(freq)
    buzzer.duty(duty)
    buzzer.freq(freq)
    await asyncio.sleep(duration)
    buzzer.duty(0)

def press(freq):
    cancel_tasks()
    tasks.append(asyncio.create_task(buzz(10, freq, .2)))
    
def cancel_tasks():
    print('cancel ' + str(len(tasks)) + ' task(s)')
    for task in tasks:
        task.cancel()
    tasks.clear()

async def main():
    # C (octave 4)
    btn_red.close_func(press, (262,))
    # D (octave 4)
    btn_green.close_func(press, (294,))
    # E (octave 4)
    btn_blue.close_func(press, (330,))
    # main program loop
    while True:
        await asyncio.sleep(.01)

if __name__ == "__main__":
    try:
        btn_red = Switch( Pin(18, Pin.IN, Pin.PULL_UP) )
        btn_green = Switch( Pin(5, Pin.IN, Pin.PULL_UP) )
        btn_blue = Switch( Pin(22, Pin.IN, Pin.PULL_UP) )

        buzzer = PWM(Pin(25, Pin.OUT), duty=0)
        tasks = []
        asyncio.run(main())
    finally:
        print("goodbye")
        cancel_tasks()
        buzzer.deinit()
```

#### Instructions
 - Create the keyboard script
 - Run the keyboard script
 
**Mary Had a Little Lamb**:
 
*blue, green, red, green, blue, blue, blue*

*green, green, green*

*blue, blue, blue*

*blue, green, red, green, blue, blue, blue, red, green, green, blue, green, red*
 
