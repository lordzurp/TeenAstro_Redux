# TeenAstro Redux - Changelog
#### a mini version of the TeenAstro mini version
===========================

## Main Board

### v3.0 - 23/05/2020

#### New features

* ajout MOSFet de protection contre les inversions de polarité
* ajout pastille pour X1 - éclairage réticule
* liaison RF nRF24 sur bus SPI
	* /CS relié à A0-D14
	* /CE relié à A1-D15
	* librairie arduino : https://tmrh20.github.io/RF24/

####Bug Fixes

* nothing yet

### v2.41 - 10/5/2020

* basé sur teenastro mini v2.4.1
* suppresion du port ST4
* alim 5V intégrée (XL1509-5.0)
* driver moteur TMC5160 intégré (x2)
* battrie CR1220
* module GPS intégré


## Focuser

### v3.0 - 23/05/2020

* basé sur TeenAstro main v2.4.1
* TMC5160 intégré
* liaison avec la carte principale : VCC, GND, +5V, Vbatt, RX3/TX3


## Hand Controller

### v3.0 - 23/05/2020

#### New features

* multiplexage des boutons via un 74HC151
	* tous les boutons sont forcés à GND et passent à +3.3V à l'état actif
	* livrairie arduino : https://playground.arduino.cc/Code/MUX151/
	* connexion du 74HC151 :
		* S0, S1, S2 reliés respectivement à GPIO15, GPIO12, GPIO14
		* Y relié à GPIO13
* liaison RF nRF24 sur bus SPI
	* librairie arduino : https://tmrh20.github.io/RF24/
	* /CS et /CE reliés à GPIO0 -> flag de config : RF24_TINY
* gestion autonome de batterie Li-Ion **BQ24075**
	* Vin via USB
	* Vout sur le +5V
	* Vbatt relié à **Tout**
		* analog input, max 1V
		* ratio 1/5.7, Vbatt 4.2V = 0.737V)
		* API **system_adc_read**
	* switch pour couper l'alimentation de la carte
* mini platine micro-USB + power switch déporté

#### Bug fixes

* connecteur FCP au pas de 1.0mm
* cablage du connecteur modifié (/RES à Vdd)
* CH340G changé pour CH340C
* modif cablage AMS1117 (pad à +3.3V)

#### à tester 
* WiFi non fonctionnel sur v1



### v1.0 - 10/05/2020

* basé sur TeenAstro SHC v0.1
* ESP8266 + CH340C
* capa + resistances pull-down CMS
* alim 12V pour écran OLED Midas
* connecteur FCP au pas de 0.5mm (beaucoup trop petit !)