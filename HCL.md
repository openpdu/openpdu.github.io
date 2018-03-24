# OpenPDU HCL
Hardware Compatibility List

## controller board

| Board name            | CPU             | RAM       | Supported | Notes                               |
|-----------------------|-----------------|-----------|:---------:|-------------------------------------|
| Raspberry Pi 2B       | BCM2835         | 1Gb       | Yes       |                                     |
| Raspberry Pi 3B       | BCM2837         | 1Gb       | Yes       |                                     |
| Raspberry Pi 3B+      | BCM2837B0       | 1Gb       | Yes       |                                     |
| Orange Pi One         | AllWinner H3    | 512Mb     | Yes       |                                     |
| Orange Pi Zero        | AllWinner H2    | 256/512Mb | Planned   |                                     |
| Orange Pi One Plus    | AllWinner H6    | 1Gb       | Planned   |                                     |
| Orange Pi Pc          | AllWinner H3    | 1Gb       | Planned   |                                     |
| Orange Pi Pc Plus     | AllWinner H3    | 1Gb       | Planned   |                                     |
| Orange Pi Pc 2e       | AllWinner H3    | 2Gb       | Planned   |                                     |
| Orange Pi Pc 2        | AllWinner H5    | 1Gb       | Planned   |                                     |
| Orange Pi Plus 2      | AllWinner H3    | 2Gb       | Planned   |                                     |
| Orange Pi Win         | AllWinner A64   | 1Gb       | Planned   |                                     |
| Orange Pi WinPlus     | AllWinner A64   | 2Gb       | Planned   |                                     |
| Orange Pi Prime       | AllWinner H5    | 2Gb       | Planned   |                                     |
| Orange Pi Zero Plus   | AllWinner H5    | 512MB     | Planned   |                                     |
| Orange Pi R1          | AllWinner H2    | 256Mb     | Planned   | Dual Ethernet                       |
| Orange Pi Lite        | AllWinner H3    | 512Mb     | No        | Missing Ethernet                    |
| Orange Pi Lite2       | AllWinner H6    | 1Gb       | No        | Missing Ethernet                    |
| Orange Pi Zero Plus 2 | AllWinner H5    | 512Mb     | No        | Missing Ethernet                    |
| Orange Pi 2G-IOT      | Cortex-a5       | 256Mb     | No        | Missing Ethernet - Useless 2G modem |
| Orange Pi i96         | Cortex-A5       | 256Mb     | No        | Missing Ethernet                    |
| Orange Pi RK3399      | Rockchip RK3399 | 2Gb       | No        | Board too big                       |

## power board
Any power supply capable to power the controller board is good. Please refer to the controller manufacturer website.

## relays board
Cheap relays boards are available for few bucks. These boards comes with cheap relays and are usually managed via GPIO. So for a 8 channel relays board, there are 10 pin: GND, 1 pin for each relay, 5Vdc.
Usually the relays in this board are "rated" for 5A or even 10A. Please don't trust these values.
