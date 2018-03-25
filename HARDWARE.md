# Hardware
We're splitting hardware configurations in different categories:

- DIY Switched (you can turn on/off each outlet)
- DIY Switched and metered (total power consumption is monitored)
- DIY Switched and per-outlet metered (each outlet's power consumption is monitored)
- Switched and metered (with our open-hardware relays board)

The system is composed by the following modules:

 - DC power supply
 - controller board
 - relays board

## DC Power supply
The power supply will power the controller and the power board, taking the power from the existing power switch (it's uncommon to have a rack power strip without a power button; in this case it's required to add a power button).

## Controller
The controller board will be a commonly available one (let's say a Raspberry PI 2/3, Orange Pi, ...).
See the [HCL](HCL) for more details.
We prefer the OrangePi over the RaspberryPi because it's more open (and cheap).
There won't be wireless support at the moment.

## Relays board
In the "DIY way" the relays board is a cheap 8 relays board, GPIO controlled. It's possible to obtain the metering features by adding some AC current sensors.

# Outlets
A possible scenario is the use of a (commonly available) rackmount enclosure with mounted power sockets.
It'll be possible to use front-mounted power sockets (shucko and so on) for power bricks and back-mounted power sockets with [IEC 60320 C14](https://en.wikipedia.org/wiki/IEC_60320) inlets.
When chosing an existing non-smart PDU to retrofit, take into consideration the way the outlets are connected: if there's a common bus connecting the poles (like a copper bar or similar), that's harder to adapt if compared to a PDU that has real wires.

# Extra components

 - another custom board to monitor the input current and voltage, i2c based
 - status display (i2c based): this will be configured via the web interface
 - humidity / temperature sensor (you guessed: i2c based)
 - rev.2 power board with differential current metering
