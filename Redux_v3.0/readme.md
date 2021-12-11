# TeenAstro Redux Project
#### a mini version of the TeenAstro mini version
===========================

## Redux 3.0 - the Finale Edition


===========================
### Pre release notes
The board isn't still validated, please don't go to built it now !!!
Also, the firmware isn't yet ready to publish

===========================

This version is a mix between the main and the mini board, trying to have a (very) small board size who can be easily integrated with mounts, and to keep the extended functions of the main unit

## Evolution from v2.4 series

### Teensy 4.0
The (not so) new Teensy 4.0 is a beast of computing power, with a 600MHz Cortex-M7 CPU.
It is almost pin-to-pin compatible with Teensy 3.2, modulo the UART.

The biggest difference is the 4.0 **isn't 5V compliant**, having to switch to a  logic voltage of 3.3V for the whole board and SHC.

The routing of the board has been updated accordingly, and to follow new form-factor constraints. So, specific firmware is needed, with branch 3.0 (under developpement)

### Integrated stepper driver
To reduce assembling complexity, the motor drivers are soldered directly to the board.
It provides more reliable connections and easier production.

The chosen drivers are **TMC2660**

They have all the benefits and internal functions of the TMC5160, but with integrated MOSfet, capable of driving 3A max stepper motors, protected by resettable fuses

### on-board GPS
There is the place to solder a GPS module directly on the board.

Depending of the case choice, it may need to have external antenna (not enough place inside, or metal case who reduce antenna gain)

### Focuser
**awaiting software devloppement**

The board can be used for main mount control **or** focuser / derotator control. The additionnal chip (DS1302) is on board, can be used by the focuser firmware and ignored by the main firmware.

there is a link port, to rely the 2 boards and provide unified controls with a crossover cable.
The function depend on which firmware is uploaded to the board.

### Reworked Power supply
The Power Input is protected from inversion polarity, ESD and short-circuit with a resettable 3A fuse.

The ON/OFF switch is now a logic-level switch, which don't have to support full board current. Any simple switch can do the job. There are 2 pads to solder wires, and it is possible to short them if no need of power-off

The logic voltage is **3.3V**, according of Teensy 4.0 requirements (see below)

The button cell is now a CR1220 (standard CR2032 is far too big now)

### Protected I/O
the SHC port and the link port are ESD-protected, so you can plug it while the board is ON (although it isn't recommended ...)

### Removed features
* no longer ST4 port : since mount guidance requipes a computer, having only the USB_link option shouldn't be a big issue


## Firmware update needed (WiP)
* renewed pinout
* TMC2660 support
* second motor on focuser : can be used for secondary focuser or derotator. some code is available in OnStep, need to review and merge
* INDI driver : unified control of mount and focuser with a single USB link


## Production notes

**Follow JLCpcb capabilities**

* 2-layers board
* Min track width : 0.2mm
* Min clearence : 0.2mm
* Via size : 0.25/0.5mm

#### SMD parts
the whole SMD parts are picked from the JLCpcb assembly list, so you can order fully SMD-assembled board.

#### Additionnals parts
* Teensy 4.0
* GPS module (neo-6 compatible)
* Motor connectors ( 4 ways pitch 3.5mm or wires)
* ON/OFF switch (optional)
* Reticule connector (optional)