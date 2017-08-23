---
layout: post
title: HS6 - Quelle heure est-il aujourd'hui ? - Initiation à Ruby
date: 2015-01-28 08:00
author: jeremy
published: true
categories: [En passant, Hors série]
---
<a href="http://www.ruby-doc.org/core-2.2.0/Time.html">Time</a> is an abstraction of dates and times. <a href="http://www.ruby-doc.org/core-2.2.0/Time.html">Time</a> is stored internally as the number of seconds with fraction since the <em>Epoch</em>, January 1, 1970 00:00 UTC.
Voilà ce que nous apprend la documentation officielle. Ce qui serait en français :
La classe **Time** est une représentation de dates et heures. La classe **Time** stocke en interne le nombre de secondes et de microsecondes depuis le 1 Janvier 1970 00:00 UTC.


###
###
###Time
La classe **Time** dispose de tout un tas de fonctions, j'en afficherait quelques unes ici, mais vous les retrouverez toutes dans un lien menant à la doc plus bas.
**.new**

```ruby
t = Time.new
```
<!--break-->

C'est le constructeur, sans argument, il fait référence à la date et heure actuelle. A noter que la fonction **.now** fait exactement la même chose.
**.day, .month, .hour, .min, .sec**.

```ruby
t = Time.new
puts t.day
#Sortie : 27
puts t.month
#Sortie : 1
puts t.hour
#Sortie : 7
puts t.min
#Sortie : 20
puts t.sec
#Sortie : 17
```

Affiche le jour du mois. Le numéro du mois. L'heure. Les minutes. Et les secondes.
Vous pourrez donc retrouver le reste des fonctions disponibles sur la documentation : <a href="http://www.ruby-doc.org/core-2.2.0/Time.html">http://www.ruby-doc.org/core-2.2.0/Time.html</a>
Pensez à y aller régulièrement dès que vous découvrez une nouvelle classe ou nouvelle méthode pour savoir à quoi ça correspond ou à quoi ça sert. Elle est particulièrement bien écrite et peut se révéler très utile.
À demain !
