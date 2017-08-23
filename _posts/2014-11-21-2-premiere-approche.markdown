---
layout: post
title: 2 - Première approche
date: 2014-11-21 09:52
author: jeremy
published: true
categories: [Initiation à Ruby]
---
#### **Hello World**
Comme vous vous en doutez maintenant on peux afficher notre "Hello World" avec puts. On peux aussi l'afficher avec print mais à la différence de puts, il ne fait pas de retour à la ligne en fin de chaîne.

```
  puts "Hello World"

  print "Hello World"
  print "Hello World"

  #=> Hello World
  #=> Hello WorldHello World
```
<!--break-->
#### **Les objets**
En ruby, c'est très simple, tout, absolument tout est objet. Un nombre, une chaine de caractère, rien qu'écrire "Hello" c'est créer un objet. Mais si c'est objet, on peux leur affecter une méthode ?
Oui, exemple :
```ruby
  puts "Hello World".capitalize
  #=> HELLO WORLD
  puts 4.next
  #=> 5
  puts "Hello".concat(" World")
  #=> Hello World
```


#### **Les variables**
Section assez courte, explication en image.
```ruby
  a = true
  b = "Hello world"
  c = 5

  a, b, c = true, "Hello world", 5
  #=> a = true
  #=> b = "Hello world"
  a, b = b, a
  #=> a = "Hello world"
  #=> b = true
```
