## Momentary Switch

#### Materials
 - Assembled circuit from Blink LED using definite repetition example
 - 2.25" x 1 red wire (from previous)
 - 1.00" x 1 black wire
 - Momentary switch x 1
 - Red button cap x 1

[Circuit Drawing](lesson01-09.pdf)

#### Code
```Python
btn_red = Pin(18, Pin.IN, Pin.PULL_UP)
btn_red.value()
# press button
btn_red.value()
# release button
btn_red.value()
```

#### Instructions
 - Assemble circuit
 - Enter the code using the REPL prompt
