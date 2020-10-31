# TeenAstro Redux Project - Changelog
#### a mini version of the TeenAstro mini version
===========================

## SuperMini - PI Edition

### v3.0 beta 2 - 16/10/2020

**Fully revamped board**

#### New features
* Teensy 4.0 : **break** teensy 3.2 compatibility due of change in pins assignement
* encoders headers

#### Changes
* 4-layers board
* Raspberry PI 3 form factor
* compatible with PI 3B cases
* new 5V power circuit

#### Bug Fixes


### v3.0 beta 1 - 23/05/2020

**NOT RELEASED and NOT TESTED**

#### New features

* ajout MOSFet de protection contre les inversions de polarité
* Ajout header pour accueillir le focuser
* liaison RF nRF24 sur bus SPI
	* /CS relié à A0-D14
	* /CE relié à A1-D15
	* librairie arduino : https://tmrh20.github.io/RF24/

#### Changes

* passage de la batterie sur la face BOT
* réorganisation de l'alim 5V

#### Bug Fixes

* rajout pastille pour X1 - éclairage réticule

### v2.41 - 10/5/2020

**Initial release**

* basé sur teenastro mini v2.4.1
* suppresion du port ST4
* alim 5V intégrée (XL1509-5.0)
* driver moteur TMC5160 intégré (x2)
* battrie CR1220
* module GPS intégré


## SuperRedux

### v2.5 beta 1 - 16/10/2020

**Initial release**

* based on 2.4.2 Mini version
* minimal version

## Focuser

### v3.0 beta 2 - 16/10/2020

**Fully revamped board**

* match the beta 2 main board
* TMC2130 onboard
* deported connectors to main board


### v3.0 beta 1 - 23/05/2020

**NOT RELEASED and NOT TESTED**

* basé sur TeenAstro main v2.4.1
* TMC5160 intégré
* liaison avec la carte principale : VCC, GND, +5V, Vbatt, RX3/TX3


## Hand Controller

### v3.0 beta 1 - 23/05/2020

**WIFI NON FONCTIONNEL**

#### New features

* multiplexage des boutons : **PCA9554APW**
	* bus I2C, adresse 0x20
	* /INT relié à GPIO13
	* tous les boutons sont forcés à GND et passent à Vcc à l'état actif
	* livrairie arduino : https://github.com/AD0ND/PCA9554
* liaison RF : **nRF24L01+**
	* bus SPI
	* /CS et /CE reliés à GPIO0 -> flag de config : RF24_TINY
	* librairie arduino : https://tmrh20.github.io/RF24/
* gestion de batterie Li-Ion **BQ24075**
	* Vin via USB
	* Vout sur le +5V
	* Vbatt relié à Tout
		* analog input, max 1V
		* ratio 1/5.7, Vbatt 4.2V = 0.737V)
		* API **system_adc_read**
	* inter physique pour couper l'alimentation de la carte
* mini platine micro-USB + power switch déporté

#### Bug fixes

* connecteur FCP au pas de 1.0mm
* cablage du connecteur modifié (/RES à Vdd, capas ...)
* ajout du quartz pour le CH340G
* modif cablage AMS1117 (pad à +3.3V)

#### à tester 
* WiFi non fonctionnel sur v1

### v1.0 - 10/05/2020

**Initial release**

**NON FONCTIONNEL**

* basé sur TeenAstro SHC v0.1
* ESP8266 + CH340G
* capa + resistances pull-down CMS
* alim 12V pour écran OLED Midas
* connecteur FCP au pas de 0.5mm (beaucoup trop petit !)