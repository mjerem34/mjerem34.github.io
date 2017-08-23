---
layout: post
title: 45 - Comment raccourcir vos liens avec les routes ? Initiation à Ruby
date: 2015-03-16 08:00
author: jeremy
published: true
categories: [Rails]
---
Dans cet article, on va parler de la redirection de liens et plus particulièrement des routes d'URL.


<<
<em>Pour suivre ce cours il est plus que conseillé d’avoir sous la main <a href="http://french.railstutorial.org/chapters/beginning" target="_blank">ce lien</a> ou <a href="https://www.dropbox.com/sh/uuwaqjqbc8y3ybv/AACjqwYvxqHaXxADTjBp48-Ra?dl=0" target="_blank">ces fichiers pdf</a>, pour rappel, les cours sont basés dessus et cet article reprend le chapitre </em><em>5</em><em>.</em>
>>
### **Avertissement**
Avant de commencer, je tiens à préciser que les cours seront dorénavant plus courts et moins explicites. Je vous conseille donc plus que jamais de vous aider avec les liens fournis.
<!--break-->

### **Routage**
Aujourd'hui on va donc s'attaquer aux routage d'url. C'est quoi ?
Le routage d'url c'est quand vous allez sur une page de votre application, l'url est : **localhost:3000/pages/home**. Et bien nous on veut que ça ressemble plus à ça : **localhost:3000/**
Tout simplement. Alors comment ça se passe ? Déjà on commence par les tests.

### **Les tests**
Pour rappel, on veux créer un test d'intégration avec **rspec** et pour les liens du layout de notre application. Pour ça on va donc générer les tests avec cette commande :

```ruby
$ rails generate integration_test layout_links
  invoke rspec
  create spec/requests/layout_links_spec.rb
```

Pour tester si notre page répond à la bonne adresse (prenons par exemple la page d'accueil qui répondra à l'adresse ' / ') on va se servir de la même méthode que les premiers tests, soit ceux ci :

```ruby
describe "GET #home" do
  it "returns http success" do
    get :home
    expect(response).to have_http_status(:success)
  end
do
```

Lorsque l'on génère notre fichier test on obtient un fichier (**spec/requests/layout_links_spec.rb**) contenant déjà ceci :

```ruby
require 'rails_helper'

RSpec.describe "LayoutLinks", type: :request do
  describe "GET /layout_links" do
    it "works! (now write some real specs)" do
      get layout_links_index_path
      expect(response).to have_http_status(200)
    end
  end
end
```

Et bien on va faire un mix des deux ce qui nous donnera quelque chose comme ça :

```ruby
RSpec.describe "LayoutLinks", type: :request do
  it "devrait trouver une page Accueil à '/'" do
    get '/'
    expect(response).to have_http_status(:success)
  end
```

A vous d'adapter le reste des pages. Vous pouvez maintenant lancer les tests et vérifier qu'ils échouent.
On peux maintenant passer à l'étape suivante.

### **Redirection**
Rendez vous dans le fichier **config/routes.rb**. C'est ici que va avoir lieu la redirection, et voici comment ça se passe :

```ruby
Rails.application.routes.draw do
  get '/', :to => 'pages#home'
  get '/contact', :to => 'pages#contact'
  get '/about', :to => 'pages#about'
  get '/signin', :to => 'pages#signin'
  get '/signup', :to => 'pages#signup'
  get '/help', :to => 'pages#help'
end
```

Maintenant que les routes sont paramétrées, il faut indiquer à chaque lien que l'on a fait une redirection. Donc on va dans chaque partiel de page. À ce moment là il y a deux façons de faire, comme ça (c'est comme ça que j'ai fait personnellement) :

```html
<header>
  <% logo = image_tag("mwitter.jpg", :alt => "Mwitter", :class => 'img-rounded', size: "200x200")%>
  <%= link_to logo, '/'%>
  <nav>
    <ul class="unstyled inline">
      <li><%= link_to "Home", '/' %></li>
        <li><%= link_to "Signup", '/signup' %></li>
          <li><%= link_to "Signin", '/signin' %></li>
    </ul>
  </nav>
  <h1>Welcome on Mwitter</h1>
</header>
```

ou :

```html
<header>
  <% logo = image_tag("mwitter.jpg", :alt => "Mwitter", :class => 'img-rounded', size: "200x200")%>
  <%= link_to logo, root_path%>
  <nav>
    <ul class="unstyled inline">
      <li><%= link_to "Home", root_path %></li>
        <li><%= link_to "Signup", signup_path %></li>
          <li><%= link_to "Signin", signin_path %></li>
    </ul>
  </nav>
  <h1>Welcome on Mwitter</h1>
</header>
```

Voyez que j'en ai profité pour mettre le lien de la page d'accueil lorsque l'on clique sur le logo. Et surtout, notez que à la ligne 2, le " **=** " n'est plus présent ! Si vous le laissez, deux logos apparaitront.
Vous pouvez déjà aller essayer votre nouveau routage : **<a href="http://localhost:3000/">http://localhost:3000/</a> **qui vous mènera à la page d'accueil et <a href="http://localhost:3000/signin">**http://localhost:3000/signin**</a> qui vous mènera à la page de connexion.

Bye !
