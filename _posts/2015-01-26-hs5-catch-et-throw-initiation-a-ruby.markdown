---
layout: post
title: HS5 – Catch et Throw – Initiation à Ruby
date: 2015-01-26 08:00
author: jeremy
published: true
categories: [En passant, Hors série]
---
On va revenir un peu en arrière pour expliquer une fonction que l'on a pas vu. Vous allez voir que c'est simple. Cette fonction est peut-être connue des plus vieux Rubyistes mais dans le cas où certains n'auraient pas la moindre connaissance de cette dernière, j'ai eu l'idée d'en faire un petit Hors série. C'est parti.

###Catch et Throw
Cette fonction très simple pourrait être comparée à **while** puisqu'elle permet de créer des boucles.
Voilà son fonctionnement :


```ruby
catch (:fin) do
  i = 1
  while (true)
    puts i
    i += 1
throw :fin if i == 6
    end
end
puts "Fin"
```
<!--break-->

Oui, c'est aussi simple que cela. Le bloc **catch** est en réalité un bloc d'instruction qui contiendra toutes les instructions à réaliser tant que le **throw** n'est pas invoqué. Le **:fin** prends ça place ici pour indiquer en quelques sorte le nom du **throw**, en faisant cela, on indique quel **catch** s'arrêtera à ce moment là.
Il faut aussi savoir que l'instruction **throw** n'as pas besoin de se situer dans la même méthode. Je suppose que sa principale utilité vient de là.
À demain !
