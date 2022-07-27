## PWM - RTTTL Async

#### Materials
 - Assembled circuit from previous lesson

```Python
# async_rtttl_player.py

import uasyncio as asyncio

async def play_tone_async(freq, msec, pwm, duty):
    print('freq = {:6.1f} msec = {:6.1f}'.format(freq, msec))
    if freq > 0:
        pwm.freq(int(freq))         # Set frequency
        pwm.duty(duty)              # Set duty
    await asyncio.sleep(msec*0.001) # Play for a number of msec    
    pwm.duty(0)                     # Stop playing
    await asyncio.sleep_ms(50)      # Delay 50 ms between notes


async def play(song, pwm, duty):
    try:
        for freq, msec in song.notes():
            await play_tone_async(freq, msec, pwm, duty)
    finally:
        pwm.duty(0)
```
```Python
# async_rtttl_player_test.py

import uasyncio as asyncio
from async_switch import Switch
from output import Output as Led
from machine import Pin, PWM
from internal import TinyPICODotStar
import async_rtttl_player
import songs
from rtttl import RTTTL

RED = (255, 0, 0, .5)
GREEN = (0, 255, 0, .5)

def cancel_tasks(tasks):
    print('cancel ' + str(len(tasks)) + ' task(s)')
    for task in tasks:
        task.cancel()
    tasks.clear()
def play_song(song):
    led_red.off()
    led_green.on()
    dotstar.on(GREEN)
    cancel_tasks(dotstar_tasks)
    tune = RTTTL(songs.find(song))
    dotstar_tasks.append(asyncio.create_task(async_rtttl_player.play(tune, pwm, 5)))
def stop_song():
    led_red.on()
    led_green.off()
    dotstar.on(RED)
    cancel_tasks(dotstar_tasks)

async def main():
    led_red.on()
    dotstar.on(RED)
    btn_red.close_func(play_song, ('StarWars',))
    btn_green.close_func(play_song, ('Imperial', ))
    btn_blue.close_func(stop_song)
    
    while True:
        await asyncio.sleep(.01)

if __name__ == '__main__':
    led_red = Led( Pin(26, Pin.OUT) )
    led_green = Led( Pin(27, Pin.OUT) )

    btn_red = Switch( Pin(18, Pin.IN, Pin.PULL_UP) )
    btn_green = Switch( Pin(5, Pin.IN, Pin.PULL_UP) )
    btn_blue = Switch( Pin(22, Pin.IN, Pin.PULL_UP) )

    dotstar = TinyPICODotStar()
    pwm = PWM(Pin(25, Pin.OUT), 10, 0)

    dotstar_tasks = []
    try:
        # asyncio.run - top level entry point (should only be called once)
        asyncio.run(main())
    finally:
        print("goodbye")
        led_green.off()
        led_red.off()
        cancel_tasks(dotstar_tasks)
        dotstar.kill()
        pwm.duty(0)
        pwm.deinit()
```
#### Instructions
 - Create the async_rtttl_player module
 - Create the async_rtttl_player_test script
 - Run the async_rtttl_player_test script
