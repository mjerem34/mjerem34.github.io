---
layout: post
title: 17 - Exceptions Partie 1/5 - Initiation à Ruby
date: 2015-01-08 08:00
author: jeremy
published: true
categories: [Initiation à Ruby]
---
Il se peut que l'exécution de votre code retourne des erreurs, ces erreurs peuvent être de toutes sortes, allant d'un simple problème d'accès à un fichier, à un problème d'accès une base de données.
Nous allons voir ensemble, les blocs d'exécutions mis à notre disposition pour gérer ces erreurs.


###A moins que.
On va revenir avec du code un peu plus léger aujourd'hui avec ceci :

<!--break-->

```ruby
class TestError
  def hello(person)
    puts "Hello #{person}"
    #SORTIE : Hello
    if (person.nil?)
      raise
    end
  end
end
test = TestError.new
test.hello(nil)
#SORTIE : exceptions.rb:6:in `hello': unhandled exception
#SORTIE : from exceptions.rb:11:in `<main>'
```


Pour bien comprendre ce code on commencera par la fin, lors de la création d'un objet **nil**. C'est ici que tout le code prends son sens. Revenons au début, je crée une simple classe contenant une méthode qui prendra quelque chose en argument, comprenez bien que cela peux arriver si il vous manque une donnée à un endroit précis. Je demande donc a la méthode **hello** d'afficher *Hello "person" * sauf qu'ici **person** vaut justement **nil**, la sortie sera donc simplement *Hello*.
Pour éviter ça on peut simplement se servir de **if** en le combinant à **raise** et **.nil?**.
Vous connaissez **if**. Pour rappel **.nil?** Sert à vérifier si l'argument vaut **nil**. L'inconnu ici c'est **raise**, il suffit de regarder ce que j'ai en sortie pour savoir ce qu'il fait. Voyons les sorties de plus près :


```ruby
#SORTIE : exceptions.rb:6:in `hello': unhandled exception
#SORTIE : from exceptions.rb:11:in `<main>'
```

On peux voir qu'en ligne 6 il y a un problème. *Unhandled exception* qui signifie *exception non gérée* fait référence à **raise** présent en ligne 6. Il nous retourne une erreur en nous signalant ce que l'ont voulait. On lui a demandé de sortir une erreur si **person** vaut **nil** et il l'a fait, tout simplement. La deuxième ligne quant à elle correspond à la ligne où l'exécution s'est arrêtée et à cause de quoi l'exécution se bloque.
