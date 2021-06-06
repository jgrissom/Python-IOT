## Momentary Switch

#### Materials
 - Assembled circuit from Blink LED using definite repetition example
 - 2.5" x 1 red wire (from previous)
 - 1.00" x 1 black wire
 - Momentary switch x 1
 - Red button cap x 1

#### Circuit
[Circuit Drawing](lesson01-09.pdf)

#### Code
```Python
btn = Pin(5, Pin.IN, Pin.PULL_UP)
btn.value()
# press button
btn.value()
# release button
btn.value()
```

#### Instructions
 - Assemble circuit
 - Enter the code using the REPL prompt
