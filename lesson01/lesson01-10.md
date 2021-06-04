## Momentary Switch Driven LED

#### Materials
 - Assembled circuit from Momentary switch example

#### Code
```
while True:
    led.value(btn.value())
    sleep(.01)
```

#### Instructions
 - Enter the code using the REPL prompt
 - PRACTICE: Alter the code so the LED lights up when the button is pressed and turns off when the button is released
