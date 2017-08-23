---
layout: post
title: 34 - Rails - Initiation à Ruby on Rails
date: 2015-02-18 08:00
author: jeremy
published: true
categories: [Rails]
---
On y est, l'installation de **Rails** ! Mais non, restez, n'ayez pas peur ! On parlera de tout ici, de la simple installation de **Rails** jusqu'à l'installation de **Mysql** à la réinstallation de **Mysql** ... !



###Rails
Ceux qui on suivit les cours depuis leur début ont certainement **Rails** de déjà installé. Il suffit de tester avec la commande **rails -v** à entrer dans le prompt.
Pour les autres voici la commande à exécuter pour installer **rails** : **gem install rails**
Le reste se fait tout seul.
<!--break-->

### **Mysql**
Rails utilise par défaut **sqlite3** mais ici on se servira de **Mysql**. Voici donc l'installation pour les distributions Ubuntu :
Lancer dans le prompt : **sudo apt-get install mysql-server**.
Si tout se passe bien vous aurez une fenêtre qui s'ouvrira où on vous demandera de créer un mot de passe pour le compte utilisateur "Root". Mettez le mot de passe que vous voulez. Si tout s'est bien passé, c'est fini, il vous suffit de tester avec la commande **: mysql -u root -p**
Si l'installation s'est bien exécutée il s'affichera ceci :

```ruby
$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 42
Server version: 5.5.41-0ubuntu0.14.04.1 (Ubuntu)

Copyright (c) 2000, 2014, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

Sinon si comme moi vous avez cette erreur : **ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) ** voyez le chapitre suivant.

### **Réinstallation**
Ca arrive parfois que vous ayez une erreur lors de la connection à la base de données, dans ce cas google est la pour vous aider mais si vous avez la même erreur que j'ai eu il suffit de suivre ces étapes :

*
	* sudo apt-get remove --purge mysql-server mysql-client mysql-common
	* sudo apt-get autoremove
	* sudo apt-get autoclean
	* sudo rm -rf /var/lib/mysqlsudo
	* apt-get install mysql-server


Pensez à bien mettre le mot de passe !
J'ai trouvé cette astuce sur : <a href="http://stackoverflow.com/questions/18526315/mysql-wont-install-on-ubuntu-11-04">http://stackoverflow.com/questions/18526315/mysql-wont-install-on-ubuntu-11-04</a>
### **Windows**
L'installation de Rails se fait de la même manière que sur Ubuntu. En revanche vous trouverez votre bonheur pour **mysql** sur : <a href="http://dev.mysql.com/downloads/mysql/">**http://dev.mysql.com/downloads/mysql**</a><a href="http://dev.mysql.com/downloads/mysql/">/</a>



C'est tout pour le moment, on va y aller doucement hein, on va pas brusquer les esprits. ;)
