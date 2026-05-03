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
