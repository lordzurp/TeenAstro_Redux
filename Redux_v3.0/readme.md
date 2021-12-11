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

### Evolution from v2.4 series

#### Teensy 4.0
The (not so) new Teensy 4.0 is a beast of computing power, with a 600MHz Cortex-M7 CPU.
It is almost pin-to-pin compatible with Teensy 3.2, modulo the UART.

The biggest difference is the 4.0 **isn't 5V compliant**, having to switch to a  logic voltage of 3.3V for the whole board.

The routing of the board has been updated accordingly, and to follow new form-factor constraints. So, specific firmware is needed, with branch 3.0 (under developpement)

#### Integrated stepper driver
To reduce assembling complexity, the motor drivers are soldered directly to the board.
It provides more reliable connections and easier production.

The chosen drivers are **TMC2660**

They have all the benefits and internal functions of the TMC5160, but with integrated MOSfet, capable of driving 3A max stepper motors, protected by resettable fuses

#### on-board GPS
There is the place to solder a GPS module directly on the board.

Depending of the case choice, it may need to have external antenna (not enough place inside, or metal case who reduce antenna gain)

#### Focuser
**awaiting software devloppement**

The board can be used for main mount control **or** focuser / derotator control.

there is a link port, to rely the 2 boards and provide unified controls with a crossover cable.
The function depend on which firmware is uploaded to the board.

#### Reworked Power supply
The Power input is protected from inversion polarity, ESD and short-circuit with a resettable 3A fuse.

The logic voltage is **3.3V**, according of Teensy 4.0 requirements (see follow)

#### Protected I/O
the SHC port and the link port are ESD-protected, so you can plug it while the board is ON (although it isn't recommended ...)

#### Removed features
* There is no longer ON/OFF switch
* no ST4 port : as the guiding of the mount requipes computer, having only the USB link option should not be a big issue



### Production notes

**Follow JLCpcb capabilities and parts list**

* 2-layers board
* Min track width : 0.2mm
* Min clearence : 0.2mm
* Via size : 0.25/0.5mm

#### Additionnals parts
* Teensy 4.0
* GPS module (neo-6 compatible)
* Motor connectors ( 4 ways pitch 3.5mm)
* Reticule connector (optional)