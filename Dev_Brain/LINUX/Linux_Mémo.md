
Cours [Linux_Intro] « Linux : introduction et premiers pas » - Thierry Bouedo - Kercode / GRETA Bretagne Sud

# **1. Historique et philosophie**

|   |   |
|---|---|
|**Date**|**Événement**|
|Années 1970|**Unix** créé par AT&T (monde universitaire)|
|1977|**BSD** (Berkeley Software Distribution), libre de code AT&T en 1991|
|1983|**Richard Stallman** lance **GNU** (« GNU is Not Unix ») ; GCC dès 1985 ; noyau **Hurd** inachevé|
|1991|**Linus Torvalds** crée le **noyau Linux**, publié sous **licence GPL**|

**GNU + noyau Linux = GNU/Linux.**

- **Logiciel libre** (GPL) : 4 libertés = utiliser, étudier, modifier, redistribuer
    
- **Interopérabilité** : protocoles standardisés, **formats ouverts** (ex. Apache)
    
- **Communauté** : entraide et partage
    

# **2. Distributions**

**Distribution** = noyau Linux + système GNU + outils d'installation/administration + gestionnaire de paquets + logiciels tiers.

|   |   |   |
|---|---|---|
|**Famille**|**Exemples**|**Gestionnaire de paquets**|
|Debian|Debian, **Ubuntu**|apt|
|Red Hat|RedHat, Fedora, CentOS|dnf (ex-yum)|

Bureaux : Gnome, KDE… Gestion des services : systemd (Ubuntu, Fedora).

# **3. Structure du système**

**Couches** (du centre vers l'extérieur) : Matériel → **Noyau** → Bibliothèque C (**Glibc**) → Services → Applications. Le noyau expose environ 380 **appels système**.

- Avantages : modularité (maintenance, évolution, portabilité) et développement collaboratif (fiabilité)
    

## **Modules du noyau**

Emplacement : /lib/modules/$(uname -r)/

|   |   |
|---|---|
|**Commande**|**Rôle**|
|lsmod|Lister les modules (= contenu de /proc/modules)|
|sudo insmod <chemin>/<nom>.ko|Charger un module|
|sudo rmmod <nom>|Retirer un module|

Catégories de dossiers : arch/ (processeurs, crypto, kvm), fs/ (systèmes de fichiers : fat, ext4, btrfs), sound/, video/, kernel/, crypto/, drivers/ (un dossier par type de périphérique).

## **Infos matériel (hardware)**

|                   |                                                      |
| ----------------- | ---------------------------------------------------- |
| **Commande**      | **Rôle**                                             |
| lspci             | Périphériques du bus PCI (bas niveau)                |
| cat /proc/meminfo | Mémoire vive                                         |
| cat /proc/cpuinfo | Processeur(s)                                        |
| cat /proc/devices | Périphériques installés (plus haut niveau que lspci) |
| df -m / df -k     | État des disques et partitions (Mo / Ko)             |

## **Infos logiciel (processus en cours d'exécution)**

|              |                                                    |
| ------------ | -------------------------------------------------- |
| **Commande** | **Rôle**                                           |
| top          | Tous les processus : PID, nom, CPU, mémoire, temps |
| ps aux       | Plus lisible, **indique le propriétaire**          |

**À retenir :** top et ps exploitent /proc/. Ce n'est **pas** la liste des logiciels installés (ça, c'est la gestion des paquets).

# **4. Système de fichiers**

**Attention :** Linux est **sensible à la casse** (Fichier ≠ fichier).

Arborescence : / racine → /bin /boot /dev /etc /home /lib /var /proc… Les dossiers perso sont dans /home/<utilisateur>.

**Navigation**

|**Commande**|**Rôle**|
|pwd|Où suis-je ?|
|ls / ls -al|Contenu du dossier (détaillé + fichiers cachés)|
|cd <chemin>|Changer de dossier|

- **Chemin relatif** : cd martin/images ou cd ./martin/images
    
- **Chemin absolu** (commence par /) : cd /home/lisa
    
- **Remonter** : cd .. (1 niveau), cd ../.. (2 niveaux), cd ../videos
    

 **Manipulation des fichiers**


|**Commande**|**Rôle**|**Remarques**|
|mkdir <dossier>|Créer un dossier|-p crée tout le chemin|
|rmdir <dossier>|Supprimer un dossier **vide**||
|touch <fichier>|Créer un fichier vide||
|rm <fichier>|Supprimer un fichier|**Définitif** ; jokers : rm image*.jpg|
|rm -r <dossier>|Supprimer dossier + contenu|Récursif|
|cp <source> <dest>|Copier|-r pour un dossier|
|mv <source> <dest>|Déplacer|Marche sur les dossiers sans -r|
|mv <ancien> <nouveau>|**Renommer**|Même commande que déplacer|

## **Liens symboliques (raccourcis)**

ln -s <chemin_physique> <lien>

ln -s ./audio/blues ./favori

- rm <lien> supprime le lien seulement
    
- **Attention** : rm <lien>/ (avec le / final) détruit **aussi le contenu ciblé**
    

**Redirection et pipe**


|**Opérateur**|**Rôle**|**Exemple**|
|>>|Rediriger la sortie vers un fichier (ajoute à la fin)|ls -al >> dir.txt|
|>|Idem mais **écrase** le fichier|ls -al > dir.txt|
|\||**Pipe** : sortie d'une commande = entrée de la suivante|ps aux \| grep firefox|
|history|Affiche les commandes tapées||

**Utilisateurs et groupes**

- /etc/passwd : utilisateurs (id, groupe primaire, shell…)
    
- /etc/group : groupes
    
- Commandes : useradd, usermod, groupadd…
    

 **Droits (permissions)**

**3 catégories** : **u** (user, propriétaire) · **g** (groupe) · **o** (others, autres) · **a** (all, tous)

**3 droits** : **r** lecture · **w** écriture (et suppression) · **x** exécution

-rwxr-x--x   fichier   ->  u=rwx  g=r-x  o=--x

drwxr-x--x   dossier   ->  d = répertoire

**À retenir :** Sur un **dossier**, x = droit de passage / voir le contenu.


|**Commande**|**Rôle**|
|chmod [ugoa][+-=][rwx] <fichier>|Modifier les droits (par le propriétaire)|
|chown [-R] <nouveau-proprio> <fichier>|Changer le propriétaire|
|chgrp [-R] <nouveau-groupe> <fichier>|Changer le groupe|

+ ajoute · - retire · = affecte exactement · -R = récursif (dossiers)


|**Exemple**|**Effet**|
|chmod o+rw fichier.txt|Les autres peuvent lire/écrire (peu sécurisé)|
|chmod a-x fichier.txt|Plus personne n'exécute|
|chmod go=r fichier.txt|Groupe et autres en lecture seule|
|chmod 755 fichier|Notation numérique : r=4, w=2, x=1 par catégorie (rwxr-xr-x)|

# **5. Gestion des paquets**

|   |   |   |
|---|---|---|
|**Action**|**Debian/Ubuntu (****apt****)**|**Red Hat/Fedora (****dnf****)**|
|Installer|apt install <paquet>|dnf install <paquet>|
|Installer un fichier|apt install /chemin/fichier.deb||
|Mettre à jour l'index|apt update|(automatique)|
|Mettre à jour|apt upgrade [<paquet>]|dnf update [<paquet>]|
|Désinstaller|apt remove <paquet>|dnf remove <paquet>|
|Désinstaller + config|apt purge <paquet>||
|Rétrograder||dnf downgrade <paquet>|
|Infos|apt show <paquet>|dnf info <paquet>|
|Lister|apt list|dnf list / dnf list installed|
|Rechercher|apt search <mot>|dnf search <mot>|
|Trouver par fichier||dnf provides /usr/bin/fichier|

**Astuce :** Sur Ubuntu, toujours en sudo. update met à jour la **liste**, upgrade met à jour les **logiciels**.

**TP 5.a** : lister les paquets → chercher gimp → l'installer → le lancer.

# **6. Services (daemons)**

- Chaque programme qui tourne = un **processus**, identifié par un **PID**
    
- **Daemon / service** : processus en tâche de fond, sans terminal, de durée indéterminée, qui attend une tâche. Son parent est le **PID 1** (mort uniquement à l'arrêt du système)
    
- La plupart démarrent au boot
    

|   |   |
|---|---|
|**Commande (systemd)**|**Rôle**|
|systemctl|Lister les services|
|systemctl status <service>|Statut|
|systemctl start <service>|Démarrer|
|systemctl stop <service>|Arrêter|
|systemctl restart <service>|Redémarrer|
|systemctl enable <service>|Lancer au démarrage|

**TP 6.a : serveur web Apache**

apt search apache2

sudo apt install apache2

sudo systemctl start apache2

systemctl status apache2

# contenu à placer dans /var/www/html

# test : http://localhost/

**TP 6.b : partage de disque NFS** (en binôme, serveur + client)

- **Serveur** : installer NFS serveur → activer avec systemctl → configurer /etc/exports (export avec droits restreints) → vérifier avec showmount -e
    
- **Client** : créer un **point de montage** → mount le disque du voisin → option : l'inscrire dans /etc/fstab (à **effacer** en fin de TP)
    

# **7. Réseau**

|   |   |
|---|---|
|**Commande**|**Rôle**|
|ping <adresse>|La machine répond-elle ?|
|ip addr|Adresse IP et config réseau (ipconfig = Windows)|

**SSH** (connexion à distance)

sudo apt install openssh-server    # installer openSSH

ssh login@adresse_ip               # se connecter

ssh-keygen -t ed25519              # créer sa clé

ssh-copy-id login@adresse_ip       # copier la clé publique chez le voisin

# **Pièges à retenir**

- rm est **définitif** (pas de corbeille) ; rm -r encore plus
    
- mv sert à **déplacer ET renommer**
    
- rm lien/ détruit le contenu ciblé
    
- Sensible à la casse
    
- chmod : u propriétaire, **`g` groupe**, o autres, a tous
    
- >> ajoute, > écrase
    
- top / ps = processus **en cours**, pas les logiciels installés
    
- apt update ≠ apt upgrade
    

**Erreurs dans le support de cours :** slide droits (4/5) « a pour le groupe » → c'est **g** ; slide droits (5/5) man chown pour la notation numérique → c'est **`man chmod`** ; slide NFS « show mount » → **`showmount`**.

# **Auto-test : TP « La médiathèque »**

- Reconstruire membres/martin/{images, audio/{blues, classique}} et membres/lisa/multimedia avec mkdir -p et touch
    
- Copier music002.mp3 dans le dossier de Lisa
    
- Déplacer les morceaux du blues vers le classique
    
- Supprimer le compte de Lisa depuis classique : rm -r ../../../lisa