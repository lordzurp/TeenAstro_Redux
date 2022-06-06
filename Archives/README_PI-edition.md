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

The Great Fall 2020 containment yielded the second prototype, which was designed to fit into a Raspberry PI 3B enclosure, and becomes the **SuperMini PI Edition**

As a side project started with a joke ("I'm sure it can fit into a tic-tac box !"), the **SuperRedux** flavor followed a different way from the first draw, with stacking boards upto the Teensy board, and goes to a even smaller product

## Features
All the features of TeenAstro regular boards are present in the SuperMini version

* Compatible with **TeenAstro software**
* ASCOM and INDI USB driver
* TMC5160 motor driver
* up to 25V power voltage
* up to 3A stepper motor
* Polarity inversion protection
* focuser board extension
* on-board GPS
* on-board WiFi module

the SuperRedux version lacks in some features, due to the small size

* Compatible with **TeenAstro software**
* ASCOM and INDI USB driver
* TMC5160 motor driver
* up to 25V power voltage
* up to 3A stepper motor
* NO polarity inversion protection
* NO focuser
* NO GPS

## So, what is new ?
Some improvements were made from the publicly released version 2.4, based on the 2.5 work (teensy 4.0) and the [NafaBox Hardware project](https://github.com/dragonlost/NAFABox-hardware)

* **Teensy 4.0** new board, more powerfull CPU, but in 3.3V only, and with a different pins mapping
* **direct connection** to the PI, with the GPIO UART. no more USB cord
* smaller board, excpecially for the SuperRedux, which make possible direct integration **into** the mount enclosure
* compatible with the NafaBox stack, with direct interco to power bus and PI GPIO

## Sources
All necessary files are available in this repo, so you can build your own easily. Don't forget to take a look into the [project homepage](https://groups.io/g/TeenAstro/wiki/Home)
The software is available from [TeenAstro repo](https://github.com/charleslemaire0/TeenAstro)

## Build
The boards were designed to be **assembled by JLCpcb**, a Chinese specialist in prototypes (the gerbers files follows their specs and the list of components is selected from their catalog).

A additional part list from [Farnell](https://fr.farnell.com) is provided.
Some parts are specific, but there most are common components which can be bought from any seller

Further instructions can be found into the dedicated sub-folders



## Support
Questions and discussion should be on the mailing list (also accessible via the
web) at the [TeenAstro Group](https://groups.io/g/TeenAstro/topics).

## License
GPL v3

## Author
lordzurp
based on great work of [Charles Lemaire](https://github.com/charleslemaire0/TeenAstro) and [Howard Dutton](http://www.stellarjourney.com) (and a lot of contributors)