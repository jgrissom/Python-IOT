## Practice: Connect ESP32 to WiFi

#### Materials
 - Assembled circuit from Connect ESP32 to WiFi example

#### Instructions
 - Add the Buzzer class to the GPIO module (**Hint** it will be similar to the Led class)
   - Add the constructor
   - Add the flicker method (timer id -5)
   - Add the off() method (make sure to deinit the flicker timer)
 - While Wi-Fi is connecting, blink the dotstar red (255, 0, 0, .5) continuosly
 - Once Wi-Fi is connected, flicker the buzzer for 100 ms and blink the dotstar green (0, 255, 0, .5) 3 times
