# Site Hamnet F6KGL

Ceci est le conteneur docker pour le site hamnet de F6KGL.
Tout le html va dans le dossier public-html.

Ce conteneur marche sur httpd (ou apache2) et permet l'affichage d'un site statique simple.
Il permet aussi de faire le role de passerelle entre hamnet et le site wordpress du radioclub.
client hamnet <~~~hamnet~~~> serveur hamnet passerelle <~~~internet~~~> site wordpress.

Ne pas oublier de renseigner le domaine du site dans my-httpd.conf ligne 241 !
 
installation
```sudo docker build -t f6kgl-site .```
```sudo docker run -dit --name f6kgl-site-app -p 80:80 f6kgl-site```

--detach , -d 		Run container in background and print container ID
--interactive , -i 		Keep STDIN open even if not attached
--tty , -t 		Allocate a pseudo-TTY

pour le redémarrage ajouter --restart always
https://docs.docker.com/config/containers/start-containers-automatically/

Supprimer le conteneur
lister les conteneurs
```sudo docker container ls```
stopper le conteneur
```sudo docker stop <id conteneur>```
supprimer le contenur
```sudo docker rm <id conteneur>```
lister les images dispo
```sudo docker images```
supprimer l'image
```sudo docker image rm <img name>```


Par Maxime F4IQN
maxime1.favier@protonmail.ch
Redistribution limité aux membres du radioclub F6KGL
