---
layout: post
title: 5 - Les boucles - Initiation à Ruby
date: 2014-11-27 09:30
author: jeremy
published: true
categories: [Initiation à Ruby]
---

### WHILE
     Certains d'entre vous la connaissent très bien. En français, WHILE signifie TANT QUE.

     On peux alors imaginer une boucle qui fonctionnerais de la sorte : TANT QUE la condition n'est pas remplie, alors écrire ....

     Imaginez une boucle qui afficherait les 10 premiers nombres. Voilà comment ça se passe ...
<!--break-->
```ruby
i = 0

while i < 10
	puts i
	i += 1
end
#=> 0
#=> 1
#=> 2
#=> 3
#=> 4
#=> 5
#=> 6
#=> 7
#=> 8
#=> 9
```

     Une seule notion peut être particulière ici, c'est la ligne 5 : " i+=1 ". C'est en fait la forme abrégée de " i = i +1 ". Cela sert tout simplement à rajouter 1 au compteur i pour que la boucle puisse avancer. Sans ça, i, que l'on appelle aussi incrémenteur, resterait à 0 et la boucle serait infinie. Attention aux boucles infinies, dans le meilleur des cas vous obtiendrez une erreur et dans le pire des cas ... Brrrr, je n'ose pas y penser...

### UNTIL
     Voilà une autre commande aussi simple que while mais qui peux être très utile dans certains cas : UNTIL, qui signifie " jusqu'a ". Comme WHILE, on peux maintenant imaginer une boucle :
```ruby
i = 0

until i > 10
	puts i
	i += 1
end
#=> 0
#=> 1
#=> 2
#=> 3
#=> 4
#=> 5
#=> 6
#=> 7
#=> 8
#=> 9
```
     On a donc, ligne 3, notre boucle : jusqu’à ce que i soit supérieur à 10, écrire i. En incrémentant i on s'assure donc que dès lorsque i est supérieur à 10, la boucle s'arrête.

### LOOP ... BREAK
     Attention, cette boucle est infinie, ne pas laisser à la portée des enfants...
```ruby
i = 0
loop do

	puts i
	i += 1
	if i == 10
		break
	end
end
#=> 0
#=> 1
#=> 2
#=> 3
#=> 4
#=> 5
#=> 6
#=> 7
#=> 8
#=> 9
#=> 10

```
     Aller c'est parti !

* Ligne 1 – Déclaration de la variable d'incrémentation, ou, compteur.
* Ligne 3 – Ouverture de la boucle LOOP avec DO
* Ligne 5 – On écrit la valeur de I
* Ligne 6 – On incrémente I pour éviter une fois de plus les boucles infinies
* Ligne 7 – La partie intéressante, on ouvre un IF qui se chargera de vérifier la valeur de I, et si I vaut moins de 10 la boucle est cassée par BREAK sinon la boucle continue jusqu'à ce que I soit égal à 10.


### FOR … IN
     Cette commande est très simple à comprendre, je ne m'attarderais pas dessus. Voilà son fonctionnement :
```ruby
for i in 0..10
	puts i
end
#=> 0
#=> 1
#=> 2
#=> 3
#=> 4
#=> 5
#=> 6
#=> 7
#=> 8
#=> 9

```
Vous allez me dire, on dirait une forme simple de while … Oui et non, on peux s'en servir pour parcourir des tableaux très simplement. Mais nous verrons tout ça dans un prochain chapitre.

### NEXT
     Cette commande sert simplement à passer une itération pendant la boucle. Une image vaut mieux que 10 mots :
```ruby
for i in 0..10
	if i == 5
		next
	end
	puts i
end
#=> 0
#=> 1
#=> 2
#=> 3
#=> 4
#=> 6
#=> 7
#=> 8
#=> 9

```

     On retrouve notre boucle FOR IN comme précédemment mais avec une particularité. La commande NEXT, ici elle est paramétrée de sorte à ne pas faire le PUTS I lorsque I vaut 5.
