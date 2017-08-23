---
layout: post
title: 14 - La classe Object - Initiation à Ruby
date: 2014-12-17 08:30
author: jeremy
published: true
categories: [Initiation à Ruby]
---
En Ruby tout n'est pas seulement objet, tout est Object. Un peu plus de détails sur cette classe mère des autres classes mères.

Cet article présentera beaucoup de méthodes qui sont accessibles grâce à cette méthode mère. Mais avant tout, expliquons cette classe Object.

Il s'agit simplement d'une classe qui est au dessus des autres, toutes les classes que nous créons seront par conséquent des classes filles à celle-ci. Et donc ça change quoi ? Pour l'instant pas grand chose à part que par conséquent, les classes que nous créons disposent de méthodes supplémentaires et que l'on à pas besoin de récrire.

Démonstration avec un exemple tout simple.

<!--break-->

```ruby
#encoding : utf-8
class Persons
  def initialize(name, surname, year, birth)
      @name = name
      @surname = surname
      @year = year
      @birth = birth
  end
  def presentation
    puts "Hi, my name is #{@name} #{@surname}, i have #{@year} year old and i was born in #{@birth} !"
  end
end
homer = Persons.new("Simpson", "Homer", 40, 1989)
homer_copy = Persons.new("Simpson", "Homer", 40, 1989)
marge = Persons.new("Simpson", "Marge", 40, 1989)
bart = Persons.new("Simpson", "Bart", 10, 1989)
lisa = Persons.new("Simpson", "Lisa", 8, 1989)
maggie = Persons.new("Simpson", "Maggie", 2, 1989)
ogier = Persons.new("Ogier", "Sébastien", 30, 1983)

puts homer == homer_copy
#Sortie : false
marge_copy = marge
puts marge == marge_copy
#Sortie : true
```


On part sur une base très simple encore ici en déclarant 7 objets dont, vous aurez remarqué, un, qui est juste une copie, comme son nom l'indique.

L'opérateur "==" se charge de tester si nos objets sont identiques ou non. Combiné à "puts", on peux lui faire écrire en sortie "true" ou "false".

Non je ne me suis pas trompé. On a bien false en sortie. Laissez moi vous expliquer.

En fait, "==" ne teste pas directement si les paramètres des objets sont identiques. Il vérifie si les deux objets représentent un même objet en mémoire.

C'est pourquoi le deuxième test renvoie "true", puisqu'il s'agit d'une véritable copie. On pourrait comparer cela à un "raccourci pour aller à". Donc, que ce soit "marge" ou "marge_copy", les deux amènent à la même valeur en mémoire.

###Object_id



```ruby
puts homer.object_id
#Sortie : 16200860
puts marge.object_id
#Sortie : 16200740
marge_copy = marge
puts marge_copy.object_id
#Sortie : 16200740

puts homer.equal?(homer_copy)
#Sortie : false
puts homer_copy.object_id
#Sortie : 16200780
puts marge.equal?(marge_copy)
#Sortie : true
```


"object_id", cette méthode nous permet de, vous l'aurez deviné, connaître l'identifiant de l'objet voulu. Je m'en sert ici pour connaître l'identifiant de l'objet "homer" et "homer_copy", qui rappelons le, ne sont pas une même instance d'un objet. Et bien on en à la preuve ici avec la méthode "object_id" qui montre clairement que les deux objets ont des valeurs différentes.

Quant à "marge" et "marge_copy", "object_id" prouve une nouvelle fois que les deux objets n'en sont en fait qu'un seul. D'où le terme de "raccourci pour aller à".

La méthode "equal?" quant à elle vérifie si les identifiants des deux objets en paramètres sont identiques. On pourrait presque la comparer à l'opérateur "==".
###Display


```ruby
puts homer.inspect
#Sortie : #<Persons:0x000000019c3528 @name="Simpson", @surname="Homer", @year=40, @birth=1989>
puts marge.display
#Sortie : #<Persons:0x000000025ae540>

  def to_s
    "#{@name}, #{@surname}, #{@year}, #{@birth}"
  end
bart.display
#Sortie : Simpson, Bart, 10, 1989
```


Vous vous rappelez de "inspect". Voilà comment ça se présente avec un objet. On peux faire quasiment la même chose en moins bien (tout dépend de l'utilité) avec la méthode "display". Enfin, la méthode "to_s" quant à elle permet de réordonner tout le contenu de "display" de façon à écrire ce que l'on veux dans l'ordre qu'on le veux.

Cet article était un très bref aperçu des possibilités offertes par la classe Object, nous en apprendrons plus tout au long de notre parcours.
