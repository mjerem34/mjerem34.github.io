---
layout: post
title: Comment créer deux listes liées avec Ruby On Rails et Ajax ?
date: 2015-10-02 08:00
author: jeremy
published: true
categories: [Uncategorized]
---
Ça faisait super longtemps que je n'avais pas écrit pour le blog ! Et ça fait plaisir de recommencer un peu.

Petite explication au sujet de cet article :

Je suis en train de créer une application de gestion de tickets d'incidents (kézako?). Pour ceux qui ne connaîtraient pas, allez jeter un œil à GestSup, dont je me suis inspiré (dont je salue les créateurs).

Donc j'ai du passer par l'étape de création de listes liées. Deux jours après, j'en suis ressorti vainqueur !

Voici donc ma solution :

<!--break-->


Petit rappel sur la structure de l'application :

Base de données en MYSQL structurée ainsi (uniquement les parties dont on aura besoin):

Une table 'Incidents' :
*
	* id
	* title
	* content
	* category_id
	* sous_category_id

Une table 'Categories':
*
	* id
	* name

Une table 'Sous_categories':

id
*
	* name
	* category_id

Je veux faire ces listes liées à la création de mon incident, donc sur la page app/views/incidents/new (avec un render 'form_new').

Il me faut donc créer deux select_tag dans ma page de formulaire :

```ruby
# app/views/incidents/_form_new.html.erb

<%= form_for @incident, html: { multipart: true } do |f| %>

<div class="field">
  <%= f.label "Catégorie" %><br>
  <%= select_tag "incident[category_id]", options_for_select(@categories.collect{|category| [category.name.titleize, category.id]}, 1), {} %>
  <%= select_tag "incident[sous_category_id]", options_for_select(@sous_categories.collect{|sous_category| [sous_category.name.titleize, sous_category.id]}, 0), {} %>
  <br>
</div>

<% end %>
```


Vous pouvez remarquer que dans mon 'options_for_select' je récupère des valeurs d'on ne sait où. Voici d'où :

```ruby
# app/controller/incidents_controller.rb

  def new
    @incident = Incident.new
    @categories = Category.all
    @sous_categories = SousCategory.where("category_id = ?", Category.first.id)
  end

  # GET /incidents/1/edit
  def edit
  end

  def update_subcats
    @sous_categories = SousCategory.where("category_id = ?", params[:category_id])
    respond_to do |format|
      format.js
    end
  end
```


Je ne vous met pas tout le code du controller mais uniquement les méthodes new et update_subcats (que j'expliquerais après). Ici donc dans la méthode new, en plus de déclarer un nouvel incident (Incident.new[qui sert à la création du formulaire et pour savoir où envoyer les données]), je récupère dans ma table toutes les catégories (id et name) ainsi que les sous catégories qui appartiennent à la première catégorie. Pourquoi ?

Car lorsque je vais afficher ma page de formulaire, je veux qu'il s'affiche quelque chose à l'écran, à savoir une catégorie(la première dans la table) et ses sous catégories.

La méthode 'update_subcats' quant à elle va servir à, comme son nom l'indique, mettre à jour la liste des sous catégories qui s'afficheront dans mon select_tag.

Étant donné qu'on crée une nouvelle méthode dans le controller, il faut lui créer sa route:


```ruby
#config/routes.rb

Rails.application.routes.draw do
  resources :incidents do
    member do
      get :update_subcats
    end
  end
end
```



Maintenant on va s'occuper de créer le code qui remplacera le contenu de la liste de sous categories par le nouveau contenu, pour cela on crée un nouveau fichier coffee dans :


```ruby
#app/view/incidents/update_subcats.coffee

$("#incident_sous_category_id").empty().html("<%= escape_javascript(options_for_select(@sous_categories.collect{|sous_category| [sous_category.name.titleize, sous_category.id]}))%>");
```


Et pour finir le fichier ajax situé :


```coffee
#app/assets/javascripts/incidents.coffee

$ ->
	$(document).on 'change', '#incident_category_id', (evt) ->
		$.ajax '/incidents/:id/update_subcats',
			type: 'GET',
			dataType: 'script',
			data: {
				category_id: $('#incident_category_id option:selected').val()
			}
			error: (jqXHR, textStatus, errorThrown) ->
				console.log("AJAX Error: #{textStatus}, #{jqXHR}, #{errorThrown}")
			success: (data, textStatus, jqXHR) ->
				console.log("Dynamic category select OK!")
```

Juste pour le fun, je vous laisse comprendre ce bout de code tout seul.



Bye !
