---
layout: post
title: 17 – Exceptions Partie 5/5 – Initiation à Ruby
date: 2015-01-19 08:01
author: jeremy
published: true
categories: [Initiation à Ruby]
---
###Personnalisation
Comme si cela ne suffisait pas, il y a encore un moyen pour écrire un message personnalisé. Cette fois ci on va surcharger le **message** de l'exception.

 Comme ceci :



```ruby
class Existing < RuntimeError
  def initialize(person)
    @person = person
  end
  def message
    puts "The user #{@person} is already registered !"
  end
end
```
<!--break-->


Lorsqu'on reviens à notre création de classe **Existing**, il suffit de recréer une méthode **message**, pour la surcharger, nous aurons ainsi en sortie **The user #<Person:0x0000000177a3e8> is already registered ! **



```ruby
class TestError
  def hello(person)
    if (person.nil?)
      raise("Person is empty !")
    end
    if (person.existing)
      raise(Existing.new(person))
    end
  end
end
```


Attention, il faudra ensuite, lors de la déclaration de **raise**, lui indiquer de stocker l'erreur à l'endroit voulu.

###Obligation
Cela peux être très ennuyant que l'exécution se stoppe en cas d'erreur, et on aura souvent besoin d'une roue de secours. Dans ces cas on utilisera **ensure** qui se traduirait ici par *dans tous les cas faire*. Pourquoi ? Parce que même lorsqu'il n'y a pas d'erreur, le **ensure** s'exécute. Exemple :



```ruby
begin
  test = TestError.new
  test.hello(person)
  rescue Exception => e
    puts "Fatal error, computer exploding ! Error type : #{e.message}"
  ensure
    puts "But you can connect !"
end
```


Le bloc **ensure** se place juste après les **rescue**, suivi de l'instruction à exécuter.
