---
layout: post
title: 39 - Pages web statiques avec Rails - Le début - Initiation à Ruby on Rails
date: 2015-03-05 08:00
author: jeremy
published: true
categories: [Rails]
---
Dans cet article, je vous propose de commencer une application Rails. Il s'agit en réalité de pages web statiques. Mais restez, vous risquez d'être surpris. On y va !
<<
<em>Pour suivre ce cours il est plus que conseillé d'avoir sous la main <a href="http://french.railstutorial.org/chapters/beginning" target="_blank">ce lien</a> ou <a href="https://www.dropbox.com/sh/uuwaqjqbc8y3ybv/AACjqwYvxqHaXxADTjBp48-Ra?dl=0" target="_blank">ces fichiers pdf</a>, pour rappel, les cours sont basés dessus et cet article reprend le début du chapitre 3.</em>
>>
###Le commencement du début.
Comme le titre l'indique, il faut bien commencer quelque part. On démarre donc cette nouvelle application en la créant simplement comme on sait si bien le faire :

```ruby
rails new sample_app -T
```
<!--break-->

Ha, petite découverte ici, l'option **-T** (attention à la majuscule). Cette nouvelle option sert à ne pas ajouter le dossier **test** dans l'app. Pourquoi ? Parce qu'on ne va pas se servir du framework de tests par défaut mais de **RSPEC**.
Maintenant qu'on sait ce que l'on veux et que notre application est crée, il faut la configurer correctement.
Et quand je parle de la configurer je veux dire, installer toutes les **gems** dont on aura besoin pour notre app. Il faut donc les renseigner dans le fichier **gemfile**.
Pour rappel, ce fichier contient toutes les gems et leur versions qu'il faudra installer via la commande **bundle install** pour que l'app fonctionne correctement.
La source fournit un modèle du fichier **gemfile**. Le voici :

```ruby
source 'http://rubygems.org'

gem 'rails', '3.0.7'
gem 'sqlite3-ruby', '1.3.2', :require => 'sqlite3'

group :development do
  gem 'rspec-rails', '2.5.0'
end

group :test do
  gem 'rspec', '2.5.0'
  gem 'webrat', '0.7.1'
end
```

Seulement, ce fichier **gemfile** est trop vieux pour être mis en place. Il faut donc le mettre à jour. De quoi avons nous besoin ou pas ? Voici le même fichier **gemfile** avec les correspondances d'aujourd'hui :

```ruby
source 'http://rubygems.org'#==========> Déjà présent dans notre gemfile = à supprimer

gem 'rails', '3.0.7'#== > Derniere version = 4.2.0, déjà présent dans notre gemfile = à supprimer
gem 'sqlite3-ruby', '1.3.2', :require => 'sqlite3'#==========> pour macintosh... à supprimer

group :development do
  gem 'rspec-rails', '2.5.0'#==========> dernière version de la gem = 3.2.1 = à mettre à jour
end

group :test do
  gem 'rspec', '2.5.0'#==========> dernière version de la gem = 3.2.0 = à mettre à jour
  gem 'webrat', '0.7.1'#==========> dernière version de la gem = 0.7.3 = à mettre à jour
end
```

Ce qui nous donne donc un fichier ressemblant à ça :

```ruby
# Inclusion de rspec pour development
group :development do
  gem 'rspec-rails', '3.2.1'
end
# Inclusion de rspec pour test
group :test do
  gem 'rspec', '3.2.0'
  gem 'webrat', '0.7.3'
end
```

Bien sûr, il s'agit de la partie à ajouter dans votre **gemfile** et non pas le **gemfile** complet !
Une fois ceci fait, on peux lancer la commande **bundle install**.
Et pour finir ce début, il faut installer les fichiers nécessaires à **rspec**. Pourquoi ? Pour que Rails l'utilise, tout simplement. On se servira donc de la commande : **rails generate rspec:install**.
Prennez de bonnes habitudes, pushez votre application !
Maintenant que notre application est convenablement configurée, on continue la création et on passe donc aux pages. Nous allons créer 3 pages : "Home" (la page d'accueil), "Contact" et "À propos". Pour ce faire nous allons une fois de plus utiliser l'outil **generate** :

```ruby
rails generate controller Pages home contact
```

Comme vous pouvez le voir, je n'ai pas mis la page "À propos", on la créera manuellement plus tard.
Etant donné que je ne m'occupe que de la partie pratique ici, je vous propose de lire toute la partie théorique sur le livre que je vous ai fourni, il est accessible <a href="http://french.railstutorial.org/chapters/beginning">ici</a> ou <a href="https://www.dropbox.com/sh/uuwaqjqbc8y3ybv/AACjqwYvxqHaXxADTjBp48-Ra?dl=0">ici</a>.
Je vous laisse lire jusqu'au chapitre 3.2 inclus et on se retrouve demain pour un nouvel article !
Bye !
