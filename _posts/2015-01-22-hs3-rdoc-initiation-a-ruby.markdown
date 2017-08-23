---
layout: post
title: HS4 – RDOC – Initiation à Ruby
date: 2015-01-22 08:00
author: jeremy
published: true
categories: [Hors série]
---
Hier on a parlé de **rdoc**. Maintenant que vous connaissez les bases, il vous faut aussi connaître les options, et c'est ce dont on va parler tout de suite !

```ruby
--all ou -a
#Sert à inclure les méthodes privées et protégées.
```


```ruby
--charset ou -c
#Le jeu de caractère du fichier source (iso-8859-1 ou utf8 pour les caractères français)
```
<!--break-->


```ruby
--exclude ou -x
#Ignore les fichiers ou répertoires correspondant au motif
```


```ruby
--force-update ou -U
#Force la régénération de la documentation même si aucun fichier n'a été changé depuis la dernière génération. C'est utile lorsque vous utilisez une configuration différente de rdoc
```


```ruby
--help ou -h
#Affichage de l'aide et des commandes possibles.
```


```ruby
--include ou -i
#Liste, séparés par une virgule, les répertoires utilisés par l'instruction : include.
```


```ruby
--inline-source ou -S
#Le code source est inclus dans la documentation.
```


```ruby
--line-numbers ou -N
#Affiche le numéro de ligne.
```


```ruby
--one-file ou -1
#Un seul fichier contient la documentation, on utilise l'option -n pour préciser le nom du fichier.
```


```ruby
--op ou -o dir
#Spécifie le répertoire de destination de la documentation.
```


```ruby
--style ou -s stylesheet url
#Spécifie un chemin vers une feuille de style.
```


```ruby
--title ou -t texte
#Spécifie le titre de la page.
```

Comme vous le voyez c'est uniquement des commandes, je les mets pour que ceux qui les cherchent, puissent les obtenir facilement mais elles sont également trouvable sur internet.
À demain !
