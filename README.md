# RP2040-CE-based-tool-assisted-input.  WIP
Simple tool assited way to input to most physicial game consoles.

This project was first disscused with my brother when he got "tomodachi life living the dream" when he got to the custom food creataion, he said he wanted a way to get pictures of real stuff into the game.
From my limited knowlage the most common way was to "emulate the game" and draw it using a program. But on offical hardware it would be close to impossibale.

I've decided to use the RP2040-CE firmware as the switch/controller input. The firmware is optimized for fightboxes that require low latancy. Fitting with the need for low latancy inputs for tool assited inputs.
Added LEDs and bypass switches for Debugging if needed. The LED brightness can be controlled with the poteniometer. 
The RP2040 connecting to the pc needs a dedicated software to read images and input it to the pc.  *thinking of adding support for reading pre made tool assisted files for easier exicution without pc.

I hope that this simple project would be helpful to al who wish to push the limits of the switch on offical hardware. With no modification.
In theory you can plug this adapter to any switch and run it.


Many thanks to the RP2040-CE community for developping the wonderful firmware that would be needed for this project. 
And to my brother who wrote the software for this device.

How to build

Get the required parts first.
26　3mm 2.2vLED (Any color would do)

26　1/6 100KΩ resistor

54　1/6 1KΩ resistor

1　  3386P-1-103 1KΩ potentiometer

1　  Switch

26　 6x6mm 4pin tactical swtich

2　  RP2040 pico (Type C variant would be best)

1   Custom PCB (You could build this by hand on a universal PCB but it's going to take forever.)

Check the release tab for the PCB files

<img width="1742" height="665" alt="Screenshot_20260509_174313" src="https://github.com/user-attachments/assets/10292ef1-3559-4d4d-87fb-5e0ea38b9d66" />

<img width="3508" height="2480" alt="Controller adapter tool assistaed board_annotated" src="https://github.com/user-attachments/assets/2d39d9b7-5b11-498d-928a-a5f3ff6e4d4d" />

After solding all the parts, flash the Right side pico with the RP2040-CE firmware. 

Do a check on all the GPIO pins to make sure it's working

Flash **

WIP
