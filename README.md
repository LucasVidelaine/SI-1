# DÉVELOPPEMENT D’UN LANGAGE SPÉCIFIQUE POUR DES ANIMATIONS GRAPHIQUES SIMPLES

#### Auteur : Clément Stoliaroff

L'objectif de ce projet était de développer un interpreteur de commandes pour des éléments graphiques

--------

* [Exercice 1 - Prise en main de la couche graphique](#exercice-1--prise-en-main-de-la-couche-graphique)

* [Exercice 2 : Première version d’un interpréteur de script](#exercice-2--Première-version-dun-interpréteur-de-script)

  * [Exercice 2.1 : Script de configuration](#exercice-21--script-de-configuration)
  
  * [Exercice 2.2 : Script d’animation](#exercice-22--script-danimation)

----------------

# Exercice 1 : Prise en main de la couche graphique

L'objectif de cet exercice était de programmer le déplacement de carré, appelé robi, d'un bord à l'autre tout en changeant de couleur aléatoirement.

La seule difficulté lors de cette première étape était la découverte du projet.

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
