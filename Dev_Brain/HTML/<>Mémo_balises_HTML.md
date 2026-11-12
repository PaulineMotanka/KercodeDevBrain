---
tags: [html, memo, web]
---

# HTML

## Squelette minimal
```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Titre</title>
  <link rel="stylesheet" href="css/style.css">
</head>
<body></body>
</html>
```

## Texte
| Balise | Rôle |
|---|---|
| `<h1>` à `<h6>` | Titres (h1 = principal, un seul) |
| `<p>` | Paragraphe |
| `<strong>` | Importance forte (gras sémantique) |
| `<em>` | Emphase (italique sémantique) |
| `<br>` | Retour à la ligne (orpheline) |
| `<hr>` | Séparation thématique |
| `<blockquote>` | Citation longue |

## Listes
```html
<ul> <li>Non ordonnée</li> </ul>   <!-- puces -->
<ol> <li>Ordonnée</li> </ol>       <!-- numéros -->
```

## Liens et médias
```html
<a href="page.html">Lien interne</a>
<a href="https://exemple.fr" target="_blank" rel="noopener">Lien externe</a>
<a href="#contact">Ancre vers id="contact"</a>
<img src="images/photo.jpg" alt="Description" width="600" height="400">
<figure> <img src="..." alt="..."> <figcaption>Légende</figcaption> </figure>
```

## Balises sémantiques de structure
| Balise | Rôle |
|---|---|
| `<header>` | En-tête de page ou de section |
| `<nav>` | Menu de navigation |
| `<main>` | Contenu principal (unique) |
| `<section>` | Bloc thématique avec titre |
| `<article>` | Contenu autonome (article, fiche) |
| `<aside>` | Contenu secondaire |
| `<footer>` | Pied de page |
| `<div>` / `<span>` | Neutres (sans sens), en dernier recours |

## Tableaux
```html
<table>
  <thead><tr><th>Nom</th><th>Prix</th></tr></thead>
  <tbody><tr><td>Tirage A3</td><td>40 €</td></tr></tbody>
</table>
```

## Formulaires
```html
<form action="traitement.php" method="post">
  <label for="email">Email</label>                          <!-- for = id du champ -->
  <input type="email" id="email" name="email" required>
  <label for="msg">Message</label>
  <textarea id="msg" name="msg"></textarea>
  <button type="submit">Envoyer</button>
</form>
```
Types d'`input` : `text`, `email`, `password`, `number`, `date`, `checkbox`, `radio`, `file`.

## Attributs courants
| Attribut | Usage |
|---|---|
| `id` | Identifiant **unique** |
| `class` | Groupe réutilisable (cible CSS) |
| `href` / `src` | Destination d'un lien / source d'un média |
| `alt` | Texte alternatif d'une image |
| `lang` | Langue |
| `title` | Info-bulle |
| `required`, `placeholder`, `disabled` | Formulaires |

## Commentaire
```html
<!-- Ceci n'est pas affiché -->
```

## Commandes Ubuntu utiles
| Commande | Effet |
|---|---|
| `mkdir -p ~/projets/site/{css,js,images}` | Crée l'arborescence d'un projet |
| `touch index.html` | Crée un fichier vide |
| `code .` | Ouvre le dossier dans VSCode |
| `xdg-open index.html` | Ouvre la page dans le navigateur |
| `ls -R` | Liste tous les fichiers |
| `tree` | Arborescence (installer : `sudo apt install tree`) |

## Raccourcis VSCode
| Raccourci | Effet |
|---|---|
| `!` + `Tab` | Squelette HTML |
| `Ctrl+S` | Enregistrer |
| `Shift+Alt+F` | Formater/indenter |
| `Ctrl+/` | Commenter la ligne |
| `Ctrl+Espace` | Suggestions |
| `ul>li*3` + `Tab` | Emmet : crée une liste de 3 `li` |

## Liens
[[HTML - Procédure]] · [[CSS - Mémo]]