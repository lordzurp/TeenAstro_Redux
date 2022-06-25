# TeenAstro v3

## 2 ans plus tard, on en est où ?
5 versions fabriquées, plein de blocs logiques testés (driver moteur, alim ...), plusieurs form factors essayés, du plein format raspberry PI à la boite de tic-tac

Rien n'était pleinement satisfaisant, trop grand, pas adapté pour rentrer dans un boitier, trop compliqué à assembler ...

Puis est arrivé la Révolution : les **MicroMod Sparkfun**. 
un format standardisé de micro-controleurs dispo en plusieurs diversités (STM32, teensy, esp32 ...) avec un connecteur commun

ça supprime la principale contrainte du teensy : les pins traversants qui empèche de faire une carte CMS propre

nouveau design autour de ce nouveau teensy
tous les autres blocs ont été testé et validé sur les différents proto (sauf le GPS intégré, mais il y a un failsafe apour un module standard)

### Points clés

- #### Carte CMS livrée assemblée à 90+ %
	c'est l'objectif depuis le début : proposer un design CMS tout intégré et assemblé en usine (chez JLCpcb). Pour réduire la barrière de la soudure des composants, le casse-tête du sourcing ...

- #### Teensy 4 M.2
	Nouvelle version dev par sparkfun (en collab avec PJRC)

	format M.2, le connecteur des cartes wifi de laptop

	40 I/O dispobile, autant que le TeensY 4.1, avec un format de 22x22mm

- #### driver moteur TMC2660
	plus performant que les 2130, moins cher que les 5160
	
	interface hard et soft identique (juste à changer le constructeur)
	
	MOSFET intégrés jsuqu'à 2.8A

	**3 drivers moteur**, permet d'integrer le focuser sans rajouter un 2e teensy

- #### entrées pour des encodeurs ABN
	le teensy 4 a  un **module hardware** de gestion des encodeurs, et des libraires fournissent des méthodes toutes prètes pour les utiliser

	essai prévu avec des encodeurs magnétiques 1024 points à 4$, en mode push-to (pas de boucle fermée pour l'instant, juste suivre les mouvements manuels)

- #### Connecteur USB-C
	c'est moderne, c'est robuste et c'est devenu le standard, tout le monde commence à avoir un cable USB-C chez lui

- #### module GPS intégré
	prévu en test sur le prochain proto, un module chinois intégré sur la carte, pour ne plus se poser la question duquel acheter parmi les 300 réfs de aliexpress

- #### gestion de la carte (encore en chantier)
	gestion des alims PI, teenastro, reset ...

- #### alim
	supporte jusqu'à 25V

	pensé pour être relié à une batterie de visseuse (20V Li-Ion)

	mesure de la conso du système, tension batterie ... en I2C relié au teensy

### Versions prévues (design en phase finale)

- #### Version HAT
	HAT : Hardware Attached on Top -> carte montée au dessus

	format standardisé d'extension pour micro-controleur (avec chacun ses specs) : arduino, PI, ESP ...

	respecte les specs de la fondation PI pour les HAT

		- EEPROM d'auto-config du PI
		- protection de l'alimentation (évite les conflits si le PI est déjà alimenté)
		- format de la carte standard à tous les HAT

	principal intéret : communication directe entre le teenastro et le pi via les pins GPIO (UART_1), libère un USB sur le pi

	reprend tous les ajouts cités plus haut

	compatible avec la plupart des boitiers PI (qui exposent les GPIO, bien sur)

	PCB 4 couches, CMS double face
	
- #### Version Redux
	reprend toutes les fonctions de la version standard actuelle, + les ajouts de la version HAT (sans la liaison avec le pi)

	connexion des moteurs sur bornier, encodeur + ST4 + T° focuser + polar sur header 2.54mm
	
	prévu pour un boitier alu extrudé de 60x80 (hammond) ou intégration directement dans la monture (impression 3D)

	PCB 4 couches, CMS double face

- #### Version Mini
	c'est la version "low cost" developpée pour mon projet principal (kit de modif d'un petit dobson de table, le 130 heritage de SW)

		- 2 moteurs
		- GPS intégré
		- encodeurs
		- pas d'interface avec le PI
		- pas de ST4

	prévu pour un boitier alu extrudé de 60x80 (hammond)

	PCB 4 couches, CMS simple face

### Evolution du soft
Dans un premier temps, il y a juste un remap des pins à faire dans le firmware pour récuperer les fonctions de base

(j'ai une carte avec un pinout modifié et un teensy 4.0 qui tourne actuellement, juste avec une branche 290)

les chantiers à prévoir pour exploiter pleinement les ajouts :

- intégration du code focuser dans le teensy principal
- ajout de la gestion des encodeurs (lib existantes)
- ajouter une option dans le menu pour désactiver les moteurs, pour permettre les mouvements manuels sur un dobson sans débrayage mécanique
- gestion de la batterie : mesure tension, conso ... icone batterie (100/75/50/25%) (ya des libs toute pretes)
- comm avec la carte, menu de gestion des alims (eteindre le pi)


### prix de revient 

calcul préliminaire à la grosse, fabrication en chine, **ne prend pas en compte le surcout double-face** (pas encore actif chez JLCpcb, mais ils m'ont promis que ça arrive ibnetôt ...)

**par lot de 5**

Version HAT : **56€**

Version Redux : **50€**

Version Mini : **38€**

**par lot de 25**

Version HAT : **40€**

Version Redux : **35€**

Version Mini : **25€**

#### Composants à rajouter (toutes versions)

	- connecteurs moteur (bornier à vis)
	- headers
	- Teensy M.2 (25-30€)
	- téléco
	- pile rechargeable LM1220