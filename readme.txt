----------------------------------------------------------------
ST Blitter Rev.C2
Blitter, IDE, TOS decoder, ET4000 connector for Atari ST(M)

(c)2020 Anders Granlund
www.happydaze.se
----------------------------------------------------------------

This hardware is provided 'as-is', without any express
or implied warranty. In no event will the authors be held
liable for any damages arising from the use of this hardware.

These files are distributed under the GPL v2, or at your
option any later version. See LICENSE.TXT for details

----------------------------------------------------------------



----------------------------------------------------------------
BOM:
----------------------------------------------------------------
ATF1504 CPLD
R1,R2,R5,R6 = 2K2 (size 0805)
R3,R4,R7,R8,R9 = 4K7 (size 0805)
All caps are 0.1uF (size 0805)


----------------------------------------------------------------
Blitter:
----------------------------------------------------------------
It is important to set the "Blitter Enable" solder-jumpers to
the correct ON/OFF position depending on if a blitter has
been fitted or not.
These jumpers are located in the CPU socket area.



----------------------------------------------------------------
IDE:
----------------------------------------------------------------
The IDE interface responds as the first interface by default.
You can change the interface number by soldering the "IDE address"
jumpers. For example, if O means open and X means soldered:

"O O" = interface 0
"O X" = interface 1
"X 0" = interface 2
"X X" = interface 3

The IDE function can be completely disabled by soldering the
"IDE Disable" jumper.


----------------------------------------------------------------
TOS decoding:
----------------------------------------------------------------
The current firmware no longer requires the original ROM CE from
the motherboard (RCEI on the leftmost header at the CPU socket)

It will fully decode TOS1.xx, TOS2.xx and TOS3.xx roms
and send the CE signal out on the RCEO pin.

TOS decoding feature can be completely disabled by
soldering the "ROM disable" jumper.



----------------------------------------------------------------
Graphics card
----------------------------------------------------------------
ET4000 feature can be completely disabled by soldering
the "ET Disable" jumper.


See "et4000.jpg" for how to wire up a graphics card.

NOTE: This assumes an ET4000 which only need +5V and GND.
If your particular card requires +12V / -12V then you need to
wire that up to the corresponding pins on the ET4000.
(+12V is pin B9 and -12V is pin B7)


The interface is based on STGA by Till Harbaum:
http://www.harbaum.org/till/atari/index.html

I have personally only tested it with the ET4000 drivers
that come with NVDI 5.03.
Other drivers, such as Ideks NOVA driver for STGA or
Till's own STGA driver will most likely work too and
may or may not be easier to set up - I have never tried them.


If you are using the NVDI driver you need to do the following
when you are configuring your hardware and screen modes using
the VMF-4000 tools:

Select "manuell" graphics card with the following values:
Screenbaseaddress:   $FEC00000
Registerbaseaddress: $FECF03B0

Make sure "16bit I/O" is selected and use the following
register values for the CLUT:
 8bit : 00
15bit : A0
16bit : C0
24bit : F0

Some useful hints on STGA under NVDI can be found here:
https://forum.atari-home.de/index.php?topic=12789.0



Note:
Atari drivers are quite picky about which ET4000 they support.
Especially when it comes to RAMDAC and/or clock generator.
I don't know the details so I tried a few cards in a machine
that had a known working VOFA setup, picked one that worked
and wired it to the STGA interface on this board.

atari-home.de is a good source for finding threads about
using graphics card on the Atari.
Frank Lukas there is extremely knowledgable on the subject.


