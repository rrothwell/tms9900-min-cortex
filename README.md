# TMS9900: Mini-Cortex Build

## Scope ##
Summary of a mini-Cortex build. 

## Introduction ##

As one of Stuart Conner's demonstation projects it uses specialised IO with an emphasis on software development. It uses a TMS9995 microprocessor with support for extended memory, compact flash storage and a graphics processor. 

### IO ###
1. 5 bits of write only digital IO. Implemented via the TMS9995's CRU (direct serial) interface.
1. Video display processor interface supporting the F18A, a 40 pin DIL socket plugin. This implements the behaviour of the TMS9918 family of VDP's using an FPGA.
2. A Compact Flash daughter board. Support is provided in some software for FAT32 with the file system providing files as virtual volumes. Capacity ranges from 256M to 4 Gig.
3. A USB serial interface provides a connection to a PC via a terminal program such as Terraterm (PC) or Serial (MacOS). 
