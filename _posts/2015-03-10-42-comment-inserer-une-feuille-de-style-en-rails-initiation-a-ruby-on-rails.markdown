---
layout: post
title: 42 – Comment insérer une feuille de style en Rails – Initiation à Ruby on Rails
date: 2015-03-10 08:00
author: jeremy
published: true
categories: [Rails]
---
Dans cet article, nous allons parler de l'intégration de feuilles de style CSS dans un fichier **erb**. Mais ne vous inquiétez pas, cela ne nous prendra pas sept millions et demi d'années.

<<
<em>Pour suivre ce cours il est plus que conseillé d’avoir sous la main <a href="http://french.railstutorial.org/chapters/beginning" target="_blank">ce lien</a> ou <a href="https://www.dropbox.com/sh/uuwaqjqbc8y3ybv/AACjqwYvxqHaXxADTjBp48-Ra?dl=0" target="_blank">ces fichiers pdf</a>, pour rappel, les cours sont basés dessus et cet article reprend le chapitre </em><em>4</em><em>.</em>
>>
Étant donné que nous avons déjà les bases de Ruby, nous n'allons pas finir ce chapitre 4 qui ne serait que radoter. Et vu que je n'ai pas 42 ans, je ne radote pas !
<!--break-->

###Déclarer une feuille de style CSS en Rails
J'aime bien la cuisine pas vous ?
Ingrédients :

*
	* <a href="http://getbootstrap.com/2.3.2/assets/bootstrap.zip" target="_blank">Bootstrap</a>
	* Un gestionnaire de fichiers Zip
	* Votre application crée via **rails new qui da****te d'hier**. J'espère que vous ne jettez pas vos ingrédients pas terminés !
	* Une console de commande
	* Un éditeur de texte tel que <a href="https://atom.io/" target="_blank">Atom</a> (très bon, possibilité d'ajouter pleins d'épices additionnelles sans en altérer le goût).
	* Un clavier (vous pouvez essayer sans mais c'est à vos risques et perils)

Temps de préparation : 10 minutes | Temps de cuisson : 5 minutes

### **Étape 1**
Ouvrez votre invite de commande et faites préchauffer votre serveur avec la commande **rails s** et vérifiez que tout fonctionne correctement. Jettez un oeil à la police d'écriture de votre page **home**, elle risque de changer.

### **Étape 2**
Une fois que vous avez téléchargé Bootstrap, ouvrez le avec le gestionnaire prévu à cet effet. Attention, toutes les parties de cet ingrédient sont à garder, elles pourront servir pour la suite. Dézippez donc tout le contenu du dossier **Bootstrap** présent dans l'archive dans le dossier **sample_app/app/assets**. Normalement, des dossiers sont déjà présents, faites les simplement fisionner.

### **Étape 3**
Allez dans le dossier **sample_app/app/views/layouts**. Ouvrez le fichier **application.html.erb**. Insérez cette partie de code :

```ruby
<%= stylesheet_link_tag 'bootstrap', :media => 'screen' %>
```

entre les balises **<head></head>**. Et juste après la <a href="http://unruby.com/41-comment-mettre-en-place-les-tdd-partie-2-initiation-a-rails" target="_blank">balise de sécurité</a>.
Vous remarquerez aussi que je n'ai pas précisé la nature du fichier comme ceci **bootstrap.css**. Il n'y à pas besoin de mettre la racine mais vous pouvez tout de même la garder pour vous en servir dans d'autres programmes.

### **Étape 4**
Allez dans le dossier **sample_app/config/initializers** et ouvrez le fichier assets.rb. Ajoutez ensuite la ligne :

```ruby
Rails.application.config.assets.precompile += %w( bootstrap.css)
```

Vous pouvez aussi simplement modifier la dernière ligne pour qu'elle corresponde et enlever le # avant.

### **Étape 5**
Relancez le serveur Rails. Retournez sur votre navigateur et actualisez la page, vous devriez y voir un changement.

### **Étape 6 (optionnelle)**
Si votre page manque de gout vous pouvez toujours rajouter un peu d'épices en allant dans le fichier ** sample_app/app/views/pages/home.html.erb** et en ajoutant à la balise **<p>** une classe comme ceci :

```html
<p class="text-warning">Find me in app/views/pages/home.html.erb</p>
```

Mais ne vous inquiétez pas, il y en a pour tous les gouts :

```html
<p class="muted">Find me in app/views/pages/home.html.erb</p>
<p class="text-error">Find me in app/views/pages/home.html.erb </p>
<p class="text-info">Find me in app/views/pages/home.html.erb</p>
<p class="text-success">Find me in app/views/pages/home.html.erb</p>
```

<<
« Quarante-deux ! cria Loonquawl. Et c'est tout ce que t'as à nous montrer au bout de sept millions et demi d'années de boulot ?
— J'ai vérifié très soigneusement, dit l'ordinateur, et c'est incontestablement la réponse exacte. Je crois que le problème, pour être tout à fait franc avec vous, est que vous n'avez jamais vraiment bien saisi la question. »
>>
Bye !
