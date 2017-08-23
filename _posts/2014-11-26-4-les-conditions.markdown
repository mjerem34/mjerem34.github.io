---
layout: post
title: 4 - Les conditions - Initiation à Ruby
date: 2014-11-26 15:54
author: jeremy
published: true
categories: [Initiation à Ruby]
---
#### If / Else

    Ceux qui viennent déjà d'un autre langage de programmation connaissent sans doute les instructions conditionnelles. Dont la plus célèbre d'entre elles : If/Else.
    Nous allons donc directement commencer avec une forme abrégée de If, mais avant tout, il nous faut savoir comment on s'en sert et à quoi cela peut servir.
    Comme vous devez savoir, If vient de l'anglais qui signifie "Si" et Else qui signifie "Sinon".
    Vous devez maintenant vous douter à quoi cela peux servir. Juste un exemple très simple : la vérification d'un mot de passe de connexion à un espace utilisateur.
    Passons maintenant au concret ! La structure de If se présente comme ceci :
<!--break-->
```ruby
my_name = "Jeremy"

if my_name == "Jeremy"
	puts "Hello Jeremy !"
elsif my_name == "Georges"
	puts "Hello Georges !"
else
	puts "Hello #{my_name} !"
end
```


    Explications :

* Ligne 1 - Je déclare une variable my_name qui contient Jeremy.
* Ligne 3 - Je vérifie ensuite avec IF si elle vaut "Jeremy".
* Ligne 4 - Et si c'est le cas, j'écris "Hello Jeremy".
* Ligne 5 - Je teste si la variable ne vaut pas "Georges" avec elsif.
* Ligne 6 - Si la variable est identique à ma condition, j'écris alors "Hello Georges".
* Ligne 7 - Roue de secours, si aucune des deux conditions n'est vraie alors...
* Ligne 8 - J'ecris "Hello  #{contenu de variable my_name}".
* Ligne 9 - Fin d'IF.

#### Forme abrégée de If
    Plus j'avance, plus j'ai l'impression que le Ruby c'est en fait une grosse abréviation de tous les langages qui puissent exister. On connais cette forme de if depuis longtemps en C, et Matz à eu la très bonne idée de la faire passer du côté clair de la force. Voici la version abrégée de IF/ELSE:
```ruby
father = true
dark_vador = "Je suis ton père !"
luke = "Noooooooooooon !"

puts father ? dark_vador + " " + luke : "Luke dit : Je vais te tuer Dark Vador !"
```
    Pour ceux qui ne l'auraient pas encore compris, on réduit la commande a une seule ligne !
    Une fois mes trois variables déclarées, je fais mon test conditionnel en ligne 5.
     Ici, le "?" représente le IF, il teste ma variable father juste avant. Et si elle vaut TRUE alors elle affiche le contenu des deux variables dark_Vador et Luke. ELSE, représenté par les " : " ça affiche ma chaîne de caractère passée en paramètre.

#### UNLESS
    Y'en a qui viennent de Perl ici ? Bienvenue chez vous !
    Pour faire simple, UNLESS sert à vérifier si l'opposé vaut TRUE. Exemple :
```ruby
force = false
puts "La force est avec toi jeune rubywan !" unless force

#=> La force est avec toi jeune rubywan !
```


#### CASE
     Aller c'est bientôt fini. CASE est donc la dernière instruction conditionnelle que je présenterais.

    Voilà à quoi ça ressemble :
```ruby
myName = "Bart"

case my_name
	when "Bart"
		puts "Hi Bart!"
	when "Marge"
		puts "Hi Marge!"
	when "Lisa"
		puts "Hi Lisa!"
	when "Homer"
		puts "Hi Homer!"
	when "Maggie"
		puts "Hi Maggie!"
	else
		puts "Hi Family!"
end
```

     Chaque WHEN représente un cas de figure à tester et le ELSE (non obligatoire mais conseillé) est une roue de secours au cas où aucune des autres conditions n'est remplie.

    A vous de deviner ce que l'on obtient dans ce cas là.

    C'est fini pour aujourd'hui, n'hésitez pas a échanger vos impressions et vos avis via les commentaires. Si vous avez des conseils, ils sont les bienvenus.
