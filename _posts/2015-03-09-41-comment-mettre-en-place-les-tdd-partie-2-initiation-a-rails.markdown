---
layout: post
title: 41 - Comment mettre en place les TDD ? Partie 2 - Initiation à Ruby on Rails
date: 2015-03-09 08:00
author: jeremy
published: true
categories: [Rails]
---
Dans cet article, je vous propose de créer une page et d'éffectuer les tests de fonctionnement TDD.



<<
<em>Pour suivre ce cours il est plus que conseillé d’avoir sous la main <a href="http://french.railstutorial.org/chapters/beginning" target="_blank">ce lien</a> ou <a href="https://www.dropbox.com/sh/uuwaqjqbc8y3ybv/AACjqwYvxqHaXxADTjBp48-Ra?dl=0" target="_blank">ces fichiers pdf</a>, pour rappel, les cours sont basés dessus et cet article reprend le début du chapitre 3.</em>
>>
Ça y est vous avez écrit les tests ? Non ? Bon à demain alors. Non je déconne, pour ceux qui ont galéré, voici la correction.
<!--break-->

```ruby
require 'rails_helper'

RSpec.describe PagesController, type: :controller do

  describe "GET #home" do
    it "returns http success" do
      get :home
      expect(response).to have_http_status(:success)
    end
  end

  describe "GET #contact" do
    it "returns http success" do
      get :contact
      expect(response).to have_http_status(:success)
    end
  end

  describe "GET #about" do
      it "returns http success" do
        get :about
        expect(response).to have_http_status(:success)
      end
    end


end
```

Hé oui, c'est tout... C'était pas si compliqué si ? Bon, maintenant qu'on a écrit ces tests, il faut les tester. Vous savez comment on fait : **rspec spec/**
Si vous avez tout fait dans les règles de l'art, la commande devrait vous renvoyer une erreur.
Maintenant créons la page.

###La Page (avec un P majuscule)!
Pour la petite transition, il faut savoir qu'une "page" s'appelle en Rails, une Vue. Vous pourrez donc trouver ces "vues" dans le dossier .... "sample_app/app/views" !
Dans notre cas, un dossier a été créé lorsqu'on a lancé la commande **rails generate Pages ...**
Ce dossier, qui s'appelle **pages** contient nos deux pages déjà existantes, soit : **home** et **contact**.
Voyez un peu leur format : .html.erb. Tout le monde ici connait **html**. Pour le reste, **erb** permet simplement de pouvoir insérer du code **rails** dans une page **html **(merci pour cette grossière explication).
Créons donc notre page au même format, ça donnera donc : **about.html.erb**. Une fois créée, ouvrez la et insérez ceci :

```ruby
<h1>Pages#about</h1>
<p>Find me in app/views/pages/about.html.erb</p>
```

Pour ceux qui ne connaissent pas le **html**, sachez que la balise **h1** signale un titre de "hauteur" 1, dans l'échelle des titres (de **h1** à **h6**), c'est le plus haut, on s'en servira pour les titres principaux de nos pages web. La balise **p** signifie **paragraphe**, elle est là pour délimiter le paragraphe.
Maintenant ceci fait, testez votre page. Lancez votre commande et insérez comme d'habitude : **rails s** et rendez vous à cette adresse : <a href="http://localhost:3000/pages/home">**http://localhost:3000/pages/home**</a> . Cette adresse vous emmènera sur la page d'accueil que vous avez créé précédemment. Tout fonctionne bien ? Parfait, allez maintenant sur la page que l'on vien de créer : <a href="http://localhost:3000/pages/about">**http://localhost:3000/pages/about**</a> . Que se passe t'il ? Erreur ? Pourquoi ? Notre page est bien créée pourtant... Pour comprendre ce qu'il se passe il faut aller dans les configurations de routage de notre application. Où on trouve ça ? Ici : **sample_app/config/routes.rb**. Ce fichier contient toutes les chemins d'accès a vos pages. Vous remarquez qu'il en manque un non ? Et bien ajoutez le dernier, celui pour la page **about**.
Ha mais attendez, il faut aussi signaler à notre controlleur de pages que l'on en a ajouté une non ? Vous le trouverez ici : **sample_app/app/controllers/pages_controller.rb.** Il suffit de suivre la syntaxe ici aussi. Ne vous inquiétez pas si rien n'est écrit entre le **def/end**.
Maintenant vous pouvez accéder à votre page avec l'adresse précédente.

### **Le retour des tests.**
Notre page est enfin crée, récapitulatif, on a écrit nos tests (étape 1), on a vérifié qu'ils ne fonctionnaient pas (!!!étape 2!!!), on a créé notre page (étape 3) et maintenant, étape 4 on refait nos tests, lancez donc **rspec spec/**. Et si vous avez tout fait comme il le fallait vous ne devriez pas avoir d'erreur, sinon refaites tout depuis le début.
Un peu de fantasie, mettons un titre à notre page. Comment on fait ?
Avant tout, il faut savoir que Rails est très intelligent, et surtout très gentil, puisqu'il nous permet de ne pas copier plusieurs fois le même code. Comment il fait ? Nous avons 3 pages, la syntaxe d'**html** veut que le **doctype** soit identique sur toutes les pages. Pourquoi donc réécrire pareil sur les 3 fichiers ? Il suffirait de créer un 4ème fichier contenant le **doctype** et de faire une sorte de **require** sur les autres non ? Donc où trouver ce 4ème fichier ? Dans : **sample_app/app/views/layout/application.html.erb**.
Ouvrez ce fichier, vous voyez qu'il contient bien le **doctype **(vous voyez que je ne ment pas!).
Donc vous aurez sûrement remarqué que toutes nos pages s'appellaient **SampleApp**. C'est parce que le titre défini ici est valable pour toutes les pages. Pour commencer changeons ce titre par quelque chose de mieux : **Simple App du tutoriel Unruby** ... Non attendez !!!!
Et les tests ? On les écrit pas ? On se rend donc dans le fichier **pages_controller_spec.rb** et on ajoute un test. Ce test devra tester (...) si le titre de nos pages est bien ce que l'on attend. Pour ce faire, je vais vous aider un petit peu... Mais si vous en avez le courage, cherchez sur internet comment faire.









Sinon, voilà :

```ruby
require 'rails_helper'

RSpec.describe PagesController, type: :controller do
  render_views

  describe "GET #home" do
    it "returns http success" do
      get :home
      expect(response).to have_http_status(:success)
    end
    it "doit avoir le bon titre" do
      get :home
      expect(response.body).to include('<title> Simple App du tutoriel Unruby | Accueil</title>')
    end
  end

  describe "GET #contact" do
    it "returns http success" do
      get :contact
      expect(response).to have_http_status(:success)
    end
      it "doit avoir le bon titre" do
        get :contact
        expect(response.body).to include('<title> Simple App du tutoriel Unruby | Contact</title>')
      end
  end

  describe "GET #about" do
    it "returns http success" do
      get :about
      expect(response).to have_http_status(:success)
    end
    it "doit avoir le bon titre" do
      get :about
      expect(response.body).to include('<title> Simple App du tutoriel Unruby | À Propos</title>')
    end
  end
end
```

Avez vous remarqué la ligne 3 ? Vous avez vu que j'ai fait le fou en écrivant ces tests, j'ai même écrit le nom de la page à la suite !
Enregistrez et testez. C'est bon ? Erreur ? Maintenant on peux changer nos titres.
Revenez au fichier **application.html.erb**. Et mettez donc le titre **Simple App du tutoriel Unruby | Accueil**.
Validez et faites vos tests. Quoi ? Il n'y en a qu'un seul qui passe ? Pas normal ça ... Ah si, toutes les pages s'appellent **Accueil**... Comment faire pour que chaque page s'appelle différement. Pour ça il faut insérer une variable globale dans notre fichier et contenant le nom de la page. Pour ce faire on va dans le fichier **simple_app/app/controllers/pages_controller.rb** et on crée une variable globale contenant le nom de la page pour chaque page, ce qui devrait nous donner à la fin quelque chose comme ça :

```ruby
class PagesController < ApplicationController
  def home
    @title = "Accueil"
  end

  def contact
    @title = "Contact"
  end

  def about
    @title = "À Propos"
  end
end
```

Maintenant on retourne dans notre fichier contenant le **doctype** et dans la balise **title** on insère un peu de code **ruby** pour indiquer la variable globale. Un peu comme ça :

```ruby
<title>Simple App du Tutoriel Unruby | <%= @title %></title>
```

En effet, les balises **<%= **et **%> **permettent d'ajouter du code **ruby**.
D'ailleurs on peux retrouver cette ligne :

```ruby
<%= yield %>
```

Qui est normalement en ligne 8. Elle sert à que tout le code que vous avez écrit dans les pages **home, contact** et **about** se retrouve à cet endroit. Donc au final, notre fichier sera complet. La balise ligne 5 est une balise de sécurité, veillez à toujours la mettre (plus de détails dans le livre).
C'est fini pour ce chapitre 3 et pour aujourd'hui, vous pouvez envoyer vos changements sur git si ce n'est pas déjà fait et vous entrainer à faire d'autres pages. Je vous invite aussi à lire l'intégralité du cours fourni pour tous les détails.
Bye !
