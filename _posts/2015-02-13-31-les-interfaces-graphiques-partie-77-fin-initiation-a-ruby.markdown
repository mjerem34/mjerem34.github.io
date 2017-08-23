---
layout: post
title: 31 – Les interfaces graphiques Partie 7/7 FIN – Initiation à Ruby
date: 2015-02-13 08:00
author: jeremy
published: true
categories: [Initiation à Ruby]
---
### **NoteBook**
Ce composant est en réalité très simple, il permet la création d'onglets. Voyez plutôt :

<!--break-->


```ruby
#_________________Onglets__________________
onglets = Tk::Tile::Notebook.new(window){
	pack
}

#_________________Frame__________________
frame_label = TkFrame.new(window){
	width 50
	height 50
	pack({'side' => 'top'})
}
frame_connexion = TkFrame.new(onglets){
	width 150
	height 150
	pack
}
frame_button = TkFrame.new(window){
	width 50
	height 50
	pack({'side' => 'bottom', 'pady' => 20})
}
frame_radio = TkFrame.new(onglets){
	width 50
	height 50
	pack
}
frame_list = TkFrame.new(onglets){
	width 100
	height 100
	pack
}

onglets.add( frame_connexion, {'text' => "Connexion"})
onglets.add( frame_radio, {'text' => "Boutons Radio"})
onglets.add( frame_list, {'text' => "Pays"})
```

C'est dans la partie **Onglets** qu'on les crée, encore une fois, juste une syntaxe.
En revanche, c'est lors de la création des **frame** qu'il faut faire attention ! Puisque au lieu de les ancrer à la fenêtre principale, il faut les ancrer aux onglets, voyez le changement de paramêtre ligne **12, 22, 27**. J'ai ancré ces composants au composant onglet. Pour finir, il faut créer les onglets et leur donner un titre. Attention à placer les dernières lignes après la création des **frame** sinon vous aurez une belle erreur. Mais je vous laisse découvrir.
Le prochain article présentera l'exercice que je vous donne, rassurez vous ce sera très simple.
