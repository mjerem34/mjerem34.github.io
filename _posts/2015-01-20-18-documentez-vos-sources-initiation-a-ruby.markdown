---
layout: post
title: 18 - Documentez vos sources - Initiation à Ruby
date: 2015-01-20 08:00
author: jeremy
published: false
categories: [Initiation à Ruby]
---
Je sais je sais. Mais j'ai bien réfléchi et c'est bien mieux comme ça. Les articles "Bonne résolution" ne paraîtront plus chaque jour. Je sais que c'est très important d'écrire, surtout pour un développeur, mais à l'heure actuelle, mon objectif premier est de connaître les bases de Ruby le plus rapidement pour pouvoir mettre en exécution tout ce que j'apprends. On a enfin terminé les exceptions, maintenant on s'attaque à la documentation !


Les commentaires dans un code sont une chose essentielle, mais ça vous le saviez déjà. Cette "documentation" un peu précaire peut prendre une forme un peu plus lisible.

###Rdoc
Soit, deux fichiers :
**maClasse.rb :**



```ruby
#Ma classe
class MaClasse
	#Ma méthode
	def methode
	end
end
```
<!--break-->

Et :
**autreClasse.rb :**



```ruby
#Mon autre classe
class AutreClasse
	#Mon autre méthode
	def autreMethode
	end
end
```


Oublions le code un petit moment et intéressons nous au shell. Dans cette étape nous allons donc créer une documentation pour notre code. Voilà comment ça se passe :
Ouvrez votre shell favori puis dirigez vous dans le dossier contenant les deux fichiers : **maClasse.rb **et **autreClasse.rb**.
Une fois ceci fait, lancez simplement la commande **rdoc**. Vous devriez obtenir quelque chose du genre : <a href="https://unruby.files.wordpress.com/2015/01/rdoc.png"><img class="aligncenter size-full wp-image-439" src="https://unruby.files.wordpress.com/2015/01/rdoc.png" alt="rdoc" width="634" height="424" /></a>
A ce moment là, un répertoire **doc** est créé contenant des pages HTML. La page principale étant **index.html**. Ouvrez ce fichier et vous tomberez sur une page à peu près similaire à la mienne :
<a href="https://unruby.files.wordpress.com/2015/01/rdoc_html.png"><img class="aligncenter size-full wp-image-440" src="https://unruby.files.wordpress.com/2015/01/rdoc_html.png" alt="rdoc_html" width="634" height="585" /></a>
Et c'est donc ici que la magie opère, sur votre gauche vous apercevrez toutes les classes/modules/méthodes employées dans votre code. En cliquant dessus vous obtiendrez le détail de chacune comme ceci :<a href="https://unruby.files.wordpress.com/2015/01/rdoxhtmlautreclasse.png"><img class="aligncenter size-full wp-image-441" src="https://unruby.files.wordpress.com/2015/01/rdoxhtmlautreclasse.png" alt="rdoxhtmlautreclasse" width="634" height="275" /></a>
Article assez court aujourd'hui je manque cruellement de temps mais ça ira mieux dans les prochains jours.
À demain !
