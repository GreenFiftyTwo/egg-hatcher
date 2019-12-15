## Egg Hatcher

Automatically hatch eggs in Pokemon Sword and Shield by emulating a controller on a Teensy++ v2.0

#### How to use

Prerequisites:
1) Full pokemon party
2) Lead pokemon isn't holding an item
3) Pokemon with Flame Body ability is in party, but not in lead spot (not required if egg species has less than 20 egg cycles)
4) Oval charm is recommended
5) Route 5 Nursery Lady has an egg ready

Exit the Nursery on Route 5 and plug in the controller. It will automatically sync with the console, walk up to the Nursery Lady, take the egg and put it at the top of the party, and walk around inside the nursery to hatch it. It will start over and do this in a loop.

Note that due to eggs having a random chance of being generated there will always be a possible, yet slim chance that an egg is not ready when you go to get a new one.  Currently this breaks the loop, however I hope to fix this in a future release.  This is part of the reason that the character walks 20 egg cycles regardles of what species you are hatching.  After 20 egg cycles the chance of an egg not being ready is very slim, especially with the oval charm.

In case you see issues with controller conflicts while in docked mode, try using a USB-C to USB-A adapter in handheld mode. In dock mode, changes in the HDMI connection will briefly make the Switch not respond to incoming USB commands, skipping parts of the sequence. These changes may include turning off the TV, or switching the HDMI input. (Switching to the internal tuner will be OK, if this doesn't trigger a change in the HDMI input.)

This repository has been tested using a Teensy 2.0++.

#### Compiling and Flashing onto the Teensy 2.0++
Go to the Teensy website and download/install the [Teensy Loader application](https://www.pjrc.com/teensy/loader.html). For Linux, follow their instructions for installing the [GCC Compiler and Tools](https://www.pjrc.com/teensy/gcc.html). For Windows, you will need the [latest AVR toolchain](https://www.microchip.com/mplab/avr-support/avr-and-arm-toolchains-c-compilers) from the Microchip site. See [this issue](https://github.com/LightningStalker/Splatmeme-Printer/issues/10) and [this thread](http://gbatemp.net/threads/how-to-use-shinyquagsires-splatoon-2-post-printer.479497/) on GBAtemp for more information. (Note for Mac users - the AVR MacPack is now called AVR CrossPack. If that does not work, you can try installing `avr-gcc` with `brew`.)

LUFA has been included as a git submodule, so cloning the repo like this:

```
git clone --recursive https://github.com/greenfiftytwo/egg-hatcher
```

will put LUFA in the right directory.

Now you should be ready to rock. Open a terminal window in the `egg-hatcher` directory, type `make`, and hit enter to compile. If all goes well, the printout in the terminal will let you know it finished the build! Follow the directions on flashing `Joystick.hex` onto your Teensy, which can be found page where you downloaded the Teensy Loader application.

#### Potential Upgrades

1) I would like to make it handle the situation where the Nursery Lady doesn't have an egg ready without breaking the loop
2) I would like to optimize it to hit 20 eggs/hour, preferably without having to use different code for different egg cycles
3) I would like to clean up the code and shorten it
4) I would like to make a seperate program that automates releasing a box or two of pokemon

#### Thanks

Big thanks to bertrandom for his BOTW snowballer thrower that this code and a thousand others are forked from.  You made automating the switch much more accessible to beginning coders.

Thanks to Shiny Quagsire for his [Splatoon post printer](https://github.com/shinyquagsire23/Switch-Fightstick) which bertrandom forked and progmem for his [original discovery](https://github.com/progmem/Switch-Fightstick) that began it all.

