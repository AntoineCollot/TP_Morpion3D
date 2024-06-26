﻿# TP Morpion 3D
Le projet et les scripts doivent être autant que possible maintenue propres et bien rangés. Les scripts déjà présents ne doivent pas être modifiés à moins de l'être demandé dans une question.

On veut réaliser un jeu de Morpion, mais en 3D et à potentielement plus que 2 joueurs. Les joueurs jouent un jeton chacun leur tour. On ne peut pas viser le centre initialement, il faut d'abords qu'un joueur fasse un "trou" sur un bords en plaçant un jeton.

![alt text](Morpion3D.gif "Demo")

## 1 - Camera

*Dans un script __RotatePlayCube__*

1. Faire en sorte que l'on puisse faire tourner le cube de jeu selon l'axe vertical à l'aide des flèches horizontales du clavier.

*Dans un script __RotateCamera__*

2. Faire en sorte que l'on puisse faire tourner la camera autour du cube de jeu selon l'axe horizontal (de haut en bas) à l'aide des flèches verticales du clavier.
3. Limiter la rotation à maximum 45 degrés vers le haut et vers le bas.

## 2 - Visée

*Dans un script __PlayerAim__*

Chacune des cellules composant le cube de jeu est un GameObject possédant un BoxCollider et un composant issue du script __PlayCell__.
Le script __PlayCell__ contient notamment les coordonées de la cellule, ainsi que plusieures méthodes publiques. 

1. Détecter quelle cellule est survolée par la souris, et accéder à son composant PlayCell.
2. Si une nouvelle cellule est survolée, appeler la méthode __OnHoverEnter__ sur celle-ci et __OnHoverExit__ sur l'ancienne.
3. Lors d'un clique de la souris, afficher un message dans la console donnant les coordonnées de la cellule cliquée.

## 3 - Système de jeu
Le script __Player__ contient une classe C# (ce n'est pas un composant car pas d'héritage de MonoBehaviour). Il possède des données liées à la couleur et au jeton d'un joueur.

*Dans un script __GameManager__*

1. Créer un tableau de joueurs publique et le paramétrer dans l'éditeur pour au moins 2 joueurs.
2. Pour remplir le champ tokenPrefab, créer un prefab de jeton pour chaque joueur à l'aide d'une sphère. Dupliquer le matérial TokenPlayer autant de fois que nescessaire et les assigner à chaque jeton.
3. Paramètrer une couleur pour chaque joueur, en paramétrant la couleur du jeton et la couleur dans le tableau de joueurs. Penser à bien configurer l'alpha de la couleur du joueur (à 0% de base, on recommande ~30%).
4. Créer une fonction __PlayInCell__ prennant en entrée une cellule *PlayCell*. Elle doit permettre de jouer un jeton dans une cellule, donc pour cela:
	1. Instantier une instance du prefab token du joueur actuel à la position de la cellule.
	2. A l'aide de la méthode appropriée de PlayCell, assigner le jeton fraichement instancié à la cellule.
5. Appeler PlayInCell lors du clique de la souris dans __PlayerAim__.
6. Créer une fonction qui permette de passer au joueur suivant, l'appeler à la fin de PlayInCell.
	* Ajouter la ligne suivante à la fonction, qui permet d'afficher la couleur du joueur actuel.
	```
	Shader.SetGlobalColor("_CurrentPlayerColor", players[currentPlayer].color);
	```

A ce stade, le jeu devrait être jouable correctement.

## 4 - Gagner

*Dans la classe __Player__ à compléter*

1. Noter dans une liste les coups joués par le joueur.
2. On doit trouver un moyen de détécter un alignement de 3 jetons pour déterminer si le joueur à gagné. Pour cela, trouver un algorithme qui permette de détecter si il y a un alignement dans les coups joués par le joueur (idéalement pas seulement en rapport avec le dernier coup joué). Expliquer cet algo dans un readme. On priviligiera  l'élégance et la simplicité de l'algo aux performances.
3. Implémenter cet algo dans une méthode qui retournera un booléen.
4. Appeler cette méthode à la fin de __PlayInCell__, afficher un message dans la console lorsqu'un joueur gagne.

## 5 - Polish
1. Ajouter un effet de particules au placement d'un jeton. Le but ici est de montrer la maitrise du système de particules, la qualité de l'effet est importante.

## Rendu (compte dans le barème)

* __Par mail : antoine.collot@live.com__
* Object du mail: ESME TPMorpion3D Groupe [NOM1]-[NOM2]-[NOM3]
* Le code source du projet, donc un zip contenant les dossiers *"Assets"* et *"ProjectSettings"* et *"Packages"* de votre projet Unity. Par exemple avec https://wetransfer.com/ ou lien du projet sur github.
* Un gif ou une courte vidéo du projet pour montrer les différentes features en état de marche.
* Un readme avec la question 4-2 mais aussi auquel vous pouvez ajouter des eventuelles informations utiles.
