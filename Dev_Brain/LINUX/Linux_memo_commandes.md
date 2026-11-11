---
tags:
  - linux
  - ubuntu
  - terminal
  - memo
  - commandes
  - formation-greta
date: 2026-11-03
cours: Linux – Introduction et premiers pas (Thierry Bouedo, nov. 2026)
---

# Mémo des commandes Linux

#linux #memo #terminal #bash #ubuntu

Fiche détaillée : []



---

## 1. Se repérer et naviguer

| Commande           | Définition                                            |
| ------------------ | ----------------------------------------------------- |
| `pwd`              | Où suis-je ? (affiche le dossier courant)             |
| `ls`               | Liste le contenu du dossier                           |
| `ls -l`            | Liste détaillée (droits, propriétaire, taille, date)  |
| `ls -a`            | Montre aussi les fichiers cachés (commençant par `.`) |
| `ls -al`           | Les deux à la fois                                    |
| `cd <chemin>`      | Change de dossier                                     |
| `cd ..`            | Remonte d'un niveau                                   |
| `cd ../..`         | Remonte de deux niveaux                               |
| `cd /home/lisa`    | Chemin **absolu** (part de `/`)                       |
| `cd martin/images` | Chemin **relatif** (part d'ici)                       |
| `cd`               | Retour au dossier personnel                           |

Rappel : `.` = ici · `..` = dossier parent · `/` = racine · **sensible à la casse**.

---

## 2. Créer, copier, déplacer, supprimer

| Commande                 | Définition                                   |
| ------------------------ | -------------------------------------------- |
| `mkdir <dossier>`        | Crée un dossier                              |
| `mkdir -p a/b/c`         | Crée tout le chemin si les dossiers manquent |
| `touch <fichier>`        | Crée un fichier vide (ou met à jour sa date) |
| `cp <source> <dest>`     | Copie un fichier                             |
| `cp -r <dossier> <dest>` | Copie un **dossier** (récursif)              |
| `mv <source> <dest>`     | Déplace un fichier ou dossier                |
| `mv <ancien> <nouveau>`  | **Renomme** (même dossier)                   |
| `rm <fichier>`           | Supprime un fichier, **définitif**           |
| `rm -r <dossier>`        | Supprime un dossier et tout son contenu      |
| `rmdir <dossier>`        | Supprime un dossier **vide**                 |
| `ln -s <cible> <lien>`   | Crée un **lien symbolique** (raccourci)      |

**Joker** : `*` = n'importe quoi. Ex. `rm image*.jpg` , `cp *.txt sauvegarde/`.
⚠️ Ne jamais écrire `rm <lien>/` avec un `/` final (peut toucher le contenu visé).

---

## 3. Lire, chercher, comparer

| Commande                     | Définition                               |
| ---------------------------- | ---------------------------------------- |
| `cat <fichier>`              | Affiche le contenu d'un fichier          |
| `head -n <N> <fichier>`      | Affiche les N premières lignes           |
| `tail -n <N> <fichier>`      | Affiche les N dernières lignes           |
| `less <fichier>`             | Lit page par page (`q` pour quitter)     |
| `grep <motif> <fichier>`     | Cherche un texte dans un fichier         |
| `find <dossier> -name <nom>` | Cherche des fichiers par nom             |
| `file <fichier>`             | Indique le type d'un fichier             |
| `stat <fichier>`             | Droits, propriétaire, dates d'un fichier |
| `diff <f1> <f2>`             | Compare deux fichiers ligne par ligne    |
| `cmp <f1> <f2>`              | Compare deux fichiers                    |
| `which <commande>`           | Où se trouve ce programme                |

---

## 4. Redirection et pipe

| Symbole     | Définition                                                   | Exemple                  |
| ----------- | ------------------------------------------------------------ | ------------------------ |
| `>>`        | Ajoute la sortie d'une commande **à la fin** d'un fichier    | `ls -al >> dir.txt`      |
| `>`         | Envoie la sortie dans un fichier en **l'écrasant**           | `ls > liste.txt`         |
| `\|` (pipe) | La sortie de la commande 1 devient l'entrée de la commande 2 | `ps aux \| grep firefox` |

---

## 5. Droits et propriétaires

| Commande                     | Définition                                       |
| ---------------------------- | ------------------------------------------------ |
| `ls -l`                      | Affiche les droits : `d rwx r-x --x`             |
| `chmod [ugoa][+-=][rwx] <f>` | Change les droits (lettres)                      |
| `chmod 755 <f>`              | Change les droits (chiffres)                     |
| `chown [-R] <user> <f>`      | Change le **propriétaire** (souvent avec `sudo`) |
| `chgrp [-R] <groupe> <f>`    | Change le **groupe**                             |
| `umask`                      | Droits par défaut à la création                  |
| `sudo <commande>`            | Exécute avec les droits administrateur           |

**Lettres** : `u` propriétaire · `g` groupe · `o` autres · `a` tous · `+` ajoute · `-` retire · `=` fixe.
**Droits** : `r` lire (4) · `w` écrire (2) · `x` exécuter / traverser (1).

| Chiffres | Lettres     | Usage typique             |
| -------- | ----------- | ------------------------- |
| `755`    | `rwxr-xr-x` | programme, dossier public |
| `644`    | `rw-r--r--` | fichier normal            |
| `600`    | `rw-------` | fichier privé             |
| `751`    | `rwxr-x--x` | exemple du cours          |

Exemples du cours : `chmod o+rw f` · `chmod a-x f` · `chmod go=r f`

---

## 6. Utilisateurs et groupes

| Commande / fichier                | Définition                                 |
| --------------------------------- | ------------------------------------------ |
| `whoami`                          | Qui suis-je ?                              |
| `id`                              | Mon identifiant (UID) et mes groupes (GID) |
| `groups`                          | Liste des groupes de l'utilisateur         |
| `useradd <nom>` / `adduser <nom>` | Crée un utilisateur                        |
| `usermod`                         | Modifie un utilisateur                     |
| `userdel <nom>`                   | Supprime un utilisateur                    |
| `groupadd <nom>`                  | Crée un groupe                             |
| `passwd [<nom>]`                  | Change un mot de passe                     |
| `su <nom>`                        | Prend l'identité d'un autre utilisateur    |
| `who` / `w`                       | Qui est connecté                           |
| `/etc/passwd`                     | Fichier des utilisateurs                   |
| `/etc/group`                      | Fichier des groupes                        |

---

## 7. Informations système

**Matériel**

| Commande | Définition |
|---|---|
| `lspci` | Périphériques du bus PCI |
| `lscpu` | Infos processeur |
| `lsusb` | Périphériques USB |
| `free -h` | Mémoire (RAM) utilisée / libre |
| `df -h` | Espace disque par partition |
| `du -sh <dossier>` | Taille d'un dossier |
| `uname -a` | Infos noyau et système |
| `uname -r` | Version du noyau |
| `uptime` | Depuis quand le système tourne |
| `cat /proc/meminfo` | Détails mémoire |
| `cat /proc/cpuinfo` | Détails processeur |
| `cat /proc/devices` | Périphériques installés |

**Modules du noyau**

| Commande | Définition |
|---|---|
| `lsmod` | Liste les modules chargés |
| `sudo insmod <fichier>.ko` | Charge un module |
| `sudo rmmod <nom>` | Retire un module |

**Processus**

| Commande | Définition |
|---|---|
| `top` | Processus en direct (PID, CPU, mémoire) |
| `ps aux` | Liste des processus **avec le propriétaire** |
| `ps aux \| grep <nom>` | Filtre sur un programme |
| `kill <PID>` | Arrête un processus |

---

## 8. Paquets : installer des logiciels

**Debian / Ubuntu : `apt`** (nb sudo)

| Commande                    | Définition                                      |
| --------------------------- | ----------------------------------------------- |
| `apt update`                | Rafraîchit la **liste** des paquets disponibles |
| `apt upgrade`               | Met à jour **tous** les paquets installés       |
| `apt install <paquet>`      | Installe                                        |
| `apt install ./fichier.deb` | Installe depuis un fichier `.deb`               |
| `apt remove <paquet>`       | Désinstalle                                     |
| `apt purge <paquet>`        | Désinstalle **et** efface la configuration      |
| `apt autoremove`            | Supprime les paquets devenus inutiles           |
| `apt search <mot>`          | Cherche un paquet                               |
| `apt show <paquet>`         | Infos sur un paquet                             |
| `apt list`                  | Liste des paquets                               |

**RedHat / Fedora : `dnf`**

| Commande | Définition |
|---|---|
| `dnf install <p>` | Installe |
| `dnf update [<p>]` | Met à jour |
| `dnf downgrade <p>` | Revient à une version antérieure |
| `dnf remove <p>` | Désinstalle |
| `dnf list [installed]` | Liste (disponibles / installés) |
| `dnf search <mot>` | Cherche dans les descriptions |
| `dnf provides <fichier>` | Quel paquet contient ce fichier |
| `dnf info <p>` | Infos |

---

## 9. Services (systemd)

| Commande                           | Définition                       |
| ---------------------------------- | -------------------------------- |
| `systemctl`                        | Liste les services               |
| `systemctl status <service>`       | État d'un service                |
| `sudo systemctl start <service>`   | Démarre                          |
| `sudo systemctl stop <service>`    | Arrête                           |
| `sudo systemctl restart <service>` | Redémarre                        |
| `sudo systemctl enable <service>`  | Lance au démarrage de la machine |

Exemple (activité 6.a) : `systemctl status apache2` · test sur `http://localhost/` · contenu dans `/var/www/html`.

---

## 10. Réseau et accès distant

| Commande                    | Définition                           |
| --------------------------- | ------------------------------------ |
| `ping <adresse>`            | La machine répond-elle ?             |
| `ip addr`                   | Mon adresse IP et ma config réseau   |
| `ifconfig`                  | Idem (ancienne commande)             |
| `ssh <login>@<adresse>`     | Se connecter à une machine distante  |
| `ssh-keygen`                | Crée sa clé SSH                      |
| `curl <URL>` / `wget <URL>` | Récupère / télécharge depuis une URL |

⚠️ `ipconfig` (slide) = Windows. Sous Linux : `ip addr`.

**NFS (partage de disque, activité 6.b)** : `/etc/exports` (côté serveur) · `showmount -e` (voir ce qui est exporté) · point de montage + `mount` (côté client) · `/etc/fstab` (montage permanent, à nettoyer après le TP).

---

## 11. Archives et compression 

| Commande                       | Définition                  |
| ------------------------------ | --------------------------- |
| `tar -czvf a.tar.gz <dossier>` | Crée une archive compressée |
| `tar -xzvf a.tar.gz`           | La décompresse              |
| `zip -r a.zip <dossier>`       | Crée un zip                 |
| `unzip a.zip`                  | Décompresse un zip          |

---

## 12. Aide et confort du terminal

| Commande / raccourci | Définition                            |
| -------------------- | ------------------------------------- |
| `<commande> --help`  | Résumé des options                    |
| `help <commande>`    | Aide des commandes intégrées au shell |
| `man <commande>`     | Manuel complet (`q` pour quitter)     |
| `history`            | Historique des commandes tapées       |
| `clear`              | Efface l'écran                        |
| `exit`               | Quitte la session                     |
| `Tab`                | Complète automatiquement un nom       |
| `↑` / `↓`            | Rappelle les commandes précédentes    |
| `Ctrl + C`           | Interrompt la commande en cours       |
| `Ctrl + L`           | Efface l'écran                        |

---

## 13. Dossiers importants

| Dossier | Contient |
|---|---|
| `/` | Racine de tout |
| `/home` | Dossiers personnels |
| `/etc` | Configuration |
| `/bin` | Commandes de base |
| `/boot` | Démarrage |
| `/dev` | Périphériques |
| `/lib` | Bibliothèques, modules du noyau |
| `/proc` | État du noyau et des processus (virtuel) |
| `/var/www/html` | Racine du serveur web Apache |

---

## Les 10 commandes à connaître par cœur

`pwd` · `ls -al` · `cd` · `mkdir` · `touch` · `cp` · `mv` · `rm` ⚠️ · `chmod` · `sudo apt install`
