# RP2040-CE-based-tool-assisted-input.  WIP
Simple tool assited way to input to most physicial game consoles.

This project was first disscused with my brother when he got "tomodachi life living the dream" when he got to the custom food creataion, he said he wanted a way to get pictures of real stuff into the game.
From my limited knowlage the most common way was to "emulate the game" and draw it using a program. But on offical hardware it would be close to impossibale.

I've decided to use the RP2040-CE firmware as the switch/controller input. The firmware is optimized for fightboxes that require low latancy. Fitting with the need for low latancy inputs for tool assited inputs.
Added LEDs and bypass switches for Debugging if needed. The LED brightness can be controlled with the poteniometer. 
The RP2040 connecting to the pc needs a dedicated software to read images and input it to the pc.  *thinking of adding support for reading pre made tool assisted files for easier exicution without pc.

I hope that this simple project would be helpful to al who wish to push the limits of the switch on offical hardware. With no modification.
In theory you can plug this adapter to any switch and run it. And send input from the PC thus adding support for unsupported hardware to work on the switch.



Many thanks to the RP2040-CE community for developping the wonderful firmware that would be needed for this project. 
And to my brother who wrote the software for this device.

Shout out to the GIMX community for giving me inspiration for the way this device works.
Although the GIMX project has quite down, their passions passes though.

How to build

Get the required parts first.

26　3mm 2.2vLED (Any color would do)

26　1/6 100KΩ resistor

54　1/6 1KΩ resistor

26  2N7000 TO92 N transistor

1　  3386P-1-103 1KΩ potentiometer (can be a smaller value)

1　  PCB Switch

26　 6x6mm 4pin tactical swtich

2　  RP2040 pico (Type C variant would be best)

1   Custom PCB (You could build this by hand on a universal PCB but it's going to take forever.)

Check the release tab for the PCB files

<img width="1742" height="665" alt="Screenshot_20260509_174313" src="https://github.com/user-attachments/assets/10292ef1-3559-4d4d-87fb-5e0ea38b9d66" />

<img width="3508" height="2480" alt="Controller adapter tool assistaed board_annotated" src="https://github.com/user-attachments/assets/2d39d9b7-5b11-498d-928a-a5f3ff6e4d4d" />

After solding all the parts, flash the Right side pico with the RP2040-CE firmware. 

https://gp2040-ce.info/

Do a check on all the GPIO pins to make sure it's working

After building the device, Press S2 while plugging in the USB to load to the web config tool.

S2 is third right from the most buttom left button.

You'll need to diable all the addons to be able to use all the pins.

There's a quiurk, on GP0 GP1.  You need to enter the "Peripheral Mapping" tab and enable I2C0, make sure both SDA and SCL is set to "Unset"
Enter RGB LED Config and set the "Data GPIO PIN" to -1
And enter the Add-Ons config tab and disable all. (Depends on your use case)
Next Go to add-on trubo config. Turn on and set LED off or -1.

After saving and rebooting, you can configure the GPIO Pin Mapping to your liking.
The PCB is wired as GP0-GP0.  GP1-GP1 etc....  

Remember. You need to set the GPIO to any input or else the LED debug will be on. Even after setting the GPIO to any input and the LED is on. Double check your soldering and wiring quality.

(For testing the left side pico)

Now flash the left side pico with Micropython. https://micropython.org/download/RPI_PICO/

After flashing it, write this code in.
(Used AI for the simple testing only)

「
from machine import Pin
from time import sleep_ms, ticks_ms

# GPIO list
pins = [
    0, 1, 2, 3, 4, 5, 6, 7,
    8, 9, 10, 11, 12, 13, 14, 15,
    16, 17, 18, 19, 20, 21,
    22, 26, 27, 28
]

gpio = []

# Setup all GPIO as outputs LOW initially
for p in pins:
    pin = Pin(p, Pin.OUT)
    pin.value(0)
    gpio.append(pin)

pin_count = len(gpio)

# Total cycle time = 1000 ms
# Each pin ON time:
step_time = int(1000 / pin_count)

while True:

    cycle_start = ticks_ms()

    for pin in gpio:

        # MOSFET ON
        pin.value(1)

        sleep_ms(step_time)

        # MOSFET OFF
        pin.value(0)

    # Optional timing correction
    elapsed = ticks_ms() - cycle_start

    if elapsed < 1000:
        sleep_ms(1000 - elapsed)
  *」

Plug both Pico into the pc and run the code.
Open a Controller tester of your choice
The Debugging LEDS should be flashing very fast, and the controller testing should be going crazy.

We have fnished building the GP2040-CE base tool.

You can config the GP2040-CE side pico to your liking. And download any software that you need to use for your required purpose.

