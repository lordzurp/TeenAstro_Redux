# TeenAstro Redux
#### a mini version of the mini version
===========================

## What is Redux ?
The main goal of this flavour of TeenAstro hardware is to achieve the smallest board possible, and by extension the smallest case.

This is obtained by onboarding lot of modular parts, like stepper drivers or power supply, in a almost fully SMD board.

to be convenient to produce, the board was engineered to be assembled by JLCpcb, an china prototype specialist (the part list is selected inside their catalog).


## Who Redux is for ?
Smaller, simplier (and a bit cheaper), Redux version is althrough intented in priority to beginners who want a plug and forget solution, just working with their first telescope.

See next point, the limitations would say a no-go for enthusiats with already tons of material.

If you want to use sophisticated hardware, please take a look on regular TeenAstro boards

## Features
Almost all the features of TeenAstro regular board

* Compatible with TeenAstro Mini version software
* Teensy 3.2 powered
* on-board GPS
* TMC5160 motor driver
* up to 25V power voltage
* up to 3A stepper motor
* 2.12" OLED screen, in a modified SNES gamepad (china clone of course !) 

However, there are a few variations and limitations against the mini and main versions :

* no ST4 port
* no focuser option
* no replaceable part, meaning if something goes wrong, the whole board will dying ...
* no fuse, so be **very** careful with power supply (related to previous point, it's a **die-and-rebuy** version)

## Sources

The project is separated in 2 parts, jointed on the same PCB for easier way

* Main board, who receive the Teensy and the GPS modules

![Schematic Main Board](/Schematics/Main_board.png)
![Main Board - top](/Pictures/Main_board-topt_.png)
![Main Board - bot](/Pictures/Main_board-bot.png)

* Hand controller, who integrate a discret version of Wemos D1 (based on ESP8266 MCU)

![Schematic Hand Controller](/Schematics/Hand_controller.png)
![Hand Controller - top](/Pictures/Hand_controller-top_.png)
![Hand Controller - bot](/Pictures/Hand_controller-bot_.png)


## Build
The choices made for this board, due to small size and SMD asembly, lead to an increased skill needed to achieve the complete building of the project against the other versions. Be aware of your skill before you go to do a Redux version.

* FPC connector with 0.5mm pitch. use soldering flux !
* Mini-USB thru-holes connector with 0.8mm pitch
* SMD pins headers whosen't stay in their holes (because they don't have holes)
* **very** small board with little place to work

these points said, the board come moslty assembled, and you'll have few components to add

## Parts list

* PCB on [EasyEDA](https://easyeda.com/lordzurp/TeenAstro_Redux) (direct ordering on JLCpcb inside the soft) : 200€ includind customs and shipping, for 5 kits 
* Teensy 3.2 ~24€ piece
* GPS module like [Neo-6](https://www.ebay.fr/itm/GY-NEO6MV2-NEO-6M-GPS-Module-APM2-5-Flight-Control-w-IPX-interface-For-Arduino/273932103174?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2057872.m2749.l2649) from 5 to 30€, depending of your patience
* [SNES gamepad](https://www.amazon.fr/dp/B07R91BTKZ/) 6€ the twice
* Componants on [Farnell / Element14](https://fr.farnell.com/webapp/wcs/stores/servlet/PFOrderCopy?orderId=vDW5TcPW5zSxy%2fe6zh5%2fCJKzbsLq7ImEPYU0hqMQlGM%3d_IBM_2&langId=-2&storeId=10160&catalogId=15001&URL=AjaxOrderItemDisplayView&ICID=TREML010-007) 290€ for 5 kits

#####Do **bulk orders**, 10 or 20 kits at once, you'll save lot of money

the kit costs around the 150 €

## Support
Questions and discussion should be on the mailing list (also accessible via the
web) at the [TeenAstro Group](https://groups.io/g/TeenAstro/wiki/Home).

## License
MIT

## Author
lordzurp
based on great work of [Charles Lemaire](https://github.com/charleslemaire0/TeenAstro), [Howard Dutton](http://www.stellarjourney.com)