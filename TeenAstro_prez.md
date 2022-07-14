# TeenAstro v3

![GitHub release](https://img.shields.io/badge/Version-0.9-orange.svg)


## 2 ans plus tard, on en est où ?
7 versions fabriquées, plein de blocs logiques testés (driver moteur, alim ...), plusieurs form factors essayés, du plein format raspberry PI à la boite de tic-tac

Rien n'était pleinement satisfaisant, trop grand, pas adapté pour rentrer dans un boitier, trop compliqué à assembler ... mais on s'approche d'un truc bien (les 2 dernières à droite)

![ScreenShot](https://raw.githubusercontent.com/lordzurp/TeenAstro_Redux/master/Images/Teenastro_prototypes.jpg)

Puis est arrivé la Révolution : les [**MicroMod Sparkfun**](https://www.sparkfun.com/micromod).

 ![teensy](https://cdn.sparkfun.com//assets/parts/1/5/1/3/2/16402-SparkFun_MicroMod_Teensy_Processor-04.jpg)

un format standardisé de micro-controleurs dispo en plusieurs diversités (STM32, teensy, esp32 ...) avec un connecteur commun (M.2, le connecteur des cartes wi-fi de portables et des SSD)

ça supprime la principale contrainte du teensy : les pins traversants qui empèche de faire une carte CMS propre

nouveau design autour de ce nouveau teensy

tous les autres blocs ont été testé et validé sur les différents proto (sauf le GPS intégré, mais il y a un failsafe apour un module standard si les perfs ne sont pas au rendez-vous)

### Points clés

- #### Carte CMS livrée assemblée à 90+ %
	c'est l'objectif depuis le début : proposer un design CMS tout intégré et assemblé en usine (chez JLCpcb). Pour réduire la barrière de la soudure des composants, le casse-tête du sourcing ...

- #### Teensy 4 M.2
	Nouvelle version dev par sparkfun (en collab avec PJRC)

	46 I/O, 5 UART ...

	le schéma est compatible avec le Teensy 4.1 (42 GPIO accessibles directement)
	
- #### driver moteur TMC2660
	plus performant que les 2130, moins cher que les 5160
	
	interface hard et soft identique (juste à mettre à jour le constructeur)
	
	MOSFET intégrés jsuqu'à 2.8A (protégé par des polyfuses 3A)

- #### entrées pour des encodeurs ABN
	le teensy 4 a  un **module hardware** de gestion des encodeurs, et des libraires fournissent des méthodes toutes prètes pour les utiliser

- #### Connecteur USB-C
	c'est moderne, c'est robuste et c'est devenu le standard, tout le monde commence à avoir un cable USB-C chez lui

	uniquement utilisé pour la connexion au PC, ne gère pas l'alim (Power Delivery)

- #### module GPS intégré
	prévu en test sur le prochain proto, un module chinois intégré sur la carte, pour ne plus se poser la question duquel acheter parmi les 300 réfs de aliexpress

	en plan B, header pour un neo-6/7/8 classique

- #### alim
	supporte jusqu'à 25V

	pensé pour être relié à une batterie de visseuse (20V Li-Ion)

- #### port ST4
	dispo uniquement sur la Mini Classic

	les résistances de pull-up sont toujours présentes sur les 2 autres cartes, pour la compatibilité du firmware

### Fonctions abandonnées

* Après avoir beaucoup cresué la question de l'**alim via USB-C** (Power Delivery), c'est (pour moi) une fausse bonne idée :

	* necessité d'avoir un µC qui gère la négo entre l'alim et la carte (code en + au boot du Teensy + gestion des interrupt)

	* risque de blocage si l'alim ne peut pas valider le profil demandé

	* alimenter la monture via le port USB-C d'un laptop peut paraitre cool, mais ça va sucer la batterie très vite, et en cas de gros problème ça flingue tout

	* matos encore très anarchique : les seuls alims "correctes" sont celles de laptop, les chargeurs de télephone ne proposent pas (encore) de profil d'alim suffisant -> 3 users sur 4 aura la mauvaise alim, et ça va pas marcher ...

	-> le bon vieux **jack 2.1mm** reste le plus simple et efficace

* 3e moteur : techniquement, ça rentre, mais enormément de code à modifier pour integrer le focuser dans le module principal.



### Versions prévues (design en phase finale)


les [Schémas](https://github.com/lordzurp/TeenAstro_Redux/blob/master/HAT/Schematic_TeenAstro_v3.0.pdf) en PDF et le [schéma tout-sur-une-page](https://github.com/lordzurp/TeenAstro_Redux/blob/master/HAT/Schematic_TeenAstro_v3.0_single_sheet.png) en png

- #### Version Mini-HAT

![ScreenShot](https://raw.githubusercontent.com/lordzurp/TeenAstro_Redux/master/Images/TeenAstro_v3.0_Mini-HAT.thumb.png)

HAT : Hardware Attached on Top -> carte montée au dessus

format standardisé d'extension pour micro-controleur (avec chacun ses specs) : arduino, PI, ESP ...

respecte les specs de la fondation PI pour les HAT

	- EEPROM d'auto-config du PI (GPIO et overlays)
	- protection de l'alimentation (évite les conflits si le PI est déjà alimenté)
	- format de la carte standard à tous les HAT

principal intéret : communication directe entre le teenastro et le pi via les pins GPIO (UART_1), libère un USB sur le pi

compatible avec la plupart des boitiers PI (qui exposent les GPIO, bien sur)

- #### Version Mini Redux

![ScreenShot](https://raw.githubusercontent.com/lordzurp/TeenAstro_Redux/master/Images/TeenAstro_v3.0_Mini-Redux_small.png)

La version mini de la Mini

prévu pour un boitier alu extrudé de 60x80 (hammond) ou intégration directement dans la monture (impression 3D)

- #### version Mini Classic

**design à terminer**

![Schéma](https://raw.githubusercontent.com/lordzurp/TeenAstro_Redux/master/HAT/Schematic_TeenAstro_v3.0_trad.png)
![ScreenShot](https://raw.githubusercontent.com/lordzurp/TeenAstro_Redux/master/Images/TeenAstro_v3.0_planche_a_clous.png)

* Compatible avec la Mini 2.4

* pour une upgrade à moindre frais vers le teensy 4 + encodeurs

### Evolution du soft

- modif du pinout
- gestion des TMC2660 à peaufiner
- ajout de la gestion des encodeurs (lib existantes)
- ajouter une option dans le menu pour désactiver les moteurs, pour permettre les mouvements manuels sur un dobson sans débrayage mécanique (push-to avec les encodeurs)
- gerer plusieurs profils de télescope directement depuis la raquette, à la manière des sites
- ajout d'une option pour choisir le mode de connexion au PC : usb ou UART directe

### prix de revient 

Avec les 2 drivers moteurs, le GPS et tous les composants CMS assemblés

* par lot de 5 : **50€**

* par lot de 25 : **35€**

#### Composants à rajouter

	- connecteurs moteur (bornier à vis)
	- headers
	- Teensy M.2 (25-30€)
	- téléco
	- pile rechargeable LM1220
	- header 40pts (HAT)