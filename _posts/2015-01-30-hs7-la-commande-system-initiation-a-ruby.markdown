---
layout: post
title: HS7 - La commande system - Initiation à Ruby
date: 2015-01-30 08:17
author: jeremy
published: true
categories: [En passant, Hors série]
---
Il se peut que vous ayez besoin d'utiliser une ligne de commande dans votre programme. Dans ce cas là, une solution existe !




```ruby
puts "Fin de commande : #{$?}" if system "cmd.exe /C dir"

result = `cmd.exe /C dir`
puts result
```
<!--break-->

Vous connaissez la commande **dir** sur Windows ? C'est l'équivalent de **ls** sous Linux. Elle retourne tout le contenu du dossier dans le quel on est.
intéressons nous d'abord à la première commande, la raison de notre présence ici, la méthode **system**. Cette méthode prend en argument une chaîne de caractère correspondant à une ligne de commande et retourne **true** si tout s'est bien passé et **false** si il y a eu une erreur. La variable **$?** contient la valeur de sortie.
En revanche, il n'est pas possible de récupérer le contenu de la variable directement à partir de **$?**.
Il faudra donc passer par cette deuxième commande, et se servir de : `
A demain !
