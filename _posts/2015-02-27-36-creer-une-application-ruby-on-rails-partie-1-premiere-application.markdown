---
layout: post
title: 36 - Créer une application Ruby On Rails - Partie 1 - Première application - Initiation à Ruby on Rails
date: 2015-02-27 08:00
author: jeremy
published: true
categories: [Rails]
---
Maintenant que l'installation est faite on commence la création de notre application Ruby on Rails !
Pour ceux qui ne lisent pas le livre fourni, il faut savoir que l'application crée dans ce chapitre s'efféctuera à l'aide du **générateur d'échaffaudage** (scaffold generator). Mais dans le prochain chapitre on réalisera une application sans cet outil pour bien comprendre les fondements du framework.

### **Génération du squelette et paramétrage.**
La création de l'application et la génération du squelette se font comme ceci :

```ruby
$ rails new first_app
```
<!--break-->

Vous pourrez ensuite trouver dans votre dossier un sous dossier "first_app". Entrez à l'intérieur, voilà votre première application !

Prenez aussi la bonne habitude d'envoyer votre travail sur GitHub à chaque nouvelle version de celle ci !
Pour rappel, mettez vous dans le dossier de votre application pour réaliser ces quelques commandes :

```ruby
$ git init
$ git add .
$ git commit -m "First !!"
$ git remote add origin <adresse_du_depot_GitHub.git>
$ git push origin master
```

Maintenant que vous avez envoyé votre application sur GitHub, nous pouvons la lancer !

```ruby
$ rails s
=> Booting WEBrick
=> Rails 4.2.0 application starting in development on http://localhost:3000
=> Run `rails server -h` for more startup options
=> Ctrl-C to shutdown server
[2015-02-24 09:08:08] INFO  WEBrick 1.3.1
[2015-02-24 09:08:08] INFO  ruby 2.2.0 (2014-12-25) [x86_64-linux]
[2015-02-24 09:08:08] INFO  WEBrick::HTTPServer#start: pid=7299 port=3000


Started GET "/" for 127.0.0.1 at 2015-02-24 09:08:14 +0100
Processing by Rails::WelcomeController#index as HTML
  Rendered /home/jeremy/.rvm/gems/ruby-2.2.0/gems/railties-4.2.0/lib/rails/templates/rails/welcome/index.html.erb (1.3ms)
Completed 200 OK in 46ms (Views: 38.7ms | ActiveRecord: 0.0ms)
```

Lançons donc notre application avec la commande **rails s** ou **rails server** présentée plus haut.
A la ligne 3 vous trouverez l'adresse à laquelle vous accèderez à votre application : <a href="http://localhost:3000/">**http://localhost:3000**</a>.
Vous pouvez stopper le serveur en faisant Ctrl-C, comme indiqué.
C'est bien beau tout ça mais faut qu'on avance ! On ne va pas se servir de la page de démarrage de ruby pour notre application !
! --- Pensez à Push votre application --- !



Pour cette première application on va créer un système de micro-blog à la Twitter où les utilisateurs pourront poster des messages. Ce qui veut dire qu'il nous faut de quoi gérer les utilisateurs et les messages. Pour cela nous avons besoin de deux tables différentes. Une première, nommée **users** et contenant un **ID** (identifiant du **user**), un champ **pseudo** contenant le pseudo ... Hum .. Et pour finir, un champ **email** contenant ... Bref vous avez compris !
Pour les messages maintenant, nous avons besoin d'une table contenant un champ **ID** (identifiant du message), un champ **content** pour stocker le contenu du message** **et un champ **user_id** pour définir qui a posté le message.




J'ai été confronté à quelques erreurs donc cet article s'arrête ici pour le moment, je ferais un article contenant toutes ces erreurs et les solutions que j'ai trouvé et continuerais le tutoriel normalement.
