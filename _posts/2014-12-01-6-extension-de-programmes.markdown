---
layout: post
title: 6 - Extension de programmes - Initiation à Ruby
date: 2014-12-01 08:30
author: jeremy
published: true
categories: [Initiation à Ruby]
---
### REQUIRE
     Qui a dit qu'on avait besoin d'un seul fichier pour créer un programme, un site web ou un jeu ?
     Dans la simple logique des choses, une commande a été mise en place pour permettre la liaison de plusieurs fichiers, qui, plus tard formeront le programme. Alors c'est par exemple le cas de Ruby on Rails qui est un framework et qu'il faut donc relier à notre fichier à nous. Passons au code.
<!--break-->
```ruby
#require1.rb

def wozniak (namewoz)

  puts "Hi, my name is #{namewoz} !"

end
```
```ruby
#require2.rb

require "require1.rb"


def jobs (namejobs)

  puts "Hi, my name is #{namejobs} !"
  puts "I am pleased to introduce you Steve !"

  wozniak ("Steve")

end

jobs("Steve")
```

     Voilà nos deux fichiers, à gauche require1.rb (ce qui pourrait être notre framework), où on stocke notre première méthode et à droite le fichier "exécutif" où l'on retrouve notre REQUIRE.

     Revenons a notre premier fichier, vous voyez que je crée une méthode appelée "wozniak", rien de bien sorcier. C'est dans notre "require2.rb" que ça se corse. Ligne 3 nous avons notre require qui pointe donc vers le premier fichier "require1.rb".

     J'en profite pour créer une seconde méthode appelée "jobs" pour mettre en place mon programme et dans cette méthode, à la ligne 11, j'appelle celle du premier fichier et je passe une chaîne de caractère en paramètre.

     J'exécute enfin ma méthode «  jobs « , qui, si je m'explique bien, ira cherche la méthode "wozniak"  dans le premier fichier.
