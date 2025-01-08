# TMS9900: Mini-Cortex Build

## Scope ##
Summary of a mini-Cortex build. 

## Introduction ##

As one of Stuart Conner's demonstation projects it uses specialised IO with an emphasis on software development. The micocomputer board uses a TMS9995 microprocessor with support for extended memory, compact flash storage and a graphics processor. PCB's are purchased from Stuart Conner with other components via email request.

The project with documentation. schematics, firmware and software is provided at [Mini-Cortex System](http://www.stuartconner.me.uk/mini_cortex/mini_cortex.htm).

### IO ###
1. 5 bits of write only digital IO. Implemented via the TMS9995's CRU (direct serial) interface.
1. Video display processor interface supporting the F18A, a 40 pin DIL socket plugin. This implements the behaviour of the TMS9918 family of VDP's using an FPGA.
2. A Compact Flash daughter board. Support is provided in some software for FAT32 with the file system providing files as virtual volumes. Capacity ranges from 256M to 4 Gig.
3. A USB serial interface provides a connection to a PC via a terminal program such as Tera Term (PC) or Serial (MacOS). 

### Software ###

Firmware is provided on a AT28C256 EEPROM, or it can be burnt into such an EEPROM using the bin files provided. A TL866 II Plus works fine for this task. An AT27C256 OTP eprom can also be pressed into service by rerouting a few pin connections.

Three sets of firmware are provided:
1. EVMBug (monitor), Cortex BASIC (computer language), MDEX (operating system), unix 6 (operating system).
2. Cortex BASIC, extended (computer language).
3. EVMBug (monitor), FIG Forth (computer language).

### Connection ###

Connection requires the serial terminal software on the PC to use 9600 baud, 7 bits, even parity, 1 stop bit, no flow control. After reset (button press on the PCB) there is no activity on the terminal, but it responds to a keypress by displaying a firmware selection menu with 1, 2 or 4 items, depending on which firmware is used.

## Assembly ##

A component kit was purchased via eBay user hth-tech. Search for "TI TMS9995 Mini Cortex Homebrew IC Kit". The PCB's for the mini-cortex and the compact flash daughter board were ordered directly from Stuart Conner. Also from eBay, a range of small capacity Compact Flash drives were purchased for testing.

The board was soldered with turned-pin sockets and other components. The PCB was cleaned using a specialised flux-removal detergent and then isopropanol in an ultrasonic bath. Metal standoffs were used to mount the compact flash daughter board. The screws were shortened a little with a miniature abrasive disc driven by a drill. Standoffs were also attached at the corners of the PCB to avoid shorts when laid on a conductive surface.

The USB serial module pinout just happens to match the USB pinout on the board, so no further wiring was required. Due to some confusion in starting unix a regulated 5V power supply was attached, and the 5V link on the USB serial module was cut. This provides power supply levels closer to 5V, but its probably unnecessary.

The INT jumper on the board has to be installed. Without it the unix firmware locks up just before the login prompt.

A USB connected media reader module with CF Card support was used to inspect the contents of a selected Compact Flash card to verify that it was working. Under Windows 10, the card was (slow) formatted as FAT32 with 4096 byte allocation blocks. The 4 supplied files, MDEX_DEV0.DSK, MDEX_DEV1.DSK, LSX_DEV0.DSK, LSX_DEV1.DSK were then copied to the CF Card as mounted by the reader. The CF card is then transferred to the Mini-Cortex.

![image](https://github.com/user-attachments/assets/a5c0f6d0-6a57-4438-9a1e-caff2b0c7e94)

## Verification ##
EEPROM 1 was inserted into the PCB socket, the board was reset and each option exercised in turn by keying its number. To exit the option the board was reset. The following tests were run:
1. Some monitor commands were executed. Note that the commands for TiBug and EVMBug are different. The commands are documented at ["TIBUG and EVMBUG System Monitors"](http://www.stuartconner.me.uk/tibug_evmbug/tibug_evmbug.htm#evmbug).
