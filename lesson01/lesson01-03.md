## MicroPython Driven LED Circuit

#### Materials
 - Assembled circuit from previous lessone
 - 1.50" x 1 red wire
 - 1.00" x 1 black wire
 - Micro-USB to USB-A wire

[Circuit Drawing](lesson01-03.pdf)

#### Code
```Python
from machine import Pin
led_red = Pin(26, Pin.OUT)
led_red.on()
led_red.off()
```

#### Instructions
 - Assemble circuit
 - Connect MCU to computer using Micro-USB wire
 - Launch Thonny
 - Update to Micropython 1.15 ([micropython.org](https://micropython.org/))
 - Connect to MCU - Run - Select Interpreter ...
 - Show the MicroPython REPL (Read Evaluate Print Loop) prompt - View - Focus Shell
 - Enter the code using the REPL prompt
