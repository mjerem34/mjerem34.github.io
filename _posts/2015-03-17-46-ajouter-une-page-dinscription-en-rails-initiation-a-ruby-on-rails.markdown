---
layout: post
title: 46 - Ajouter une page d'inscription en Rails ? - Initiation à Ruby On Rails
date: 2015-03-17 08:49
author: jeremy
published: true
categories: [Rails]
---
Dans cet article, on va voir comment créer une page d'inscription pour notre projet et terminerons le chapitre 5.

<<
<em>Pour suivre ce cours il est plus que conseillé d’avoir sous la main <a href="http://french.railstutorial.org/chapters/beginning" target="_blank">ce lien</a> ou <a href="https://www.dropbox.com/sh/uuwaqjqbc8y3ybv/AACjqwYvxqHaXxADTjBp48-Ra?dl=0" target="_blank">ces fichiers pdf</a>, pour rappel, les cours sont basés dessus et cet article reprend le chapitre </em><em>5</em><em>.</em>
>>
### **Generate**
Vous vous en doutiez peut être, pour créer la page d'inscription il faut générer le **controller **avec** rails generate** :

```ruby
$ rails generate controller Users new

$ rm -rf spec/views
$ rm -rf spec/helpers
```
<!--break-->

Les deux dernières commandes servent à supprimer les dossiers **views **et **helpers** du dossier **spec**. Nous en auront pas besoin.
Vous remarquerez aussi qu'un test **spec** a été créé à l'occasion, ainsi que la vue **new.html.erb** et un **helper** pour le **user**. Vous pouvez dores et déjà créer des tests pour vérifier la page **new.html.erb** en vous aidant de ce que vous avez déjà appris.
Il faut aussi remplacer notre première page **/signup** par celle ci. Modifiez donc les routes, le titre de la page ainsi que l'adresse des boutons. Sauf si vous avez utilisé la méthode **signup_path** au lieu de **"/signup"**.
Bye !
