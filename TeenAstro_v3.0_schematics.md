# TeenAstro v3.0

## Revue électronique détaillée

### Teensy

On passe du Teensy 3.2 au Teensy 4.1, au format MicroMod (by [sparkfun](https://www.sparkfun.com/products/16402)

* de la patate à revendre, chip à 600MHz

* + d'UART, + de GPIO, module encodeur hardware (toutes les pins du 4.1 sont dispo)

* pas de pin à souder, s'installe comme un module WiFi d'ordi portable

* prix : autour de 26-28€ ttc (encore dispo chez digikey !)

 ![teensy](https://cdn.sparkfun.com/c/264-148/assets/learn_tutorials/1/2/6/6/MM_Teensy_PB_Thumb.jpg)


![teensy](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_teensy.png)

#### Pin Out

(les numéros correspondent aux **alias Arduino**, pas aux broches du connecteur)

* **SPI** : 
	* SDO 11
	* SDI 12
	* SCK 13
* **UART**
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
* **Moteur 1** (RA/AZ)
	* DIR 35
	* STEP 34
	* ENA 38
	* CS 39
* **Moteur 2** (DEC/ALT)
	* DIR 8
	* STEP 7
	* ENA 36
	* CS 23
* **Encodeur 1**
	* A 2
	* B 30
	* N 4
* **Encodeur 2**
	* A 33
	* B 31
	* N 3
* **I2C** (non cablé)
	* SDA 18
	* SCL 19
* **I/O**
	* Led 27
	* PI Shutdown 28
	* Sonde Temp (non cablé) 29
	* GPS PPS 5
	* Reticule X1 (non cablé) 40
* **Port ST4** (pull-up, non cablé)
	* RA+ 24
	* RA- 10
	* DEC+ 22
	* DEC- 25

## GNSS

![gps](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_gps.png)

* pour test : module GPS + Beidou AM336 intégré, connecteur antenne UF.L

* secours : Module GPS NEO-6/7/8 classique ( 4 pins)

## Port USB

![usb](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_usb.png)

* Connecteur USB-C

* Liaison PC

Après avoir beaucoup cresué la question de l'alim via USB-C (Power Delivery), c'est une fausse bonne idée :

* necessité d'avoir un µC qui gère la négo entre l'alim et la carte (code en + au boot du Teensy + gestion des interrupt)

* risque de blocage si l'alim ne peut pas valider le profil demandé

* matos encore très anarchique : les seuls alims "correctes" sont celles de laptop, les chargeurs de télephone ne proposent pas (encore) de profil d'alim suffisant -> 3 users sur 4 aura la mauvaise alim, et ça va pas marcher ...

-> le bon vieux jack 2.1mm reste le plus simple et efficace

## Raspberry PI 

#### version Mini HAT

* Connexion directe à un PI via le GPIO

* gestion du profil des ports GPIO via une EEPROM sur la carte (norme HAT)

* libère un port USB sur le PI


### GPIO

![pi](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_pi.png)

#### Config Pinout

* Serial
	* TX GPIO14
	* RX GPIO15
* Shutdown Signal GPIO26

### EEPROM

![eeprom](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_eeprom.png)

#### Overlay et DTparam

* Led red : heartbeat

* Led green : CPU activity

## Power

### Protection inversion

![power_in](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_power_in.png)

* Protection contre les inversions

* Protection contre les surtensions

* Fusible réarmable (polyfuse) 3A

### Step-down

![step_down](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_step_down.png)

* Umax 25V
* Imax 3A

### Batterie

![battery](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_battery.png)


* **LM1220** rechargeable, se recharge lorsque que le TeenAstro est branché, autonomie théorique 3 mois

* **ne pas installer de pille CR1220 !!!**

### Protection PI

![back_power](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_back_power.png)

* utilisation d'un CI spécialisé pour proteger au max le PI (limite de courant)

* Empeche d'envoyer l'alimentation vers le PI s'il est déjà alimenté

### Protection ESD

![esd](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_esd.png)

* Ecrétage des surtensions sur jack et USB

## Pilotes de moteur **TMC2660C**

![motor](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_motor.png)

* MosFet intégré

* Imax 2.8A

* Sense resistance 0,075R

* Connecteurs moteur
	* Rapide 
	* Vis 
	* DB9 (version mini)

## Encodeurs

![encoders](https://github.com/lordzurp/TeenAstro_Redux/raw/master/Images/schematic_encoders.png)

* Gestion hardware par le Teensy 4
	* Libraires :
		* [Hardware Quadrature Library](https://github.com/mjs513/Teensy-4.x-Quad-Encoder-Library)
		* [PJRC Library](https://www.pjrc.com/teensy/td_libs_Encoder.html)

* Tension 5V (conversion 3V3 pour le teensy)

* header à broches 2x5 points


