---
layout: post
title: HS3 – Les accesseurs– Initiation à Ruby
date: 2015-01-15 08:39
author: jeremy
published: true
categories: [En passant, Hors série]
---
Notion assez importante en POO, j'ai omis de vous en parler au tout début mais maintenant qu'on en a besoin, c'est un passage obligé.
Avant tout chose il faut savoir que les attributs des objets, c'est à dire : **test.color** . **Color** étant l'attribut, il n'est pas accessible directement en passant par un objet.


<!--break-->

###Une méthode
Exemple :

```ruby
class Person
  def initialize(nom)
    @nom = nom
  end
end
user1 = Person.new("Jeremy")
puts user1.nom
#SORTIE : accessor.rb:9:in `<main>': undefined method `nom' for #<Person:0x00000000c69760 @nom="Jeremy"> (NoMethodError)
```

Lorsqu'on fait puts user1.nom, on se retrouve, non pas avec le bon résultat de notre demande, mais avec une erreur qui signale que la méthode nom n'est pas définie. Pour que **@nom** soit accessible comme ceci il faudrait créer une méthode qui, elle, afficherait la variable.

```ruby
class Person
  def initialize(nom)
    @nom = nom
  end
  def nom
    @nom
  end
end
user1 = Person.new("Jeremy")
puts user1.nom
#SORTIE : Jeremy
```

Dans cet essai, une fois créé la méthode nom, ma commande fonctionne et affiche ce que je souhaite.

###The accessor
Alors, bien évidemment, une solution plus simple est possible.


```ruby
class Person
  def initialize(nom)
    @nom = nom
  end
  attr_accessor :nom
end

user1 = Person.new("Jeremy")
puts user1.nom
#SORTIE : Jeremy
```

J'ai quand même pris soin d'enlever la méthode nom, que j'ai remplacé par **attr_accessor :nom**. On pourrait comparer cette commande par un **chmod**, qui vous autorise l'écriture et la lecture d'un fichier. Ici, je donne l'accès en écriture et en lecture à l'attribut nom. Attention, je précise une dernière fois, c'est un accès en écriture ET en lecture. Vous allez comprendre.

###
###The reader

```ruby
class Person
  def initialize(nom)
    @nom = nom
  end
  attr_reader :nom
end

user1 = Person.new("Jeremy")
puts user1.nom
#SORTIE : Jeremy
```

Voilà pourquoi j'ai précisé. Il existe aussi un **attr_reader** qui lui, octroie à l'objet, uniquement un accès en lecture à l'attribut. D'où le reader...

###The Lecter

```ruby
class Person
  def initialize(nom)
    @nom = nom
  end
  attr_writer :nom
end

user1 = Person.new("Jeremy")
puts user1.nom
#SORTIE : accessor.rb:9:in `<main>': undefined method `nom' for #<Person:0x00000000e5f740 @nom="Jeremy"> (NoMethodError)

user1.nom = "Robert"
class Person
  attr_accessor :nom
end
puts user1.nom
#SORTIE : Robert
```

Evidemment, il y a aussi un accesseur en écriture. **attr_writer**, rempli sa fonction et lorsque on tente de lire l'attribut, on se retrouve avec une erreur. Le fameux **undefined method**. Normal, puisque notre attribut n'est pas accessible en lecture.
Tentons de modifier l'attribut **nom**. Pas d'erreur, on peux maintenant vérifier en placant un **attr_accessor** dans notre classe **Person**, recrée pour l'occasion. On peux voir qu'on obtien bien la nouvelle valeur en sortie.
