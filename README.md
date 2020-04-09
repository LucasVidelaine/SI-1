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
	
	* [Exercice 4.2 :  Ajout et suppression dynamique d’éléments graphiques]()

	* [Exercice 4.3 : Ajouter des éléments à des conteneurs]()
	
	* [Exercice 4.4 : Création et exécution de scripts]()
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

Le résultat est le suivant :

![Exécution de l'exercice 2.2](/exercice_2_2.gif)

# Exercice 3 : Introduction des commandes

Le but de cet exercice était d'améliorer la structure du programme en mettant en place un interface fonctionnelle nommée "Command", contenant une seule méthode : la méthode abstraire run(), ainsi que des classes implémentant cette interface, représentant les différentes commandes exécutables.

Cette amélioration permet en effet de simplifier l'ajout de nouvelles commandes. En effet, avant cette amélioration, il fallait ajouter le code de chaque commande dans le même fichier, alors que maintenant, il suffit de créer une nouvelle classe Command, et d'ajouter son exécution dans l'interpreteur.

Je n'ai pas non plus rencontré de difficulté particulière lors de cet exercice.

Le script que j'ai exécuté est le suivant :

```
(script
	(space sleep 20000)
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

Le résultat est le suivant :

![Exécution de l'exercice 3](/exercice_3.gif)

# Exercice 4 : Sélection et exécution des commandes

## Exercice 4.1 : Référencement des objets et enregistrement des commandes

## Exercice 4.2 : Ajout et suppression dynamique d’éléments graphiques

## Exercice 4.3 : Ajouter des éléments à des conteneurs

## Exercice 4.4 : Création et exécution de scripts
