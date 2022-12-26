# TeenAstro Redux Project
#### a mini version of the TeenAstro mini version
=========================

## What is TeenAstro ?
TeenAstro is a **Telescope controller** for Equatorial and Altazimuth mounts (incluing Dobson).
It is a tribute to the FS2 system from Michael Koch.

TeenAstro is an **open source, open hardware** do-it-yourself DIY project, forked from OnStep, the first mature controller based on Arduino hardware. The fork aims to focus on *one* hardware setup, to be easier to build, instead of the large versatility of OnStep who can be scary when have to  choose between all the versions available.

## What is Redux project ?
The primary goal of this flavour of TeenAstro hardware is to get the **smallest board possible**, and by extension the smallest case.

This is achieved by **onboarding** some modular parts, such as stepper drivers or power supply, in a **almost fully SMD** board. But that comes with tradeoffs, the main one being the lack of ability to change parts if something goes wrong.

It started in the Great Spring 2020 containment, and the first prototype resulted in an all-in-one functional product, with 2-axis drivers, in an 80x40mm board. But a few things were left out during development, like "fit into a box" ...

The Great Fall 2020 containment yielded the second prototype, and too many followed ...

As a side project started with a joke ("Can it fit into a tic-tac box ?"), the **SuperRedux** flavor followed a different way from the first draw, with stacking boards upto the Teensy board, and goes to a even smaller product. It works, but was a nightmare to built.

Great Shortage in 2022 make Teensy boards very hard to find, so a new challenger comes into the MicroMod form-factor, made by Sparkfun : an standard M.2 connector, with small minimal MCU board embedded.

At 2023, the final version of v2.6 is **ready to build**


![3D_board](https://raw.githubusercontent.com/lordzurp/TeenAstro_Redux/master/Redux_v2.6/TeenAstro_v2.6-Redux_2_board_3D.png)

## Features
Almost all the features of TeenAstroMini boards are present in the v2.6 version

* Compatible with **TeenAstro software**
* ASCOM and INDI USB driver
* **MicroMod Teensy** (from Sparkfun) to reduce footprint
* TMC2660 motor driver
* 12V 1.5A PowerDelivery input
* up to 2A stepper motor
* on-board GPS

Removed features :

* no ST4 port - guiding via USB only
* no polar LED output


## So, what is new ?
Some improvements were made from the publicly released version 2.4, based on the 2.5 work (teensy 4.0)

* **Teensy 4.0** new board, more powerfull CPU, but in 3.3V only, and with a different pins mapping
* **MicroMod form-factor**, no more headers to sold
* **on-board stepper drivers** 
* **smaller board**, which make possible direct integration **into** the mount enclosure

## Sources
All necessary files are available in this repo, so you can build your own easily. Don't forget to take a look into the [project homepage](https://groups.io/g/TeenAstro/wiki/Home)
The software is available from [TeenAstro repo](https://github.com/charleslemaire0/TeenAstro)

## Build
The boards were designed to be **assembled by JLCpcb**, a Chinese specialist in prototypes (the gerbers files follows their specs and the list of components is selected from their catalog).
Complete productions files are available for direct order from JLCpcb..

Additionnals components :

* M3x4mm screw (for M.2 module)
* GNNS Module (NEO-6/7/8 successfully tested)
* 1220 Battery SMD holder : https://fr.farnell.com/multicomp/ch291-1220lf/battery-holder-smt-12mm/dp/2064722


## Support
Questions and discussion should be on the mailing list (also accessible via the
web) at the [TeenAstro Group](https://groups.io/g/TeenAstro/topics).

## License
GPL v3

## Author
lordzurp
based on great work of [Charles Lemaire](https://github.com/charleslemaire0/TeenAstro) and [Howard Dutton](http://www.stellarjourney.com) (and a lot of contributors)