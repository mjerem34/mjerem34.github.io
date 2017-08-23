---
layout: post
title: 13 - L'héritage - Initiation à Ruby
date: 2014-12-16 08:30
author: jeremy
published: true
categories: [Initiation à Ruby]
---

**L'héritage** est une notion très importante dans la **programmation orientée objet**. C'est ce que l'on va découvrir dans cet article.

Plantons le décor...

Imaginez une mère et son fils. La science a démontré qu'un fils possède forcément quelques uns des gênes de sa mère avec d'autres en plus. Ca s'appelle **l'héritage**. En programmation c'est quasiment pareil. Lorsque l'on crée une classe, nous créons la classe mère. Voyez ça comme cela :

<!--break-->

```ruby
class Mother
    def initialize(hair, eyes, name)
        @hair = hair
        @eyes = eyes
        @name = name
    end
    def description
        puts "My name is #{@name}, i have #{@hair} hair and #{@eyes} eyes."
    end
    def say_hello
        puts "Hello !"
    end
end

mary = Mother.new("blond", "blue", "Smith")
mary.say_hello
#Sortie : Hello !
mary.description
#Sortie : My name is Smith, i have blond hair and blue eyes.
```


Ici notre Mother a les cheveux blonds, les yeux bleus et s'appelle Smith. Il s'agit ici d'une simple déclaration d'objet et de sa classe, on a déjà vu ça dans l'article précédent.

Maintenant je voudrais créer une classe fille. Et c'est là que ça devient difficile.
 On ne peux pas simplement créer une classe en dessous qui porterait un autre nom comme ça :


```ruby
class Son
    def initialize(hair, eyes, name, height)
        @hair = hair
        @eyes = eyes
        @name = name
        @height = height
    end
end

john = Son.new("blond", "grey", "Smith", 184)
john.say_hello
#Sortie : heritage.rb:47:in `<main>': undefined method `say_hello' for #<Son:0x0000000236af40> (NoMethodError)
john.description
#Sortie : heritage.rb:42:in `<main>': undefined method `description' for #<Son:0x00000001afd448> (NoMethodError)
```

Sinon vous aurez ces erreurs là et rien ne fonctionnera.

Pour ce faire il faut donc procéder de la sorte :



```ruby
class Daughter < Mother
    def initialize(hair, eyes, name, height) super(hair, eyes, name)
        @height = height
    end
    def description
        puts "My name is #{@name}, i have #{@hair} hair, i have #{@eyes} eyes and i am #{@height} centimeters"
    end
end

alex = Daughter.new("blond", "brown", "Smith", 158)
alex.say_hello
#Sortie : Hello !
alex.description
#Sortie : My name is Smith, i have blond hair, i have brown eyes and i am 158 centimeters
```


###Surcharge de constructeur
Ici je crée donc ma classe fille appelée Daughter. Pour indiquer que c'est une classe fille, je l'indique avec l'opérateur **<**. Je fais ensuite une **surcharge du constructeur**. A quoi ça sert ?

Ca sert à rajouter des arguments pour la classe fille en reprenant ceux de la classe mère. Je reprends donc les mêmes arguments que la classe Mother en rajoutant "height". Ensuite, pour indiquer que les autres arguments appartiennent à la classe Mother je me sert du mot-clé "**super**" en suivant la syntaxe correcte. Il faut bien sûr ajouter ensuite le transfert de variable, comme dans la classe mère.
<<Attention : il faut faire très attention à coller la première parenthèse avec le nom de la méthode sinon il en sortira une erreur !

Conseil : Je vous conseille, lors de la création d'une méthode d'écrire directement le "end" qui la termine pour éviter de l'oublier.>>

###Surcharge de méthode
Vous aurez sûrement remarqué que j'ai recréé la méthode "description". En fait, j'ai fait une **surcharge de méthode. **Ca consiste à récrire une méthode déjà présente dans la classe mère. Sauf que seulement la classe fille aura accès à cette "nouvelle version" de la méthode. Encore une fois, c'est lié à l'ordre d'exécution. Même si je réexécute la méthode "mary.description" j'aurais toujours le même résultat.

En revanche vous pouvez voir aussi que la classe fille accède, elle, aux méthodes de la classe mère. C'est pourquoi lorsque je fais "alex.say_hello" Alex dit "Hello !".

Et si je ne veux pas tout récrire ?


```ruby
class Daughter < Mother
    def initialize(hair, eyes, name, height) super(hair, eyes, name)
        @height = height
    end
    def description
        super
        puts "And i am #{@height} centimeters."
    end
end

alex = Daughter.new("blond", "brown", "Smith", 158)

alex.description
#Sortie : My name is Smith, i have blond hair and brown eyes.
#Sortie : And i am 158 centimeters.
```


Si je ne veux pas tout récrire, je me sert aussi du mot-clé "super" !

C'est super non ? Chut ...

Ici j'ai repris ma classe Daugther sans récrire la classe Mother, vous la retrouverez plus haut.

Dans la méthode description qui est surchargée j'ai utilisé "super" ce qui me renverra le résultat de la méthode présente dans Mother. Arrête j'ai la tête qui tourne.

Je peux ensuite insérer une nouvelle fonctionnalité à ma méthode et l'exécuter.
###
###Modification de classe sur un objet
Vous avez vu dans les bouts de code précédents que lorsque alex say_hello, j'ai en sortie "Hello !". Jusque la tout est normal. J'ai envie de changer et que dorénavant, alex ne dise plus la même chose.
Ruby permet de faire ça aussi, oui. Je peux modifier la méthode uniquement pour un objet choisi.
Zoom :


```ruby
class << alex
    def say_hello
        puts "您好"
    end
end
alex.say_hello
#Sortie : 您好
mary.say_hello
#Sortie : Hello !
```


Ici c'est avec l'opérateur << que je redéfinis la méthode "say_hello" uniquement pour alex. Vous voyez bien que lorsque je fais "mary.say_hello" j'ai bien en sortie "Hello !". Est-ce que je parle en chinois ou vous comprenez ?
