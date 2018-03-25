# Software
This is an embedded system, and [Alpine Linux](https://www.alpinelinux.org) is the best choice, because it runs from RAM and it's very stable.

We still want to support other operating systems, at least [raspbian](https://www.raspbian.org/).

## Features
- web interface for management (based on [ACF](https://wiki.alpinelinux.org/wiki/Alpine_Configuration_Framework_Design)): at the moment you can switch on-off the outlets and edit the config files
- select the startup boot condition

## Planned features
- bonjour (avahi) autodiscovery
- snmp interface for accessing system data, actual and cumulative power consumpion (for each port and global), port status...
- power on/off based on planning, timer, sunrise/sunset, counter, random (or based on humidity/temperature if the corresponding sensor is connected)
- web api for external scripts (remote power commands and so on)
- email/telegram alerting
- port grouping
- alerts/triggers for power consumption of individual ports or the whole system
- power management (say you want to limit total power to 500W, you can prioritize ports and switch off the power hungry ones)
- send remote commands BEFORE poweroff
- grouping of multiple OpenPDUs
- poweroff a port when the power is below a specified level
- current consumption and analysis for appliance identification (like smappee)
- remember the last state of each port when the system is powered back on
- configuration of the optional LCD/OLED display: you can configure a set of slides with different data (global current/voltage status, port status, ip address, notifications)
- [NUT](http://networkupstools.org) integration
- (using an USB or an RS232 port) UPS connection and sharing via NUT
- [OpenHAB](https://www.openhab.org/) integration
- [home-assistant.io](https://www.home-assistant.io/) integration
- thermal regulation based on external sensors and fan management
- dedicated web interface
- [raspbian](https://www.raspbian.org/) support
