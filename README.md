# botbible
Robot pour chat IRC chrétienne en PHP pour encourager dans la foi et la connaissance biblique
Vous pouvez adapter ce programme à souhait.
Ce programme se connectera sur une chaine IRC sur le serveur Freenode. Modifiez-le avant de le tester sur une chaine IRC vous appartenant
Ce programme donne le niveau administrateur au robot lui-même est au nick Rodolphe, et donne aux pseudo contenant "pasteur" un niveau supplementaire

* Droit réservé
600 questions/réponses de biblequest.net
Versets biblique au hazard : evandis.com
Versets biblique Louis Second 21 : getbible.net


* Configurer sa chaine IRC 
Choisir et Enregistrer votre pseudo (nick) sur le serveur
/nick monpseudo
/msg nickserv register votremotdepasse votreemail

  -Choisir et enregistrer le nom de votre salon
  ...
/join #votresalon
/msg chanserv register #votresalon votremotdepasse descriptiondusalon
...

  -Vous pouvez ensuite configurer votre chaine à souhait
  ...
/msg Chanserv SET #votresalon DESC description
/msg Chanserv SET #votresalon URL votreurl
...

* Installation sur un serveur
  -Vous pouvez l'installer de plusieurs manière, ici je vous propose de l'installer sur un serveur VPS Debian 9.
  -Nous allons créer un service
  -Installer php si ce n'est pas déjà fait
```
$ php -v
$ sudo apt update
$ sudo apt install apt-transport-https ca-certificates curl software-properties-common
$ curl -fsSL https://packages.sury.org/php/apt.gpg | sudo apt-key add 
$ sudo add-apt-repository "deb https://packages.sury.org/php/ $(lsb_release -cs) main"
$ sudo apt update
$ sudo apt install php7.2-common php7.2-cli
```
  -Déposer votre fichier botBible.php dans un répertoire
  -Créer un service
```
$ cd /etc/systemd/system
$ vi botbible.service
```
```
  -Ajouter ceci dans ce fichier
[Unit]
Description=BotBible to IRC Channel
After=network-online.target

[Service]
Type=simple
ExecStart=php /votrerepertoire/botBible.php
Restart=always

[Install]
WantedBy=multi-user.target
```
  -Enfin, vous devez démarrer le service
```
$ systemctl start botbible.service
```

