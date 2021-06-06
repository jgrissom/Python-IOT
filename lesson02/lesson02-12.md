## Battery Management

#### Materials
 - Assembled circuit from the Battery voltage & charge status example

#### Code
```
# battery_test.py

import tinypico as TinyPICO
from GPIO import Led
from time import sleep
from machine import Timer

led_green = Led(27)
led_yellow = Led(26)
led_red = Led(25)

def leds_off():
    led_red.off()
    led_yellow.off()
    led_green.off()
def led_on(led, charge_status):
    if charge_status:
        led.blink(200, -1)
    else:
        led.on()

def check_battery_status(t):
    battery_voltage = TinyPICO.get_battery_voltage()
    charge_status = TinyPICO.get_battery_charging()
    
    print("\nBattery Voltage is {}V".format( battery_voltage ) )
    print("Battery Charge State is {}\n".format( charge_status ) )
    
    leds_off()
    if battery_voltage > 3.5:
        led_on(led_green, charge_status)
    elif battery_voltage <= 3.5 and bv > 3.1:
        led_on(led_yellow, charge_status)
    else:
        led_on(led_red, charge_status)

timer = Timer(-10)
timer.init(period=3000, mode=Timer.PERIODIC, callback=check_battery_status)

try:
    while True:
        # do other stuff...
        print('doing other stuff')
        sleep(1)
except KeyboardInterrupt:
    timer.deinit()
    leds_off()
    print('goodbye')
```

#### Instructions
 - Create the battery_test module
 - Import the battery_test module into the main module
