---
layout: post
title: 29 – Les interfaces graphiques Partie 5/? – Initiation à Ruby
date: 2015-02-11 08:00
author: jeremy
published: true
categories: [Initiation à Ruby]
---
###Menu
Ca aussi vous connaissez, les menus **Fichier**, **Edition**, **Outils**, **Aide**, tout en haut de la fenêtre.


Un menu est donc composé d'entrées de type **cascade, checkbutton, command, radiobutton**, ou **separator**. Je vous laisse découvrir les fonctionnalités de chaque type.

```ruby
#Création du menu ===>
menu = TkMenu.new(window)
menu.add('command',
		{'label' => 'Item',
		'command' => Proc.new(){puts "Test Ok !"},
		'underline' => 0 })
menu.add('separator')
menu.add('command',
		'label' => "Exit",
		'command' => Proc.new(){window.destroy},
		'underline' => 1)
mb = TkMenu.new

#Ajout du menu ===>
mb.add('cascade',
		{'menu' => menu,
		'label' => 'File'})

#Association à la fenêtre ===>
window.menu(mb)
```
<!--break-->

Quelques nouveautés ici :

*
	*
**label** : l'étiquette de l'entrée

	*
**command** : le code à invoquer lors d'un clic

	*
**underline** : le numéro de caractère à souligner pour autoriser la sélection par clavier


Pour finir il est imporant d'associer le menu à la fenêtre que vous voulez avec la méthode **.menu**.

### **MessageBox**
Une **MessageBox** est une boîte de dialogue modale (qui bloque l'application tant qu'elle n'est pas fermée). Cela peut servir à avertir l'utilisateur d'une erreur par exemple. Les options sont :

*
	*
**Info**

	*
**Warning**

	*
**Error**

	*
**Question**


Ce sont les options **icon**, elles définissent la nature du message.

```ruby
#_________________MessageBox__________________
Tk::messageBox :type => 'yesno',
				:message => 'Are you sure you want to install the program ?',
				:icon => 'question', :title => 'Install'

Tk::messageBox :message => 'Have a good day'
```

Ici on retrouve une **messageBox** de type **yesno** c'est à dire avec les réponses **oui** et **non** de possible. Notre message ainsi que la nature du message et son titre.
Le second **messageBox** affiche simplement un message sans conséquences.
Je viens tout juste de découvrir la documentation de **Tk**, je cherchais un truc du style depuis un moment sans pouvoir mettre la main dessus, mais pour vous éviter de chercher voici le lien : <a href="http://www.tkdocs.com/tutorial/index.html">**http://www.tkdocs.com/tutorial/index.html**</a>

###TopLevel
Un composant **Toplevel** est tout simplement une fenêtre supplémentaire pour notre programme, elle agit comme la première. C'est à dire qu'on peux y intégrer des **boutons**, **menus**, **radiobutton**, ...
En revanche, elle dépend bien sûr de la fenêtre principale, si cette dernière est fermée, la **Toplevel **se ferme aussi !

```ruby
#_________________TopLevel__________________
window_1 = TkToplevel.new(window){
	title "New window"
}
button_ok_window_1 = TkButton.new(window_1){
	pack({'padx' => 20, 'pady' => 20})
	text "ok"
	command proc{
		window_1.destroy
	}
}
```
