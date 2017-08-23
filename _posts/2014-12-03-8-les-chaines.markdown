---
layout: post
title: 8 - Les chaînes - Initiation à Ruby
date: 2014-12-03 08:34
author: jeremy
published: true
categories: [Initiation à Ruby]
---
###!!! Ce post contient des spoilers sur la saison 1 de Game of Thrones !!!
     Arrête d'écrire pour le lendemain, t'es en retard à chaque fois sur tes vannes...

     En rassemblant en moyenne 18,4 millions de téléspéctateurs, la série est devenue la plus populaire, et tout ça en 4 saison, espérons que je fasse de même avec ce blog.

     Mais sujet légèrement plus barbant avouez le, puisque on continue notre folle aventure autour de Ruby et aujourd'hui on parlera des chaînes. Puisque j'en ai acheté une jolie paire pour ma voiture pour cet hiver... Non, arrête.
<!--break-->

     Ok donc les chaînes, on en a déja parlé très brièvement mais sous leur forme la plus simple puisque aujourd'hui on les abordera façon objet. Etant donné que tout est objet en Ruby, vous allez en manger des objets... On n'est pas là pour plaisanter !

###Ecriture
     Petit rappel, en Ruby, tout est objet, et les chaînes en font partie, une chaîne est donc un objet de classe “String” et un ensemble de caractères.

     Aller on commence tout de suite.

```ruby
  #encoding : utf-8

  # Theon Greyjoy à Robb Stark qui va partir en guerre :
  puts "Tu as ... \n peur ?"
  puts "\tIl semblerait."
  puts 'C\'est bien.'
  puts "\\ Pourquoi est-ce bien \x3F \\"

  puts <<FIN
  Ça veut dire que tu n'es pas bête.
  FIN
```

* Ligne 4 - `\n` qui effectue un retour à la ligne.
* Ligne 5 - `\t` qui insère une tabulation.
* Ligne 7 - `\\` double anti-slash qui insère un , vous l'aurez compris, il faut échapper l'anti-slash.
* Ligne 7 - `\x3F` insère un “?”. La syntaxe est comme suit : xHH où HH signifie hexadécimal, on pourra donc insérer un caractère sous sa forme hexadécimale.
* Ligne 9 - `<<FIN` indique à puts que la fin de la chaîne se fera lorsque je l'indiquerais avec le mot FIN. Ici on a pas besoin de mettre des apostrophes ou des guillemets. Remarque : l'éditeur me colore la moitié tel une chaîne de caractère après l'apostrophe mais il s'exécute correctement.
* Ligne 10 – Avec cette syntaxe on a pas besoin non plus d'échapper l'apostrophe.
* Ligne 11 – On indique à puts que la chaîne est terminée.

###Opérateurs
     On aime les images chez Unruby, pourquoi s'en priver ?

```ruby
  #encoding : utf-8

  puts "L'abeille coule\n" * 10
  puts "Tous ceux qui ne sont pas nous ..." + "sont nos ennemis."
  puts "Audacieuse mesure Messire" << "tout autant qu'admirable" << "mais est-il sage d'aller tirer la queue du Lion " << 63
```

     J'aurais eu du mal de répéter 10 fois la phrase “L'abeille coule” mais j'y suis arrivé avec l'opérateur * . J'ai juste rajouté un `\n` pour que le retour soit plus esthetique.

     La concaténation quant à elle s'éffectue avec l'opérateur +. Très basique.

     L'opérateur << permet lui aussi de concaténer des chaînes et même de rajouter un numéro de caractère, ici 63 en décimal qui vaut “?”

###Fonctions de lecture
     La fonction count a pour but de compter les occurences de la lettre que vous rentrez en paramètre.
```ruby
  #encoding : utf-8

  # Tyrion Lannister :
  puts "La seule différence entre nous et les sauvageons, c'est que quand le mur a été érigé, nos ancêtres ont eu la bonne fortune de se trouver du bon côté.".count('e')

  # Tyrion Lannister quittant Châteaunoir :
  puts "Entre le froid et moi l'un de nous est de trop, et lui ne semble pas décidé à s'en aller.".count("^o")

  # Ned Stark à Jaime :
  puts "Je ne combat pas dans les tournois parce que quand je combat un homme pour de vrai, je ne veux pas qu'il sache ce que je sais faire.".count("ou")

  # Robert Barathéon :
  puts "Lancell, par les dieux quel prénom réellement stupide. Lancell Lannister. Qui t'a appelé ainsi ? Je ne sais quel débile mental atteint de bégaiement.".count("a-c")
```

     On ajoutera ^ pour qu'il compte toutes les lettres sauf celle entrée en paramètre. On rentrera deux caractères à rechercher et count se chargera de compter combien d'occurence de chaque lettre est présente dans la chaîne.

Enfin, on pourra utiliser une intervale pour rechercher tous les caractères se situant dans celle-ci.

```ruby
  #encoding : utf-8

  puts "À notre prochaine rencontre, nous parlerons de ta mère.".empty?
  puts "".empty?

  puts "Ned Stark".include?("Stark")
  puts "Ned Stark est mort ?".include? ("mort")

  puts "Jon Snow".length
```

     On terminera ici pour les fonctions de lecture avec .empty? Qui indique si la chaîne est vide ou non, include qui vérifie la présence d'une chaîne dans une autre, et enfin length qui est assez similaire à count, qui compte combien de caracères sont présents dans la chaîne.

###Les fonctions d'écriture

```ruby
  #encoding : utf-8

  puts "cerSEi lannIster".capitalize
  #=> Cersei lannister

  puts "[" + "Daenerys".center(20, "*") + "]"
  #=> [******Daenerys******]

  puts "Eddard Stark".chomp("Stark")
  #=> Eddard

  puts "Jon Snow".crypt("hg")
  #=> hg7m2ILVsBe1E
```

     On trouvera ici plusieurs fonctions, dont :

* `.capitalize` qui converti la première lettre de la chaîne en majuscule et les autres en minuscule.
* center qui servira à définir une taille à la chaîne de caractère et qui ajoutera ce que l'on rentre en paramètre et le nombre de fois que l'on veut.
* `.chomp` qui supprimera la chaîne rentrée en paramètre dans la chaîne sélectionnée.
* `.crypt` qui, vous l'aurez compris, crypte la chaîne. On peux rentrer deux caractères en paramètre pour différer la forme cryptée. Il n'existe pas de fonction pour décripter, cela pourrait servir à stocker un mot de passe d'inscription pour, par la suite pouvoir le comparer avec la forme cryptée de celui rentré par l'utilisateur lors de la connexion.

```ruby
  #encoding : utf-8

  puts "Quelle superbe armure. Pas la moindre éraflure.".delete("e")
  #=> Qull suprb armur. Pas la moindr éraflur.

  puts "Je sais. Les gens cherchent à m'atteindre depuis des années mais aucun d'eux n'a jamais réussi.".delete("^e")
  #=> eeeeeeeeeee

  puts "Vous avez bien choisi vos adversaires alors.".delete("ea")
  #=> Vous vz bin choisi vos dvrsirs lors.

  puts "J'ai un don pour ça.".delete("a-d")
  #=> J'i un on pour ç.
```

     On retrouvera quasiment la même syntaxe que pour la fonction count pour la fonction delete ici.

```ruby
  #encoding : utf-8

  puts "Theon Greyjoy".downcase
  #=> theon Greyjoy

  puts "Robb Stark".upcase
  #=> ROBB STARK

  puts "    Lord  Baelish".strip
  #=> Lord Baelish

  puts "Hellooooooo".squeeze("o")
  #=> Hello

  puts "Hello world".tr('o', '0')
  #=> Hell0 W0rld
```

     Plusieurs nouvelles commandes ici, dont :

* `.downcase` : qui converti en minuscule TOUS les caractères.
* `.upcase` : qui converti en majuscule TOUS les caractères.
* `.strip` : qui supprime les espaces blancs, on peux également supprimer ceux de gauche avec lstrip et ceux de droite avec rstrip.
* `.reverse` : qui inverse l'ordre de la chaîne de caractère.
* `.squeeze` : qui supprime les ocurrences successives d'un même caractère, si on ne rentre pas de paramètre il supprime tous les caractères qui se succèdent.
* `.tr` : qui échange une lettre passée en paramètre par un autre entrée elle aussi en paramètre.

Bonne journée !!
