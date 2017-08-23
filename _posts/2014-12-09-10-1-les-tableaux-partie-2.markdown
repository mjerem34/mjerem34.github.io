---
layout: post
title: 10.1 - Les tableaux Partie 2 - Initiation à Ruby
date: 2014-12-09 08:29
author: jeremy
published: True
categories: [Initiation à Ruby]
---
###Fonctions
     On commence directement avec la première fonction :
```ruby
arr = [
  ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger"],
  ["Simpson", "Homer", "Marge", "Bart", "Lisa", "Maggie"]
]
puts arr.assoc("Simpson").inspect
#=> ["Simpson", "Homer", "Marge", "Bart", "Lisa", "Maggie"]
```
<!--break-->
     Ici, la fonction assoc ne trouve son utilité uniquement avec les sous-tableaux. Elle permet de sélectionner le sous-tableau contenant notre paramètre en premier élément. Ici je passe en paramètre "Simpson", assoc va donc chercher le sous-tableau dont le premier élément est "Simpson".
```ruby
arr = ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger"]
arr1 = arr.collect{|i| i.capitalize}

puts arr1.inspect
#=> ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger"]

arr.clear
puts arr
#=>
```

     Ici j'ai supprimé le deuxième sous-tableau pour ne garder que celui là et le transformer en tableau simple, j'en ai profité aussi pour enlever la première lettre majuscule. Je me sert de la fonction collect pour transformer la première minuscule en majuscule, et ça grâce à un bloc d'instruction prenant en paramètre la fonction capitalize que vous connaissez déjà. Lorsque j'affiche le contenu de mon tableau, je m'apperçois que la fonction a fait son travail. Je finis par nettoyer le premier tableau avec la fonction clear parce que, attention, la fonction collect nécéssite la création d'un autre tableau!
```ruby
arr = ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger"]
arr1 = [nil, "Bart", nil, "Marge", nil, "Maggie"]

arr.concat(arr1)
puts arr.inspect
#=> ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger", nil, "Bart", nil, "Marge", nil, "Maggie"]

puts arr.compact.inspect
#=> ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger", "Bart", "Marge", "Maggie"]
```

     Vous n'avez jamais entendu parlé de nil ? Si on pourrais donner une définition a nil ce serait "rien". Donc dans mon arr1 j'ai 3 éléments vides, sans aucune valeur.
     La première fonction, concat, permet de concaténer deux tableaux, un peu comme le "+". Il faut juste sélèctionner notre premier tableau et puis entrer le second en paramètre.
     La deuxième fonction, elle, se charge de supprimer les nil, ou éléments vides.

```ruby
arr = ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger"]

arr.delete("Francine"){
  puts "Item not found"
}
puts arr.inspect
#=> ["Smith", "Stan", "Hayley", "Steve", "Roger"]

arr.delete_at(3){
  puts "Item not found"
}
puts arr.inspect
#=> ["Smith", "Stan", "Hayley", "Roger"]

arr.delete_if{|i| i == "Smith"}
puts arr.inspect
#=> ["Stan", "Hayley", "Steve", "Roger"]
```

     La fonction delete permet de supprimer l'élément entré en paramètre, ici je demande qu'il supprime l'élément "Francine" et s'il ne le trouve pas, il exécute puts qui me previendra alors qu'il n'a pas trouvé l'élément.
     Mais on peux faire mieux que cela, puisque au cas ou on ne se rappelle pas de ce qui est présent dans le tableau, on peux supprimer ce qu'on veux avec l'index. Ici je demande à delete_at de supprimer l'élément numéro 4. Je ne me suis pas trompé, un tableau à un index débutant à 0, en écrivant 3 ici je demande donc de supprimer le 4 ème élément.
     Enfin, on peux supprimer un élément suivant une condition, ici je demande a delete_if de supprimer un élément lorsqu'il le rencontre. I représente l'élément dans le tableau, la fonction if parcours tous les éléments jusqu'a la fin et si la condition est vrai, il supprime l'élément. Ici j'ai fait en sorte qu'il supprime "Smith" quand il le rencontre. Fonctionnement : if commence à parcourir le tableau, il tombe sur "Smith", il le transfère dans le i et teste la condition, elle vaut bien vrai, alors il supprime l'élément. If continue à parcourir le tableau, il tombe sur "Stan" qui, lorsqu'il est transféré à i n'est pas égal à "Smith", la condition vaut alors false, "Stan" n'est pas supprimé.

```ruby
arr = ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger"]

puts arr.empty?
#=> false

puts arr.each{|i| i.replace("Simpson")}.inspect
#=> ["Simpson", "Simpson", "Simpson", "Simpson", "Simpson", "Simpson"]

arr.clear
puts arr
#=>

puts arr.empty?
#=> true
```
     Vous vous rappellez surêment de la fonction empty?, et bien elle fonctionne aussi avec les tableaux.
     Avant de commencer, je teste si mon tableau est vide avec la fonction empty? Que vous connaissez déjà.
     La fonction each se charge elle de parcourir simplement le tableau voulu et prend en paramètre un bloc d'instruction, ici j'ai demandé que tous les éléments soient remplacés par un autre. Il faut bien comprendre que dans ce cas ci, i devient l'élément du tableau qui est en train d'être parcouru.
     Je vide mon tableau avec clear, je l'affiche, il est bien vide. Je vérifie avec la fonction empty?, résulat, true, mon tableau est vide.
```ruby
arr = ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger"]

puts arr.fill("Simpson").inspect
#=> ["Simpson", "Simpson", "Simpson", "Simpson", "Simpson", "Simpson"]

puts arr.fill("Smith", 1, 3).inspect
#=> ["Simpson", "Smith", "Smith", "Smith", "Simpson", "Simpson"]
```
     La fonction fill permet de remplacer des éléments dans un array par un et un seul autre entré en paramètre. Dans la deuxième option on peux voir que j'ai rajouté des éléments, il s'agit en fait d'index. Le chiffre 1 signifie qu'il faut commencer à remplacer à l'index 1, donc au deuxième élément. Le chiffre 3 signifie qu'il faut remplacer 3 éléments en tout. Voilà pourquoi j'obtiens 1 fois "Simpson", 3 fois "Smith" et 2 fois "Simpson".
     On pourrait également entrer un bloc d'instruction en paramètre qui j'imagine pourrai multiplier, diviser, ou autre les éléments d'un array.
```ruby
arr = [["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger"], ["Simpson", "Homer", "Marge", "Bart", "Lisa", "Maggie"]]

puts arr.inspect
#=> [["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger"], ["Simpson", "Homer", "Marge", "Bart", "Lisa", "Maggie"]]

arr1 = arr.flatten
puts arr1.inspect
#=> ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger", "Simpson", "Homer", "Marge", "Bart", "Lisa", "Maggie"]]

puts arr1.index("Bart")
#=> 8
puts arr.include?("Lisa")
#=> true
```
     Reprenons nos deux sous-tableaux, on les affiche, le résultat est correct. Maintenant imaginons que je veux les rassembler en un seul et unique tableau, j'utilise pour cela la fonction flatten.
     Je veux ensuite connaître l'index de l'élément "Bart" dans le tableau, je peux le faire avec la fonction index, attention, cette fonction ne marche pas pour des sous-tableaux.
     Pour finir je veux vérifier la présence d'un élément dans le tableau, j'utilise la fonction include?, que l'on connais déjà très bien.
```ruby
arr = ["Smith", "Stan"]
arr.insert(2, "Francine")
#=> ["Smith", "Stan", "Francine"]

arr.push("Hayley", "Steve", "Roger", "Francine")
puts arr.inspect
#=> ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger", "Francine"]

arr.unshift("Roger")
puts arr.inspect
#=> ["Roger", "Smith", "Stan", "Francine", "Hayley", "Steve", "Roger", "Francine"]

arr.shift
#=> "Roger"
puts arr.inspect
#=> ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger", "Francine"]

arr = arr.uniq
puts arr.inspect
#=> ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger"]

a = arr.shift
puts a
#=> ["Smith"]
```
     Là ça commence à devenir dur hein ? Ce ne sont que des fonctions, notez les dans un bloc note et sachez qu'elles existent au moment où vous en avez besoin.
     On commence avec un petit tableau contenant uniquement 2 éléments. Je veux rajouter tous les autres. Je commence par la fonction insert qui prends en paramètre la position à laquelle je veux que mon élément soit placé, viens ensuite l'élément en question.
     Push, cette fonction se charge elle d'insérer les éléments mais uniquement à la fin du tableau. Oui j'ai entré 2 fois "Francine", attendez.
     Unshift lui, fais l'inverse de push puisqu'il ajoute le ou les éléments uniquement au début du tableau. Je sais j'ai remis "roger" ! Attendez.
     Si il y a unshift c'est qu'il doit y avoir shift non ? Et bien oui ! Shift quand à lui permet de supprimer uniquement le premier élément du tableau (il retourne l'élément "shifté").
     Et pour finir pour l'instant, on peux supprimer les doublons dans un tableau avec la fonction uniq.
```ruby
arr = ["Smith", "Stan", "Francine", "Hayley", "Steve", "Roger"]

puts arr.length
#=> 6

puts arr.join("-")
#=> Smith-Stan-Francine-Hayley-Steve-Roger

puts arr.sort.inspect
#=> ["Francine", "Hayley", "Roger", "Smith", "Stan", "Steve"]

puts arr.values_at(2, 4, 5).inspect
#=> ["Francine", "Steve", "Roger"]
```
     Bien évidemment on peux afficher combien d'éléments sont présents dans un array, pour cela on utilisera la fonction length, attention car cette fonction compte aussi les nil.
     La fonction join quant à elle permet d'afficher tous les éléments du tableau en une seule chaîne, on peux entrer un argument en paramètre qui agira comme séparateur.
     On peux aussi les classer, avec la fonction sort.
     Ou bien récupérer les valeurs d'éléments de l'index entré en paramètre avec values_at.
```ruby
arr = ["Smith", "Smith", "Smith", "Smith"]
arr1 = ["Stan", "Francine", "Hayley", "Steve", "Roger"]

arr2 = arr1.zip(arr)
puts arr2.inspect
#=> [["Stan", "Smith"], ["Francine", "Smith"], ["Hayley", "Smith"], ["Steve", "Smith"], ["Roger", nil]]
```
     Pour finir, on apprendra comment créer deux sous-tableaux à partir de deux tableaux différents. Et on fera ça avec la fonction zip.
A demain !
