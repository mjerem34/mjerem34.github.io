---
layout: post
title: 1.1 - L'interpréteur
date: 2014-11-20 15:49
author: jeremy
published: true
categories: [Initiation à Ruby]
---

Mauvaise nouvelle pour certains, Ruby utilise beaucoup la console de commande.
L'interpréteur Ruby sert tout simplement à executer le code que vous écrivez. Une fois Ruby installé sur votre ordinateur, pour vérifier si tout s'est bien passé et que Ruby fonctionne bien, ouvrez votre shell et entrez d'utiliser la commande : **ruby -v**. Si l'installation s'est déroulée correctement, vous devriez avoir en retour **ruby x.x.x** .
Je n'afficherais ici uniquement les commandes principales, pour voir toutes celles disponibles, utilisez la commande : "**ruby -h**" .
On peux essayer une expression ruby par la commande : **ruby -e "puts 1+1"**.
<!--break-->
Autres options :

* **-c** : demande de ne vérifier uniquement la syntaxe.

* **-C** : se positionne dans un répertoire avant exécution.

* **-d** : fixe le flag $DEBUG à vrai (true) pour exécuter et débugger votre script.

* **-I** : spécifie un répertoire contenant des sources, cette commande peut être répétée plusieurs fois.

* **-r** : indique qu'une librairie est nécessaire avant exécution.

* **-S** : l'interpréteur utilise la variable d'environnement PATH pour trouver les scripts.

* **-w** : demande l'affichage des avertissements.

* **-W** : définit le niveau des avertissements souhaité (0 : aucun, 1 : moyen, 2 : fort)

#### **Ok, mais et nos fichiers .rb ?**
Il suffit de les lancer avec l'interpréteur grace a la commande : **ruby nomdefichier.rb** .
Ne pas oublier d'être dans le dossier ou le fichier est présent.

#### **C'est tout ?**
Oui, l'interpréteur est assez simple d'utilisation pour l'instant.
