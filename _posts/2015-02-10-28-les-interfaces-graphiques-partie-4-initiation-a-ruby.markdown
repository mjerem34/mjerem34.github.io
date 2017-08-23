---
layout: post
title: 28 – Les interfaces graphiques Partie 4/? – Initiation à Ruby
date: 2015-02-10 08:00
author: jeremy
published: false
categories: [Initiation à Ruby]
---
###CheckButton
Un **checkButton** est une case à cocher. On peux stocker la valeur dans une variable. Cette valeur peux être : **1** pour **coché** et **0** pour **décoché**.

```ruby
#_________________CheckButton__________________
sure = TkCheckButton.new(frame_button){
	text "Are you sure ?"
	pack({'before' => button_below})
}
```

<!--break-->

On pourrait aussi retourner si la case est cochée ou pas :

```ruby
button_below.bind("1", proc {
	puts "Hi !"
	puts sure.variable == 1 ? "Coche" : "Decoche"
})
```

### **RadioButton**
Un **RadioButton** est très similaire à un **CheckButton** sauf que lorsqu'il fait partie à un **groupe**, un seul bouton peut être coché. Vous devez très bien les connaitre sous cette forme :

```ruby
#_____________RadioButton_______________
etat = TkVariable.new
term = ["Yes", "No"]

term.each{
	|accept|
	ok = TkRadioButton.new(frame_radio){
		text accept
		value accept
		pack
	}
	etat = ok.variable
	ok.command(proc{
		puts etat.value
	})
}
```

Avant de commencer la création du bouton, on crée une **variable** qui stockera la valeur de sortie du bouton. Ensuite on crée un **tableau** contenant les valeur des boutons appartenant au groupe. On peux ensuite s'attaquer à la création des **RadioButton**. On récupère notre **valeur** dans la variable **etat**.
La méthode **.command** sert à détecter la sélection.
Voilà ce que l'on obtient :<a href="https://unruby.files.wordpress.com/2015/02/radio.png"><img class="aligncenter size-full wp-image-531" src="https://unruby.files.wordpress.com/2015/02/radio.png" alt="radio" width="168" height="224" /></a>
On pourrait aussi vérifier si le bouton **Yes** est bien sélectionné lors du clic sur **Ok** comme ça :

```ruby
button_below.bind("1", proc {
	puts "Hi !"
	puts sure.variable == 1 ? "Coche" : "Decoche"
	puts etat.value == "Yes" ? "Yes" : "No"
})
```

Il suffit de rajouter la vérification, ici en ligne 4.

###Listbox
Vous connaissez les **Listbox **? Mais si, vous savez, quand on vous demande votre pays pendant une inscription. Voilà comment ça se passe :

```ruby
#_________________ListBox__________________
list_choices = [
	'United States',
	'France',
	'Spain',
	'United-Kingdom',
	'China'
]
list_choices_variable = TkVariable.new
list_choices_variable.value = list_choices

list_country = TkListbox.new(frame_list){
	listvariable list_choices_variable
	pack({'side' => 'left'})
}
list_country.yscrollbar(TkScrollbar.new(frame_list) .pack({'side' => 'right', 'fill' => 'y'}))
```

Comme vous le voyez, les choix se présentent sous forme de tableau simple. Ensuite, on stocke se tableau dans une variable tk pour qu'il soit possible de l'utiliser dans notre **TkListbox**.
**Attention c'est TkListbox et pas TkListBox ! J'ai passé 30 minutes dessus et maintenant je sais que c'est un b minuscule !**
La dernière ligne sert à ajouter une barre de défilement verticale, pour parcourir toute la liste.
On peux aussi faire en sorte que l'utilisateur puisse sélectionner plusieurs pays avec l'option **selectmode** et les valeurs **single **ou **multiple**.
Pour finir, on peux détecter la valeur en sortie comme ça :

```ruby
#_________________Bind__________________
button_below.bind("1", proc {
	puts "Hi !"
	puts sure.variable == 1 ? "Coche" : "Decoche"
	puts etat.value == "Yes" ? "Yes" : "No"
	puts list_choices[list_country.curselection[0]]
})
button_cancel.bind("1", proc{
	window.destroy
})
```
