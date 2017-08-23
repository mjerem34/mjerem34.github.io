---
layout: post
title: 11 - Tables de hachage - Initiation à Ruby
date: 2014-12-10 08:30
author: jeremy
published: true
categories: [Initiation à Ruby]
---
Encore mal à la tête ? On va y aller plus doucement aujourd'hui.

Hier on parlais des des tableaux, mais dans tout ça vous avez sûrement douté des indices. Certes ce n'est pas très utile pour afficher une valeur dans un tableau. Alors comment faire autrement ? C'est ce dont on va parler aujourd'hui.


###Explications
     Une table de hachage est une sorte de tableau sauf qu'au lieu d'avoir un index classique (0, 1, 2, 3...), c'est vous qui gérez les index. Ça peut être utile pour les gros tableaux, pour s'y retrouver plus facilement.
<!--break-->

###Construction
     Voilà comment se construit une table de hachage ou tableau associatif (je vous avais dis que c'était un tableau) :
```ruby
arr = Hash.new()
arr["Gran Turismo 7"] = "Out 2016"
arr["Ralph Baer"] = "92 years R.I.P"
arr["God of War PS4"] = "Confirmed !"

puts arr.inspect
#=> {"Gran Turismo 7", "Out 2016", "Ralph Baer", "92 years R.I.P", "God of War PS4", "Confirmed !"}
```

     Oui, même une table de hachage est un objet. Je ne le répèterais jamais assez, en Ruby TOUT est objet. Donc on crée la table de hachage sous forme d'objet. On attaquera les objets très bientôt, tremblez... Mais non c'est facile la programmation orientée objet... Hum !
     Donc j'ai ajouté 3 nouvelles entrées à ce tableau associatif, la syntaxe est assez symple à assimiler, les ex-php ne se sentiront pas dépaysés. Vous savez, le plus dur ce n'est pas la syntaxe, le plus dur c'est apprendre à se servir de la syntaxe.
     Ca peux paraître lourd comme ça mais ne vous en faîtes pas, il existe un moyen un peu plus allégé pour créer des tables de hachage :
```ruby
arr = {
  "Gran Turismo 7" => "Out 2016",
  "Ralph Baer" => "92 years R.I.P",
  "God of War PS4" => "Confirmed !"
}

puts arr.inspect
#=> {"Gran Turismo 7", "Out 2016", "Ralph Baer", "92 years R.I.P", "God of War PS4", "Confirmed !"}
```


###Fonctions
     Quelques fonctions utiles :
```ruby
arr = {
  "Gran Turismo 7" => "Out 2016",
  "Ralph Baer" => "92 years R.I.P",
  "God of War PS4" => "Confirmed !"
}

arr.keys.each {|i|
  puts i
}
#=> Gran Turismo 7
#=> Ralph Baer
#=> God of War PS4
```

     Ici, la fonction *keys*, qui s'utilise dans une fonction *each* permet d'afficher, comme son nom l'indique, les clés du tableau.
     On peux faire a peut près la même chose mais cette fois ci afficher les valeurs avec la fonction *values* :
```ruby
arr = {
  "Gran Turismo 7" => "Out 2016",
  "Ralph Baer" => "92 years R.I.P",
  "God of War PS4" => "Confirmed !"
}

arr.values.each {|i|
  puts i
}
#=> Out 2016
#=> 92 years R.I.P
#=> Confirmed !
```

     On obtient donc en sortie non plus les clés mais les valeurs du tableau.
     Voici quelques fonctions supplémentaires :
```ruby
arr = {
  "Gran Turismo 7" => "Out 2016",
  "Ralph Baer" => "92 years R.I.P",
  "God of War PS4" => "Confirmed !"
}

puts arr.index("Out 2016").inspect
#=> "Gran Turismo 7"

puts arr.has_key?("Gran Turismo 7")
#=> true
puts arr.has_value?("91 years R.I.P")
#=> false
puts arr.length
#=> 3
```

     *has_key?* s'occupe de vérifier si une clé existe sous le nom entré en paramètre, ici ("Gran Turismo 7") et renvoie *true* ou *false*.
     *has_value?*, s'occupe lui de vérifier si une valeur du nom entré en paramètre est présent et renvoie true ou false.
     La fonction *length*, qu'on a déjà vu dans un autre article, s'occupe de renvoyer la longueur de ce que l'on veut. Ici je lui demande de renvoyer combien de valeurs il y a dans mon tableau. Il renvoie 3 car il n'additionne pas valeurs + clés, chaque clé et sa valeur comptent pour 1.
```ruby
arr = {
  "Gran Turismo 7" => "Out 2016",
  "Ralph Baer" => "92 years R.I.P",
  "God of War PS4" => "Confirmed !"
}

arr.each {
  |key, value|
  puts "La clé est : #{key}, la valeur est : #{value}"
}
#=> La clé est : Gran Turismo 7, la valeur est : Out 2016
#=> La clé est : Ralph Baer, la valeur est : 92 years R.I.P
#=> La clé est : God of War PS4, la valeur est : Confirmed !
```

     On peux aussi utiliser la fonction each pour, comme ici, afficher les clés et valeurs dans une chaîne de caractère mais on peux bien évidemment utiliser each autrement, avec une autre fonction par exemple. Il existe quand même des dérivés de cette fonction, comme each_key ou each_value qui permettent de prendre en paramètre uniquement la clé ou la valeur.

```ruby
arr = {
  "Gran Turismo 7" => "Out 2016",
  "Ralph Baer" => "92 years R.I.P",
  "God of War PS4" => "Confirmed !"
}
arr2 = {"Hello" => "World", "Hi" => "World"}

arr.replace(arr2)
puts arr.inspect
#=> {"Hello" => "World", "Hi" => "World"}
```

     La fonction replace, comme son nom l'indique, remplace la table voulue par la table entrée en paramètre, on peux aussi directement entrer le contenu de la nouvelle table au lieu du nom de la table.
```ruby
arr = {
  "Gran Turismo 7" => "Out 2016",
  "Ralph Baer" => "92 years R.I.P",
  "God of War PS4" => "Confirmed !"
}

arr.delete("Ralh Baer")
puts arr.inspect
#=> {"Gran Turismo 7" => "Out 2016", "God of War PS4" => "Confirmed !"}

arr.clear
puts arr.inspect
#=> {}
```

     Les deux dernières fonctions. Delete permet de supprimer la valeur qui correspond à la clé rentrée en paramètre. Et enfin la fonction clear, comme on l'a déjà vu aussi, supprime toutes les clés et valeurs associées de la table de hachage.
A demain !
