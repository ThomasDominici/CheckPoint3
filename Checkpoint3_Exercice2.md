# Partie 1 : Gestion des utilisateurs : 

## Q 2.1.1 : 

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO2/q211.JPG?raw=true)

## Q 2.1.2: 

Pour la création de ce compte, j'ai utilisé :

```Bash
adduser thomas
```

Il s'agit de mon compte utilisateur personnel. Je lui ai donné un mot de passe long et complexe et aucun droit particulier pour éviter tout problème de sécurité. 


# Partie 2 : Configuration de SSH : 

## Q 2.2.1 et Q 2.2.2 :

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO2/q221-q222.JPG?raw=true)

## Q 2.2.3 : 

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO2/q223a.JPG?raw=true)

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO2/tttt.JPG?raw=true)

# Partie 3 : Analyse du stockage : 

## Q 2.3.1 : 

Avec **lsblk**, nous voyons les différents disques et systèmes de fichiers.  
On a ici une disque **sda** de 8 Go, partitionné entièrement et avec mise en place d'un RAID 1 sur le système de fichier **md0**.  
**md0** est divisé en plusieurs partitions : **md0p1** qui contient le boot, **md0p2** de 1K et **md0p5** monté en LVM er qui contient le SWAP et le home.

## Q 2.3.2 :

Ici, on utilise le type de stockage RAID 1 couplé avec du LVM (Logical Volume Manager). Il manque cependant un dique pour le RAID 1 qui consiste à duppliquer les données sur un second disque (mirroring).

## Q 2.3.3 : 

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO2/q233.JPG?raw=true)

## Q 2.3.4 :

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO2/q234a.JPG?raw=true)
![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO2/q234b.JPG?raw=true)

## Q 2.3.5 :

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO2/q235.JPG?raw=true)

Il reste 7.51 GiB dans le volume.

# Partie 4 : Sauvegardes : 

## Q 2.4.1 : 

Nous allons expliquer les 3 rôles suivants : 
- bareos-dir : Director, c'est le chef d'orchestre. Il planifie et contrôle les sauvegardes et le reste des éléments de Bareos.
- bareos-sd : Bareos Storage Daemon, permet d'effectuer des suavegardes qui sont effectuées par un Storage Daemon. On peut faire de sauvegardes sur différents supports.
-  bareos-fd : Bareos File Daemon, c'est l'agent que l'on installe sur chaque machine cliente pour laquelle on veut effectuer des sauvagardes. Collecte et envoie les informations au Storage Daemon.


# Partie 5 : Filtrage et analyse réseau : 

## Q 2.5.1 :

Actuellement, les règles appiquées sur NetFilter sont :  
- Acceptation des ping IPv6 entre voisins
- Acceptation des ping IPv4
- Acceptation du SSH
- Acceptation du ping vers le localhost

## Q 2.5.2 : 

Les types de communications autorisées sont le SSH et le protocole ICMP (ping). 
On le voit grâce aux lignes : 

```
tcp dport ssh accept
ip protocol icmp accept
ip6 nexthdr icmpv6 accept
```


## Q 2.5.3 :

On interdit ici les tentatives de connexions invalides grâce à la ligne :
```
ct state invalid drop
```
Le drop est en effet la commande de blocage de NetFilter.

## Q 2.5.4 : 

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO2/q254.JPG?raw=true)



#  Partie 6 : Analyse de logs : 

## Q 2.6.1 : 

Pour lister les échecs de connexion sur le serveur, nous pouvons aller dans **/var/log/faillog** ou taper la commande suivante : 
```Bash
faillog -u root
```

Cette commande nous donne le résultat suivant :  

![img](https://github.com/ThomasDominici/CheckPoint3/blob/Ressources/ImagesEXO2/q261.JPG?raw=true)

Comme nous pouvons le voir, il n'y a pas eu d'échecs de connexion sur ce serveur pour **root**. Après essai avec **wilder** et **thomas** on a aussi 0 échecs.
