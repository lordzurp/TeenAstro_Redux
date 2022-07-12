# TeenAstro v3.0

## Revue électronique détaillée

### Teensy

 ![teensy](https://cdn.sparkfun.com/c/264-148/assets/learn_tutorials/1/2/6/6/MM_Teensy_PB_Thumb.jpg)

Format MicroMod (by [sparkfun](https://www.sparkfun.com/products/16402)

![teensy](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_teensy.png)

#### Pin Out

(les numéros correspondent aux **alias Arduino**, pas aux broches du connecteur)

* SPI : 
	* SDO 11
	* SDI 12
	* SCK 13
* UART
	* Serial : USB 
	* Serial1 : Debug (libre, pastilles sous le PCB)
		* TX 1
		* RX 0
	* Serial2 : N/C
	* Serial3 : GPS
		* TX 14
		* RX 15
	* Serial4 : Connexion Raspberry PI
		* TX 17
		* RX 16
	* Serial5 : téléco
		* TX 21
		* RX 20
* Moteur 1 (RA/AZ)
	* DIR 35
	* STEP 34
	* ENA 38
	* CS 39
* Moteur 2 (DEC/ALT)
	* DIR 8
	* STEP 7
	* ENA 36
	* CS 23
* Encodeur 1
	* A 2
	* B 30
	* N 4
* Encodeur 2
	* A 33
	* B 31
	* N 3


* Led 27
* PI Shutdown 28
* I2C (non cablé)
	* SDA 18
	* SCL 19
* Sonde Temp (non cablé) 29
* GPS PPS 5
* Reticule X1 (non cablé) 40
* Port ST4 (pull-up, non cablé)
	* RA+ 24
	* RA- 10
	* DEC+ 22
	* DEC- 25

## Raspberry PI 

![pi](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_pi.png)

### Config Pinout

* Serial
	* TX GPIO14
	* RX GPIO15
* Shutdown Signal GPIO26

## EEPROM

![eeprom](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_eeprom.png)

### Overlay et DTparam

* Led red : heartbeat

* Led green : CPU activity

## Power

### Protection

![power_in](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_power_in.png)

* Protection contre les inversions

* Fusible réarmable (polyfuse) 3A

### Step-down

![step_down](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_step_down.png)

* Umax 25V
* Imax 3A