## MicroPython Driven LED Circuit

#### Materials
 - Assembled circuit from MCU 3.3V Pin Driven LED Example
 - 1.25" x 1 red wire
 - 1.00" x 1 black wire
 - Micro-USB to USB-A wire

#### Circuit
[Circuit Drawing](lesson01-03.pdf)

#### Code
```Python
from machine import Pin
led = Pin(25, Pin.OUT)
led.on()
led.off()
```

#### Instructions
 - Assemble circuit
 - Connect MCU to computer using Micro-USB wire
 - Launch Thonny
 - Connect to MCU - Run - Select Interpreter ...
 - Show the MicroPython REPL (Read Evaluate Print Loop) prompt - View - Focus Shell
 - Enter the code using the REPL prompt
