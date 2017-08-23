---
layout: post
title: 23 - Réseaux et protocoles - Initiation à Ruby
date: 2015-02-03 08:00
author: jeremy
published: true
categories: [Initiation à Ruby]
---
Salut à tous ! Je suis super heureux de vous annoncer qu'on peux enfin appercevoir le boût du tunnel ! Alors, certes il nous reste du chemin à faire à l'extérieur mais au moins on sera à l'air libre !
On s'approche enfin de la sphère Rails ! Pour ceux qui viennent d'arriver, Rails c'est ce que l'on convoite depuis le tout début ! Et on y est presque ! Aujourd'hui on va s'attaquer aux **Sockets**, avec les connexions **TCP/IP, UDP, HTTP, FTP, SMTP, POP3** !
Pour les plus débutants, sachez qu'une connexion, quelle qu'elle soit, fonctionne sur un protocole réseau, un parmis les 6 plus haut, évidemment il en existe d'autres, mais on ne parlera que de ceux là aujourd'hui. Si vous ne connaissez pas le fonctionnement d'internet (o-O), il faut savoir que le moyen de communication est basé sur une relation serveur/client. Le serveur se met à l'écoute sur un port donné et le client se met en contact avec un serveur par son adresse IP et son numéro de port.

### **TCP/IP**
**S****erveur**
Pour construire un serveur de communication **TCP/IP** on utilisera la classe **TCPServer** (attention aux majuscules) qui est une dérivée de la classe **TCPSocket**. Elle prend en paramêtre le numéro de port et éventuellement l'adresse sur laquelle on écoute (ce serveur peut avoir plusieurs cartes réseaux).
La méthode **.accept** va mettre le serveur en attente d'une connexion client.
Voici un exemple de serveur web écoutant un client sur le port 81 :

<!--break-->

```ruby
require 'socket'

serveur = TCPServer.new(81)

client = nil
while(client = serveur.accept)
	Thread.new(client) {|client|

		requete = client.gets

		#Envoi de la réponse
		client.puts("HTTP/1.0 200 OK")
		client.puts("Content-Type:text/html")
		client.puts
		client.puts "<html><body><h1>Hello World</h1></body></html>"

		client.close
	}
end
```


Pour le tester vous même, il suffit de lancer une page internet et entrer <a href="http://127.0.0.1:81/">http://127.0.0.1:81</a>. Un magnifique **Hello World** fera son apparition.
**Client**
Côté client, la pratique est quasiment la même. A ceci près que l'on utilisera un objet de type **TCPSocket **pour réaliser notre demande au serveur :


```ruby
require 'socket'

socket = TCPSocket.new("www.google.fr", 80)

Thread.new(socket){|socket|

		socket.puts("GET / HTTP/1.0")
		socket.puts("host: www.google.fr")
		socket.puts

		while socket.gets()
			puts $_
		end
		socket.close

	}

infos = TCPSocket.gethostbyname("www.google.fr")
infos.each {
	|info|
	if info.is_a?(Array) then
		info.each {
			|info2|
				puts "- #{info2}"
		}
	else
		puts info
	end
}
#Sortie : www.google.fr
#Sortie : 10
#Sortie : 2a00:1450:400c:c03::5e
#Sortie : 173.194.67.94
```

On va s'intérresser d'abord à la première partie, de la ligne 1 à 17 :
Comme pour le serveur, on retrouve notre création d'objet prenant en paramètre l'adresse du site et le port que l'on souhaite utiliser. Dans le **Thread** on effectue une connexion directe au serveur de Google.
Dans la deuxième partie on se sert de la méthode **gethostbyname** pour soutirer des informations au serveur de Google.

###UDP
**Client/Serveur**
Le protocole **UDP** quant à lui ne procède pas à la vérification de la bonne transmission des données. Il n'y a pas d'établissement de connexion au préalable. On retrouvera donc uniquement la classe **UDPSocket. **
**Serveur :**

```ruby
require 'socket'
serveur = UDPSocket.new
serveur.bind('127.0.0.1', 81)

while info = serveur.recvfrom(10)
	puts info
end
```


En **UDP, **c'est la méthode **bind** qui est utilisée pour écouter sur un port. La méthode **recvfrom** prends en argument la taille maximale du paquet attendu et retourne des informations sur l'émetteur.
**Client : **

```ruby
require 'socket'

client = UDPSocket.new
client.connect('127.0.0.1', 81)
client.send "OK", 0
```

Côté client en revanche, c'est la méthode **connect** qui entre en jeu pour se connecter au serveur voulu.

###HTTP

```ruby
require 'net/http'

#Connection à Google
google = Net::HTTP.new('www.google.fr', 80)

#Réponse de Google
reponse = google.get('/')

puts reponse.code
#Sortie : 200 (Qui veut dire que tout est ok)
puts reponse.message
#Sortie : OK (Tout est ok encore)
puts reponse.body
#Sortie : (On obtient le code HTML de la page Google)
```

Pour se connecter au serveur de Google, on crée toujours un objet (décidémment, je crois qu'en Ruby, tout est objet !). Attention quand même car la méthode de création diffère un peu des autres façons.
Ici je me sert de la méthode **get **pour récuperer la page <a href="http://www.google.fr/">**www.google.fr**</a>. Elle prends en paramètre le chemin vers un document. La méthode **post** quant à elle peux prendre deux autres arguments :

*
	<li style="text-align:justify;">
Des données à envoyer

	*
Des champs d'en-têtes de la requête **HTTP**


###FTP
Pour rappel, le protocole **FTP** sert essentiellement au transfert de fichiers entre deux machines distantes. Un serveur** FTP** est d'ailleurs utilisé dans ces cas là...(Ouuuaaaahouuuuh). L'accès à ce serveur ce fait par une adresse ip et un numéro de port. Dans la plupart des cas il est nécessaire de posséder un compte utilisateur pour gérer le serveur.
C'est donc lors de la création de l'objet **FTP** que l'on indique en paramètre la localisation du serveur et le compte d'accès. Si la connexion est refusée, une exception de classe **Net::FTPPermError** sera levée.

```ruby
require 'net/ftp'

begin

	ftp = Net::FTP.new('monserveurftp.com', 'moncompte', 'monmotdepasse')

	puts "Contenu du répertoire : #{ftp.pwd}"
	ftp.list().each {
		|fichier|
		puts "- #{fichier}"
	}
end
```

Voici une liste non exsaustive des méthodes disponibles :

<ul style="text-align:justify;">
	*
**chdir** : Change de répertoire courant

	*
**delete** : Supprime un fichier ou dossier

	*
**getbinaryfile** : Récupère un fichier binaire

	*
**gettextfile** : Récupère un fichier texte

	*
**list** : Retourne le contenu du répertoire

	*
**mkdir** : création d'un répertoire

	*
**mtime** : dernière date de modification d'un fichier

	*
**putbinaryfile** : Envoi d'un fichier binaire sur le serveur

	*
**puttextfile** : Envoie d'un fichier texte sur le serveur

	*
**pwd** : Indique le répertoire courant

	*
**rename** : Renomme un fichier ou dossier

	*
**return_code** : Retourne le code de la dernière opération


Attention à fermer la connexion avec la méthode **close**

### **SMTP**
Ce protocole est très utilisé pour l'envoi de mail. Il est basé sur le protocole **TCP/IP** donc il nécessite une connexion préalable.

```ruby
require 'net/smtp'

begin

	from = "adresseDeLexpediteur@test.com"
	smtp = Net::SMTP.start('smtp.MonserveurSMTP.fr') {
		|smtp|
			puts "Envoyer un email"

		msg = "Sent from : #{from}"
		msg += "Subject : Test SMTP"
		msg += "This is the message !"

		smtp.send_message(msg, from, ["unDestinataire@test.com", "etPeutEtreUnAutre@test.com"])
	}
	rescue Exception => e
		puts e.message
end
```

La méthode **SMTP.start** prend en argument l'adresse du serveur **SMTP** et son port (habituellement 25).

###POP3
Ce protocole sert à la consultation de vos mails lequels sont stockés sur un serveur **POP3** auquel on se connecte avec un compte de messagerie. Encore une dernière fois, c'est un objet de la classe **Net::POP3** qui permettra de se servir de toutes les commandes possibles. Il prend en argument l'adresse du serveur **POP3**.
La méthode **start** quant à elle servira à la connexion et prend en paramètre le nom du compte et le mot de passe. En cas d'erreur, il sera renvoyé une exception : **Net::POPAuthenticationError**.

```ruby
require 'net/pop'

begin
	#Identification du serveur POP3
	pop = Net::POP3.new('LeServeurPop3.com')

	#Démarrage d'une session POP3
	pop.start('monIdentifiant', 'monMotDePasse') {|pop2|
		puts "Connexion"

		#Récupération des emails
		pop2.each_mail(){|message|
			puts "En-tete : " + message.header
			puts message.pop
		}
	}

	rescue Exception => e
		puts e.message
end
```

La méthode **delete** permet de supprimer un message.
