## PWM - Buzzer Play Songs

#### Materials
 - Assembled circuit from previous lesson

[Note Frequency Chart](NoteFrequencyChart.pdf)
#### Code
```Python
# simple_songs.py

from machine import Pin, PWM
from time import sleep

buzzer = PWM(Pin(25, Pin.OUT), duty=0)

# use lists to store note frequencies for octaves 0-8
c = [ 16, 33, 65, 131, 262, 523, 1047, 2093, 4186 ] 
d = [ 18, 37, 73, 147, 294, 587, 1175, 2349, 4699 ]
e = [ 21, 41, 82, 165, 330, 659, 1319, 2637, 5274 ]
f = [ 22, 44, 87, 175, 349, 698, 1397, 2794, 5588 ]
g = [ 25, 49, 98, 196, 392, 784, 1568, 3136, 6272 ]
a = [ 28, 55, 110, 220, 440, 880, 1760, 3520, 7040 ]
b = [ 31, 62, 123, 247, 494, 988, 1976, 3951, 7902 ]

# use dictionary to store songs
playlist = {
    "little_lamb": [ e[5], d[5], c[5], d[5], e[5], e[5], e[5], 0, d[5], d[5], d[5], 0, e[5], e[5], e[5], 0, e[5], d[5], c[5], d[5], e[5], e[5], e[5], c[5], d[5], d[5], e[5], d[5], c[5] ],
    "twinkle_twinkle": [ g[5], g[5], d[6], d[6], e[6], e[6], d[6], 0, c[6], c[6], b[5], b[5], a[5], a[5], g[5], 0, d[6], d[6], c[6], c[6], b[5], b[5], a[5], 0, d[6], d[6], c[6], c[6], b[5], b[5], a[5], 0, g[5], g[5], d[6], d[6], e[6], e[6], d[6], 0, c[6], c[6], b[5], b[5], a[5], a[5], g[5] ],
    # TODO: DO-RE-MI-FA-SO-LA-TI-DO
}

def buzz(duty, freq, duration):
    buzzer.duty(duty)
    buzzer.freq(freq)
    sleep(duration)
    buzzer.duty(0)

def play(track):
    try:
        for note in playlist[track]:
            if note != 0:
                buzz(10, note, .3)
            else:
                sleep(.3)
            buzzer.duty(0)
    except KeyboardInterrupt:
        buzzer.freq(0)
        buzzer.duty(0)
```
#### Instructions
 - Create the songs module
 - NOTE: this code is NOT asynchronous
 - From the REPL, type the following commands:
```Python
import simple_songs
simple_songs.play("little_lamb")
simple_songs.play("twinkle_twinkle")
```
- On your own, add DO-RE-MI-FA-SO-LA-TI-DO to the playlist and test it using the REPL
