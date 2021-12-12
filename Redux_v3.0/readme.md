# TeenAstro Redux Project

#### A mini version of the TeenAstro mini





[![GitHub release](http://img.shields.io/badge/Version-3.0_RC0-orange.svg?style=flat)][release]
[![GPL 3.0 License](https://img.shields.io/badge/license-GPL_3.0-blue.svg?style=flat)][license] 

[release]: https://github.com/lordzurp/TeenAstro_Redux/releases
[license]: https://raw.githubusercontent.com/lordzurp/TeenAstro_Redux/master/LICENSE





===========================

## Redux 3.0 — the Finale Edition
===========================

### Pre-release notes

> The board isn’t validated yet, please don’t build it right now! Also, the firmware isn’t final neither.

===========================

This version is a mix between the main board and the mini board. The idea is to have a (very) small board that can easily integrate with mounts while still retaining the extended functions of the main unit.


## 3D view

![3D_top](https://raw.githubusercontent.com/lordzurp/TeenAstro_Redux/master/Redux_v3.0/TeenAstro_Redux%20v3.0%20-%202_board_3D%20TOP.png) ![3D_bot](https://raw.githubusercontent.com/lordzurp/TeenAstro_Redux/master/Redux_v3.0/TeenAstro_Redux%20v3.0%20-%202_board_3D%20BOT.png)

## Schematics

![ScreenShot](https://raw.githubusercontent.com/lordzurp/TeenAstro_Redux/master/Redux_v3.0/TeenAstro_Redux%20v3.0%20-%201_schematic.png)


## Evolution from the v2.4 series

### Teensy 4.0
The (not so) new Teensy 4.0 is a beast of computing power, with a 600 MHz Cortex-M7 CPU. It is almost pin-to-pin compatible with the Teensy 3.2, except for the UART.

The main difference is that the 4.0 **isn’t 5 V compliant**, the logic voltage is 3.3 V across the board and the SHC.

The board’s routing was updated to comply with the constraints of the new form factor. As a consequence, specific firmware is needed, with branch 3.0 (under development).

### Integrated Stepper Driver
To minimize the assembling complexity of the unit, the motor drivers are soldered directly to the board. This makes for more reliable connections and easier production.

The chosen drivers are the **TMC2660**.

They include all the benefits and internal functions of the TMC5160, but with integrated MOSfet which is capable of driving the 3A max stepper motors and is protected by resetting fuses.

### Onboard GPS
There is a space on the board to solder a GPS module.

Depending on the casing, you may need an external antenna (if there’s not enough place inside, or if the casing is made of metal which would reduce the gain of the antenna).

### Focuser
**Awaiting software development**

The board can be used either to control the mount or the focuser or the derotator. The onboard additional chip (DS1302) can be used by the focuser’s firmware and ignored by the main firmware.

A link port allows connecting the two boards and it also provides unified controls with a crossover cable. The use depends on which firmware is uploaded to the board.

### Reworked Power Supply
The power input is protected from polarity inversion, ESD and short-circuiting by a resetting 3A fuse.

The ON/OFF switch is now a logic-level switch, it doesn’t have to support the full-board current. Any regular switch will do the job. Two pads are added for soldering the wires and one can short-circuit them if there is no need for a power-off switch.

The logic voltage is **3.3 V**, as per the Teensy 4.0 requirements (see below).

The button battery is now a CR1220 (standard CR2032 is far too big).

### Protected I/O
The SHC port and the link port are ESD-protected, so you can plug them while the board is ON (although this isn’t recommended…).

### Removed Features
*	no ST4 port anymore: since the mount guiding requires a computer, having only the USB_link option shouldn’t be a problem.

## Firmware and software update needed (WiP)
*	new pinout
*	TMC2660 support
*	Uploader and Config tool, to support new branch
*	additional motor on the focuser: can be used for a secondary focuser or derotator. Some code is available in OnStep, need to review and merge
*	INDI driver: unified control of mount and focuser with a single USB link

## Production Notes
**Follows JLCpcb Capabilities**

*	2-layer board
*	Min track width: 0.2 mm
*	Min clearance: 0.2 mm
*	Via size: 0.25/0.5 mm

#### SMD parts
The whole SMD parts are sourced from the JLCpcb assembly list, so you can order a fully SMD-assembled board.

#### Additional parts
*	Teensy 4.0
*	GPS module (neo-6 compatible)
*	Motor connectors (4 ways pitch 3.5 mm or wires)
*	ON/OFF switch (optional)
*	Reticule connector (optional)

