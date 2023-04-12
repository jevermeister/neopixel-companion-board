# Neopixel companion board

This is a board to control and power Neopixels (WS2812 and derivatives) using a separate microcontroller.

**Please note that the board doesn't feature any fuses to keep it compact. If for whichever reasons you get a short, bad things may happen!
If in doubt, add a 5A fuse after the microfit connector for additional safety**

To reliably control and power also large strips, the board does a couple of things:

* A 1000uF capacitor for each strip to buffer initial power spikes which may cause the Neopixel controller to brownout due to voltage drops (which would cause the strip to now show anything)
* A 4.7k pulldown resistor for each microcontroller pin to make sure these pins are not floating. While most microcontrollers have integrated pulldowns which could be activated, this won't hurt and ensure a stable communication.
* A level shifter (SN74AHCT125D) as Neopixel expect 5V logic levels while most 32-bit microcontrollers have only 3.3V. Often they also work with 3.3V voltage but not always, that is why we make sure they will with a level shifter. In case you already have 5V logic level - This won't hurt at least and the level shifter is able to deal with it.
* Provide high current connectors. Each strip is connected using Molex Microfit 3.0 connectors which are rated up to 5A. The board itself is connected with screw terminals rated up to 18A.

I already put LCSC/JLCPCB part numbers in the design so you should be able to order these either assembled or know which parts to get.
Please note that I used a TE 796949-2 screw terminal on my PCB which is not available at LCSC so the one I put in there should also fit and work but I didn't test it.

How to wire it:
* Attach microcontroller pins to the JST-XH terminal labeled 1 2 3 4, these correspond to the J1 to J4 molex connectors

Best case those are pins which go straight to the microcontrollers without anything in between. I used PE7 to PE10 located at the EXP1 connector of my BigTreeTech Octopus Pro 1.0
* Attach a 5V power supply (don't try anything higher or the capacitors *will* pop) to the screw terminals, polarity is shown on the board


