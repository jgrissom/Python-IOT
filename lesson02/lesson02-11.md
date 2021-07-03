## TinyPICODotStar Practice

#### Materials
 - Assembled circuit from previous lesson
 - 2.50" x 2 yellow wires
 - 2.25" x 1 blue wires
 - 1.00" x 1 black wires
 - 1.00" x 1 yellow wire
 - 1.00" x 1 blue wire
 - Blue led x 1
 - Yellow led x 1
 - 330 Ohm resistor x 2
 - Momentary switch x 1
 - Yellow button cap x 1

[Circuit Drawing](lesson02-11.pdf)

#### Instructions
 - Assemble the circuit
 - Modify the dotstar_test script as follows
   * When the red button is pressed, flicker the red led & the dotstar red - use (255, 0, 0, .5)
   * When the green button is pressed, flicker the green led & the dotstar green - use (0, 255, 0, .5)
   * When the blue button is pressed, flicker the blue led & the dotstar blue - use (0, 0, 255, .5)
   * When the yellow button is pressed, blink the yellow led & the dotstar yellow infinitely - use (255, 255, 0, .5)
   * Don't forget to kill the dotstar & turn off all leds when the program ends
