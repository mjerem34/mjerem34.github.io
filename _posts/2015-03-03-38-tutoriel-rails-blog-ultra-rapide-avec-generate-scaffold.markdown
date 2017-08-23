---
layout: post
title: 38 - Tutoriel Rails - Blog ultra rapide avec generate scaffold ! - Initiation à Ruby on Rails
date: 2015-03-03 08:00
author: jeremy
published: true
categories: [Rails]
---
###Les utilisateurs
Donc pour ceux qui sont perdus dans tout ce fatras de tutoriels, sachez qu'on a déjà créé notre application rails avec :

```ruby
$ rails new first_app
```

On continue donc pour créer notre projet de micro-blogging à la Twitter en créant un système qui gérera les utilisateurs. Pour cela on va utiliser le système d'échafaudage (scaffold), ça se passe comme ça :
<!--break-->

```ruby
$ rails generate scaffold User pseudo:string email:string
```

Ensuite, il faut faire migrer la base de données avec **rake** comme ceci :

```ruby
$ rake db:migrate
== CreateUsers: migrating ====================================================
-- create_table(:users)
-> 0.0017s
== CreateUsers: migrated (0.0018s) ===========================================
```

Vous pouvez dores et déjà accéder à votre application en allant sur cette adresse : **<a href="http://localhost:3000/">http://localhost:3000/</a> . **Sans oublier de lancer votre serveur avec **rails s**.
Vous ne verrez aucun changement bien entendu. Pour voir ce que l'on vient de faire, il faut se rendre sur <a href="http://localhost:3000/users/">**http://localhost:3000/**</a>**<a href="http://localhost:3000/users/">users/</a> **.
A ce moment là, si vous avez une erreur, rendez vous dans la partie précédente pour la solution.
Une fois sur l'adresse indiquée plus haut, vous pouvez découvrir les différents boutons qui permettent de gérer les utilisateurs. Voir livre pour plus de détails.
Si vous voulez plus de détails sur le système MVC, je vous laisse regarder le livre fourni pour l'occasion.

###Les messages
Maintenant qu'on a créé les utilisateurs, il nous faut créer les messages ! Et pour donc continuer ce tutoriel sans fausses notes, on utilisera **scaffold** !

```ruby
$ rails generate scaffold Microposts content:string user_id:integer
```

Ici vous avez sûrement repéré le **user_id**, il représente l'identifiant de l'utilisateur ayant posté le message.
Vous pouvez maintenant aller faire un tour sur <a href="http://localhost:3000/microposts">http://localhost:3000/microposts</a> pour avoir la liste (vide pour l'instant) de vos messages postés par vos utilisateurs.

Et je vous abandonne en vous laissant à la découverte du nouveau micro-blog que vous venez de créer. Rassurez vous, le prochain chapitre sera un peu plus complet et détaillé. Je rappelle que cette partie là ne traitait que de l'aperçu rapide des fonctionnalités.
