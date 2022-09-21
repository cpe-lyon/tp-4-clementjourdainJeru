# Exercice 1. Commandes de base

1.  Pour mettre à jour notre système, il faut utiliser les commandes `sudo apt update`, puis `sudo ap upgrade`
2.  On crée un alias "maj" en tapant `alias maj='sudo apt update | sudo apt upgrade`. Pour conserver cet alias au prochain démarrage, il faut le stocker dans bashrc
3.  Grâce à /var/log/dpkg.log, on sait que les 5 derniers paquets installés sont initramfs-tools, dbus, man-db, libc-bin et cryptsetup-initramfs
4.  Les derniers paquets installés avec la commande `apt install` sont trouvables avec la commande `grep " install " /var/log/dpkg.log`, et donc sont os-prober, libevdev2, thermald, upower, usbmuxd
5.  Les commandes pour trouver le nombre de paquets installés sont `apt list --installed | grep -c "installé"` et `dpkg --list | wc --lines`, et l'on trouve respectivement 606 et 611 paquets. Cette différence provient du fait que apt compte les lignes et qu'il existe des lignes soit de description soit d'erreur
6.  Il existe plus de 68000 paquets disponibles si l'on cherche sur aptitude.
7.  Glances permet d'afficher l'état des principales ressources, tldr convertit les pages man en explications concises, et hollywood te fais hacker comme un film hollywoodien qui ne comprend rien au hacking
8.  Les paquets permettant de jouer au sudoku sont gnome-sudoku, ksusdoku, nudoku

# Exercice 2. 

La commande ls provient du paquet coreutils, qui peut être trouvé avec la commande `dpkg -S /bin/ls`
```
#!/bin/bash

commande=$1

which -a $commande | xargs dpkg -S 2> /dev/null | cut -d":" -f1
```
# Ecercice 3.
```
#!/bin/bash

function param()
{
        param=$(apt list -a $1)
        if [[ $param == *"installé"* ]]; then
                 echo "INSTALLE"
        else
                echo "NON INSTALLE"
        fi
}

param $1
```

# Exercice 4.

On liste les programmes venant de coreutils avec `dpkg -L coreutils`. Le fichier `[` est un test pour vérifier le type des fichiers et comparer leurs valeurs

# Exercice 5. 

Il faut tout d'abord installer aptitude avec `sudo apt install aptitude`. Lynx est un navigateurs web en mode texte utilisable via une console ou un terminal, tandis que Emacs est  un éditeur de texte très puissant, extensible et personnalisable. Pour les installer avec aptitude il faut les chercher avec `/`, puis `+`, double g puis l'installer en tant que root.

# Exercice 6.


