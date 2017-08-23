---
layout: post
title: 3.1 - Les variables
date: 2014-11-25 11:50
author: jeremy
published: true
categories: [Initiation à Ruby]
---
### Retour sur les variables.
    Vous avez pu voir dans mes précédents articles que j'utilise des noms assez étranges quand je nomme des variables. Des noms avec des tirets avant, des tirets au millieu, sans tiret, avec majuscule, sans majuscule.

### Pourquoi ?
    Imaginez que chacun d'entre nous écrivait du Ruby comme cela lui chante, ce serai N'import'Nawak ! Une convention a donc été mise en place pour garder l'ordre dans toutes ces lignes de codes. Et dans cette convention, on retrouve les noms de variables.
    Tous les exemples que je vous ai présentés sont conformes à la convention. Il en va de même du nom des méthodes. Petit rappel des formes acceptées.
<!--break-->

```ruby
  #////Conforme////#
  firstVar = "Avec une minuscule au début et une majuscule au second mot"
  second_var = "Sans majuscule et avec un tiret entre les mots"
  var4 = "Sans majuscule et avec un chiffre à la fin"

  #////Non-Conforme////#
  1var = "Avec un chiffre au début"

  #////A ne pas utiliser////#
  =begin  break elsif module  retry unless
  =end  case  end next  return  until
  BEGIN class ensure  nil self  when
  END def false not super while
  alias defined?  for or  then  yield
  and do  if  redo  true
  begin else  in  rescue  undef

```

Les variables déclarées de cette façon sont des variables dites "locales". C'est à dire qu'elles sont dépendantes du bloc où elles ont été créées, à l'exterieur de ce bloc ces variables disparaissent. Un solution pour remédier à cela : les variables globales, que j'expliquerais dans un prochain billet.

### Les constantes.
    Voilà un autre type de variables. Celles ci, appellées constantes sont particulières puisque lorsque vous les avez déclarées, vous ne pouvez plus changer leur valeur.

```ruby
  PI = 3.14159265359

  PI = 18.5
  #=> Erreur car constante non modifiable
```
