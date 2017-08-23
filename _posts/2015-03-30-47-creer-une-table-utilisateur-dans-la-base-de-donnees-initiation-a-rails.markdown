---
layout: post
title: 47 - Créer une table utilisateur dans la base de données - Initiation à Rails
date: 2015-03-30 08:00
author: jeremy
published: true
categories: [Uncategorized]
---
Dans cet article, on va créer des utilisateurs et les insérer dans notre base de données en mettant les tests en avant.



<<
<em>Pour suivre ce cours il est plus que conseillé d’avoir sous la main <a href="http://french.railstutorial.org/chapters/beginning" target="_blank">ce lien</a> ou <a href="https://www.dropbox.com/sh/uuwaqjqbc8y3ybv/AACjqwYvxqHaXxADTjBp48-Ra?dl=0" target="_blank">ces fichiers pdf</a>, pour rappel, les cours sont </em><em>ba</em><em>sés dessus et cet article reprend le chapitre </em><em>6</em><em>.</em>
>>
<!--break-->
J'espère que je vous ai manqué, je ne saurais pas trouver de véritable excuse de pourquoi il n'y as plus d'article depuis une semaine mais j'ai passé tout mon temps sur CodeWars à m'entraîner pour la BattleDev. Banana Bana !!
Mais ne vous inquiétez pas, je vous ai concocté un petit cours bien sympa, qui reprend l'intégralité du chapitre 6 du livre de Michael Hartl ! Soit dit en passant, j'ai jetté un coup d'oeil à la 3 ème édition du livre et il apparaît qu'il n'utilise plus GitHub ni même Rspec, donc faîtes attention de ne pas tomber dans le piège que les tests ne sont pas identiques. Et par rapport à la 3ème édition justement, rien n'a véritablement changé dans l'utilisation par rapport aux cours que vous trouverez ici, à savoir, les versions que j'utilise ici sont les dernières en date, soit :
**-**** Rails 4.2.0**
**- Ruby 2.2.0p0**
**- Rspec 3.2.1**
**- Bundler 1.8.2**
**- Sqlite3 1.3.10**
Mais vous pourrez trouver néanmoins des commandes qui changeront pour les prochaines versions, dans le cas où je suis au courant des futurs changements, je les écrirais dans le cours, comme vous pourrez le voir dès maintenant.

### **Model User**

```ruby
$ rails generate model User nom:string email:string
```

C'est cette commande qui vous permettra de créer un modèle utilisateur. Sa sert à insérer dans votre base de données ce que devra contenir chaque utilisateur. N'ayez pas peur si vous ne comprennez pas tout tout de suite. Continuons.
Ouvrez le fichier : **sample_app/db/migrate/<time>_create_users.rb**
Observez bien la méthode **create_table**, comme son nom l'indique, c'est elle qui va créer la table d'utilisateur **users**. Celle qui va gérer les utilisateurs. Vous pouvez voir qu'elle va créer les "colonnes" correspondant au nom et à l'email. En réalité, elle crée une troisième colonne appellée **id** qui sera, lui, unique, il permet, entre autre, de différencier deux utilisateurs mais pas uniquement.
Une fois qu'on à créé ce fichier avec la commande précedente, on peux migrer notre base de données avec :

```ruby
$ rake db:migrate
```

Qui deviendra dans **Rails 5.0** :

```ruby
$ rails db:migrate
```

Si vous avez à effectuer des changements de dernière minute, il peux être utile de se servir de :

```ruby
$ rake db:rollback
```

qui effacera toute la table **users**, vous pourrez ensuite directement rajouter à la main dans le fichier ce dont vous avez besoin.

### **Les tests**
On va donc procéder maintenant aux vérifications d'usage, tout site correctement constitué possède quelques règles d'inscription :
- L'utilisateur doit obligatoirement insérer un nom dans le champ concu à cet effet.
- L'utilisateur doit obligatoirement insérer un email dans le champ concu à cet effet.
- Le nom de doit pas être trop long
- L'adresse email doit être valide.
- L'adresse email doit être unique.
- Le mot de passe ne doit pas être ni trop long ni trop court.
Donc avant de mettre en place ces fonctionnalités, on va créer nos tests et vérifier qu'ils échouent.
Un fichier nommé **user_spec.rb** a été créé lors de la création du modèle. Rendez vous y.
Voici une petite batterie de tests, à vous de les adapter avec ce dont vous avez besoin :

```ruby
require 'rails_helper'

RSpec.describe User, type: :model do
  before(:each) do
    @attr = {
      nom: "Example User",
      email: "user@example.com",
      password: "foobarbaz",
      password_confirmation: "foobarbaz"
      }
  end

  it "doit créer une nouvelle instance avec des attributs valides" do
    User.create!(@attr)
  end

  it "devrait exiger un nom obligatoire" do
    bad_guy = User.new(@attr.merge(nom: ""))
    expect(bad_guy).to_not be_valid
  end
  it "devrait rejeter les noms trop longs" do
    long_name = "a" * 51
    bad_guy = User.new(@attr.merge(nom: long_name))
    expect(bad_guy).to_not be_valid
  end
  it "devrait accepter les adresses emails valides" do
    adresses = %w[foo@bar.com FOO_BAR@baz.com foo.bar_baz@qux.fum.com]
    adresses.each do |adress|
      bad_guy = User.new(@attr.merge(email: adress))
      expect(bad_guy).to be_valid
    end
  end
    it "devrait rejeter les mots de passe trop longs" do
    long_password = "a" * 50
    bad_guy = @attr.merge(password: long_password, password_confirmation: long_password)
    expect(User.new(bad_guy)).to_not be_valid
  end
```

Attention, ne faîtes pas de copier/coller de ce bout de code, j'y ai volontairement insérer une erreur, réécrivez le pour la trouver et puis surtout pour apprendre, vous aurez de toute façon d'autres tests à faire, soit au total 10 tests pour le modèle utilisateur.
Une fois que ces tests sont écrits, et qu'ils échouent, soit parce que vous les avaient mal écrits, soit parce que le code n'est pas présent (WTF TDD!!), on peux s'occuper de les faire passer au vert.
Rendez vous donc dans **app/model/user.rb**. Et ajoutez y des "**validates**". Voilà à quoi cela ressemble :

```ruby
class User < ActiveRecord::Base

  attr_accessor :password, :password_confirmation

  email_regex = /\A[\w+\-.]+@[a-z\d\-.]+\.[a-z]+\z/i

  validates :nom, presence: true, length: {maximum: 50}
  validates :email, presence: true, format: {with: email_regex}, uniqueness: {case_sensitive: false}
  validates :password, presence: true, length: {within: 8..40}, confirmation: true
end
```

Soit dit en passant, Michael indique qu'il faut mettre **attr_accessor :nom, :email** mais les tests d'unicité échouent si on les mets. Donc, ne les mettez pas !
C'est bien beau tout ça mais une sécurité supplémentaire a été mise en place pour pas qu'une adresse email soit en double dans votre base de données, je vous renvoie vers le livre pour plus de détails mais voici comment la résoudre :

```ruby
$ rails generate migration add_email_uniqueness_index
```

Ce code va générer un fichier dans le dossier **db/migrate** qui, une fois rempli avec ceci :

```ruby
class AddEmailUniquenessIndex < ActiveRecord::Migration
  def self.up
    add_index :users, :email, unique: true
  end

  def self.down
    remove_index :users, :email
  end
end
```

permettra que votre application soit entièrement sécurisée pour le doublon !

<<**Ha et comment on les crée nos utilisateurs ?**>>
On verra plus tard !
Bye !
