---
layout: post
title: 30 – Les interfaces graphiques Partie 6/? – Initiation à Ruby
date: 2015-02-12 08:00
author: jeremy
published: false
categories: [Initiation à Ruby]
---
### **Scale**
Un composant **scale** est un bouton glissant allant d'une valeur à une autre (ex : de 0 à 100) permettant à l'utilisateur, de choisir un nombre présent dans cette intervale.


<a href="https://unruby.files.wordpress.com/2015/02/scale.png"><img class="aligncenter size-full wp-image-547" src="https://unruby.files.wordpress.com/2015/02/scale.png" alt="scale" width="297" height="475" /></a>On paramètre les valeurs de début et de fin avec **from** et **to**. **Orient **ajuste la disposition (verticale ou horizontale). Je n'ai pas mis l'option **resolution **ici mais elle sert à faire des intervalles, au lieu de compter de 1 en 1, la barre peux avancer de 2 en 2. Et pour finir, la variable pour stocker la valeur.
Sans oublier les méthodes **get** et **set** qui permettent de récupérer et définir la valeur en cours.
<!--break-->

###Text
Ce composant permet d'afficher un champ texte où l'utilisateur peut écrire. **Width **définit la largeur du champ et **height** définit le nombre de lignes. On peux accéder à la valeur avec l'accesseur **value**.
