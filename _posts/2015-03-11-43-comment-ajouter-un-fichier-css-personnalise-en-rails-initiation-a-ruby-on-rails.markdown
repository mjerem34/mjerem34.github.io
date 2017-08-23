---
layout: post
title: 43 - Comment ajouter un fichier CSS personnalisé en Rails - Initiation à Ruby on Rails
date: 2015-03-11 08:38
author: jeremy
published: false
categories: [Rails]
---
Dans cet article, on va continuer notre lancée sur le cours Rails. Dans ce cours on se servira de Bootstrap comme base et on y ajoutera quelques fonctionnalités, vous pouvez tout de même suivre ce cours si vous ne connaissez pas le CSS.



<<
<em>Pour suivre ce cours il est plus que conseillé d’avoir sous la main <a href="http://french.railstutorial.org/chapters/beginning" target="_blank">ce lien</a> ou <a href="https://www.dropbox.com/sh/uuwaqjqbc8y3ybv/AACjqwYvxqHaXxADTjBp48-Ra?dl=0" target="_blank">ces fichiers pdf</a>, pour rappel, les cours sont basés dessus et cet article reprend le chapitre </em><em>5</em><em>.</em>
>>
Le but de ce tutoriel sera de tranformer ça :<a href="http://unruby.com/wp-content/uploads/2015/03/pages_home.png"><img class="aligncenter wp-image-756 size-medium" src="http://unruby.com/wp-content/uploads/2015/03/pages_home-300x249.png" alt="pages_home" width="300" height="249" /></a>

qui est notre page **Home** actuelle. En ça :<a href="http://unruby.com/wp-content/uploads/2015/03/mwitter_pages.png"><img class=" size-large wp-image-755 aligncenter" src="http://unruby.com/wp-content/uploads/2015/03/mwitter_pages-1024x461.png" alt="mwitter_pages" width="687" height="309" /></a>
<!--break-->


Je reconnais que c'est pas terrible mais ça permettra aux débutants d'avoir une vue d'ensemble des fonctionnalités les plus utilisées en CSS.

### **Mwitter ?**
Si vous voulez faire les choses dans les règles de l'art vous aurez besoin de ceci :<a href="http://unruby.com/wp-content/uploads/2015/03/mwitter.jpg"><img class=" size-medium wp-image-754 aligncenter" src="http://unruby.com/wp-content/uploads/2015/03/mwitter-300x200.jpg" alt="mwitter" width="300" height="200" /></a>
Qui est le logo de la société Mwitter.
Pour personnaliser Bootstrap on peux soit mettre des classes dans nos balises dans le fichier **html** soit créer un second fichier **css**, ce n'est pas très logique de faire ça vu que Bootstrap possède toutes les fonctionnalités déjà pré-écrites. Mais c'est ce qu'on va faire quand même pour que les débutants comprennent les bases. Pour créer ce second fichier il suffit de se rendre dans le même dossier où est présent Bootstrap, c'est à dire : **sample_app/app/assets/stylesheets/** . Il s'appellera comme vous voulez, j'ai choisi de mettre **style.css** pour la simplicité et la convention.
Pour le mettre en route il faut l'insérer dans notre layout d'application qui se situe dans **sample_app/app/views/layouts**. Pour rappelle se fichier contient le** html** qui sera inclus dans toutes les pages de votre site. C'est en quelque sorte le fichier principal.
Et pour finir, une fois que vous l'avez ajouté, il faut dire à Rails qu'il est présent en l'inscrivant dans **l'initializer** (**sample_app/config/initializer/assets.rb**). En passant on pourra placer notre image dans le bon dossier, soit : **sample_app/app/assets/images**.
On pourrait déjà tester que notre nouveau fichier fonctionne bien simplement en changeant la couleur du fond d'écran :

```ruby
body{
  background-color: #b2fffd;
  font-family: "DejaVu Sans", "Liberation Mono", Arial;
}
```


J'en ai profité pour rajouter une police personnalisée, il y en a trois d'écrite juste au cas où la première ne serait pas disponible, la seconde serait utilisée, et ainsi de suite.
Si cela ne fonctionne quand même pas pour vous essayez de rajouter **html** avant **body**. Pour ma part, ça a fonctionné.

### **Une mouette ?**
Maintenant qu'on a rajouté un fond à notre site on peux mettre le logo. Pour inclure une image en Rails, on utilisera la methode **image_tag**, comme ceci :

```ruby
<%= image_tag("mwitter.jpg", :alt => "Mwitter", :class => 'img-rounded', size: "200x200")%>
```

Les élements du menu sur la droite et au pied de page sont en fait une liste à puces, je vous laisse donc le loisir de chercher comment créer une <a href="https://www.ecosia.org/search/google/q/liste+%C3%A0+puces+en+html#gsc.tab=0&gsc.q=liste%20à puces en html&gsc.page=1" target="_blank">**liste à puces en html**</a> :P .

### **Signup**
Pour le bouton on se servira simplement d'un lien faisant partie de la classe dont Bootstrap se sert pour créer des boutons, soit :

```ruby
<%= link_to "Sign Up", 'signup', :class => 'btn btn-large btn-primary'%>
```

Ah oui, le bouton est en fait écrit en Rails aussi, via la méthode **link_to**. C'est ce que vous aviez besoin tout à l'heure pour faire la liste à puces contenant les liens des pages. Voyez à la fin que le bouton fait partie de trois classes distinctes : **btn, btn-large **et** btn-primary**. Je vous laisser faire un tour sur la documentation de Bootstrap que vous trouverez <a href="http://getbootstrap.com/css/#buttons" target="_blank">ici</a>.
Voici le contenu du fichier css avec toutes les explications.

```css
.container{
  width: 710 px;/*TAILLE DU CONTAINER, POUR LAISSER DES BANDES SUR LE COTÉ*/
  background-color: rgba(255, 255, 255, 0.35);/*FOND DU container*/
}

html body{
  background-color: #b2fffd; /*FOND DU SITE*/
  font-family: "DejaVu Sans", Arial;/*POLICE GÉNÉRALE DU SITE*/
}
header{
  padding-top: 20px;/*MARGE EXTERIEURE EN HAUT DU HEADER*/
  margin-bottom: 100px;/*MARGE INTERIEURE EN BAS DU HEADER*/
}
header nav{
  float:right;/*PLACE L'ÉLÉMENT À DROITE DE LA PAGE*/
  background-color: white;/*FOND DE LA BARRE DE NAVIGATION DU HEADER*/
  border-radius:5px;/*ANGLES DU FOND ARRONDIS DE 5 PIXELS*/
  font-family: Purisa, "DejaVu Sans", Arial;/*POLICE DE LA LISTE*/
  margin-top: 110px;/*MARGE EXTERIEURE EN HAUT*/
}
.content{
  background-color: white;/*FOND DU CONTENU*/
}
footer nav{
  float: left;
  margin-top: 100px;
  padding-left: 355px;/*MARGE INTERIEURE GAUCHE*/
  padding-right: 361px;/*MARGE INTERIEURE DROITE*/
  background-color: white;
  border-radius:5px;
  font-family: Purisa, "DejaVu Sans", Arial;
}
footer nav ul li{/*SELECTIONNE LES LI PRESENTS DANS UL PRESENT DANS NAV PRESENT DANS LE FOOTER*/
  display: inline;/*MET EN LIGNE LES ELEMENTS DE LA LISTE*/
}
```

Bye !
