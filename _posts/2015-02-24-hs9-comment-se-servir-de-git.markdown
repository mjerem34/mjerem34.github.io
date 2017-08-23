---
layout: post
title: HS9 - Comment se servir de GIT ?
date: 2015-02-24 08:00
author: jeremy
published: true
categories: [commit, GIT, Hors série, Hors série, Installation, merge, push]
---
On commence donc ce nouveau tutoriel sur **Rails** en prennant les devants, on va s'occuper pour l'instant d'installer **GIT**.


###Git, c'est quoi ?
**Git** c'est un **système de contrôle de version** créé par **Linus** **Torvalds** (Le créateur de **linux**, rien que ça.). Pour les plus néofites, un système de contr.... blablabla c'est un outil qui va nous permettre de sauvegarder des versions de notre application tout au long de son développement. Ca peut paraître nul mais si vous modifiez votre application de telle sorte qu'elle **ne fonctionne plus**, vous serez bien content de revenir à la version précédente pour ne pas avoir à tout **réécrire**.


<!--break-->


###Git et GitHub, c'est quoi la différence ?
En fait **GitHub** est un **service de partage de code**, autrement dit, un réseau social de code s'appuyant sur l'outil Git. Cela permet le partage de votre application à des personnes du monde entier.




###Installation
On reviendra peut être un peu plus tard sur les details théoriques mais pour l'instant on va s'occuper d'installer Git.
Rendez vous simplement sur <a href="http://git-scm.com/downloads" alt="git-scm">http://git-scm.com/downloads</a> et choisissez votre système. Si il n'est pas présent dans la liste suivez ces étapes :

*
	*
Eteignez ce qui vous sert d'ordinateur. (Altaïr ?)

	*
Sortez de chez vous.

	*
Prenez un train direction Nevers.

	*
Elevez des chêvres.





Si l'installation s'est bien déroulée, poursuivez avec la configuration :

*
	* Ouvrez votre **invite** **de** **commande**, ou **shell**.
	* Tapez ceci : **git config --global user.name "**<em>**VOTRE NOM**</em>**"**
	* Puis ceci : **git config --global user.email "**<em>**VOTRE ADRESSE EMAIL**</em>**"**




Créez un compte **GitHub** sur <a href="https://github.com/">https://github.com/</a>. Et créez des "**Repositories**". En passant, les repositories sont des sortes de dossier dans lequels on place notre application. On peux en avoir autant que l'on souhaite du moment qu'on les rend public, c'est à dire que tout le monde peut les voir. Si on veux les garder privés on peux uniquement en avoir 5 ou payer un forfait mensuel pour en débloquer d'autres.
Pour créer un repository, une fois connecté, cliquez sur le **"+"** en haut a droite de la fenêtre et cliquez sur **"New Repository..."**.
Lorsque vous êtes à l'étape suivante, que vous avez tout validé, **récupérez le lien du repo** qui devrait resembler à cela : `https://github.com/votreidentifiant/nomdurepository.git`.
Allez dans le dossier que vous souhaitez envoyer vers GitHub (servira plus tard pour les applications que l'on réalisera). Créez un dossier test pour le moment. Donc, allez dans ce dossier et faites : **git init **
Cette commande servira à désigner le dossier que l'on liera au repository GitHub.
Ajoutez ensuite les fichiers à la liste d'attente pour l'envoi avec : **git add .**
Le point est important puisqu'il indique à Git qu'il sélectionne tout le dossier. Pour indiquer ensuite à Git de sauvegarder ces fichiers sur votre ordinateur sous forme de version on utilisera : **git commit -m "Message à ajouter comme description"**. A ce stade, les données ne sont pas encore accessibles sur GitHub donc si vous formattez votre ordinateur, vous perdrez tout.
Réouvrez votre invite de commande et configurez **GitHub** avec **Git** comme ceci (vous devrez mettre votre identifiant et mot de passe GitHub pour que l'envoi puisse se faire :

```ruby
$ git remote add origin <lien_du_repository.git>
$ git push origin master

#Sortie : Username for 'https://github.com': VOTRE_IDENTIFIANT_GITHUB
#Sortie : Password for 'https://mjerem34@github.com': VOTRE MOT_DE_PASSE_GITHUB
#Sortie : Counting objects: 64, done.
#Sortie : Delta compression using up to 4 threads.
#Sortie : Compressing objects: 100% (53/53), done.
#Sortie : Writing objects: 100% (64/64), 16.40 KiB | 0 bytes/s, done.
#Sortie : Total 64 (delta 2), reused 0 (delta 0)
#Sortie : To https://github.com/mjerem34/first_app.git
#Sortie :  * [new branch]      master -> master
```

Ces deux commandes indiquent à Git qu'il doit se servir de GitHub pour stocker les fichiers et envoie les fichiers vers ce dernier. Maintenant, vous pouvez vous féliciter, vous avez effectué votre premier push sur GitHub !
Vous pouvez enfin accéder à vos fichiers sur internet.

###Branch
Git permet aussi (décidemment, c'est un outil génial !) de créer des branches, c'est à dire des copies de votre répertoire principal qui vous permettra de faire des modifications sans affecter les principaux fichiers. LA commande :

```ruby
$ git checkout -b modify-README
#Sortie : Switched to a new branch 'modify-README'
git branch
#Sortie : master
#Sortie : * modify-README
```

C'est la première commande ici qui s'occupe de créer la copie du repo et d'y basculer automatiquement, l'autre branche est suspendue et sauvegardée.
La seconde permet simplement de lister toutes nos branches, l'astérisque présent devant indique la branche sur laquelle nous nous trouvons actuellement.

###Commit
Une fois la nouvelle branche crée on peux modifier notre fichier, ici README.rdoc.
La commande **git status** permet de voir les changements qui ont eu lieu depuis le dernier **commit**.
Une fois le fichier modifié, on obtient ceci :

```ruby
On branch modify-README
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   README.rdoc

no changes added to commit (use "git add" and/or "git commit -a")
```


Enfin, un truc du style ! Ne vous etonnez pas si vous avez un truc à peu près différent. Pour l'exemple j'ai juste remplacé le contenu du fichier par "Hi !".
Maintenant il suffit d'utiliser la commande indiquée pour envoyer les fichiers au commit.
On pourrait utiliser **git add** mais **git commit -a** est une sorte de raccourci à cette commande. **Attention cependant, si vous avez inséré de nouveaux fichiers il faudra taper la commande git add.**

```ruby
$ git commit -a -m "Modifying README"
[modify-README 53fc07e] Modifying README
 1 file changed, 1 insertion(+), 28 deletions(-)
 rewrite README.rdoc (100%)
```


### **Merge**
Ensuite, si on souhaite fusionner les fichiers, il suffit d'utiliser la commande : **git checkout master** qui vous renvérra vers la branche principale et enfin : **git merge modify-README**.
Après avoir fusionné les changements, on peux supprimer la branche que l'on souhaite. Vous n'êtes pas obligés de le faire mais voici tout de même comment on fait :
Pour supprimer la branche **modify-README** on utilisera : **git branch -d modify-README**
Cette commande, à la différence de sa soeur (**git branch -D modify-README**) supprime la branche uniquement si les changements ont été fusionnés. **-D** supprimera la branche même si les changements n'ont pas été fusionnés.

###Push
On peux finalement renvoyer les modifications à GitHub avec **git push ****origin master** qui enverra uniquement la branche master ou bien utiliser **git push** qui enverra la branche courrante ou pour finir **git push origin modify-README** pour envoyer la branche ayant le même nom.
