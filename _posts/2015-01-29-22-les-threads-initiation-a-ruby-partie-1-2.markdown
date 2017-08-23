---
layout: post
title: 22 - Les threads - Initiation à Ruby Partie 1 / 2
date: 2015-01-29 09:28
author: jeremy
published: true
categories: [Initiation à Ruby]
---
###Les threads, c'est quoi ?
Pour faire un résumé simple et compréhensible par tous, imaginez un programme Ruby qui gère l'interface et qui dispose d'un bouton. Lorsque vous cliquez sur ce bouton, vous déclenchez une action. Et bien, sans **thread**, le programme se concentrera sur cette action et ignorera l'interface, ce qui la bloquera et empèchera toute autre action en même temps. A bas le multi-tâche !!!!



Un **thread** se présente donc sous forme de bloc d'instruction. Vu qu'il va exécuter une ou plusieurs instructions en parallèle, ça paraît logique .(?)

###Les threads, comment on fait ?
Le **thread **est un élément de classe **Thread**. Ruby permet de le démarrer de 3 différentes façons.
<!--break-->


```ruby
thnew = Thread.new {puts "I'm a Thread created by the .new method"}
thstart = Thread.start  {puts "I'm a Thread created by the .start method"}
thfork = Thread.fork {puts "I'm a Thread created by the .fork method"}

puts thnew.join
puts thstart.join
puts thfork.join

#Sortie : I'm a Thread created by the .new method
#Sortie : I'm a Thread created by the .start method
#Sortie : I'm a Thread created by the .fork method
```


Chaque **thread** agi indépendemment l'un de l'autre.
La deuxième partie de cet article viendra par la suite, on parlera des** semaphores** et de la classe **Mutex**. En attendant, vous pourrez trouvez plus d'informations sur les **Threads** dans la documentation, n'hésitez pas à y aller, elle est vraiment complète.
