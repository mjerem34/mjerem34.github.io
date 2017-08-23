---
layout: post
title: 20 - Vous pensiez connaître puts ? – Initiation à Ruby
date: 2015-01-23 08:00
author: jeremy
published: true
categories: [Initiation à Ruby]
---
Vous vous rappelez de cette commande qui affiche du texte en sortie ? Oui, **puts**. Pour un bref rappel, cette commande sert essentiellement à afficher : du texte, plusieurs chaînes d'un seul coup, des chiffres, des variables, et j'en passe...

 En réalité ce n'est pas puts qui fait tout ça, il utilise un objet dédié à cette fonctionnalité **$stdout**. Cet objet n'est autre qu'une variable, mais vu que tout est objet, bla bla bla ...
Il existe d'ailleurs une autre variable lui ressemblant : **$stderr**.
Voyons ces deux cas.


```ruby
puts "Hello World"

$stdout << "Hi World"

$stderr << "Hlleo Wjlrd"

#Sortie : Hello World
#Sortie : Hi World
#Sortie : Hlleo Wjlrd
```
<!--break-->

Les ex-C++ reconnaîtront cette partie. Le symbole **<** est très utilisé en C++, ici on s'en sert pour stocker notre chaîne de caractères dans la variable.
Mais **puts** n'est pas la seule fonction à pouvoir afficher quelque chose en sortie et à fonctionner de cette façon. Print se voit légèrement différente à ceci près qu'elle n'utilise pas la même variable pour stocker la sortie (**$_** au lieu de** $stdout**) et qu'elle ne fait pas de saut à la ligne.


```ruby
$\ = "\nHlleo Wjlrd\n"
$_ = "Hi World"
print

#Sortie : Hi World
#Sortie : Hlleo Wjlrd
```

Comme je vous l'avais dit, voyez en ligne 2 le fameux **$_** qui prends comme valeur :** Hi World**, puis la ligne juste après qui affiche ce que cette variable contient avec un **print** simple.
En passant vous avez dû apercevoir : **$\** à la ligne 1. Cette variable se chargera de contenir ce qui sera affiché en fin de **$_**, par défaut, la valeur de** $\** vaut **nil**.

###Bienvenue en C++ !
Retour en C++, certains doivent être content ! Pour les autres, sachez qu'il existe une alternative à **print**. Qui est ... **printf** ! Ok, c'est pas très original mais c'est comme ça, remarque, c'est plus facile à retenir !
**Printf** fonctionne d'une façon très différente de **print**.


```ruby
printf "%s %d\n", "Hello", 20
#Sortie : Hello 20
```

La commande **printf** prend en premier argument les formats dont est composé le **print**. C'est à dire que si je veux afficher, comme ici, une chaîne de caractère puis un nombre je dois mettre l'option **%s** pour la chaîne de caractères puis **%d** pour le nombre.
Voici la liste des options disponibles :

**b** : Indique qu'un nombre binaire est présent.
**c** : Un caractère.
**d** : Un entier.
**e** : Un décimal avec exposant.
**f** : Un décimal auquel on peux définir combien de nombres après la virgule.
**p** : Utilise la méthode inspect de l'objet.
**s** : Indique qu'une chaîne de caractère est présente.
**u** : Un entier non signé.
**x** : Résultat en héxadécimal.
Exemple avec **f** :

```ruby
printf "%1.2f\n", 3.141592653859793
#Sortie : 3.14
```

###Entrées
On n’a pas beaucoup vu cette commande il me semble donc je vais le re-présenter.
La commande **gets** permet de récupérer une entrée utilisateur que l'on stockera, optionnellement, dans une variable pour s'en servir ensuite. Tout comme **print**, cette commande stocke par défaut la valeur entrée dans la variable **$_** mais aussi dans **$stdin**. Ce qui rend l'affichage immédiat de l'entrée utilisateur possible de la sorte :


```ruby
print while gets
```

Ou bien pour vérifier une entrée :

```ruby
print while gets =~ /q/
```

Cette commande affichera l'entrée uniquement si l'utilisateur entre le caractère "**q**".
Je suppose qu'on pourrait s'en servir pour afficher une erreur tant que, lors de l'inscription, l'utilisateur entre une adresse email d'un mauvais format, ou que son mot de passe ne correspond aux pré requis.
