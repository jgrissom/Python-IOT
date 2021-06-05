## TinyPICODotStar Class - toggle, flicker and blink methods

#### Materials
 - Assembled circuit from the RGB Led on/off example

#### Code
```
# GPIO.py

...
    def toggle(self, color):
        if self[0] == self.BLACK:
            self[0] = color
        else:
            self[0] = self.BLACK
    def flicker(self, color, delay):
        self.on(color)
        # create software timer - runs once
        self.flicker_timer = Timer(-1)
        self.flicker_timer.init(period=delay, mode=Timer.ONE_SHOT, callback=lambda t : self.off())
    def blink(self, color, delay, end_count):
        self.blink_count = 0
        self.end_count = end_count
        self.blink_timer = Timer(-2)
        # create software timer - runs periodically
        self.blink_timer.init(period=delay, mode=Timer.PERIODIC, callback=lambda t : self.__toggle_blink(color))
    def __toggle_blink(self, color):
        if self.blink_count < (self.end_count * 2):
            self.toggle(color)
            self.blink_count = self.blink_count + 1
        else:
            self.blink_timer.deinit()
```
#### Instructions
 - Add the toggle, flicker and blink methods
 - Reboot the microcontroller
 - Using the REPL, type the following commands:
```
dotstar = TinyPICODotStar()
RED = (255,0,0)
dotstar.toggle(RED)
dotstar.toggle(RED)
dotstar.flicker(RED, 200)
dotstar.blink(RED, 200, 5)
dotstar.off()
dotstar.kill()
```
