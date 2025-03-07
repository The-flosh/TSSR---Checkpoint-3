Exercice 2 - VM Linux

Partie 1 - Gestion des utilisateurs

Q.2.1.1  
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/16.png)    
Q.2.1.2 
je préconise un mot de passe sécurisée ici : Azerty_.uiop1* 
et je le rajoute dans les sudoeur.
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/17.png)    
Partie 2 - Configuration de SSH  

Q.2.2.1   
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/18.png)      
Q.2.2.2   
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/19.png)      
Q.2.2.3    
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/20.png)      

Partie 3 - Analyse du stockage  

Q.2.3.1   
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/21.png)  
En systeme de fichier actuellement montée nous avons:  
⦁	udev
⦁	tmpfs
⦁	/dev/mapper/cp3–vf-root
⦁	/dev/md0p1
Q.2.3.2 
en type de systeme de stockage nous avons : 
⦁	udev qui utilise devtmpfs
⦁	tmpfs qui utilise tmpfs
⦁	/dev/mapper/cp3–vf-root qui utilise ext4
⦁	/dev/md0p1 qui utilise ext2
Q.2.3.3   
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/22.png)  
 deja grace a cette commande je sais maintenant que je doit réparer un raid 1 sur md0.  
je partitione ensuite le nouveau disque que je vient de rajouter (sdb).   
 ![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/23.png)  
je rajoute ensuite le sdb au raid et surveille sa resynchronisation.  
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/24.png)  
je reverifie que la sychro c’est bien faite et le travail est fini ^^. 
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/25.png)  
Q.2.3.4   
pour ajoutée le lvm j’ai utiliser : 
⦁	lvcreate -L 2G -n backup vg_name
je l’ai ensuite fomrater grace a la commande : 
⦁	mkfs.ext4 /dev/vg_name/backup
j’ai apres crée le point de montage par defaut “/var/lib/bareos/storage“ avec la commande:
⦁	mkdir -p /var/lib/bareos/storage
j’ai ensuite montée le volume logique avec cette commande : 
⦁	mount /dev/vg_name/backup /var/lib/bareos/storage
puis configurer son montage automatique au démarrage en rajoutant ceci au fichier /etc/fstab:
⦁	 /dev/vg_name/backup /var/lib/bareos/storage ext4 defaults 0 2  
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/26.png)  
  
Q.2.3.5 
avec la commande “vgs” nous pouvons voir qu’il reste 1.79G  le groupe de volume.  
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/27.png)  
Partie 4 - Sauvegardes  

Q.2.4.1 
bareos-dir : (directeur)il organise et gère la gestion de l'ensemble sauvegardes/restauration/vérification.il est aussi responsable de la gestion des jobs,de la planificationdes tache et de  la coordination des autre composant.
bareos-sd :(storage deamon) il gère le stockage des données et écrit les sauvegarde grace a ce qui lui est transmit par bareos-sd.
bareos-fd : (file deamon) il exécute les sauvegardes sur la machine du client et envoie les fichiers a bareos-sd  pour qu’il les sauvegarde, en cas de restauration il récupère les fichiée .

Partie 5 - Filtrage et analyse réseau

Q.2.5.1    
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/28.png)  
Q.2.5.2   
Les types de communication autorisées sont :
⦁	ct state established,related
⦁	iifname “lo”
⦁	tcp dport 22
⦁	ip protocol icmp
⦁	ip6 nexthdr ipv6-icmp
Q.2.5.3 
Les types de communication interdite sont :
⦁	ct state invalid

Q.2.5.4    
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/29.png)  
fait à l’aide d’internet…  
Partie 6 - Analyse de logs

Q.2.6.1 

ok : /24
nr : 
faux : 
idk je n'en ai pas trouver 
