Description of the level shift operation. [Source - Philips AN97055]
For the level shift operation, following three states have to be considered:

• State 1:
	 No device is pulling down the bus line and the bus line of the “Lower voltage” section is pulled up
by its pull-up resistors Rp to 3.3 V. The gate and the source of the MOS-FET are both at 3.3 V, so its VGS
is below the threshold voltage and the MOS-FET is not conducting. This allows that the bus line at the
“Higher voltage” section is pulled up by its pull-up resistor Rp to 5V. So the bus lines of both sections are
HIGH, but at a different voltage level.

• State 2:
	 A 3.3 V device pulls down the bus line to a LOW level. The source of the MOS-FET becomes
also LOW, while the gate stay at 3.3 V. The VGS rises above the threshold and the MOS-FET becomes
conducting. Now the bus line of the “Higher voltage” section is also pulled down to a LOW level by the 3.3
V device via the conducting MOS-FET. So the bus lines of both sections become LOW at the same
voltage level.

• State 3:
	 A 5 V device pulls down the bus line to a LOW level. Via the drain-substrate diode of the MOSFET
the “Lower voltage” section is in first instance pulled down until VGS passes the threshold and the
MOS-FET becomes conducting. Now the bus line of the “Lower voltage” section is further pulled down to
a LOW level by the 5 V device via the conducting MOS-FET. So the bus lines of both sections become
LOW at the same voltage level.

The three states show that the logic levels are transferred in both directions of the bus system, independent of
the driving section.
Other supply voltages than 3.3V for VDD1 and 5V for VDD2 can be applied. In normal operation VDD2 must be equal 
to or higher than VDD1.
