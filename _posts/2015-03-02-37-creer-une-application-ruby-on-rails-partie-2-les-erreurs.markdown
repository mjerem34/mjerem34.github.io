---
layout: post
title: 37 - Créer une application Ruby On Rails - Partie 2 - Les erreurs - Initiation à Ruby on Rails
date: 2015-03-02 08:00
author: jeremy
published: true
categories: [Rails]
---
Comme je le disais précédemment, j'ai été confronté à quelques erreurs, les voici, avec leurs solution pour mon cas :



Voilà la situation :

Je crée mon application Rails dans mon dossier nommé **Articles Tutos[Not Ready]**. Jusque là, pas de problème, je rentre dans le dossier et fais **rails s** et obtient ça :
<!--break-->

```ruby
/usr/local/rvm/gems/ruby-2.2.0/gems/railties-4.2.0/lib/rails/app_rails_loader.rb:39: warning: Insecure world writable dir /usr/local/rvm/gems in PATH, mode 042777
Warning: Running `gem pristine --all` to regenerate your installed gemspecs (and deleting then reinstalling your bundle if you use bundle --path) will improve the startup performance of Spring.
/usr/local/rvm/gems/ruby-2.2.0/gems/spring-1.3.2/lib/spring/client/rails.rb:27:in `load': no implicit conversion of nil into String (TypeError)
    from /usr/local/rvm/gems/ruby-2.2.0/gems/spring-1.3.2/lib/spring/client/rails.rb:27:in `call'
    from /usr/local/rvm/gems/ruby-2.2.0/gems/spring-1.3.2/lib/spring/client/command.rb:7:in `call'
    from /usr/local/rvm/gems/ruby-2.2.0/gems/spring-1.3.2/lib/spring/client.rb:26:in `run'
    from /usr/local/rvm/gems/ruby-2.2.0/gems/spring-1.3.2/bin/spring:48:in `<top (required)>'
    from /usr/local/rvm/gems/ruby-2.2.0/gems/spring-1.3.2/lib/spring/binstub.rb:11:in `load'
    from /usr/local/rvm/gems/ruby-2.2.0/gems/spring-1.3.2/lib/spring/binstub.rb:11:in `<top (required)>'
    from /usr/local/rvm/rubies/ruby-2.2.0/lib/ruby/2.2.0/rubygems/core_ext/kernel_require.rb:54:in `require'
    from /usr/local/rvm/rubies/ruby-2.2.0/lib/ruby/2.2.0/rubygems/core_ext/kernel_require.rb:54:in `require'
    from /home/jeremy/firstapp/bin/spring:13:in `<top (required)>'
    from bin/rails:3:in `load'
    from bin/rails:3:in `<main>'
```

Petite précision, j'obtient cela même lorsque je fais **rails -v** ou même n'importe qu'elle commande **rails**.

J'avais trouvé une solution en faisant **bundle exec rake rails:update:bin**

Seulement, d'autres erreurs faisaient leurs apparition par la suite, entre autres :

```ruby
Started GET "/users/new" for 127.0.0.1 at 2015-02-24 16:46:02 +0100
  ActiveRecord::SchemaMigration Load (0.1ms)  SELECT "schema_migrations".* FROM "schema_migrations"

ActiveRecord::PendingMigrationError (

Migrations are pending. To resolve this issue, run:

    bin/rake db:migrate RAILS_ENV=development

):
  activerecord (4.2.0) lib/active_record/migration.rb:393:in `check_pending!'
  activerecord (4.2.0) lib/active_record/migration.rb:374:in `call'
  actionpack (4.2.0) lib/action_dispatch/middleware/callbacks.rb:29:in `block in call'
  activesupport (4.2.0) lib/active_support/callbacks.rb:88:in `call'
  activesupport (4.2.0) lib/active_support/callbacks.rb:88:in `_run_callbacks'
  activesupport (4.2.0) lib/active_support/callbacks.rb:734:in `_run_call_callbacks'
  activesupport (4.2.0) lib/active_support/callbacks.rb:81:in `run_callbacks'
  actionpack (4.2.0) lib/action_dispatch/middleware/callbacks.rb:27:in `call'
  actionpack (4.2.0) lib/action_dispatch/middleware/reloader.rb:73:in `call'
  actionpack (4.2.0) lib/action_dispatch/middleware/remote_ip.rb:78:in `call'
  web-console (2.0.0) lib/action_dispatch/debug_exceptions.rb:18:in `middleware_call'
  web-console (2.0.0) lib/action_dispatch/debug_exceptions.rb:13:in `call'
  actionpack (4.2.0) lib/action_dispatch/middleware/show_exceptions.rb:30:in `call'
  railties (4.2.0) lib/rails/rack/logger.rb:38:in `call_app'
  railties (4.2.0) lib/rails/rack/logger.rb:20:in `block in call'
  activesupport (4.2.0) lib/active_support/tagged_logging.rb:68:in `block in tagged'
  activesupport (4.2.0) lib/active_support/tagged_logging.rb:26:in `tagged'
  activesupport (4.2.0) lib/active_support/tagged_logging.rb:68:in `tagged'
  railties (4.2.0) lib/rails/rack/logger.rb:20:in `call'
  actionpack (4.2.0) lib/action_dispatch/middleware/request_id.rb:21:in `call'
  rack (1.6.0) lib/rack/methodoverride.rb:22:in `call'
  rack (1.6.0) lib/rack/runtime.rb:18:in `call'
  activesupport (4.2.0) lib/active_support/cache/strategy/local_cache_middleware.rb:28:in `call'
  rack (1.6.0) lib/rack/lock.rb:17:in `call'
  actionpack (4.2.0) lib/action_dispatch/middleware/static.rb:113:in `call'
  rack (1.6.0) lib/rack/sendfile.rb:113:in `call'
  railties (4.2.0) lib/rails/engine.rb:518:in `call'
  railties (4.2.0) lib/rails/application.rb:164:in `call'
  rack (1.6.0) lib/rack/lock.rb:17:in `call'
  rack (1.6.0) lib/rack/content_length.rb:15:in `call'
  rack (1.6.0) lib/rack/handler/webrick.rb:89:in `service'
  /home/jeremy/.rvm/rubies/ruby-2.2.0/lib/ruby/2.2.0/webrick/httpserver.rb:138:in `service'
  /home/jeremy/.rvm/rubies/ruby-2.2.0/lib/ruby/2.2.0/webrick/httpserver.rb:94:in `run'
  /home/jeremy/.rvm/rubies/ruby-2.2.0/lib/ruby/2.2.0/webrick/server.rb:294:in `block in start_thread'


  Rendered /home/jeremy/.rvm/gems/ruby-2.2.0/gems/web-console-2.0.0/lib/action_dispatch/templates/rescues/_source.erb (3.5ms)
  Rendered /home/jeremy/.rvm/gems/ruby-2.2.0/gems/web-console-2.0.0/lib/action_dispatch/templates/rescues/_trace.html.erb (1.1ms)
  Rendered /home/jeremy/.rvm/gems/ruby-2.2.0/gems/web-console-2.0.0/lib/action_dispatch/templates/rescues/_request_and_response.html.erb (0.7ms)
  Rendered /home/jeremy/.rvm/gems/ruby-2.2.0/gems/web-console-2.0.0/lib/action_dispatch/templates/rescues/_web_console.html.erb (0.7ms)
  Rendered /home/jeremy/.rvm/gems/ruby-2.2.0/gems/web-console-2.0.0/lib/action_dispatch/templates/rescues/diagnostics.html.erb within rescues/layout (19.1ms)

```

J'ai créé un sujet à ce propos : <a href="http://www.developpez.net/forums/d1502176/autres-langages/autres-langages/ruby/ruby-on-rails/migrations-are-pending-to-resolve-this-issue-run-bin-rake-db-migrate-rails_env-development/">http://www.developpez.net/forums/d1502176/autres-langages/autres-langages/ruby/ruby-on-rails/migrations-are-pending-to-resolve-this-issue-run-bin-rake-db-migrate-rails_env-development/</a>

En gros, j'avais un problème de migration de base de données, pour régler ce petit soucis il fallait, juste après la création de l'application, créer la base de données en faisant **rake db:create**, ensuite faire le scaffold et pour finir faire le **rake db:migrate, **à ce moment là l'application se lançait normalement... Enfin, parfois...

Et pour finir j'ai découvert que mon soucis venait du dossier parent ! Qui était nommé **Articles Tutos[Not Ready]. **En effet, le soucis venait des crochets [ du dossier ... Donc si vous avez un soucis, vérifiez le nom de votre dossier !

Pour finir, j'ai cette erreur :

```ruby
Started GET "/users" for 127.0.0.1 at 2015-02-26 11:36:30 +0100
  ActiveRecord::SchemaMigration Load (0.1ms)  SELECT "schema_migrations".* FROM "schema_migrations"
Processing by UsersController#index as HTML
  User Load (0.5ms)  SELECT "users".* FROM "users"
  Rendered users/index.html.erb within layouts/application (3.7ms)
WARN: tilt autoloading 'coffee_script' in a non thread-safe way; explicit require 'coffee_script' suggested.
Completed 500 Internal Server Error in 42ms

ActionView::Template::Error (Could not find a JavaScript runtime. See https://github.com/sstephenson/execjs for a list of available runtimes.
  (in /home/jeremy/.rvm/gems/ruby-2.2.0/gems/turbolinks-2.5.3/lib/assets/javascripts/turbolinks.js.coffee)):
    3: <head>
    4:   <title>FirstAppTutoChapter2</title>
    5:   <%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track' => true %>
    6:   <%= javascript_include_tag 'application', 'data-turbolinks-track' => true %>
    7:   <%= csrf_meta_tags %>
    8: </head>
    9: <body>
  app/views/layouts/application.html.erb:6:in `_app_views_layouts_application_html_erb__1371078902343347276_69953446809920'


  Rendered /home/jeremy/.rvm/gems/ruby-2.2.0/gems/web-console-2.0.0/lib/action_dispatch/templates/rescues/_source.erb (11.2ms)
  Rendered /home/jeremy/.rvm/gems/ruby-2.2.0/gems/web-console-2.0.0/lib/action_dispatch/templates/rescues/_trace.html.erb (2.6ms)
  Rendered /home/jeremy/.rvm/gems/ruby-2.2.0/gems/web-console-2.0.0/lib/action_dispatch/templates/rescues/_request_and_response.html.erb (0.8ms)
  Rendered /home/jeremy/.rvm/gems/ruby-2.2.0/gems/web-console-2.0.0/lib/action_dispatch/templates/rescues/_web_console.html.erb (1.3ms)
  Rendered /home/jeremy/.rvm/gems/ruby-2.2.0/gems/web-console-2.0.0/lib/action_dispatch/templates/rescues/template_error.html.erb within rescues/layout (27.6ms)

```


Pour régler ce soucis dont je ne connais pas l'origine pour l'instant, il suffit d'aller dans le dossier visé et de supprimer la ligne citée. Soit, pour moi, dans le dossier */home/jeremy/Dropbox/Applications/first_app_tuto_chapter_2/app/views/layouts/*

dans le fichier *application.html.erb* qui est composé de ceci :

```html
<!DOCTYPE html>
<html>
<head>
  <title>FirstAppTutoChapter2</title>
  <%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track' => true %>
  <%= javascript_include_tag 'application', 'data-turbolinks-track' => true %>
  <%= csrf_meta_tags %>
</head>
<body>

<%= yield %>

</body>
</html>
```

Il faut donc supprimer la ligne :

```ruby
<%= javascript_include_tag 'application', 'data-turbolinks-track' => true %>
```






En espérant vous avoir aidé !
