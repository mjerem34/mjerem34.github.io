---
layout: post
title: 17 – Exceptions Partie 3/5 – Initiation à Ruby
date: 2015-01-13 08:52
author: jeremy
published: true
categories: [Initiation à Ruby]
---
### **Raise again.**
La commande **raise** possède plusieurs arguments possibles. Voici les quels :
**raise message ***"**Déclenchement d'une exception de classe ****RuntimeError**** suivie d'un message perso"*
**raise classe message ***"**Déclenchement d'une exception de classe entrée en paramètre suivie d'un message perso"*



<!--break-->

```ruby
    if (person.nil?)
      raise(RuntimeError, "Small error of nothing")
    end
  end
end
begin
  test = TestError.new
  test.hello(nil)
rescue => e
  puts "Fatal error, computer exploding ! Error type : #{e.message}"
end
#SORTIE : Fatal error, computer exploding ! Error type : Small error of nothing
```

Je n'affiche plus le début du code puisque ce n'est pas nécessaire.
Comme je l'ai dis un peu avant, **raise** dispose de plusieurs arguments que l'ont peux placer derrière. En voici un exemple. A la troisième ligne se situe notre fameux mot-clé. Il est suivi par **(RuntimeError, "Small error of nothing")**, en première partie est présent la classe de l'exception et en deuxième partie le message. Pour la petite explication, c'est **raise** qui *crée *"l'objet" erreur et c'est dans cet objet que sera stocké la classe et le message.
Rendez vous en ligne 10. On a remplacé le **e.class **par **e.message**, si vous vous rappelez bien, le premier nous donnait la classe de l'exception. Celui ci nous donnera, vous avez deviné, le message de l'exception.



###Exception faite.
Vous ne pourrez pas toujours connaître la nature de l'exception. C'est pourquoi il existe un outil pour vous l'indiquer.


```ruby
begin
  test = TestError.new
  test.hello(nil)
rescue Exception => e
  puts "Fatal error, computer exploding ! Error type : #{e.class}"
end
#SORTIE : Fatal error, computer exploding ! Error type : RuntimeError
```

**Exception** est en fait la plus haute classe des classes d'exception. Elle vous indiquera quelle est la nature de l'exception. Il convient qu'il faut nettoyer le **raise** et donc lui enlever les arguments. On ne voit pas de différence ici vu que l'erreur est la même.
