---
layout: post
title: 44 - Comment rendre votre code plus clair en Rails ? - Initiation à Ruby On Rails
date: 2015-03-12 08:00
author: jeremy
published: true
categories: [Rails]
---
Dans cet article, on va minifier notre code pour essayer d'y voir plus clair. Pour cela on se servira des *partiels*.
<<
<em>Pour suivre ce cours il est plus que conseillé d’avoir sous la main <a href="http://french.railstutorial.org/chapters/beginning" target="_blank">ce lien</a> ou <a href="https://www.dropbox.com/sh/uuwaqjqbc8y3ybv/AACjqwYvxqHaXxADTjBp48-Ra?dl=0" target="_blank">ces fichiers pdf</a>, pour rappel, les cours sont basés dessus et cet article reprend le chapitre </em><em>5</em><em>.</em>
>>
Les développeurs Rails sont des gens propres. Et je vais vous le prouver !
### **Stylesheets**
Vous avez pû voir qu'on à ajouté une feuille de style dans le dernier tutoriel, ce qui nous donne maintenant une balise **head** bien chargée. Mais on peux remédier à cela grâce aux **partiels**. Créons en un ! Pour ça, rendez vous dans le dossier **app/views/layouts** tout simplement et créez un fichier qui s'appellera : **_stylesheets.html.erb** . Remarquez l'underscore au début ! Il est la pour signaler que c'est un **partiel**. Aller, et puisque on est des fous, faisons en deux de plus ! Un pour le **header** et un pour le **footer** se sera déjà bien.
Une fois que vous avez fait ça, retournez dans votre fichier **layout****s**** application**.
Prélevez simplement les parties de code que vous voulez transférer dans les autres fichiers, pour nous on va récupérer donc ces trois parties :

```html
<%= stylesheet_link_tag 'bootstrap.css', :media => 'screen' %>
<%= stylesheet_link_tag 'style.css', :media => 'screen' %>
```
<!--break-->



```html
<header>
  <%= image_tag("mwitter.jpg", :alt => "Mwitter", :class => 'img-rounded', size: "200x200")%>
  <nav>
    <ul class="unstyled inline">
      <li><%= link_to "Home", 'home' %></li>
        <li><%= link_to "Signup", 'signup' %></li>
          <li><%= link_to "Login", 'Login' %></li>
    </ul>
  </nav>
  <h1>Welcome on Mwitter</h1>
</header>
```



```html
<footer>
  <nav>
    <ul>
      <li><%= link_to "Home", 'home' %></li>
      <li><%= link_to "Contact", 'contact' %></li>
      <li><%= link_to "About", 'about' %></li>
      <li><%= link_to "Help", 'help' %></li>
    </ul>
  </nav>
</footer>
```

Copiez maintenant les trois parties récupérées dans leur propre fichier respectif. Sauvegardez tout et retournez dans le fichier **layouts application**.
Vous devriez avoir quelque chose de bien vide maintenant. Ne vous inquiétez pas.
Pour terminer on va faire un appel à un **helper** qui lui se chargera d'aller chercher le fichier en question.
Ci-contre, l'**helper** pour les feuilles de style :

```html
<%= render 'layouts/stylesheets' %>
```

Vous le placerez donc dans la partie **head** du code, comme ceci :

```html
<!DOCTYPE html>
<html>
<head>
<title><%= title %></title>
<%= csrf_meta_tag %>
<%= render 'layouts/stylesheets' %>
</head>
```

Une fois fini, vous devriez obtenir un code assez clair et ressemblant à ceci :

```html
<!DOCTYPE html>
<html>
<head>
<title><%= title %></title>
<%= csrf_meta_tag %>
<%= render 'layouts/stylesheets' %>
</head>
<body>
  <div class="container"> <!--=========CONTAINER 710PX========== -->
    <%= render 'layouts/header' %>


    <div class="content"> <!--==========CONTENT=========== -->
      <%= yield %>
      <p>You can Sign Up by clicking the button blue !</p>
      <%= link_to "Sign Up", 'signup', :class => 'btn btn-large btn-primary'%>
    </div> <!--==========END-content-END=========== -->


    <%= render 'layouts/footer' %>
  </div> <!--=========END-container 710px-END========== -->
</body>
</html>
```

Pour ceux qui ne connaissent pas du tout le html, faîtes un tour rapide sur OpenClassRooms ou sur le livre fourni pour connaitre les bases, ça pourra vous aider.
Bye !
