---
layout: post
title: 17 – Exceptions Partie 2/5 – Initiation à Ruby
date: 2015-01-12 08:00
author: jeremy
published: true
categories: [Initiation à Ruby]
---
### **The interceptor.**
Maintenant que l'ont sait comment afficher des erreurs quand on le veux, il faut aussi savoir qu'on peux afficher ce que l'on veux à la place de l'erreur traditionnelle. Cela peut aller d'un simple message personnalisé jusqu'à un message qui donnera plus de précision sur l'erreur. Je vous laisse deviner le quel sera le plus utilisé à l'avenir ...

Le message personnalisé bien sûr ! On va donc commencer par ça. Voyons ensemble :
<!--break-->


```ruby
class TestError
  def hello(person)
    puts "Hello #{person}"
    #SORTIE : Hello
    if (person.nil?)
      raise
    end
  end
end

begin
  test = TestError.new
  test.hello(nil)
rescue
  puts "Fatal error, computer exploding !"
end
#SORTIE : Fatal error, computer exploding !
```

On retrouve notre petit bout de code du début avec une petite nouveauté à la fin : le bloc **begin/end** et **rescue**.
**Rescue** permet de remplacer le message d'erreur par un joli message personnalisé, évidemment le but n'est pas de faire joujou avec comme je l'ai fait dans l'exemple mais plutôt d'écrire quelque chose qui pourra nous informer sur la nature de l'erreur.


```ruby
begin
  test = TestError.new
  test.hello(nil)
rescue
  puts "Fatal error, computer exploding ! Error type : #{$!.class}"
end
#SORTIE : Fatal error, computer exploding ! Error type : RuntimeError
```

Ligne 5 on peux remarquer le fameux **$!** qui correspond à l'erreur en cours. Le **.class** quant à lui affichera la classe de l'erreur.
Une alternative est possible pour éviter d'utiliser **$!** :


```ruby
begin
  test = TestError.new
  test.hello(nil)
rescue => e
  puts "Fatal error, computer exploding ! Error type : #{e.class}"
end
#SORTIE : Fatal error, computer exploding ! Error type : RuntimeError
```

 Ici j'utilise la variable **e** pour stocker le contenu de l'erreur. Donc au lieu d'écrire **$!** on écrira **e**. Que quelqu'un me corrige mais je crois que la convention veut qu'on utilise **e** pour l'erreur courante.
