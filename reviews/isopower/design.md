# DESIGN DESCRIPTION 

This design description is for the 1m ISO container experiment boxes



## Background

This PCB is intended to host the DC-DC convertors for converting the single 24V power supply into the local voltages required for operating 12V motors and 5V Arduino via USB.

## Specification

This board is required for use by the spinner experiment, which has the following power requirements

a/ steady power usage of 20W at 12V (Maxxon AMax 32 236668	Graphite brushes, 20 Watt)
b/ peak power usage of 69W 5.7A at 12V (when motor stalled)
c/ 5V power for the Raspberry pis, typically 2.5A per Raspberry Pi; four raspberry pi connections, 1 connection for power to nano iot 33 monitoring chip.

optional features
a/ report status and current usage (e.g. for sustainability and maintenance purposes)

### Design tradeoffs

#### MCU for monitoring
We could not bother with monitoring, but that would leave us unsure of why systems were off, and also we would not build a good picture of the power usage, so we would not understand how much power redundancy to provide in future for similar experiments. For example, how reasonable is the assumption that four DC motors would draw maximum current at the same time, and that it would matter that they did so. For example, if the motors are all stalled, then power supply sag won't make much difference - they aren't moving. If they are in position control mode and all four motors reverse direction at the same time, drawing the same current as a stall, then this would potentially affect how well the measurement would match the theory, because it would not reverse direction as fast. Yet, for such a short-lived moment, how statistically likely is it that all four motors in the box would do this at the same time (which would be required to max out the DC-DC convertor), and that they would do so repeatedly? A single result deviating from the expected values should not be too challenging to get around - simply repeat the experiment.

#### USB UART on board

If we are monitoring, it would be easiest if we had a MCU to USB connection, so we could connect to a raspberry pi which would then log the data. There is a bit of a chicken and egg problem here, because if the power to the box is off, then the monitoring circuit will not provide any data. Whereas, if we had an additional USB monitoring connection .... then we could power the monitoring circuit from the USB, and connect it to another Raspberry pi that was powered externally - although this would need another plug on the wall -which we might not have.... Could we do the power monitoring in a different way, by simply putting a power monitor on the wall socket?

Or we could power a nano 33 IoT from a 5th USB socket on the power board, and have it communicate over wifi, needing no extra hole in the wall of the box. Then it's heartbeat would act as confirmation that the 5V signal was alive...

see [here](https://docs.arduino.cc/tutorials/nano-33-iot/WiFi_connection) for information on how to connect nano 33 IoT to wifi.

### Design for assembly

How will you put it together e.g. if using cable connections, how will these be manufactured?

### Design for reliability

Things go wrong with assembly and usage, even with the best of staff working on the job. So how will your design prevent itself from being damaged by accidental or even malicious misuse, e.g. reversed power supplies, or wrong power supply, incorrect peripheral connections etc (especially where terminal blocks are used, because polarity cannot be enforced very easily).

### Design for maintenance 

What parts are likely to fail, and how will they be replaced?


## Part  details

List here any helpful details which can assist in the review process, such

### Part 1

Which part, and variant(s) are you using?

#### Sourcing

Where can you get it from?

#### Size, orientation

How big is it, and which way round does the footprint need to be on the PCB? How much clearance is needed around the part e.g. for putting in wires to terminal blocks

#### Supply considerations

What is the typical, and absolute supply voltage(s)?

#### Application considerations

What supporting components are needed? 

#### Electromagnetic compatibility considerations

Note any components which should be close together, far apart, and any track length considerations







