## LEDs & Proper Resistance

#### Instructions
 - Connect mulitmeter common (COM) port to ESP32 ground
 - Connect multimeter volt/omega (VΩ) port to ESP32 pin 26
 - Place multimeter in the 200V range, observe the voltage (3.2V)
```Python
from machine import Pin
p26 = Pin(26, Pin.OUT)
p26.on()
```
 - LED Voltage limits (refer to LED mfg documentation)
   - White, Green, Blue 2.8 - 3.2V
   - Yellow, Red 1.8 - 2.2V
 - No resistance needed for White, Green or Blue LEDs with the ESP32
 - Test with White, Green or Blue LED and no resistor (@2.9V) - WHY?
 - Use a resistance calculator (https://www.petervis.com/electronics/led/led-resistor-calculator.html) to determine the amount of resistance needed for Yellow & Red LEDs
  - Vs = 3.2V
  - Vf = 2.2V
  - Rs = 50 Ohms
  - Test with Red or Yellow LED and 50 Ohm resistor (@1.9V)
```Python
p26.off()
```
