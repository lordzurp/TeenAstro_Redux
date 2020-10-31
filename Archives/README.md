# TeenAstro Redux
#### a mini version of the TeenAstro mini version
=========================

## What is TeenAstro ?
TeenAstro is a **Telescope controller** for Equatorial and Altazimuth mounts (incluing Dobson).
It is a tribute to the FS2 system from Michael Koch.

TeenAstro is an **open source, open hardware** do-it-yourself project, forked from On Step, the first mature controller based on Arduino hardware.

## What is Redux ?
The first goal of this flavour of TeenAstro hardware is to achieve the **smallest board possible**, and by extension the smallest case.

This is obtained by **onboarding** some modular parts, like stepper drivers or power supply, in a **almost fully SMD** board. But this come with compromises, the main is the **lack of backward compatibility** with original FS2 system.

All this gives this 

* Main board : 40x82mm, case : 90x50x24mm (32mm with focuser extension)

![3D View](/PCB/Main_board-3D.png)

![3D View](/PCB/Hand_controller-3D.png)


## Features
Almost all the features of TeenAstro regular board are present

* Compatible with **TeenAstro software**
* **wireless connexion** between main unit and remote
* Teensy 3.2 powered
* on-board GPS
* ASCOM USB driver
* TMC5160 motor driver
* up to 25V power voltage
* up to 3A stepper motor
* 2.42" OLED screen, in a modified SNES gamepad
* Polarity inversion protection
* focuser bpard can be easily added (with 32mm enclosure)


However, there are a few variations and limitations against the mini and main versions :

* no ST4 port
* **no** replaceable part, meaning if something goes wrong, the whole board will dying ...

## Sources

The project is separated in 3 boards

* Main board, who receive the Teensy and the GPS modules

![Schematic Main Board](/Schematics/Main_board.png)
![Main Board - top](/PCB/Main_board-top.png)	
![Main Board - bot](/PCB/Main_board-bot.png)

* Focuser, who came in top of main board
Schematic
PCB

* Hand controller, who integrate a discret version of Wemos D1 (based on ESP8266 MCU)

![Schematic Hand Controller](/Schematics/Hand_controller.png)
![Hand Controller - top](/PCB/Hand_controller-top.png).    
![Hand Controller - bot](/PCB/Hand_controller-bot.png)


## Build
The choices made for this board, due to small size and SMD asembly, lead to an **increased skill needed** to achieve the complete building of the project against the other versions. Be aware of your skill **before** you go to make a Redux version.

* small composants with small pads. **use some soldering flux** !
* SMD pins headers whosen't stay in their holes (because they don't have holes)
* **very** small board with little place to work

these points said, the board come moslty assembled, and you'll have few components to add. 

To be produced, the card was designed to be **assembled by JLCpcb**, a Chinese specialist in prototypes (the list of parts is selected from their catalog).

You can easily order the circuits alone, but without skill, practice and specials tools, you **will not** be able to solder the components on the PCB, many of them measure less than 1mm (and this is really not great to solder by hand). Don't try to save a couple of bucks, order fully assembled PCB, unless you exacly know what you do.

## Parts list

To make the project, you'll need to assemble the board :

* PCB on [EasyEDA](https://easyeda.com/lordzurp/TeenAstro_Redux) (direct ordering on JLCpcb inside the soft) : 
	* 200€ includind customs and shipping, for 5 kits 
	* 275€ for 10 kit, and discounting
* Componants on [Farnell / Element14](https://fr.farnell.com/webapp/wcs/stores/servlet/PFOrderCopy?orderId=go50hjG4clGzbzcQri22OCnaGykOMFe1bIZYWgR9xz8%3d_IBM_2&langId=-2&storeId=10160&catalogId=10001&URL=AjaxOrderItemDisplayView&ICID=TREML010-007) 290€ for 5 kits

### Screen Choice

2 OLED displays are compatible with this board, each with 4 colours (white, yellow, green and blue)

* Midas MCOT128064QV (Farnell #2769705) 2.7 "
* Midas MCOT128064U1V (Farnell #2769709) 2.42 "


the kit costs around the **100 €** by 5 pieces

#### Do **bulk orders**, 10, 20 or even 50 kits at once, you'll save lot of money

For example, a batch of 50 pieces will cost **60€ per unit**

Next, you'll have to plug these parts in :

* Teensy 3.2 ~24€ piece
* GPS module like [Neo-6](https://www.ebay.fr/itm/GY-NEO6MV2-NEO-6M-GPS-Module-APM2-5-Flight-Control-w-IPX-interface-For-Arduino/273932103174?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2057872.m2749.l2649) from 5 to 30€, depending of your patience
* [SNES gamepad](https://www.amazon.fr/dp/B07R91BTKZ/) 6€ the twice



## Support
Questions and discussion should be on the mailing list (also accessible via the
web) at the [TeenAstro Group](https://groups.io/g/TeenAstro/wiki/Home).

## License
GPL v3

## Author
lordzurp
based on great work of [Charles Lemaire](https://github.com/charleslemaire0/TeenAstro), [Howard Dutton](http://www.stellarjourney.com)