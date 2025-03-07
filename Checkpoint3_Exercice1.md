Exercice 1 - VM Windows

Partie 1 - Gestion des utilisateurs  
Q.1.1.1  
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/1.png)    
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/2.png)  
mdp : Azerty* (à changer à la prochaine connexion )  
J’ai copier le profil de kelly Rhameur et est appelé ce nouveau profil Lionel Lemarchand de par se fait il dispose des meme attribut que Kelly.  
Q.1.1.2   
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/3.png)   
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/4.png)   
Dans un premier temps j’ai créé une OU appeller “deactivatedusers”, je suis ensuite aller sur Kelly puis je l’ai déplacée dans l’OU.  
Q.1.1.3   
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/5.png)   
je suis aller dans son ancienne OU > propriété > membres puis j’ai chercher Kelly  et l’ai remove du groupe.   
Q.1.1.4 
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/6.png)   
j’ai rename le dossier de Kelly en rajoutant le “6ARCHIVE3 puis j’ai crée celui de lionel Lemarchand.  

Partie 2 - Restriction utilisateurs

Q.1.2.1  
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/7.png)   
pour modifier les les temps de connexion de Gabriel Ghul je l’ai chercher dans l’AD avec find puis propriétés et ensuite je suis aller dans logon hours dans account.j’ai ensuite selectionnée la plage demander et ai confirmée.   
Q.1.2.2   
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/8.png)   
pour bloquer sa connexion au seul ordinateur “CLIENT01” je l’ai rechercher dans l’ad avec find puis propriétés je suis ensuite aller dnas log on to est ai changer l’option “all computers” sur “The fllowinf computers” et ai rajouter “CLIENT01” dans la liste puis appliquer ces changements.
Q.1.2.3 
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/9.png)   
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/10.png)  
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/11.png)  
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/12.png)  
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/13.png)  
du coup pour faire une stratégie de mot de passe j’ai créé une GPO dans l’OU abuser je suis ensuite aller dans : configuration ordinateur>policies>windows settings >security settings>Account policies>Password policies.j’ai par la suite enabled la complexité minimal des mot de passes , j’ai aussi set un password age allant d’un jour minimum jusqu'à sa date d’expiration allant à 90 jours,j’ai ensuite defini la longueur minimal du mot de passe a 12 et ai activée l’historique des mot des passe pour les 7 precedent.

Partie 3 - Lecteurs réseaux

Q.1.3.1 
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/14.png)  
![screen](https://github.com/The-flosh/TSSR---Checkpoint-3/blob/main/chekpoint/15.png)  
pour crée la GPO dans l’OU Drive-mount j’ai deja crée une GPO sous TSSR.LAN pour que tout le monde soit concernée par celle-ci j’ai pas la suite modifier cette gpo en allant dans: Configuration utilisateur > Préférences > Paramètres Windows > Lecteurs mappés.Avant de crée les deux mapped drive j’ai partagée les deux disque (E et F) et ai nomée leurs partage “PratageE” et “PartageF” j’ai ensuite crée les deux regle mapped drive dans la GPO ou j’ai renseignée leur emplacement et la lettre du lecteur (E et F) pour les montée directement sur les clients, j’ai aussi cochée la casse reconnecter qui permet de reconnecter le lecteur a chaque ouverture de session.j’ai ensuite appliquer le tout.
