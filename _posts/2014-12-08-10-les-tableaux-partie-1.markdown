---
layout: post
title: 10 - Les tableaux Partie 1 - Initiation à Ruby
date: 2014-12-08 08:30
author: jeremy
published: true
categories: [Initiation à Ruby]
---

On démarre cette nouvelle semaine avec un cours composé éssentiellement de fonctions sur les tableaux.
###Construction
     Commençons directement par la création d'un tableau très simple :
```ruby
puts [1, 2, 3, 4, 5].inspect
#=> [1, 2, 3, 4, 5]

puts Array.new(5, "Hello World")
#=> Hello World
#=> Hello World
#=> Hello World
#=> Hello World
#=> Hello World
```
<!--break-->
     La première méthode est la plus basique que l'on peux trouver pour créer un tableau et l'afficher avec la fonction inspect. Rien de sorcier ici, il suffit de reproduire la syntaxe basique, il faut savoir qu'on peux aussi mettre des chaînes de caractères à l'intérieur.
     La seconde méthode entre dans un contexte plus compliqué puisque on crée un tableau en “mode” objet. Vous voyez d'ailleurs que la syntaxe est même différente au niveau du tableau puisque il n'y a plus de crochets mais des parenthèses. Ici, le 5 correspond à la taille de mon tableau. Je lui demande donc de créer un tableau avec 5 éléments qui sont des chaînes de caractères. A savoir aussi que cette méthode ne prend en argument uniquement un INT, d'où le 5 et en paramètre un seul et unique élément.
     On peux aussi créer un tableau de cette manière.
```ruby
puts Array.new(["Hello", "World"])
#=> Hello
#=> World
```

     Et aussi avec un bloc d'instruction en paramètre. L'utilité reste encore un peu floue pour moi donc je ne ferais pas de théories farfelues quant à son utilisation mais j'imagine qu'en entrant un bloc d'instruction on doit pouvoir faire beaucoup de choses (Are you kidding ?).
```ruby
puts Array.new(5){ |i| i * 3 }
#=> 0
#=> 3
#=> 6
#=> 9
#=> 12
```

     On peux aussi créer un tableau en plusieurs fois :
```ruby
arr = []
arr[0] = 1
arr[1] = 5
arr[2] = "Hello world"
puts arr.inspect

#=> [1, 5, "Hello World"]
```

     On peux donc imaginer commencer un tableau en début de code et le finir dans une autre partie de l'application.

###Opérateurs
     Peux t-on concaténer deux tableau ? Bien sûr ! C'est aussi facile que de concaténer deux chaînes de caractères.

```ruby
arr = [1, 2, 3]
arr1 = ["Soleil"]

puts(arr + arr1).inspect
#=> [1, 2, 3, "Soleil"]

arr += arr1
puts arr.inspect
#=> [1, 2, 3, "Soleil"]
```

     On peux directement les concaténer dans le puts, ou bien faire comme si c'était un ajout de variables avec : arr += arr1.
     Et donc on peux aussi enlever des éléments par rapport à un autre tableau ? Oui !! C'est presque plus simple que concaténer, il suffit de changer le + par un - !

```ruby
arr = [1, 2, 3]
arr1= [2]

puts (arr - arr1).inspect
#=> [1, 3]

arr -= arr1
puts arr.inspect
#=> [1, 3]
```

     On peux même concaténer de façon plus simple, décidément, tout est allégé en Ruby …

```ruby
arr = [1, 2, 3]
arr<<4

puts arr.inspect
#=> [1, 2, 3, 4]
```

     Il est aussi possible d'additioner deux tableaux sans laisser de doublons, ou même garder uniquement les éléments présents dans les deux tableaux. Et ceci aves des opérateurs déjà bien connus.
```ruby
arr = [1, 2, 3]
arr2 = [1, 2, 3, 4, 5]

arr3 = arr & arr2
puts arr3.inspect
#=> [1, 2, 3]

arr4 = arr | arr2
puts arr4.inspect
#=> [1, 2, 3, 4, 5]
```
     Mais si on ne veux pas concaténer les tableaux et simplement les comparer, il existe aussi un opérateur. On peux faire pleins de choses avec les tableaux, je vous l'avais dis.
```ruby
arr = [1, 2, 3]
arr2 = [1, 2, 3, 4, 5]
arr3 = [1, 2, 3]

puts arr == arr2
#=> false

puts arr == arr3
#=> true
```
     Ici on compare les tableau arr et arr2 qui sont différents, le retour est donc false, en revanche, lors du deuxième test, on compare arr et arr3 qui sont identiques, et le retour est true.
     Et c'est pas fini, on peux aussi multiplier les éléments d'un tableau ! Regardez :

```ruby
arr = [1, 2, 3]

arr*=2
puts arr.inspect
#=> [1, 2, 3, 1, 2, 3]
```
