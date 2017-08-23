---
layout: post
title: 17 – Exceptions Partie 4/5 – Initiation à Ruby
date: 2015-01-14 09:12
author: jeremy
published: true
categories: [Initiation à Ruby]
---
###Double raise !




```ruby
class Person
  attr_accessor :existing
end
person = Person.new

class TestError
  def hello(person)
    if (person.nil?)
      raise("Person is empty !")
    end
    if (person.existing)
      raise("Already registered !")
    end
  end
end
person.existing = true
begin
  test = TestError.new
  test.hello(person)
rescue Exception => e
  puts "Fatal error, computer exploding ! Error type : #{e.message}"
end
#SORTIE : Fatal error, computer exploding ! Error type : Already registered !
```
<!--break-->

Ne prenez pas trop garde à la deuxième ligne, demain sortira un cours sur les accesseurs, à ce moment vous comprendrez.
Dans cet exemple j'ai rajouté une exception. Rien de compliqué, il suffit de faire comme la première fois mais ... Une deuxième fois. Ici j'ai affiché le message avec **#{e.message}** donc tout s'affiche comme il faut. Si maintenant je veux faire **#{e.class}**, j'aurais toujours le même retour, à savoir : **RuntimeError**. C'est un problème puisque je ne peux plus différencier mes deux erreurs. Solution ?
Donner un autre nom à **RuntimeError**.


```ruby
class Existing < RuntimeError
end
```

Pour cela il suffit de créer une nouvelle classe qui sera fille de **RuntimeError**.
Puis d'indique dans le **raise** le nouveau nom de l'exception.
.

```ruby
if (person.existing)
      raise(Existing ,"Already registered !")
    end
```

**Attention ici a bien mettre une majuscule car il s'agit d'un nom de classe !**
On pourrait aussi rajouter un bloc **rescue** pour changer :


```ruby
begin
  test = TestError.new
  test.hello(person)
  rescue Existing => existing
    puts "This account is Already registered !"
  rescue Exception => e
    puts "Fatal error, computer exploding ! Error type : #{e.class}"
end
#SORTIE : This account is Already registered !
```

Mon nouveau bloc **rescue** demande que lorsqu'il y a une exception de classe **Existing**, ma classe personnalisée, il renvoie *This account is Already registered !*.
**Attention encore une fois, ici l'ordre des *****rescue *****est très important puisque si je les aurais inversé, le bloc que je viens d'ajouter aurait été ignoré car Ruby cherche le premier *****rescue***** compatible. Hors le deuxième est compatible lui aussi !**
