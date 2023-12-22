# Partie 1 : Gestion des utilisateurs : 

## Q 1.1.1 : 

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/q111.JPG?raw=true)

## Q 1.1.2 : 

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/q112.JPG?raw=true)

## Q 1.1.3 : 

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/q113.JPG?raw=true)

## Q 1.1.4 : 

Pour créer le dossier personnel, nous allons passer par une GPO, qui créera un dossier personnel à tous les membres du groupe sélectionné, dont Lionel Lemarchand.  

Nous créons d'abord le dossier que nous allons partager.

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/q114a.JPG?raw=true)

  Nous créons ensuite la GPO avec les bon groupe en filtre.

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/q114b.JPG?raw=true)

Nous éditons la GPO avec la création du mappage, ainsi nous attribuons la lettre I au dossier personnel.

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/q114c.JPG?raw=true)

On établit aussi un raccourci vers le bureau pour plus de facilité d'utilisation.

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/q114d.JPG?raw=true)

A chaque fois que nous créons le dossier, le raccourci et le mappage, nous allons cocher la case ci-dessous.

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/q114e.JPG?raw=true)

Nous créons le dossier dans la GPO.

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/q114f.JPG?raw=true)


Nous n'oublions pas de lier la GPO à l'OU voulue pour la mettre en place et de désactiver **Computer configuration settings disabled** dans l'onglet **Details**.


# Partie 2 : Restriction utilisateurs : 

## Q 1.2.1 : 

Pour mettre des restrictions horaires à notre employé, nous allons d'abord modifier les heures de connection dans son **acount**.

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/q121a.JPG?raw=true)

Puis nous allons mettre en place une GPO en suivant le chemin suivant : 
- Configuration ordinateur
- Windows Settings
- Paramètres de sécurité
- Stratégies locales
- Options de sécurité
- Serveur réseau Microsoft : Déconnecter les clients à l'ouverture de session heures expirent
- Enabled

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/q121b.JPG?raw=true)


Nous allons ici mettre uniquement notre employé dans la GPO et la lier à son OU mais en entreprise nous essaierons de créer des GPO plus larges pour bloquer plusieurs utilisateurs et pas qu'un seul.


## Q 1.2.2 : 

Pour empêcher notre employé de se connecter à l'ordinateur client, nous allons de nouveau créer une GPO : 
- Configuration ordinateur
- Windows Settings
- Paramètres de sécurité
- Stratégies locales
- Options de sécurité
- Deny Acces to this computer from the network

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/dsgdsgsd.JPG?raw=true)

## Q 1.2.3 : 

Pour mettre en place une stratégie de mot de passe, nous allons passer par le AD Administrative Center.

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/q123.JPG?raw=true)

Nous avons ici durci les règles de mot de passe avec une longueur minimum  de 12 caractères au lieu de 7 ainsi qu'un nombre d'échec consécutifs maximum de 3.


# Partie 3 : Lecteurs Réseaux : 

## Q 1.3.1 : 

Nous avons ici créé une GPO qui ajoute les lecteurs E: et F: sur les PC clients.
On passe donc par le biais d'un dossier partagé et on édite un mappage de dans la partie **User Configuration**.

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO1/q131.JPG?raw=true)
