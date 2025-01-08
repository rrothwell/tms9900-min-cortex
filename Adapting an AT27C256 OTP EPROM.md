# Adapting an AT27C256 OTP EPROM #

The Mini-Cortex board uses an AT28C256 for firmware storage. 
It just happens that I have a few AT27C256 OTP EPROM's on hand. \
These are faster at 70ns, but have a slightly different  pinout.

The datasheets are located at:
1. [AT28C256](https://ww1.microchip.com/downloads/en/DeviceDoc/doc0006.pdf).
2. [AT27C256](https://ww1.microchip.com/downloads/en/DeviceDoc/doc0014.pdf).

On the AT27C256 IC:
1. The VPP(1) pin needs to be raised outward and joined to the VCC(28) pin. 
2. The A14(27) pin needs to be raised outward and connected to the A14(1) board location.
This can be accomplished with the IC inserted into a spacer socket and an little solder.
![AT27C256 Top](/AT27C256%20top.jpeg)
![AT27C256 Bottom](AT27C256%20bottom.jpeg)
