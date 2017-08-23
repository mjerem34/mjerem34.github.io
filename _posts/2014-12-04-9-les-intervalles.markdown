---
layout: post
title: 9 - Les intervalles - Initiation à Ruby
date: 2014-12-04 08:36
author: jeremy
published: true
categories: [Initiation à Ruby]
---
Un article un peu allégé aujourd'hui pour compenser avec celui d'hier. On va simplement traiter les intervalles. Ça ne fera pas mal à la tête.


###Des chiffres et des lettres
     On a déjà vu légèrement les intervalles mais on va les aborder aujourd'hui un peu plus en détail. Si vous vous rappellez des boucles, vous vous rappellerez aussi de la syntaxe. Une intervalle est constituée d'un début et d'une fin, que l'on nomera d et f. En Ruby, ça se présente comme ça : “d..f” ou même “d...f”. Vous verez la différence dans un moment.
     Une intervalle étant un objet de classe Range, elle dispose de fonctions. En voici quelques unes :
<!--break-->
```ruby
  puts (1..9).to_a
  #=> 1 2 3 4 5 6 7 8 9

  puts (1...9).to_a
  #=> 1 2 3 4 5 6 7 8

  puts ((1..9).each{|i|
    print (i.to_s + " ")
  })
  #=> 1 2 3 4 5 6 7 8 9

  puts((1..9).step(2){|i|
    print(i.to_s + " ")
  })
  #=> 1 3 5 7 9 1..9
  ```
     Vous vous demanderez sans doute ce qu'est ce .to_a, il se charge en fait de créer un tableau à partir de cette intervalle, puts se charge ensuite de nous afficher ce tableau. On voit aussi la différence entre les deux méthodes.
     Il me semble qu'on avait éffleuré le each, il se charge lui aussi de parcourir l'intervalle en donnant une instruction à un bloc, ici le bloc se charge d'afficher l'intervalle en une seule ligne avec un espace entre chaque caractère. On reviendra plus en détail sur les blocs d'instructions dans un prochain article car cette notion reste légèrement floue pour moi.
     On pourrait assimiler step à each mais on verra que step propose plus de fonctionnalités, comme ici passer la chaîne de 2 en 2. Si on ne rentre pas de paramètre, il se contente de parcourir la chaîne comme each.
     Vous devez vous en douter, on peux aussi faire ça avec des lettres. Voyez par vous même :
```ruby
  puts ("a".."f").to_a
  #=> a b c d e f
```
###Utilisation
     Vous l'aurez compris, on ne va pas se servir des intervalles pour afficher les chiffres de 1 à 5.
     On utilisera donc les intervalles pour faire des boucles rapides ou même des case.
```ruby
for i in 1..7
  puts "Hello world"
end
#=> Hello worldHello worldHello worldHello worldHello worldHello worldHello world
a = 4
case a
when 1..4
  puts "Premier cas"
when 5..10
  puts "Second cas"
end
#=> Premier cas
```

     Ici je me suis contenté d'afficher des chaînes de caractères mais plus tard cela peut être utile pour vérifier des conditions sur un site.
