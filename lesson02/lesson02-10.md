## TinyPICODotStar Practice

#### Materials
 - Assembled circuit from the DotStar toggle, flicker and blink methods example
 - 2.75" x 1 yellow wire
 - 2.50" x 1 blue wire
 - 1.25" x 2 black wires
 - Momentary switch x 2
 - Blue button cap x 1
 - Yellow button cap x 1

#### Circuit
[Circuit Drawing](lesson02-10.pdf)

#### Instructions
 - Assemble the circuit
 - Modify the GPIO_test module as follows
   * When the blue button is pressed, flicker the dotstar blue - use (255, 0, 0, .5)
   * When the yellow button is pressed, blink the dotstar yellow infinitely - use (255, 255, 0, .5)
   * Don't forget to kill the dotstar when the program ends
