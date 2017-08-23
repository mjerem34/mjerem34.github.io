---
layout: post
title: 24 - Installation de Ruby Tk - Initiation à Ruby
date: 2015-02-04 08:01
author: jeremy
published: false
categories: [Initiation à Ruby]
---
On y est, 51 ème article et on commence les interfaces graphiques ! Mais d'abord, on va préparer le terrain avec Ruby Tk.


###C'est quoi ?
Ruby Tk est une librairie de composants graphiques multi-plateformes. Mais Tk n'est pas inclus dans l'installation standard SAUF si vous êtes sous Windows et que vous avez coché la petite case qu'il fallait au moment de l'installation de **RubyInstaller** avec Ruby 2.1.5 => <a href="https://unruby.wordpress.com/2015/01/21/19-installation-ruby-2-2-0-initiation-a-ruby/" target="_blank">Voir article 19 !</a>
Dans les autres cas, c'est parti pour l'installation !
<!--break-->

### **Windows**
Il suffit d'aller sur cette page : <a href="http://www.activestate.com/activetcl/downloads">http://www.activestate.com/activetcl/downloads</a> et de choisir votre version de Windows à droite.
Ensuite, exécutez le fichier téléchargé :
<a href="https://unruby.files.wordpress.com/2015/02/1w.png"><img class="aligncenter wp-image-514 size-full" src="https://unruby.files.wordpress.com/2015/02/1w.png" alt="1w" width="839" height="398" /></a>
Cliquez sur **Next**.
<a href="https://unruby.files.wordpress.com/2015/02/2w.png"><img class="aligncenter size-full wp-image-515" src="https://unruby.files.wordpress.com/2015/02/2w.png" alt="2w" width="660" height="313" /></a>Acceptez les termes de license puis cliquez sur **Next** encore une fois.
<a href="https://unruby.files.wordpress.com/2015/02/3w.png"><img class="aligncenter size-full wp-image-516" src="https://unruby.files.wordpress.com/2015/02/3w.png" alt="3w" width="660" height="313" /></a>Ne modifiez rien et cliquez sur **Next**.
<a href="https://unruby.files.wordpress.com/2015/02/4w.png"><img class="aligncenter size-full wp-image-517" src="https://unruby.files.wordpress.com/2015/02/4w.png" alt="4w" width="660" height="313" /></a>Encore une fois.
<a href="https://unruby.files.wordpress.com/2015/02/5w.png"><img class="aligncenter size-full wp-image-511" src="https://unruby.files.wordpress.com/2015/02/5w.png" alt="5w" width="660" height="313" /></a>Roh et puis après tout, cliquez sur **Cancel**, faites votre valise et partez dans les Pyrénées pour élever des vaches et des moutons !! =D
<a href="https://unruby.files.wordpress.com/2015/02/6w.png"><img class="aligncenter size-full wp-image-512" src="https://unruby.files.wordpress.com/2015/02/6w.png" alt="6w" width="660" height="313" /></a>

###MAC OS XYZ 12 version white snow leopard of the antartica
Je ne possède pas d'ordinateur de la pomme mais vous pourrez très bien trouver suivre la procédure de Windows et trouver votre bonheur sur <a href="http://www.activestate.com/" target="_blank">activestate.com</a>
Ou bien, aller faire un tour dans la baie des pirates !

###Linux
Si vous êtes sur une distribution **Linux** il suffira de suivre les mêmes directives que pour Windows, soit :

*
	<li style="text-align:justify;">
Aller sur <a href="http://www.activestate.com/activetcl/downloads">http://www.activestate.com/activetcl/downloads</a>

	<li style="text-align:justify;">
Télécharger le package "**ActiveTcl8.6.3.1.298624-linux-x86_64-threaded.tar.gz**"

	<li style="text-align:justify;">
Ouvrez le avec un extracteur de fichiers

	<li style="text-align:justify;">
Lancez le fichier **install** en administrateur

	*
Et suivez les étapes de Windows


###Tests
Vous devez sûrement vous demander maintenant, comment tester ? C'est tout simple, copiez simplement ce code et exécutez le comme vous faîtes d'habitude :


```ruby
require 'tk'
hello = TkRoot.new {
	title "Hello World"
}
Tk.mainloop
```


Les explications viendront plus tard, pour le moment on se contentera juste de ça. Si une fenêtre est apparue avec, en titre : "**Hello World**" c'est que tout est ok ! Vous avez fini.
Demain on commencera les expérimentations ! Donc, à demain !
