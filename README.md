# DÉVELOPPEMENT D’UN LANGAGE SPÉCIFIQUE POUR DES ANIMATIONS GRAPHIQUES SIMPLES

#### Auteur : Clément Stoliaroff

L'objectif de ce projet était de développer un interpreteur de commandes pour des éléments graphiques

--------

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

## Exercice 4.2 : Ajout et suppression dynamique d’éléments graphiques

Lors de cet exercice, les commades AddElement et DelElement ont été implémentées, permettant d'ajouter et de supprimer des rectangles, des cercles, des images et des labels dans l'environnement pricipal.

Ceux-ci peuvent être manipulé de la même manière que le carré robi, précédemment présent dans l'environnement.

J'ai rencontré des problèmes de compréhensions lors de cet exercice. Notamment de la commande AddElement et des classes NewElement, NewImage et NewString.

## Exercice 4.3 : Ajouter des éléments à des conteneurs

Cet exercice a permis d'ajouter des éléments graphiques à l'intérieur d'autres éléments graphiques.


Cette possibilité a cependant été enlevée des ovals en raison de problème de conteneur graphique (les éléments sortaient du cercle).

La solution choisie pour mettre en place cette possibilité est l'ajout d'un environnement dans la référence de l'élément parent afin de contenir les éléments enfant.

Lors de la création d'un élément, on lui attribut un nouvel environnement enfant.

Désormais, la référence space est contenu dans un environnement, permettant de l'appeler et contient elle-même un environnement permettant d'y disposer les éléments.

Enfin, lors de l'appel à l'interpréteur, celui-ci utilise la notation pointée, en partant de l'environnement passé en paramètre pour accéder au dernier environnement désigné.

J'ai rencontré des problèmes au niveau de la gestion des environnement.

En effet, au départ, j'ajoutais toutes les références dans le même environnement avec la notation pointée pour nommage et pour la commande DelElement, je supprimais la référence en utilisant la méthode removeIf de la classe Map.

## Exercice 4.4 : Création et exécution de scripts

