---
layout: post
title: 19 - Installation Ruby 2.2.0 - Initiation à Ruby
date: 2015-01-21 08:00
author: jeremy
published: false
categories: [Initiation à Ruby]
---
Hum … Je ne sais pas si je devrais dire ça mais … J'ai installé Windows 8.1 …
Comme un petit vieux, je m'étais habitué à Windows 7, et aujourd'hui c'est fini, j'ai installé Windows 8.1.

Mais pourquoi t'as installé Windows 8.1 alors que Windows 9 10 va bientôt sortir ?
Hé bien, je préfère que les autres essuient les plâtres pour moi, et puis je fais une réinstallation tous les 6 mois environs donc d'ici là …
Donc j'ai réinstallé Windows et Linux Mint 17.1 (Oh my god ! Mais ils ont copiés sur Windows 8.1 !). Et du coup il m'a fallu réinstaller tout … Enfin, surtout sur Windows puisque rien n'est fourni avec … De Brackets en passant par Firefox jusqu'à Saint's Row IV \o/.
Et c'est là que je me suis dit, pourquoi ne pas installer Ruby 2.2 ? Il vient tout juste de sortir donc autant en profiter. Je me lance donc dans un mini tutoriel pour expliquer comment l'installation se déroule.
Lisez tout le tutoriel au moins une fois avant de commencer !!
<!--break-->

###Windaubeows
Je me suis toujours demandé si on avait le droit de cracher sur un OS sur internet ? Mais on l'aime notre bon vieux Windows.
Alors, pour cette installation, ou mise à jour, Go sur : <a href="http://rubyinstaller.org/">http://rubyinstaller.org/</a>
**NE CLIQUEZ PAS SUR LE BOUTON ROUGE !!**
Sinon vous téléchargerez Ruby 2.2 !
Lancez le fichier et installez... Oui c'est aussi simple … Voici une série de captures d'écrans :
Vous cliquez sur *Run*.<a href="https://unruby.files.wordpress.com/2015/01/exe_ruby_installer_windows.png"><img class="size-full wp-image-447 aligncenter" src="https://unruby.files.wordpress.com/2015/01/exe_ruby_installer_windows.png" alt="exe_ruby_installer_windows" width="470" height="346" /></a>
Acceptez les termes de licence puis cliquez sur Next.<a href="https://unruby.files.wordpress.com/2015/01/license_ruby_installer_windows.png"><img class="aligncenter size-full wp-image-450" src="https://unruby.files.wordpress.com/2015/01/license_ruby_installer_windows.png" alt="license_ruby_installer_windows" width="503" height="389" /></a>
Cochez les trois cases puis cliquez sur *Install*.<a href="https://unruby.files.wordpress.com/2015/01/optionnal_ruby_installer_windows.png"><img class="aligncenter size-full wp-image-451" src="https://unruby.files.wordpress.com/2015/01/optionnal_ruby_installer_windows.png" alt="optionnal_ruby_installer_windows" width="503" height="389" /></a>
Hum …<a href="https://unruby.files.wordpress.com/2015/01/install_ruby_installer_windows.png"><img class="aligncenter size-full wp-image-449" src="https://unruby.files.wordpress.com/2015/01/install_ruby_installer_windows.png" alt="install_ruby_installer_windows" width="503" height="389" /></a>
Ha c'est fini !!<a href="https://unruby.files.wordpress.com/2015/01/finish_ruby_installer_windows.png"><img class="aligncenter size-full wp-image-448" src="https://unruby.files.wordpress.com/2015/01/finish_ruby_installer_windows.png" alt="finish_ruby_installer_windows" width="503" height="389" /></a>

C'est tout... C'est vrai que c'est simple, ma grand mère pourrait le faire. Quoi que je ne suis pas sur qu'il y ai Internet où elle est.

###
###
###Linux
Cette partie du tuto concerne uniquement les personnes disposant de distributions basées sur **Debian**. Mon Linux Mint est basé sur Ubuntu qui est lui même basé sur Debian donc tout va bien.
J'ai installé Ruby avec **RVM**, j'en ai profité pour installer **Rails** aussi, vu qu'on va bientôt y arriver.
Je me suis basé sur cette vidéo :
http://www.youtube.com/watch?v=_K3RxCRQTIo
Mais vu qu'elle est en espagnol je vais la traduire même si il n'y en a pas l'utilité. Je vous conseille quand même de lire plus bas parce que la vidéo date un peu, les commandes ont changé depuis le temps.
Ouvrez une console et installez les **dépendances** :


```ruby
sudo apt-get install build-essential git-core curl
```


**curl** servira à installer **RVM** par la suite.
Dans une nouvelle ligne, lancez cette commande :


```ruby
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
```


Elle installera les** clés d'identification**.
Puis :


```ruby
\curl -sSL https://get.rvm.io | bash -s stable --ruby --rails
```


Vous aurez pleins de commandes qui vont s'afficher, attendez simplement la fin. Ne vous étonnez pas si c'est un peu long. Patientez.
Continuez avec ceci :


```ruby
[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm" # Load RVM into a shell session *as a function*
```


Puis **sauvegardez**.
Lancez cette commande :


```ruby
source ~/.profile
```


Puis allez dans **Editer** en haut de votre shell et cliquez sur **Préférences du profil.** Une fenêtre s'ouvre avec 6 onglets, cliquez sur le **deuxième** : **Titre et commande** puis cochez la première case : **Exécuter la commande comme un interprète de connexion.**
**Fermez toutes les fenêtres** puis réouvrez un shell.
** C'est très important de fermer toutes les fenêtres de shell pour l'actualisation.**
Tapez ensuite ceci :


```ruby
rvm use 2.2 --default
```


Voilà c'est fini, vous pouvez vérifier avec la commande :


```ruby
ruby -v
```


Il s'affichera alors la version de Ruby installée sur votre ordinateur.
Si vous aviez déjà installé Ruby, cette installation mettra par défaut la dernière version, donc la 2.2.0.
Seule la première commande diffère de la vidéo, toutes les autres sont les mêmes.
Si vous avez un problème, les commentaires sont là pour ça.
<em>**Tutoriel testé sur Windows 8.1 x64(64bits) et Linux Mint 17.1 Cinnamon x64(64bits).**</em>
