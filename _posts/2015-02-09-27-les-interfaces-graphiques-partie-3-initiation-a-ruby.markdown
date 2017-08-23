---
layout: post
title: 27 – Les interfaces graphiques Partie 3/? – Initiation à Ruby
date: 2015-02-09 09:09
author: jeremy
published: false
categories: [Initiation à Ruby]
---
###Entry
Voyons maintenant comment insérer un champ texte dans notre application.

```ruby
#_________________Entry__________________
entry_username = TkEntry.new(frame_connexion){
	pack({'side' => 'top'})
}
entry_password = TkEntry.new(frame_connexion){
	pack({'side' => 'bottom'})
	show '*'
}

#_________________Variables__________________
username = TkVariable.new
password = TkVariable.new

entry_username.textvariable = username
entry_password.textvariable = password

username.value = "myusername"
password.value = "mypassword"

```
<!--break-->


Dans la première partie je vous ai rassemblé les deux champs. Seulement l'option **show** est nouvelle, elle permet de masquer le champ en affichant des *.
Dans la deuxième partie on déclare des **variables Tk** pour stocker la valeur des **Entry**. Et pour finir on affecte une valeur à nos variables **username** et **password**.
Voilà ce que l'on obtient :<a href="https://unruby.files.wordpress.com/2015/02/entry.png"><img class="aligncenter size-full wp-image-528" src="https://unruby.files.wordpress.com/2015/02/entry.png" alt="entry" width="170" height="163" /></a>
Voici le code entier :

```ruby
require 'tk'

#_________________Application__________________
window = TkRoot.new{
	title "Home"
}

#_________________Frame__________________
frame_label = TkFrame.new(window){
	width 50
	height 50
	pack({'side' => 'top'})
}
frame_connexion = TkFrame.new(window){
	width 150
	height 150
	pack({'after' => frame_label})
}
frame_button = TkFrame.new(window){
	width 50
	height 50
	pack({'side' => 'bottom', 'pady' => 20})
}

#_________________Label__________________
label = TkLabel.new(frame_label){
	text "Connexion :"
	pack({'side' => 'top'})
}

#_________________Entry__________________
entry_username = TkEntry.new(frame_connexion){
	pack({'side' => 'top'})
}
entry_password = TkEntry.new(frame_connexion){
	pack({'side' => 'bottom'})
	show '*'
}

#_________________Buttons__________________
button_below = TkButton.new(frame_button){
	text "Ok"
	pack({'side' => 'left'})
}
button_cancel = TkButton.new(frame_button){
	text "Cancel"
	pack({'side' => 'right'})
}

#_________________Variables__________________
username = TkVariable.new
password = TkVariable.new

username.value = "myusername"
password.value = "mypassword"

entry_username.textvariable = username
entry_password.textvariable = password

#_________________Bind__________________
button_below.bind("1", proc {
	puts "Hi !"
})
button_cancel.bind("1", proc{
	window.destroy
})
Tk.mainloop
```


###Exemple

```ruby
#_________________Bind__________________
button_below.bind("1", proc {
	if (username == "Jeremy" && password == "unruby")
		puts "Hi #{username} !"
	else
		puts "Wrong Username or password"
	end
})
button_cancel.bind("1", proc{window.destroy})
button_below.bind("1", proc {
	puts "Hi !"
	puts sure.variable == 1 ? "Coche" : "Decoche"
	puts etat.value == "Yes" ? "Yes" : "No"
})
```

Dans cet exemple, un système de connexion tout simple.
