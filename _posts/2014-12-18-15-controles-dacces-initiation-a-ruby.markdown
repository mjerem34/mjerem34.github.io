---
layout: post
title: 15 - Contrôles d'accès - Initiation à Ruby
date: 2014-12-18 08:30
author: jeremy
published: true
categories: [Initiation à Ruby]
---
On touche bientôt au but ! Rails nous voilà ! Enfin, pas encore, aujourd'hui on va parler des contrôles d'accès. C'est parti !
Ceux qui arrivent de Php connaîtrons sans doute les "private" et "public", je ne doute pas que cela doit exister dans beaucoup d'autres langages orientés objets. On verra que deux syntaxes sont possibles pour déterminer si une méthode est "privée" ou "protégée", et qu'une sera certainement plus pratique qu'une autre. Trève de bavardages !

###Décor
C'est l'anniversaire de Steven Spielberg aujourd'hui, mais ça c'est secondaire, aujourd'hui c'est surtout les accès aux méthodes qui sont de sortie.

<!--break-->

```ruby
#encoding : utf-8
class December
  private
    def methodToAccess
      "Je m'appelle Steven Spielberg et je suis né le 18 décembre !"
    end

  public
    def firstCallToMethod
      methodToAccess
    end
    private :methodToAccess
end
```


Voilà la syntaxe de "private", si vous avez de bon yeux vous avez remarqué que "private" est présent 2 fois. Et bien il s'agit en fait des 2 syntaxes différentes. Bien entendu, vous n'utiliserez pas les 2 en même temps.
La première syntaxe se présente comme suit : elle se place avant toutes les méthodes à mettre en "private" comme sur le code, il faudra par contre se servir du mot clé "public" pour délimiter les méthodes. Au cas où vous l'oublieriez, toutes les méthodes seront considérées comme "private".
La seconde syntaxe se présente plus bas comme ceci : elle se place en fin de classe, une fois toutes les méthodes énumérées. Il suffit d'écrire "private" suivit de 2 points et le nom de la méthode concernée collée aux 2 points. Si il y a plusieurs méthodes à passer en "private" elles seront simplement séparées de virgules et nous garderons les 2 points présent à chaque énumération.
La syntaxe est la même pour "protected".

###Private
Nous avons donc bloqué notre méthode "methodToAccess" avec "private". Voyons comment on peux quand même y accéder, je n'écrirais pas a nouveau la base du code, vous pourrez la retrouver plus haut. C'est parti :


```ruby
brad_pitt = December.new
puts brad_pitt.firstCallToMethod
puts brad_pitt.methodToAccess
#Sortie : Je suis né le 18 décembre !
#Sortie : private method `methodToAccess' called for #<December:0x0000000129ab48> (NoMethodError)
```


"private" permet donc de bloquer les appels a méthodes directs mais ne bloque pas les appels à méthodes d'autres méthodes. Compliqué ? Regardez le code encore une fois vous comprendrez.
J'aurai très bien pu faire ceci dans une classe fille et tout aurait fonctionné puisque, contrairement à d'autres langages, en Ruby, la méthode qui est "private" est accessible aussi depuis une classe fille.
Il en va de même pour "protected" qui fait tout à fait la même chose à ce niveau là.
Suite :


```ruby
class January < December
  def secondCallToMethod(c)
    c.methodToAccess
  end
  def thirdCallToMethod
    methodToAccess
  end
end

christina_aguilera = January.new
steven_spielberg = January.new

puts christina_aguilera.firstCallToMethod
#Sortie : Je suis né le 18 décembre !

puts christina_aguilera.thirdCallToMethod

#Sortie : Je suis né le 18 décembre !

puts christina_aguilera.secondCallToMethod(steven_spielberg)
#Sortie : `secondCallToMethod': private method `methodToAccess' called for #<January:0x00000001ae57d0> (NoMethodError)
```


J'ai créé une classe fille ici, juste pour diversifier un peu. Ici on peux voir, comme je l'ai dis précédemment que lorsque j'appelle la méthode à partir d'une classe fille, l'accès est quand même possible.
"thirdCallToMethod" est en fait une simple copie de "firstCallToMethod" mais dans la classe fille donc tout à fait logique qu'elle fonctionne elle aussi.
En revanche, là où bloque "private" c'est lors de l'appel à méthode prenant en argument un autre objet. En fait "private" n'autorise l'accès qu'a l'objet original de la demande, raison pour laquelle ça ne fonctionne pas.

###Protected
"protected" en revanche est bien moins stricte là dessus puisque, il ne bloque uniquement que les appels à la méthode qui est "protected".
Vous aurez donc compris que uniquement :


```ruby
puts brad_pitt.methodToAccess
```


sera bloquée.
Conclusion :
- Le mot-clé "private" ne bloque pas les appels de méthode à partir d'une autre méthode. Mais bloque les appels à la méthode directs ainsi que les appels à méthodes avec un autre objet que celui d'origine.
- Le mot-clé "protected" ne bloque uniquement que les appels à méthode directs.
