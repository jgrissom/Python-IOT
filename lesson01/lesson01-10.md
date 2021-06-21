## Momentary Switch Driven LED

#### Materials
 - Assembled circuit from Momentary switch example

#### Code
```Python
while True:
    led_red.value(btn_red.value())
    sleep(.01)
```

#### Instructions
 - Enter the code using the REPL prompt
 - PRACTICE: Alter the code so the LED lights up when the button is pressed and turns off when the button is released
