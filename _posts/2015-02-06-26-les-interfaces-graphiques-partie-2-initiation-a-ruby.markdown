---
layout: post
title: 26 – Les interfaces graphiques Partie 2/? – Initiation à Ruby
date: 2015-02-06 08:00
author: jeremy
published: false
categories: [Initiation à Ruby]
---
###Frame
La **frame** est un **conteneur** de **composant**. Comme vous allez le voir, j'ai créé deux **frame** qui servent à contenir le **label** et les **boutons** :


```ruby
require 'tk'

window = TkRoot.new{
	title "Home"
}
frame_label = TkFrame.new(window){
	width 50
	height 50
	pack({'side' => 'top'})
}
frame_button = TkFrame.new(window){
	width 50
	height 50
	pack({'side' => 'bottom', 'pady' => 20})
}
label = TkLabel.new(frame_label){
	text "I'm the label"
	pack({'side' => 'top'})
}
button_below = TkButton.new(frame_button){
	text "Below"
	pack({'side' => 'left'})
}
button_cancel = TkButton.new(frame_button){
	text "Cancel"
	pack({'side' => 'right'})
}
Tk.mainloop
```
<!--break-->

Ce qui nous donne :
<a href="https://unruby.files.wordpress.com/2015/02/frame.png"><img class="aligncenter size-full wp-image-529" src="https://unruby.files.wordpress.com/2015/02/frame.png" alt="frame" width="267" height="125" /></a>Cette fois ci je vous ai mis le code en entier pour que vous compreniez l'agencement du code et de ses différentes parties.
Il est important de signifier à chaque composant que l'on crée à quelle partie il appartient. On fait cela en l'indiquant en paramètre lors de la création de l'objet composant : **frame_label = TkFrame.new(window)**.
- Ok, c'est bien joli tout ça mais quand je clique sur n'importe quel bouton la fenêtre se ferme pas...

### **Bind**
La méthode **bind** sert à analyser les évenements. C'est à dire. Par exemple, un clic gauche de la souris est un évènement, le survol d'une certaine zone en est un aussi. Voici donc la liste des options qui permettent à **bind** d'analyser ces derniers :

<ul style="text-align:justify;">
	*
1 ou **ButtonPress-1** : clic du bouton gauche de la souris (2 pour le bouton du millieu et 3 pour le bouton de droite).

	*
**Enter** : déplacement à l'intérieur du composant

	*
**Leave** : sortie du composant.

	*
**Motion** : Déplacement de la souris

	*
**Double-1** : Double clic gauche (2 pour le bouton du millieu et 3 pour le bouton de droite)

	*
**B3-Motion** : Bouton droit avec déplacement (drag'n drop)

	*
**Control-ButtonPress-1** : clic gauche avec la touche **ctrl**

	*
**alt-ButtonPress-1** : clic gauche avec la touche **alt**


Donc, pour qu'il s'affiche quelque chose lorsqu'on clique sur chaque bouton on fait comme cela :

```ruby
button_below.bind("1", proc {
	puts "Yeah ! I'm the button Below !"
})
button_cancel.bind("1", proc{
	window.destroy
})
```

Encore une nouveauté, **window.destroy** qui sert à fermer la fenêtre lors du clic sur le bouton **cancel**.
