
| Commande                             | Description                                            |
| :----------------------------------- | :----------------------------------------------------- |
| Aide                                 |                                                        |
| git help <commande>                  | Infos sur l'utilisation d'une commande                 |
| **Démarrer**                         |                                                        |
| git init                             | Initialiser un dépôt local (à la création du projet)   |
| git clone <url>                      | Cloner (télécharger) un dépôt distant existant         |
| **Enregistrer (local)**              |                                                        |
| git status                           | Voir l'état des fichiers (modifié, stagé, supprimé…)   |
| git add <fichier/dossier>            | Ajouter à l'index (stage)                              |
| git add .                            | Ajouter tous les fichiers                              |
| git rm --cached <fichier/dossier>    | Retirer de l'index sans supprimer le fichier du disque |
| git commit -m "message"              | Enregistrer les modifs stagées                         |
| git commit -a -m "message"           | Add + commit des fichiers déjà suivis                  |
| git log / git log --oneline          | Historique des commits                                 |
| **Relier à GitHub (une seule fois)** |                                                        |
| git branch -M main                   | Renommer la branche principale en main                 |
| git remote add origin <url>          | Lier le projet au dépôt GitHub                         |
| git push -u origin main              | Premier envoi (-u obligatoire cette fois-là)           |
| **Envoyer / récupérer**              |                                                        |
| git push                             | Envoyer sur GitHub (après le premier -u)               |
| git fetch                            | Récupérer les nouveautés distantes sans fusionner      |
| git pull                             | Récupérer et fusionner dans ta branche                 |
| **Branches**                         |                                                        |
| git branch                           | Lister les branches                                    |
| git switch -c <branche>              | Créer une branche et s'y placer                        |
| git switch <branche>                 | Changer de branche                                     |
| git merge <branche>                  | Fusionner dans la branche actuelle                     |
| git push -u origin <branche>         | Envoyer une nouvelle branche                           |
| **Annuler / corriger**               |                                                        |
| git restore <fichier>                | Annuler les modifs non enregistrées                    |
| git restore --staged <fichier>       | Retirer un fichier du add                              |
| git commit --amend -m "msg"          | Corriger le dernier commit (avant push)                |
| git stash / git stash pop            | Mettre le travail de côté / le récupérer               |
