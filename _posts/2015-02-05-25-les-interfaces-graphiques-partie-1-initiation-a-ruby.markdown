---
layout: post
title: 25 - Les interfaces graphiques Partie 1/? - Initiation à Ruby
date: 2015-02-05 08:00
author: jeremy
published: false
categories: [Initiation à Ruby]
---
Ca c'est une partie qui va me plaire. Les interfaces graphiques, c'est à partir de là qu'on pourra commencer à exploiter tout ce que l'on a appris tout au long de cette aventure qui est très loin de se terminer. Vous pouvez déjà commencer à réfléchir à des petits projets personnels que vous souhaiteriez mettre en application. Attention quand même à ce que ça ne soit pas un gros site web, on n'a toujours pas abordé **Rails** donc ce n'est pas le moment. Après ce tutoriel vous pourrez créer des boutons, des listes, des menus, des barres de progression et tout un tas d'autres choses pour vous permettre de créer un petit "logiciel". Pour ma part j'ai ma petite idée d'un logiciel très simple. Mais ça fera l'objet d'un petit exercice le moment opportun.



### **Rappel**
Pour ceux qui auraient loupé le précédent article, voici comment afficher une simple fenêtre avec comme titre "**Hello World**" :

```ruby
require 'tk'
hello = TkRoot.new {
	title "Hello World"
}
Tk.mainloop
```
<!--break-->

Ce code vous affichera une petite fenêtre sans contenu, mais c'est déjà ça ! Il est aussi très important que votre code contienne la dernière ligne tout à la fin : **Tk.mainloop**

###Label
En prenant notre base plus haut, il suffit de créer un objet TkLabel pour donner un "titre" à notre section. C'est à dire ?

```ruby
label = TkLabel.new(window) {
	text "Click on the button below!"
	pack( {'padx' => 10, 'pady' => 20} )
}
```

Renvoie :
<a href="https://unruby.files.wordpress.com/2015/02/label.png"><img class="aligncenter size-full wp-image-530" src="https://unruby.files.wordpress.com/2015/02/label.png" alt="label" width="245" height="184" /></a> Alors certes pour l'instant c'est juste du texte mais ça prendra tout son sens au fur et à mesure du cours.

###Pack
Dans le code plus haut vous avez sûrement vu l'option **pack**. Cette option permet en fait de positionner votre composant. Elle prend en argument une **table de hachage** comportant des **contraintes**. Dont :

*
	*
**after** : ajoute le composant après un autre composant

	*
**before** : positionne le composant avant un autre composant

	*
**fill** : remplissage du composant dans son espace, **horizontal** avec '**x**', vertical avec '**y**', les deux avec **both** ou aucun avec **none**.

	*
**ipadx, ipady** : espace horizontal et vertical à l'intérieur du composant.

	*
**padx**, **pady** : espace horizontal et vertical à l'extérieur du composant.

	*
**side** : position du composant dans son espace grâce aux valeurs **left**, **right,** **bottom** et **top**.


Tout au long de ce tutoriel, je présenterais différentes options.




### **Button**

```ruby
button = TkButton.new(window) {
	text "It's me! The button named below!"
	pack({'after' => label})
}
```

Donne en sortie :
<a href="https://unruby.files.wordpress.com/2015/02/button.png"><img class="aligncenter size-full wp-image-527" src="https://unruby.files.wordpress.com/2015/02/button.png" alt="button" width="239" height="171" /></a>Comme toujours, ce n'est pas si dur pour l'instant, c'est juste une syntaxe à retenir et à mettre en application dans nos projets.
