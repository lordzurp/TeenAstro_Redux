# TeenAstro v3

### 2 ans plus tard, on en est où ?
5 versions fabriquées, plusieurs blcos testés (driver moteur, alim ...)
plusieurs form factors essayés, du plein format raspberry PI à la boite de tic-tac

Rien n'était pleinement satisfaisant, trop grand, pas adapté pour rentrer dans un boitier, trop compliqué à assembler ...

la révolution : les MicroMod Sparkfun. un format standardisé de micro-controleurs dispo en plusieurs diversités (STM32, teensy, esp32 ...) avec un connecteur commun
ça supprime la principale contrainte du teensy : les pins traversants qui empèche de faire une carte CMS propre

### Points clés

- Carte CMS livrée assemblée à 90+ %
	c'est l'objectif depuis le début : proposer un design CMS tout intégré et assemblé en usine (chez JLCpcb). Pour réduire la barrière de la soudure des composants, le casse-tête du sourcing ...

- Teensy 4 M.2
	Nouvelle version dev par sparkfun
	format M.2, le connecteur des cartes wifi de laptop 
	40 I/O dispobile, autant que le TeensY 4.1, avec un format de 22x22mm

- driver moteur TMC2660
	plus performant que les 2130, moins cher que les 5160
	interface hard et soft identique
	MOSFET intégrés jsuqu'à 2.8A

- 3 drivers moteur, permet d'integrer le focuser

- entrées pour des encodeurs ABN
	le teensy 4 a  un module hardware de gestion des encodeurs, et des libraires fournissent des méthodes toutes prètes pour les utiliser
	essai prévu avec des encodeurs magnétiques 1024 points à 4$, en mode push-to (pas de boucle fermée pour l'instant, juste suivre les mouvements manuels)

- Connecteur USB-C
	c'est moderne, c'est robuste et c'est devenu le standard, tout le monde commence à avoir un cable USB-C chez lui

- module GPS intégré
	prévu en test sur le prochain proto, un module chinois intégré sur la carte, pour ne plus se poser la question duquel acheter parmi les 300 réfs de aliexpress

- module de gestion de la carte
	gestion des alims PI, teenastro, reset ...
	mesure de la conso du système, tension batterie ...

### Versions prévues (design en phase finale)

- format HAT
	HAT : Hardware Attached on Top -> carte montée au dessus
	format standardisé d'extension pour micro-controleur (avec chacun ses specs) : arduino, PI, ESP ...
	respecte les specs de la fondation PI pour les HAT
		- EEPROM d'auto-config du PI
		- protection de l'alimentation (évite les conflits si le PI est déjà alimenté)
	principal intéret : communication directe entre le teenastro et le pi via les pins GPIO (UART_1), libère un USB sur le pi

- format Mini
	c'est la version "low cost" developpée pour mon projet principal (kit de modif d'un petit dobson de table, le 130 heritage de SW)
	2 moteurs, pas d'interface avec le PI, GPS intégré, pas de ST4 (inutile pour mon appli)
	prévu poru un boitier alu extrudé de 60x80 (hammond)

### Evolution du soft
de base, il y a juste un remap des pins à faire dans le firmware pour récuperer les fonctions de base

les chantiers à prévoir pour exploiter pleinement les ajouts :

- intégration du code focuser dans le teensy principal
- ajout de la gestion des encodeurs (lib existantes)
- ajouter une option dans le menu pour désactiver les moteurs, pour permettre les mouvements manuels sur un dobson sans débrayage mécanique
- comm avec la carte, menu de gestion des alims (eteindre le pi), ajout d'une icone batterie avec gestion de % (il y a des lib pour ça)


### prix de revient (calcul préliminaire, fabrication en chine)

**par lot de 25**

Version complete : **40€**

Version mini : **25€**
