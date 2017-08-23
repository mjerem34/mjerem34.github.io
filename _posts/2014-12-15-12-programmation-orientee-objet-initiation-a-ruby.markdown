---
layout: post
title: 12 - Programmation orientée objet - Initiation à Ruby
date: 2014-12-15 08:30
author: jeremy
published: true
categories: [Initiation à Ruby]
---
Gros dossier cette semaine ! J'ai préféré attendre un début de semaine pour entamer ce nouveau chapitre essentiel pour ne pas marquer de pause entre les différentes parties et que tout soit clair.
Donc petit rappel, en Ruby, tout est objet. Ou presque !

On a beaucoup parlé des objets pendant les anciens articles, mais rassurez vous, c'est pas pour ça que ça va être simple...
Donc avant d'apprendre à créer des objets il faut d'abord savoir qu'est-ce-que c'est. On pourrait comparer un objet à … un objet. Non, restez c'est là que ça devient marrant.
Imaginez un crayon, pas très difficile. Un crayon est un objet, maintenant, de quoi est composé ce crayon ?
Et bien ce crayon est composé de :

<!--break-->

```ruby
#encoding : utf-8
class CrayonDeCouleur
    def initialize(couleur, matiere_premiere, matiere_secondaire, matiere_optionelle)
        @couleur = couleur
        @matiere_premiere = matiere_premiere
        @matiere_secondaire = matiere_secondaire
        @matiere_optionelle = matiere_optionelle
    end

    def composition_crayon
            puts "Un crayon de couleur #{@couleur}, est composé de #{@matiere_premiere}, d'#{@matiere_secondaire} et de #{@matiere_optionelle}."
    end
end

crayon_bleu = CrayonDeCouleur.new("Bleu", "Bois", "Argile", "Pigments bleus")
crayon_rouge = CrayonDeCouleur.new("Rouge", "Bois", "Argile", "Pigments rouges")
crayon_vert = CrayonDeCouleur.new("Vert", "Bois", "Argile", "Pigments verts")

crayon_bleu.composition_crayon
crayon_rouge.composition_crayon
crayon_vert.composition_crayon

#Sortie : Un crayon de couleur Bleu, est composé de Bois, d'Argile et de Pigments bleus.
#Sortie : Un crayon de couleur Rouge, est composé de Bois, d'Argile et de Pigments rouges.
#Sortie : Un crayon de couleur Vert, est composé de Bois, d'Argile et de Pigments verts.
```


###Création de classe
N'ayez pas peur, je vais vous expliquer. Tout d'abord sachez qu'un crayon de couleur est composé de bois, d'argile et de pigments de la couleur voulue. J'ai pris un crayon de couleur pour pouvoir mettre plusieurs exemples.
Donc, pour qu'un CrayonDeCouleur, soit un CrayonDeCouleur, il doit être composé de @couleur, de @matiere_premiere, de @matiere_secondaire et de @matiere_optionnelle.
Ici, ma "class CrayonDeCouleur" représente ce que l'on veux créer à l'arrivée.
Le "def initialize(couleur, matiere_premiere, matiere_secondaire, matiere_optionelle)" correspond aux caractéristiques que doit avoir mes objets pour pouvoir faire partie de la classe (pour qu'on puisse dire que c'est un crayon de couleur), si il en manque une seule, une erreur se produira. On initialise nos variables d'instances, en passant, une variable d'instance est uniquement disponible à l'intérieur de la classe, c'est pourquoi on les fait "remplir" par d'autres variables, celles-ci normales, qui seront disponible quasiment partout dans le programme.
Je crée ensuite une méthode que mon CrayonDeCouleur sera capable d'exécuter, la méthode composition_crayon indiquera de quoi est composé le CrayonDeCouleur que je viens de créer. J'aurais très bien pu utiliser mon CrayonDeCouleur pour dessiner un troll face sur mon site web. A vous de juger l'utilité qu'il peut avoir.
Dans cette méthode je fais un simple puts qui renverra la valeur des variables d'instance dans une phrase, ce qui leur donnera un sens et permettra leur lecture a n'importe qui.
Ma classe se termine ici, pour dernier rappel, une classe est un ensemble de caractéristiques auxquelles mes objets doivent répondre pour en faire partie ainsi que les actions qu'ils peuvent exécuter... Si on aurait pu m'expliquer ça aussi simplement que ça...

###La création d'objets
On y est, les objets. Vous allez voir que c'est très simple en fait. Comme je l'ai déjà dit, en programmation, le plus dur à apprendre ce n'est pas la syntaxe, c'est savoir construire des programmes. Comme en Anglais, le plus dur ce n'est pas d'apprendre la longue liste de verbes "Be, Was/Were, Been, Etre", c'est de savoir construire une phrase avec.
Zoomons sur la création des objets :



```ruby
crayon_bleu = CrayonDeCouleur.new("Bleu", "Bois", "Argile", "Pigments bleus")
crayon_rouge = CrayonDeCouleur.new("Rouge", "Bois", "Argile", "Pigments rouges")
crayon_vert = CrayonDeCouleur.new("Vert", "Bois", "Argile", "Pigments verts")

crayon_bleu.composition_crayon
crayon_rouge.composition_crayon
crayon_vert.composition_crayon

#Sortie : Un crayon de couleur Bleu, est composé de Bois, d'Argile et de Pigments bleus.
#Sortie : Un crayon de couleur Rouge, est composé de Bois, d'Argile et de Pigments rouges.
#Sortie : Un crayon de couleur Vert, est composé de Bois, d'Argile et de Pigments verts.
```



J'ai enlevé la première partie où je crée la classe CrayonDeCouleur. D'ailleurs on est carrément sortie de cette classe, et imaginons même qu'on soit à l'autre bout du programme.
J'occupe mes 3 premières lignes à créer mes objets, ou mes CrayonDeCouleur. Je veux un crayon_bleu, un crayon_rouge et un crayon_vert. Vous voyez la syntaxe, il s'agit en fait de simples variables où l'on stockera à la fois l'objet et ses caractéristiques.
A noter aussi que je pourrais aussi insérer des booléens ou des int dans les caractéristiques.
Un int, d'abréviation Integer est un entier.
Ca y est, mes objets sont créés. Fin du tuto...

Non, c'est pas fini. Maintenant que mes objets sont créés, je peux leur dire quoi faire. Et donc mes objets ils sont capable de faire quoi ?
Rappel : mes objets sont capables de faire ce que je veux, du moment que j'ai programmé les actions dans ma classe auparavant.
Donc ici mes CrayonDeCouleur sont capable d'afficher à l'utilisateur de quoi ils sont composés. Allons y.
Zoom :


```ruby
crayon_bleu.composition_crayon
crayon_rouge.composition_crayon
crayon_vert.composition_crayon

#Sortie : Un crayon de couleur Bleu, est composé de Bois, d'Argile et de Pigments bleus.
#Sortie : Un crayon de couleur Rouge, est composé de Bois, d'Argile et de Pigments rouges.
#Sortie : Un crayon de couleur Vert, est composé de Bois, d'Argile et de Pigments verts.
```


Dans les 3 premières lignes j'exécute la méthode .composition_crayon que j'ai créé précédemment.

<<- Hé mais c'est comme quand on faisait "arr.inspect" pour afficher le tableau !>>
Oui, donc vous connaissez déjà cette syntaxe, pas besoin de trop s'attarder la dessus. Voyez aussi en sortie ce que l'on obtient.
Mais c'est pas tout, on peux aussi continuer à ajouter des méthodes à notre classe :


```ruby
#Autre partie de programme ///////////////
#encoding : utf-8

class CrayonDeCouleur
    def ecrire_au_crayon
        puts "Là j'écris avec un crayon. Ca se voit ?"
    end
end

bleu.ecrire_au_crayon
#Sortie : Là j'écris avec un crayon. Ca se voit ?
```


Lorsqu'on complète la classe avec d'autres méthodes, il faut savoir que la syntaxe reste la même bien entendu mais qu'on ne peux pas rajouter des caractéristiques à l'aide de la méthode "initialize".
Dernier petit tip, j'aurais pu modifier la méthode .composition_crayon au lieu d'en créer une nouvelle mais dans ce cas, les modifications n'auraient fait effet uniquement après la modification, et pas avant, c'est lié à l'ordre d'exécution, tout simplement.
A demain pour la suite !
