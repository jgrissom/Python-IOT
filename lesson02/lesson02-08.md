## TinyPICODotStar Class - turn RGB led on/off

#### Materials
 - Assembled circuit from previous lesson

#### Code
```Python
# internal.py

import tinypico as TinyPICO
from micropython_dotstar import DotStar
from machine import Pin, SoftSPI

class TinyPICODotStar(DotStar):
    def __init__(self):
        # Configure SPI for controlling the DotStar
        # Internally we are using software SPI for this as the pins being used are not hardware SPI pins
        spi = SoftSPI(sck=Pin( TinyPICO.DOTSTAR_CLK ), mosi=Pin( TinyPICO.DOTSTAR_DATA ), miso=Pin( TinyPICO.SPI_MISO) )
        # dotstar = DotStar(spi, 1, brightness = 0.5 ) # Just one DotStar, half brightness
        super().__init__(spi, 1, brightness = .5)
        TinyPICO.set_dotstar_power(True)
        self.BLACK = (0,0,0)
    def on(self, color):
        self[0] = color
    def off(self):
        self[0] = self.BLACK
    def kill(self):
        self.off()
        TinyPICO.set_dotstar_power(False)
```
#### Instructions
 - Create the internal module
 - Using the REPL, type the following commands:
```Python
from internal import TinyPICODotStar
dotstar = TinyPICODotStar()
dotstar.on((255,0,0))
dotstar.off()
YELLOW = (255,255,0)
dotstar.on(YELLOW)
dotstar.kill()
```
