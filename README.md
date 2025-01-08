# TMS9900: Mini-Cortex Build

## Scope ##
Summary of a mini-Cortex build. 

## Introduction ##

As one of Stuart Conner's demonstation projects it uses specialised IO with an emphasis on software development. The micocomputer board uses a TMS9995 microprocessor with support for extended memory, compact flash storage and a graphics processor. PCB's are purchased from Stuart Conner with other components via email request.

### IO ###
1. 5 bits of write only digital IO. Implemented via the TMS9995's CRU (direct serial) interface.
1. Video display processor interface supporting the F18A, a 40 pin DIL socket plugin. This implements the behaviour of the TMS9918 family of VDP's using an FPGA.
2. A Compact Flash daughter board. Support is provided in some software for FAT32 with the file system providing files as virtual volumes. Capacity ranges from 256M to 4 Gig.
3. A USB serial interface provides a connection to a PC via a terminal program such as Terraterm (PC) or Serial (MacOS). 

### Software ###

Firmware is provided on a AT28C256 EEPROM, or it can be burnt into such an EEPROM using the bin files provided. A TL866 II Plus works fine for this task. An AT27C256 OTP eprom can also be pressed into service by rerouting a few pin connections.

Three sets of firmware are provided:
1. EVMBug (monitor), Cortex BASIC (computer language), MDEX (operating system), unix 6 (operating system).
2. Cortex BASIC, extended (computer language).
3.  EVMBug (monitor), FIG Forth (computer language).

### Connection ###

Connection requires the serial terminal software on the PC to use 9600 baud, 7 bits, even parity, 1 stop bit, no flow control. After reset (button press on the PCB) there is no activity on the terminal, but it responds to a keypress by displaying a firmware selection menu with 1, 2 or 4 items, depending on which firmware is used.
