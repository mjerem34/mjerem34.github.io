---
layout: post
title: 16 - Modules - Initiation à Ruby
date: 2015-01-07 08:30
author: jeremy
published: true
categories: [Initiation à Ruby]
---
Salut à tous ! On y est, la reprise, j'espère que vous avez passé de bonnes vacances ainsi que de bonnes fêtes de fin d'année, je vous souhaite -un peu en retard- une bonne année 2015 et si vous ne l'avez pas encore fait je vous invite à aller voir l'article de la nouvelle résolution. Comme vous avez pu le voir, je me suis manqué, je l'avoue, je me suis laissé dépasser pas les évènements, je voulais poster des articles pour les vendredis mais ils sont passés à la trappe, tampis, mais pour me faire pardonner j'en ferais un spécial reprise mais on n’est pas là pour discuter de ça pour le moment !


Voyons donc, les modules. Qu'est-ce-que c'est et à quoi ça sert ?
<!--break-->

###Modules ?
Les modules, à quoi ça sert ? Les modules sont une nouvelle forme de structure de code. C'est à dire ? Tout simplement un moyen d'organiser son code un peu mieux.
Voilà comment ça se présente : imaginons ! Un site a besoin d'une base de donnée pour stocker tous ses utilisateurs, voilà comment on pourrait présenter cela :


```ruby
module Connection
  def log_in
    puts "You are connected at #{@name}!"
  end
  def log_out
    puts "You are disconnected !"
  end
end

module Admin
  include Connection
  class Men
    def initialize(name, surname)
      @name = name
      @surname = surname
      puts "Hi, my name is #{@name}, #{@surname} #{@name} !"
    end
  end

  class Women
    def initialize(name, surname)
      @name = name
      @surname = surname
      puts "Hello, my name is #{@surname} #{@name} !"
    end
  end
end

module Users
  class Men
    include Connection
    def initialize(name, surname)
      @name = name
      @surname = surname
      puts "Hi, i'm #{@surname} #{@name} !"
    end
  end

  class Women
    def initialize(name, surname)
      @name = name
      @surname = surname
      puts "Hello amigos ! My name is #{@surname} #{@name} !"
    end
  end
end

georges = Admin::Men.new('Smith', 'Georges')
jeannette = Admin::Women.new('La sardine', 'Jeanette')
robert = Users::Men.new('Patainsson', 'Robert')
marie = Users::Women.new('Dubois', 'Marie')

robert.log_in
marie.extend Connection
marie.log_in
```

Ouch, c'est un peu plus long que les anciens codes. Ne vous inquiétez pas on va s'en sortir !
Une petite explication de tout cela s'impose, non ?
Je présenterais les explications dans l'ordre de création et non pas dans l'ordre d'écriture, ce sera bien plus facile à comprendre. Première question, qui veux accéder à notre site ? Les administrateurs et les visiteurs.
Deux modules servent ici simplement à classer nos utilisateurs sous forme d'arbre où la base serait donc le module Admin et le module Users. Vous remarquerez en passant que le nom du module se doit de commencer par une majuscule, tout comme le nom de classe.
Voici donc nos 2 premières branches. Admin et Users. Ces deux branches se diviseront en deux pour former Men et Women cette fois ci sous forme de classe. J'ai mis cela pour mieux m'en sortir à la suite du cours, on aurait pu mettre autre chose, ce n'est qu'un exemple. Nos utilisateurs n'auront que 2 paramêtres, le nom et le prénom et se présenteront lors de leur création. Rien de bien compliqué.
Mes objets sont créés, puis, on retourne en haut du code et on crée notre module de connexion qui nous permettra de ... nous connecter. Encore une fois, ce n'est qu'un exemple, ce module ne nous connecte pas réellement, il ne fait qu'afficher une phrase ! Dans notre module de connexion on stockera donc 2 méthodes qui serviront à connecter et déconnecter l'utilisateur. On s'ennuierais presque.
En fait vous avez sûrement tilté à la création des objets, oui il y a une légère différence depuis la dernière fois. A quoi ça correspond ? Nos deux modules, que sont Admin et Users comportent une classe Men et Women chacune.
Il se produirait une erreur si l'ont ferait simplement :

```ruby
georges = Men.new('Smith', 'Georges')
```

L'objet georges serait créé une fois dans chaque module, ce qui n'est pas bon du tout.
Pour éviter ça on a donc recours à la syntaxe au dessus.

###Intégration aux classes et aux objets.
Pour avoir accès aux méthodes présentes dans les modules il faut créer un accès lors de la création de classe, c'est la qu'intervient le fameux include Connection.
On connaît déjà include, c'est donc encore plus simple ici puisque pas besoin d'insérer de chemin, juste le nom du module. Avec cette méthode on peux exécuter une méthode comme d'habitude comme je l'ai fait avec robert.log_in.
Pour l'inclure cette fois ci dans un seul objet et non pas une classe entière on utilisera le mot-clé extend suivi du nom du module, ce que je fais avec marie.extend Connection .
La suite revient normalement en utilisant la même syntaxe que robert.




Les plus férus me reprendrons certainement, d'ailleurs je les invite à le faire dans les commentaires pour connaître nos erreurs parce que sans conseils on avance moins vite.
