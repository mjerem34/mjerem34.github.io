---
layout: post
title: 7 - Les expressions régulières - Initiation à Ruby
date: 2014-12-02 09:30
author: jeremy
published: true
categories: [Initiation à Ruby]
---
     Alors que sort la première bande annonce de Star Wars chapitre 7, je m'attaque aujourd'hui non sans peine sur un des plus grands mythes des langages de développement qui saura donner du fil a retordre a n'importe quel codeur averti. Depuis toujours les expressions régulières font trembler ciel et terre avec leurs forme confuse et incompréhensible de tout néophyte.

     Mais, pourquoi on s'en sert si c'est si dur que ça ? Et bien en fait c'est très utile. Tout ce que l'on retiendra pour le moment c'est qu'on s'en servira plus tard pour vérifier une adresse d'un site web, une adresse mail ou même à s'assurer que l'entrée de l'utilisateur est ce que l'on attendais, mais les plus vieux d'entre nous pourront nous éclairer sur toute les utilisations possible.
<!--break-->

###Création
    Si vous avez suivi les articles depuis le début vous aurez sûrement retenu qu'en Ruby, tout est objet. On retrouve cette notion ici, il se trouve que même une expression régulière est un objet, et un objet de classe Regexp. Alors comment un crée cet objet. Ruby s'en charge tout seul lorsque l'on écrit l'expression sous ces formes :
```ruby
  # Première forme
  /expression_reguliere/

  # Seconde forme
  %r{expression_reguliere}
```

Alors que certains trouveront la seconde syntaxe plus simple, on utilisera ici la première.

###Langage
     Les expressions régulières sont considérées comme un langage à part entière. Et qui dit langage dit opérateurs spéciaux. Voici donc la liste des opérateurs que l'on utilisera le plus souvent..

* `*` : zéro ou plus de fois le caractère ou groupe de caractère qui précède.
* `+` : une ou plus de fois le caractère ou groupe de caractère qui précède.
* `?` : zéro ou une fois le caractère ou groupe de caractère qui précède.
* `{m,n}` : minimum m fois et maximum n fois le caractère ou groupe de caractère qui précède. Il est possible d'indiquer uniquement m.
* `(...)` : un caractère ou groupe de caractère.
* `[mno]` : un caractère dans cet ensemble entre crochets.
* `[^mno]` : tout sauf un caractère dans cet ensemble.
* `[m-o]` : un caractère dans l'intervalle de m à o.
* `n|m` : le caractère ou groupe n ou le caractère ou groupe m.
* `.` : représente n'importe quel caractère.
* `d` : un chiffre.
* `s` : un espace.
* `w` : un caractère de mot.


Voici maintenant un exemple d'expression régulière qui vérifie la syntaxe d'une adresse email :
```ruby
mail = "email@example.com"
/^[a-zA-Z0-9_-]+.?[a-zA-Z0-9_-]+@[a-zA-Z]+.[a-zA-Z]{2,3}$/.match (mail)
```

     Et ici, une expression régulière qui vérifie la présence d'un caractère dans une chaîne de caractère :

```ruby
  #!/bin/env ruby
  #encoding : utf-8

  string = "Si six scies scient six cyprès, alors combien de scies scient six cent six cyprès ?"
  puts /s/.match (string)
```

     Bon petite explication en français de ce à quoi correspond la première vérification :
     On retrouve donc notre syntaxe classique : /Expression régulière/.
Le ^ indique que notre recherche s'éffectuera dès le premier caractère.
[a-zA-A0-9_-], ce truc bizarre vérifie que notre email comporte un caractère dans ces intervalles. Comme vous le voyez, tout est collé, pas besoin de les séparer, c'est comme ça. On cherche donc un caractère de a à z ou de A à Z ou de 0 à 9 ou _ ou -.

Le . doit obligatoirement être échappé, voilà pourquoi un anti-slash est devant. On recherche ici si un point est présent ou non avec le ?

Si il y a un point on recherche à nouveau une chaîne de caractère ou un caractère dans ces intervalles.
On sait qu'un adresse email contient obligatoirement un @, on en fait donc la recherche en passant.
On répète a nouveau un caractère ou chaîne de caractère qui représenteront la première partie du nom de domaine.

Encore un point qui sépare les deux composantes du nom de domaine.
Et enfin, on cherche un “.fr”, “.com”, “.org”, etc … Il faudra donc qu'on cherche une chaîne de caractère de minimum 2 caractère et maximum 3 caractères. Vous aurez donc compris la syntaxe.

###Opérateurs
     La fonction match dispose d'un raccourci très pratique dans certains cas : =~
     Imaginez qu'on veuille vérifier une adresse email et indiquer à l'utilisateur si elle est valide ou non. Voilà comment on fera :

```ruby
  mail = "email@example.com"
  if mail =~            /^[a-zA-Z0-9_-]+\.?[a-zA-Z0-9_-]+@[a-zA-Z]+\.[a-zA-Z]{2,3}$/
    puts "Adresse email valide : " + Regexp.last_match(0)
  else
    puts "Adresse email non valide : " + Regexp.last_match(0)
  end
```

Vous remarquerez une nouveauté. Je me sert de Regexp.last_match(0) pour récupérer l'adresse email rentrée par l'utilisateur et la lui renvoyer dans le puts. Regexp est ordonné comme un tableau, voilà pourquoi on retrouve (0) à la fin. Nous en apprendrons plus sur les tableaux un peu plus tard.

N'ayez pas peur, je pense que les expressions régulières sont un langage tout à fait a part qui nécéssite    plusieurs années d'expérience pour en profiter pleinement.

A demain !

Et vous, vous avez mangé votre deuxième chocolat ?
