---
layout: post
title: HS - L'affectation conditionnelle - Initiation à Ruby
date: 2014-12-11 08:30
author: jeremy
published: true
categories: [affectation conditionnelle, Hors série]
---
     Petit hors série aujourd'hui très très léger. Je fais ça pour ne pas entamer la programmation orientée objet en fin de semaine. (Oups, spoil)
     Aujourd'hui donc, l'affectation conditionnelle !
     L'affectation conditionnelle permet, comme son nom l'indique, d'affecter une valeur à une variable uniquement si la variable est vide.


     Voilà la syntaxe :

<!--break-->

```ruby

#encoding : utf-8
the_witcher_3 = nil
puts the_witcher_3
#Sortie :

the_witcher_3 ||= "Sortie 24 février 2014"
puts the_witcher_3
#Sortie : Sortie 24 février 2014

the_witcher_3 ||= "Sortie toujours prévue le 24 février 2014"
puts the_witcher_3
#Sortie : Sortie 24 février 2014

the_witcher_3 = "Repoussé au 19 mai"
puts the_witcher_3
#Sortie : Repoussé au 19 mai

```

Petite nouveauté ici donc, l'opérateur OU( || ). Ici, je tente plusieurs fois d'affecter une valeur à ma variable, la première tentative fonctionne puisque ma variable est vide. La deuxième ne fonctionne pas puisque la variable n'est pas vide et la dernière fonctionne puisque j'ai enlevé l'opérateur ( || ). Vous l'aurez donc compris, The Witcher 3 est bien repoussé au 19 mai prochain... A demain ! Et préparez vous pour la POO de lundi !
