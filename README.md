# DÉVELOPPEMENT D’UN LANGAGE SPÉCIFIQUE POUR DES ANIMATIONS GRAPHIQUES SIMPLES

#### Auteur : Clément Stoliaroff

L'objectif de ce projet était de développer un interpreteur de commandes pour des éléments graphiques

----------------

# Table des matières

* [Exercice 1 - Prise en main de la couche graphique](#exercice-1--prise-en-main-de-la-couche-graphique)

* [Exercice 2 : Première version d’un interpréteur de script](#exercice-2--Première-version-dun-interpréteur-de-script)

  * [Exercice 2.1 : Script de configuration](#exercice-21--script-de-configuration)
  
  * [Exercice 2.2 : Script d’animation](#exercice-22--script-danimation)

* [Exercice 3 : Introduction des commandes](#exercice-3--introduction-des-commandes)

* [Exercice 4 : Sélection et exécution des commandes](#exercice-4--sélection-et-exécution-des-commandes)

	* [Exercice 4.1 : Référencement des objets et enregistrement des commandes](#exercice-41--référencement-des-objets-et-enregistrement-des-commandes)
	
	* [Exercice 4.2 :  Ajout et suppression dynamique d’éléments graphiques](#exercice-42--ajout-et-suppression-dynamique-déléments-graphiques)

	* [Exercice 4.3 : Ajouter des éléments à des conteneurs](#exercice-43--ajouter-des-éléments-à-des-conteneurs)
	
	* [Exercice 4.4 : Création et exécution de scripts](#exercice-44--création-et-exécution-de-scripts)
	
		* [Exercice 4.4.1 : Les scripts](#exercice-441--les-scripts)
		
		* [Exercice 4.4.2 : La commande Clear](#exercice-442--la-commande-clear)
		
		* [Bonus : Lecture de gifs animés](#exercice-442--la-commande-clear)
	* [Tests](#tests)

* [Conclusion](#conclusion)
----------------

# Exercice 1 : Prise en main de la couche graphique

L'objectif de cet exercice était de programmer le déplacement de carré, appelé robi, d'un bord à l'autre tout en changeant de couleur aléatoirement.

La seule difficulté lors de cette première étape était la découverte du code existant.

Le déplacement de robi devait s'adapter au redimenssionnement de la fenêtre.

Le résultat de l'exécution est le suivant :

![Exécution de l'exercice 1](/exercice_1.gif)

----------------

# Exercice 2 : Première version d’un interpréteur de script

## Exercice 2.1 : Script de configuration

Ce deuxième exercice avait pour but d'introduire la notion de script de commande a exécuter.

Le script à exécuter dans cet exercice était le suivant :

```
(script
	(space color black)
	(robi color yellow) )
```

Je n'ai rencontré aucune difficulté particulière lors de cet exercice.

Le résultat de l'exécution est le suivant :

![Exécution de l'exercice 2.1](/exercice_2_1.PNG)

## Exercice 2.2 : Script d’animation

Dans la suite de ce deuxième exercice, le script a exécuter permettais d'effectuer une petite animation

Le script à exécuter étais le suivant :

```
(script
	(space color white)
	(robi color red)
	(robi translate 10 0)
	(space sleep 100)
	(robi translate 0 10)
	(space sleep 100)
	(robi translate -10 0)
	(space sleep 100)
	(robi translate 0 -10) )
```

Ce script introduisait les commandes suivantes :

* *translate*, qui permet de déplacer avec un décalage en x et y passé en argument
* *sleep*, qui provoque une mise en sommeil pour un nombre de millisecondes passé en argument

Là encore, je n'ai rencontré aucune difficulté particulière.

Le résultat de l'exécution est le suivant :

![Exécution de l'exercice 2.2](/exercice_2_2.gif)

# Exercice 3 : Introduction des commandes

Le but de cet exercice était d'améliorer la structure du programme en mettant en place un interface fonctionnelle nommée "Command", contenant une seule méthode : la méthode abstraite run(), ainsi que des classes implémentant cette interface, représentant les différentes commandes exécutables.

Cette amélioration permet en effet de simplifier l'ajout de nouvelles commandes. En effet, avant cette amélioration, il fallait ajouter le code de chaque commande dans le même fichier, alors que maintenant, il suffit de créer une nouvelle classe Command, et d'ajouter son exécution dans l'interpreteur.

Je n'ai pas non plus rencontré de difficulté particulière lors de cet exercice.

Le script que j'ai exécuté est le suivant :

```
(script
	(space setColor yellow)
	(robi setColor red)
	(robi translate 10 0)
	(space sleep 100)
	(robi translate 0 10)
	(space sleep 100)
	(robi translate -10 0)
	(space sleep 100)
	(robi translate 0 -10) )
```

Le résultat de l'exécution est le suivant :

![Exécution de l'exercice 3](/exercice_3.gif)

# Exercice 4 : Sélection et exécution des commandes

## Exercice 4.1 : Référencement des objets et enregistrement des commandes

Dans cet exercice, la structure du projet c'est encore améliorée avec l'implémentation des classes Reference et Environment.

Ces classes permettent d'ajouter de nouvelles commandes encore plus facilement qu'avant.

En effet, chaque référence possède des commandes et est située dans un environnement, permettant de lui attribuer des commandes facilement.

Je n'ai pas eu de problème particulier lors de cet exercice.


Le script exécuté est le suivant :

```
(space sleep 1000)
(robi setColor yellow)
(space sleep 500)
(space setColor red)
(space sleep 500)
(robi translate 30 30)
```

Le résultat de l'exécution est le suivant :

![Exécution de l'exercice 4.1](/exercice_4_1.gif)

## Exercice 4.2 : Ajout et suppression dynamique d’éléments graphiques

Lors de cet exercice, les commades AddElement et DelElement ont été implémentées, permettant d'ajouter et de supprimer des rectangles, des cercles, des images et des labels dans l'environnement pricipal.

Ceux-ci peuvent être manipulé de la même manière que le carré robi, précédemment présent dans l'environnement.

J'ai rencontré des problèmes de compréhensions lors de cet exercice. Notamment de la commande AddElement et des classes NewElement, NewImage et NewString.

Le script exécuté est le suivant :

```
(space sleep 1000)
(space setDim 1000 1000)
(space sleep 500)
(space add robi (Rect new))
(space sleep 500)
(robi translate 100 100)
(space sleep 500)
(space add momo (Oval new))
(space sleep 500)
(momo setColor green)
(space sleep 500)
(momo translate 150 150)
(space sleep 500)
(space add hello (Label new "Hello World"))
(space sleep 500)
(hello setColor black)
(space sleep 500)
(hello translate 200 0)
(space sleep 500)
(space add pif (Image new bear.jpg))
(space sleep 500)
(pif translate 0 500)

```

Le résultat de l'exécution est le suivant :

![Exécution de l'exercice 4.2](/exercice_4_2.gif)

## Exercice 4.3 : Ajouter des éléments à des conteneurs

Cet exercice a permis d'ajouter des éléments graphiques à l'intérieur d'autres éléments graphiques.

Cette possibilité a cependant été enlevée des ovals en raison de problème de conteneur graphique (les éléments sortaient du cercle).

La solution choisie pour mettre en place cette possibilité est l'ajout d'un environnement dans la référence de l'élément parent afin de contenir les éléments enfant.

Lors de la création d'un élément, on lui attribut un nouvel environnement enfant.

Désormais, la référence space est contenu dans un environnement, permettant de l'appeler et contient elle-même un environnement permettant d'y disposer les éléments.

Enfin, lors de l'appel à l'interpréteur, celui-ci utilise la notation pointée, en partant de l'environnement passé en paramètre pour accéder au dernier environnement désigné.

J'ai rencontré des problèmes au niveau de la gestion des environnement.

En effet, au départ, j'ajoutais toutes les références dans le même environnement avec la notation pointée pour nommage et pour la commande DelElement, je supprimais la référence en utilisant la méthode removeIf de la classe Map.


Le script exécuté est le suivant :

```
(space sleep 1000)
(space setDim 1000 1000)
(space sleep 500)
(space add robi (Rect new))
(space sleep 500)
(space.robi setDim 800 800)
(space sleep 500)
(space.robi setColor red)
(space sleep 500)
(space.robi add robi (Rect new))
(space sleep 500)
(space.robi.robi setDim 700 700)
(space sleep 500)
(space.robi.robi add img (Image new trex.jpg))
(space sleep 500)
(space.robi.robi.img translate 50 50)
(space sleep 500)
(space.robi del robi)
(space sleep 500)
(space.robi add robi (Oval new))
(space sleep 500)
(space.robi.robi setColor yellow)
(space sleep 500)
(space.robi.robi setDim 300 300)
```

Le résultat de l'exécution est le suivant :

![Exécution de l'exercice 4.3](/exercice_4_3.gif)

## Exercice 4.4 : Création et exécution de scripts

### Exercice 4.4.1 : Les scripts

Désormais, les Références embarquent la possibilité de créer, de supprimer et d'exécuter des scripts.

Afin de mettre en place ces possibilitées, les classes AddScript, DelScript et RunScript ont été ajoutées, un HashMap de commande a été ajoutée dans la classe Reference et le méthode run a été modifiée.

La méthode AddScript rajoute une commande RunScript, possédant une ExprList en attribut de classe, représentant le script avc ses paramètres.

La méthode DelScript supprime simplement le script du HashMap de script de la Reference. C'est là tout l'intérêt de ce HashMap : cela évite de donner la possibilitée à l'utilisateur de supprimer des commandes primitives.

La méthode RunScript modifie les paramètres par les valeurs saisies par l'utilisateur, pui exécute les expressions une par une.

Enfin, La modification de la méthode run de la classe Reference permet de tenter d'exécuter un script si aucune commande n'a primitive ne correspond au nom de commande saisie par l'utilisateur.

Les principales difficultées que j'ai rencontré était de modifier les paramètres par les valeurs saisies par l'utilisateur, ainsi que d'accéder à la référence en cours à l'aide de l'interpréteur. Dans ce but, Les Références connaissent désormais leur nom et leur environnement parent.

### Exercice 4.4.2 : La commande Clear

La commande clear a été implémentée, permettant de vider un élément de ses éléments enfants, ainsi que son environnement de ses références.

Une classe Clear a été ajoutée et une méthode clear a été rajoutée

La difficultée ici était de parcourir le HashMap de l'environnement tout en supprimant les éléments sans provoquer de ConcurrentModificationException.

Le script exécuté dans l'exercice 4.4 est le suivant :

```
(space sleep 1000)
(space setDim 1000 1000)
(space sleep 500)
( space addScript empty ( ( self ) ( self clear ) ) )
(space sleep 500)
(space add robi (Rect new))
(space sleep 500)
(space add gif (Image new nyan_cat.gif))
(space sleep 500)
(space.gif translate 100 100)
(space sleep 500)
(space empty)
(space sleep 500)
( space addScript addImage ( ( self filename ) (self add im ( Image new filename ) ) ) )
(space sleep 500)
( space addImage nyan_cat.gif) )
(space sleep 500)
(space clear)
(space sleep 500)
( space add robi (Rect new ) )
(space sleep 500)
( space.robi addScript addRect ( ( self name w c ) ( self add name ( Rect new ) ) ( self.name setColor c ) ( self.name setDim w w ) ) )
Le script addRect a bien été ajouté
(space sleep 500)
( space.robi addRect mySquare 30 yellow )
```

Le résultat de l'exécution est le suivant :

![Exécution de l'exercice 4.4](/exercice_4_4.gif)

### Bonus : Lecture de gifs animés

Désormais, les images au format .gif sont animées. Dans ce but, la classe GImage implémente désormais l'interface ImageObserver, permettant de passer cette classe en paramètre de la méthode drawImage de Graphics2D, et redéfinie la méthode imageUpdate de cette interface, permettant de détecter une mise à jour de cette image à l'aide d'un thread et la repeint donc à chaque mise à jour.

La manière d'obtenir le lien du fichier a également été modifiée dans la classe NewImage. En effet, il semble qu'avec la méthode read de la classe ImageIO, cela ne fonctionne pas. Je n'ai cependant pas trouvé plus d'explication à ce sujet.

Le résultat est le suivant :

![Exécution de l'exercice gif](/exercice_gif.gif)

## Tests

Des classes de tests dans les différents exercices ont été mises en places afin de simplifier ces derniers.

# Conclusion

Ce projet m'a permis de mieux comprendre comment structurer un projet. En effet, l'implémentation de l'interface Command à grandement simplifier le projet.

De plus, le fait que les references contiennent leur propres environnement a grandement simplifié la dernière étape de ce projet sur la partie de la suppression de scripts.

En effet, quand une référence est détruite et que celle-ci possédait des références enfant, les scripts de ses enfants dispaissent avec eux.
