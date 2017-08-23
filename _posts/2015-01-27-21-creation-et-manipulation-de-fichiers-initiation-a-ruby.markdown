---
layout: post
title: 21 – Création et Manipulation de fichiers – Initiation à Ruby
date: 2015-01-27 08:01
author: jeremy
published: true
categories: [Initiation à Ruby]
---
Comme son nom l'indique, aujourd'hui, l'article va parler de la création de fichiers, une étape assez importante puisque nous en auront besoin plus tard.
Vous verrez que c'est assez simple de créer un fichier ou un dossier en Ruby.


###
###
### **Fichier**
La création de fichier dépend de la classe **File**. C'est à dire que l'on fera appel à cette classe pour créer notre fichier. Comme ceci :


```ruby
f = File.new("C:/temp/newfile.txt", "w+")
```
<!--break-->

On crée donc notre fichier comme l'on créerait un objet contenant deux arguments. En premier lieu le chemin du fichier et en second les permissions de ce dernier. Voici les différentes permissions possibles :

*
	<li style="text-align:justify;">**r **: Lecture (mode par défaut)
	<li style="text-align:justify;">**r+ **: Lecture et écriture
	<li style="text-align:justify;">**w **: Ecriture seulement, si le fichier n'existe pas il sera créé, sinon il sera récrit.
	<li style="text-align:justify;">**w+** : Pareil à **w** mais la lecture est quand même possible.
	<li style="text-align:justify;">**a **: Pareil à **w** sauf que si le fichier existe, l'écriture se fera à la suite.
	<li style="text-align:justify;">**a+ **: Idem que **a** mais la lecture est possible.

###
###
###Lecture
La lecture d'un fichier, ici un fichier texte, peux se faire très facilement avec la fonction **gets**.


```ruby
while (f.gets)
  puts $_
end
f.close
```

Vous vous rappelez sûrement de **$_**. Pour ceux qui étaient coincés dans une caverne ces derniers jours, **$_** est une variable qui contient ce qui doit être affiché. Revoir le cours 20 Entrées et Sorties.
Il faut noter que le fichier doit être fermé avec la méthode **close** à la fin de son utilisation.
Attention, il peut y avoir une erreur lors de la lecture du fichier et à ce moment là, il ne sera pas fermé, on peut régler ce souci avec l'instruction **ensure** :


```ruby
begin
  while (f.gets)
    puts $_
  end
ensure
f.close
end
```

On peux même vérifier si notre fichier est fermé correctement comme ceci :


```ruby
if(f.closed?)
  puts "Le fichier est bien fermé"
else
  puts "Le fichier n'est pas fermé"
end
```

###
###
###Ecriture
L'écriture d'un fichier se fait de manière très simple elle aussi. On se servira de la méthode **puts**, **print** ou **printf** pour cela :


```ruby
f.puts "Ceci est une autre ligne du fichier"
```

Il faut toujours retenir que la fermeture du fichier est quelque chose d'important et qu'il vaut mieux l'exécuter dans tous les cas, donc avec **ensure** !
On pourrait aussi vérifier si le fichier est accessible en écriture avec la méthode **writable?**.



###Dossier
La création de dossier s'effectue de la même manière que la création de fichier, via la classe **Dir**. Les options sont identiques. Cependant, l'affichage du contenu est en plus pour la lecture de dossier et s'opère comme ceci :


```ruby
puts Dir["C:/temp/*.*"]
```

Ici j'afficherais tous les éléments du dossier **temp**. Vous vous rappellez des expréssions régulières ? Et bien l'affichage des dossiers se fait à peu près pareil. Voilà les options :

*
	<li style="text-align:justify;">**** **: Les sous-répertoires.
	<li style="text-align:justify;">*** **: Tous les caractères.
	<li style="text-align:justify;">**?** : Un caractère.
	<li style="text-align:justify;">**[ m – n ] **: Tous les caractères de **m** à **n**.
	<li style="text-align:justify;">**[ ^ m – n ]** : Tous les caractères sauf ceux de **m **à **n**.
	<li style="text-align:justify;">**{ m, n, ... }** : La chaîne **m** ou **n** ou autre.

Ca explique donc ce que j'ai montré un peu plus haut qui voudrait dire "Afficher les éléments contenant n'importe quel caractère, puis un point, puis n'importe quel caractère à nouveau. Donc tous les fichiers.
On ne peux supprimer un dossier uniquement si il est vide et via ces deux commandes : **delete** ou **rmdir**.



###Différentes fonctions
Je vous invite à chercher sur <a href="http://www.ruby-doc.org/core-2.2.0/File.html">http://www.ruby-doc.org/core-2.2.0/File.html</a> les différentes fonctions et méthodes disponibles avec la classe **File**.


À demain !
