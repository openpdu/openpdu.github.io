# The OpenPDU project

OpenPDU is an OpenHardware and OpenSource project for a network-connected PDU.

The goal is to build a modular system than can be used to retrofit an existing 19" rack PDU to a real networked PDU.

A secondary goal is the use of commonly available hardware, where possible, at least for the main controller.

## Hardware
The first iteration will cover the scenario of a retrofit of an existing (rack) power strip. In any case we'll keep separated the system into the following modules:

 - DC power supply
 - controller board
 - power board

 The power supply will power the controller and the power board, taking the power from the existing power switch (it's uncommon to have a rack power strip without a power button; in this case it's required to add a power button).

 The controller board will be a commonly available one (let's say a Raspberry PI 2/3, Orange Pi, ...). The requirements are:

  - capable of running linux (Alpinelinux or Raspbian)
  - at least 256mb of RAM
  - ethernet port
  - GPIO/i2c port
  - (40pin connector? some orangepis have only 26)

 We prefer the OrangePi over the RaspberryPi because it's more open (and cheap).

 There won't be wireless support at the moment.


The power board will be a custom made board, with these requirements:

 - 4-8 relays
 - after each relay we need a current meter
 - LED output for the relay status (pin only)
 - i2c communication with the controller

### Secondary scenario
Another possible initial scenario is the use of a (commonly available) rackmount enclosure with mounted power sockets.
It'll be possible to use front-mounted power sockets (shucko and so on) for power bricks and back-mounted power sockets with [IEC 60320 C14](https://en.wikipedia.org/wiki/IEC_60320) inlets.


### Extra components

 - another custom board to monitor the input current and voltage, i2c based
 - status display (i2c based): this will be configured via the web interface
 - humidity / temperature sensor (you guessed: i2c based)
 - rev.2 power board with differential current metering

### Power board Design

For the first iteration of the project we won't talk about the controller and the power supply, just because we'll use some readily available parts. We also won't talk about the input current and voltage monitor board but this will be implemented in the next iteration. So let's jump into the power board.

Normal (economic?) PDUs are using only one current probe for the input, in this board we have individual per-port current transformers. FTW.

To ativate relays we'll use a MCP23008: it's a chip that communicates with the controller via i2c (3 address bit, 0x20-0x27) using two wires that can be shared with other i2c devices, you then have 8 i/o that can be configures as input or output. This will work in the range of 2.7V to 5.5V so it'll work with 3V3 and 5V. 20mA is the maximum sink/source current.
Relays: omron G5RL-1A-E-LN DC5 (5V, but it's 80mA to activate the coil so we need more juice)
current metering: ADS130E08


**APC is using 2 internal power supplies for 24v (for murata relays) and 3.3v (for the electronics)**
**fuse?????**

## Software
This is an embedded system, so Alpine Linux[Alpine Linux](https://www.alpinelinux.org) is the best choice. We still want to support other operating systems, at least Raspbian.
Planned features are:

 - web interface for management
 - bonjour (avahi) autodiscovery
 - snmp interface for accessing system data, actual and cumulative power consumpion (for each port and global), port status...
 - power on/off based on planning, timer, sunrise/sunset, counter, random (or based on humidity/temperature if the corresponding sensor is connected)
 - web api for external scripts (remote power commands and so on)
 - email/telegram alerting
 - port grouping
 - alerts/triggers for power consumption of individual ports or the whole system
 - power management (say you want to limit total power to 500W, you can prioritize ports and switch off the power hungry ones)
 - send remote commands BEFORE poweroff
 - poweroff a port when the power is below a specified level
 - current consumption and analysis for appliance identification (like smappee)
 - remember the last state of each port when the system is powered back on
 - configuration of the optional LCD/OLED display: you can configure a set of slides with different data (global current/voltage status, port status, ip address, notifications)
 - [NUT](http://networkupstools.org) integration
 - (using an USB or an RS232 port) UPS connection and sharing via NUT
 - OpenHAB integration
 - home-assistant.io integration
 - thermal regulation based on external sensors and fan management

 We'll start with Alpine Linux, so the go-to solution for web management is [ACF](https://wiki.alpinelinux.org/wiki/Alpine_Configuration_Framework_Design)
