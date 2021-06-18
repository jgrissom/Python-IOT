## Practice: MicroPython urequests

#### Materials
 - Assembled circuit from Install MicroPython urequests example
 - 3.00" x 1 white wire
 - 1.25" x 1 black wire
 - Small momemtary switch x 1
 - White, black or gray button cap x 1

[Circuit Drawing](lesson03-06.pdf)

#### Instructions
 - Assemble the circuit
 - Create a new python module requests_test
 - When the red, green, blue, or yellow buttons are pressed, this module will post to the api { 'word': 'your_name', 'color': 'color_of_button_pressed' }
 - When the small button is pressed, use a get request to retrieve all words and save them to a file ('words.json') on your microcontroller
