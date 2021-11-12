# pcb-review
Documents to help with reviewing printed circuit board designs for remote laboratory experiments

## Background

PCB design is often about keeping track of the impacts of lots of small tid bits of data. Small mistakes can range from the merely annoying to the moderately expensive. Some of the things that can go wrong with even relatively simple embedded systems include getting the polarity of a power connector backwards, putting a footprint down that is the wrong size, or the wrong way up, getting pin headers that only take a round pin when your daughteroard is supplied with square pins, oversizing a track because you remembered the stall current from a motor wrong, forgetting to put pull-ups on an I2C bus, then adding them when they are not needed on a level shifting circuit which has it's own pullups, not leaving space around a terminal block to get wires in, leaving off mounting holes for the PCB, selecting the wrong pins on a microcontroller because you thought you'd use `analogWrite` then you device you want a different pulse width modulation frequency, so you need to use `SAMD21_Turbo_PWM`, needing to add a level shifter, needing to change the pin you get your 5V reference from when you change the arduino type from nano to nano every. Some of these have happened to us, and some of them nearly happened. Since there is an awful lot to keep a track of, I thought I'd try and formulate a design document that works for us (skip some of things we don't need to worry about, and add in some things that we do).

Ideally we'd also have a change control process so that we only have to sign off again on bits that have changed ...

A spreadsheet is probably a useful way to address this issue.






