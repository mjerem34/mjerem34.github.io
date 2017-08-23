---
layout: post
title: 40 - Comment mettre en place les TDD ? - Partie 1 - Initiation à Ruby on Rails
date: 2015-03-06 08:44
author: jeremy
published: true
categories: [Rails]
---
Dans cet article, on va parler d'une méthode de développement qu'on appelle **TDD** (**Test Driven Development**) ou en français **Développement Piloté par les Tests**.



<<
<em>Pour suivre ce cours il est plus que conseillé d’avoir sous la main <a href="http://french.railstutorial.org/chapters/beginning" target="_blank">ce lien</a> ou <a href="https://www.dropbox.com/sh/uuwaqjqbc8y3ybv/AACjqwYvxqHaXxADTjBp48-Ra?dl=0" target="_blank">ces fichiers pdf</a>, pour rappel, les cours sont basés dessus et cet article reprend le chapitre 3.</em>
>>
### **TDD, c'est quoi ?**
Concrêtement, TDD, voilà comment ça se passe :
<!--break-->

*
	* On écrit des tests avant d'écrire une seule ligne d'application.
	* On teste les tests (oO) pour être sûr qu'ils échouent.
	* On écrit juste le code suffisant pour passer les tests.
	* Si ça marche on peux refactoriser notre code, sinon c'est qu'il y a un souci, soit venant des tests, soit venant de l'application.
	* On teste notre application avec les tests écrits précédemment.

Ne vous prenez pas la tête encore avec la théorie, continuez même si vous n'avez pas compris, j'expliquerais au fur et à mesure. D'ailleurs si vous voulez de la théorie, allez voir <a href="http://www.wikiwand.com/fr/Test_Driven_Development" target="_blank">ici</a>.

###Rappelle toi l'été dernier.
Non, juste hier ça suffira. Vous vous rapellez les pages qu'on à réalisé avec cette comande :

```ruby
$ rails generate controller Pages home contact
```

Avant tout, commencez par supprimer les dossiers **helpers **et **views**. Nous n'en auront pas besoin dans ce tuto.
Ensuite, ouvrez le fichier se situant dans le dossier **controllers**. Vous pourrez trouver une explication à tout ce code en parcourant le livre fourni. Mais il faut tout de même savoir que "ce code" permet de vérifier si chaque page de notre application renvoie une réponse correcte. Ce qui voudrait dire que dans sa globalité, elles fonctionnent. Vous pouvez remarquer à quelle partie appartient quelle page aux lignes 5 et 12.
Donc, récapitulatif, nos tests sont écrits, nos pages sont écrites elles aussi... On peux tester tout ça non ? On peux le faire dès maintenant en exécutant ceci :

```ruby
$ rspec spec/

/home/jeremy/Desktop/sample_app/db/schema.rb doesn't exist yet. Run `rake db:migrate` to create it, then try again. If you do not intend to use a database, you should instead alter /home/jeremy/Desktop/sample_app/config/application.rb to limit the frameworks that will be loaded.
..
Finished in 0.01195 seconds (files took 1.48 seconds to load)
2 examples, 0 failures
```

D'ailleurs, si comme moi, vous avez une alerte, suivez les instructions et lancez la commande indiquée **rake ****db:migrate**.

Ici, la dernière ligne nous indique que tout s'est bien déroulé. Les tests sont passés avec succès.
Je vous conseille de lire le livre si vous voulez des notions plus avancées sur le sujet des tests.

###
###Bon, on la crée c'te page ?!
Non.

###Ha oui, les tests d'abord.
Tout à fait, maintenant qu'on a testé nos pages **home** et **contact** il nous manque à créer la page **about**(à propos) et ses tests. Donc on commence par les tests. Vous pourrez les deviner facilement, prennez le temps de bien comprendre la structure des autres tests. Je ne donnerais d'ailleurs pas d'explication pour les créer, sauf pour les plus novices, sachez qu'ils s'écrivent toujours dans le même fichier, soit **/sample_app/spec/controllers/pages_controller_spec.rb**
Ha et ... Il ne sert à rien de vous référer au livre ... Il utilisait une ancienne version de **Rspec** et de **Rails
