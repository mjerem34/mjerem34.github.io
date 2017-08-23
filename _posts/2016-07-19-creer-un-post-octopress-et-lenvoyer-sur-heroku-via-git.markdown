---
layout: post
title: "Créer un post Octopress et l'envoyer sur heroku via git"
date: 2016-07-19 11:16:02 +0200
author: jeremy
comments: true
categories:
---

* ```
  $ rake new_post["Créer un post Octopress et l'envoyer sur heroku via git"]
  ```
* Modifier le fichier se situant à :
  * ```
    source/_posts/2016-07-19-creer-un-post-octopress-et-lenvoyer-sur-heroku-via-git.markdown
    ```
* <!--break-->
```
  $ rake generate
  ```
* ```
  $ git add .
  ```
* ```
  $ git commit -m "Ajout page Créer un post Octopress et l'envoyer sur heroku via git"
  ```
* ```
  $ git push heroku master
  ```
