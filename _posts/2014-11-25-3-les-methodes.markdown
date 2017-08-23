---
layout: post
title: 3 - Les méthodes
date: 2014-11-24 10:50
author: jeremy
published: true
categories: [Initiation à Ruby]
---
Alors une méthode c'est quoi ? Pas la moindre idée ? Pour ceux qui viendraient de PHP, on pourrais comparer une méthode à une function ( ). Pour les autres une méthode est un bloc d'instruction commençant par def, qui se termine par end et qui contient des .... instructions !
    Comme on aime faire les choses dans la simplicité chez Unruby voici comment on crée une méthode.
```ruby
  def hello() #Création de la méthode "hello" avec def
    puts "Hello world" #Contenu de la méthode
  end #fin de la méthode

  hello() #exécution de la méthode
  #=> Hello World
```
<!--break-->

Voyez l'image, ici la méthode Hello affiche Hello World via puts.
Veuillez noter que j'ai fait une petite erreur dans cette méthode. Laquelle ?

#### Hello who ?
    Encore une fois les utilisateurs PHP se sentiront chez eux à un argument près.
    Alors déjà pourquoi donner des arguments aux méthodes ? Imaginez votre espace utilisateur. Il vous affiche "Bonjour Georges". Et bien le développeur se servira d'une méthode prenant pour argument -ici who- qui ira chercher dans la base de donnée votre nom. Enfin, je pense.
```ruby
  def hello(who)
    puts "Hello #{who} !" #utilisation de la variable passée en paramètre
  end
  hello("Doctor")
  #=> Hello Doctor !
```

    Comme vous pouvez le voir notre précédente méthode prend en argument who. Avec un peu de logique on peux aisaiment comprendre qu'à la ligne 3, puts affiche ce qui est présent dans la variable who.
    Mais y'a quoi dans cette variable ? Et bien notre fameux "Doctor" de la ligne 7.
    Récapitulatif. On crée une méthode prenant un argument (que l'on pourrait comparer a une variable) ligne 1. On donne l'instruction en ligne 3. Puis on fini par exécuter la méthode avec ce que contient notre argument ou variable.
    Vous devez vous en douter maintenant, oui, notre méthode peux prendre en compte plusieurs arguments. Il suffit pour cela de les ajouter les uns à la suite des autres comme ceci :
```ruby
  def hello(firstPerson, second_person, thirdPerson, fourthPerson, baby)
    puts "Hello #{firstPerson}, #{second_person}, #{thirdPerson} !"
    puts "Hi #{fourthPerson} and #{baby}"
  end

  hello("homer", "marge", "bart", "lisa", "maggie")
  #=> Hello homer, marge, bart !
  #=> Hi lisa and maggie
```

    Vous avez surement remarqué quelque chose dans cette capture d'écran. Je n'ai pas mis de parenthèses lors de l'exécution de la méthode. Pourquoi ? Tout simplement car ce n'est pas obligé donc je montre les différentes techniques. Et aussi parce que lorsque je les met j'ai une erreur. Donc autant les enlever, mais si vous pouvez les mettre n'hésitez pas, mettez les !

#### Prédéfinis ?
    Nous pourrons avoir besoin que certains arguments soient parfois prédéfinis. La méthode est très simple. Il suffit de faire les choses de la façon la plus logique que vous pensez. Simplement comme si c'était une variable, ex : first_arg = "I" .
```ruby
  def multiArg(firstArg = "I", secondArg = "love", thirdArg = "Ruby")
    puts "Voila les arguments prédéfinis : #{firstArg}, #{secondArg}, #{thirdArg}"
  end

  multiArg()
  #=> Voilà les arguments prédéfinis : I love Ruby
```
    Les deux premières lignes sont ce que l'on appelle des commentaires magiques, je les ai découvert après avoir subi une erreur ligne 6 pour le mot "prédéfinis" qui n'acceptais pas les accents.
    Pour revenir aux arguments, il faut préciser aussi que même si ce sont des valeurs par défaut, elles peuvent être remplacées par une autre.

```ruby
  def multiArg(firstArg = "I", secondArg = "love", thirdArg = "Ruby")
    puts "Voila les arguments prédéfinis : #{firstArg}, #{secondArg}, #{thirdArg}"
  end

  multiArg("You", "Hate", "PHP")
  #=> Voilà les arguments prédéfinis : You Hate PHP
```


    J'ai donc remplacé les arguments "I", "love", "Ruby" par mes trois entrées lors de l'exécution.
