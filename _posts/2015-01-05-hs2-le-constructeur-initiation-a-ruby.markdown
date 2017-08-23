---
layout: post
title: HS2 - Le constructeur - Initiation à Ruby
date: 2015-01-05 08:30
author: jeremy
published: true
categories: [Hors série]
---
Le constructeur est une méthode un petit peu particulière. Elle sert à définir les paramètres nécessaires à la création d'un objet.


Je sais qu'on en a déjà parlé vaguement dans le dernier article mais je voulais approfondir le sujet comme je le ferais dans ces articles Hors Série avec plusieurs autres sujets.
Donc, on a déjà parlé de cette méthode qu'est initialize mais j'ai omis de vous présenter une fonctionnalité de celle ci.
Petit rappel, la méthode initialize se présente comme ceci :

<!--break-->

```ruby
class Person
    def initialize(nom)
        @nom = nom
    end
end
```

Ici, lorsque je crée ma méthode j'indique qu'elle prends en paramètre 1 argument. L'argument se stockera dans la variable @nom que je transfère dans la variable d'instance @nom. Un Hors série viendra pour expliquer les nouveaux types de variables.
Imaginons maintenant une méthode initialize prenant en paramètre 2 arguments de plus. Rien de bien sorcier, je les transfère eux aussi dans des variables d'instance et il suffira de les déclarer à la création de l'objet. Imaginez une dernière fois que je ne veuille pas entrer un des paramètres. Il se produira une erreur.



###Argument par défaut
Sauf si j'insère un argument par défaut lors de la déclaration de la méthode initialize.
Démonstration :


```ruby
class Person
    def initialize(nom, prenom, age = 25)
        @nom = nom
        @prenom = prenom
        @age = age
    end
    def bonjour
        puts "Hi, my name is #{@prenom} #{@nom}, #{@age} years old."
    end
end
john = Person.new("Doe", "John")
john.bonjour
#Sortie : Hi, my name is John Doe, 25 years old.
```


On a déjà vu un cas a peu près similaire dans un ancien article. C'est lors de la déclaration de mes arguments que j'indique si oui ou non ils auront une valeur par défaut.
Pour cela il suffit de l'indiquer comme si c'était une variable. En revanche, si l'on souhaite donner une valeur à @age on le fera normalement et la valeur par défaut sera remplacée par la nôtre.
