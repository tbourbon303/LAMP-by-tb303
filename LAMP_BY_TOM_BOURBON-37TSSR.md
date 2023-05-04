# Lamp by Tom Bourbon [37 TSSR 2022]

## Apache :

Installation d'apache 2.4 avec *apt install apache2*

![](https://drive.google.com/uc?id=1bG4F_6fb3OZqxGGguMoORXoBcMK-0QUx)

activation du module SSL et generation du certificat auto signé avec ;
*a2enmodssl*
*a2ensite default-ssl*
***openssl req $@ -new -x509 -days 3650 -nodes -out /etc/apache2/apache.pem -keyout /etc/apache2/apache.pem***

![](https://drive.google.com/uc?id=18sxlVVp-LA2QJghJiwLrEQOqDpTLhwNK)



Après genération du certificat on renseigne son chemin dans la conf d'apache, ici dans site.conf car default-ssl.conf  à était rm (suite du tp)



![](https://drive.google.com/uc?id=1yQJlMEVYH4yIrs8ekhTdl-BapAYn5TnQ)



Redirection http vers https (toujours dans le même fichier)



![](https://drive.google.com/uc?id=1XER9jD_XlebScgdfANjUjrYBcinQYOYP)



Je commente Directory /var/www/html pour éviter un conflit dans le fichier apache2.conf

*nano /etc/apache2/apache2.conf*



![](https://drive.google.com/uc?id=1mmfwZJdz6VFiptUgWtCxZz1apKDs1gJ7)



Je crée en mode user le dossier www

*mkdir /home/user/www*

![](https://drive.google.com/uc?id=1pqWU-m5D_t0BaCEMIGKfDOSor_r_WgmU)



Changement de proprio pour que ce soit apache 

**chown -R www-data:www-data /home/user/www*

*usermod -a -G www-data user*



Et changement des droits pour le dossier www pour l'utilisateur *userdeb* dans mon cas

*chmod -R 775 /home/user/www*



Conf de site.conf



![](https://drive.google.com/uc?id=12a9C2MdoKdqdSm5WtxqjWAoj0pVlDaHZ)



![](https://drive.google.com/uc?id=1JYnDgmOVeu59TR9XtBEc2N4NZJiMw0Y1)



## BSD :

Installation de mysql et test de mysql en cli



![](https://drive.google.com/uc?id=18exPh9mnFVoY7W3IYRtGY8OblP43OtyR)



## PHP :

Installation des paquets php et de PhpMyAdmin

*apt install php*

*apt install php-curl php-gd php-zip php-apcu php-xml php-ldap php-mbstring*

*apt install php-mysql*



![](https://drive.google.com/uc?id=1_K8RSNHoz2pnpoLkPP8vsOfIkCSXm1dl)

![](https://drive.google.com/uc?id=1WJBkqlaHRmVg-03XwQylrYkb-qwb-XWs)



Test de connexion sur le portail PhpMyAdmin, changement des droits root avec % et création d'un utilisateur user qui a tout les droits sur la base USER mais pas ailleurs 



![](https://drive.google.com/uc?id=1_48uy62NuOSbTSffUnWIQTcMFVvKk6Jd)



![](https://drive.google.com/uc?id=1_48uy62NuOSbTSffUnWIQTcMFVvKk6Jd)





## FTP :



Installation du service ftp et configuration du service

*apt install vsftpd*
*cp /etc/vsftpd.conf /etc/vsftpd.bak 
rm /etc/vsftpd.conf*
*nano /etc/vsftpd.conf*

Exemple de configuration disponible sur le campus.



On restart le service vsftpd puis on nmap en localhost pour voir si le port ftp est bien ouvert



![](https://drive.google.com/uc?id=1bEBzBaTR4j0X8bzzoHcANkfK0LEerYu3)



Et on tente une connexion via un client ftp sur notre serveur



![](https://drive.google.com/uc?id=1dCrUMC9HrrPO5ri42R2muR1jdo4KxmFu)





## Samba :

Samba pré-installé en amont donc on commence par *mv /etc/samba/smb.conf /etc/samba/smb.bak* puis on édite le fichier avec *nano /etc/samba/smb.conf*



![](https://drive.google.com/uc?id=1nNcBLPEdRGLj5vQbLkhHAi03RWKGOUxb)





Test de connexion via l'explorateur de fichier 



![](https://drive.google.com/uc?id=1aegrpuoeBuQkTZyAc-XtzAVLtRZI8bse)





## Script de sauvegarde des BSD



Dans le répértoire /root on créer un fichier avec *touch backup.sh* | *chmod +x backup.sh*
Puis on va l'éditer pour renseigner le script réalisé par Thomas Cherrier *nano backup.sh*



![](https://drive.google.com/uc?id=1BAyAC0_ep0T8_IuOXM0b5LaVLQI4KtUM)



Ensuite on test

*./backup.sh*



![](https://drive.google.com/uc?id=1iohK1JpBYIzxvYJP74QnQAdDtV1w5WDS)





## Webmin :



Installation du certificat dans Webmin (interface web accessible par le port :10000)



![](https://drive.google.com/uc?id=1UkM5X8wqKX5R1Bi2Ccpy-Cn_D-Z9k58j)



J'ai renseigné le chemin du certificat */etc/apache2/apache.pem* dans la partie "Private key file"





## Wordpress :



Installation de Wordpress dans le dossier /www mais avant ça on va *rm -R  /home/user/www* 
Une fois le dossier /www vide on procède à un *wget* du dernier zip disponible,  *unzip* puis *mv wordpress www*
On change de proprio et on attribu les droits 
*chown -R www-data:www-data /home/userdeb/www*
*chmod -R 775 /home/userdeb/www*



![](https://drive.google.com/uc?id=1UfnLAp48Ki6beSLfWn27vkKoOhrnucTN)



Malgré le sigle Non sécurisé j'ai bien le certificat ssl actif sur cette adresse 



![](https://drive.google.com/uc?id=1q-bqOnjU1AaMvcKQSB-VE9PyazT5Ea3x)
























