This is the README file for USBasp.

USBasp is a USB in-circuit programmer for Atmel AVR controllers. It simply
consists of an ATMega88 or an ATMega8 and a couple of passive components.
The programmer uses a firmware-only USB driver, no special USB controller 
is needed.

Features:
- Works under multiple platforms. Linux, Mac OS X and Windows are tested.
- No special controllers or smd components are needed.
- Programming speed is up to 5kBytes/sec.
- SCK option to support targets with low clock speed (< 1,5MHz).
- Planned: serial interface to target (e.g. for debugging).


LIMITATIONS

Hardware:
This package includes a circuit diagram. This circuit can only be used for
programming 5V target systems. For other systems a level converter is needed.

Firmware:
The firmware dosn't support USB Suspend Mode. A bidirectional serial
interface to slave exists in hardware but the firmware doesn't support it yet.


USE PRECOMPILED VERSION

Firmware:
Flash "usbasp.atmega88.xxxx-xx-xx.hex" or
"bin/firmware/usbasp.atmega8.xxxx-xx-xx.hex" to the used controller with a
working programmer (e.g. with avrdude, uisp, ...). Set jumper J2 to activate
USBasp firmware update function.
You have to change the fuse bits for external crystal (see "make fuses").
# TARGET=atmega8    HFUSE=0xc9  LFUSE=0xef
# TARGET=atmega48   HFUSE=0xdd  LFUSE=0xff
# TARGET=atmega88   HFUSE=0xdd  LFUSE=0xff

Windows:
Start Windows and connect USBasp to the system. When Windows asks for a
driver, choose "bin/win-driver". On Win2k and WinXP systems, Windows will
warn that the driver is is not 'digitally signed'. Ignore this message and
continue with the installation.
Now you can run avrdude. Examples:
1. Enter terminal mode with an AT90S2313 connected to the programmer:
   avrdude -c usbasp -p at90s2313 -t
2. Write main.hex to the flash of an ATmega8:
   avrdude -c usbasp -p atmega8 -U flash:w:main.hex

Setting jumpers:
J1 Power target
   Supply target with 5V (USB voltage). Be careful with this option, the
   circuit isn't protected against short circuit!
J2 Jumper for firmware upgrade (not self-upgradable)
   Set this jumper for flashing the ATMega(4)8 of USBasp with another working
   programmer.
J3 SCK option
   If the target clock is lower than 1,5 MHz, you have to set this jumper.
   Then SCK is scaled down from 375 kHz to about 8 kHz.


MORE INFORMATION

For more information on USBasp and it's components please visit the
following URLs:

USBasp .......................... http://www.fischl.de/usbasp/

Firmware-only V-USB driver ...... http://www.obdev.at/products/vusb/
avrdude ......................... http://www.nongnu.org/avrdude/
libusb .......................... http://libusb.sourceforge.net/
libusb-win32 .................... http://libusb-win32.sourceforge.net/

