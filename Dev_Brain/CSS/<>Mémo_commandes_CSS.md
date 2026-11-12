---
tags: [css, memo, web]
---


## Sélecteurs
| Sélecteur | Cible |
|---|---|
| `p` | Toutes les balises `<p>` |
| `.carte` | Éléments avec `class="carte"` |
| `#menu` | L'élément avec `id="menu"` |
| `h1, h2` | h1 **et** h2 |
| `nav a` | Les `a` **dans** un `nav` |
| `ul > li` | Les `li` **enfants directs** de `ul` |
| `a:hover` | Au survol de la souris |
| `a:focus` | Au focus clavier (accessibilité) |
| `li:first-child` | Premier enfant |
| `*` | Tous les éléments |

## Intégrer du CSS (3 méthodes)
```html
<link rel="stylesheet" href="css/style.css">   <!-- ✓ recommandé : fichier externe -->
<style> p { color: red; } </style>             <!-- dans le head : petits tests -->
<p style="color: red;">Texte</p>               <!-- en ligne : à éviter -->
```

## Texte
| Propriété | Exemple |
|---|---|
| `color` | `color: #333;` |
| `font-family` | `font-family: Arial, sans-serif;` |
| `font-size` | `font-size: 1rem;` |
| `font-weight` | `font-weight: bold;` |
| `line-height` | `line-height: 1.5;` |
| `text-align` | `text-align: center;` |
| `text-decoration` | `text-decoration: none;` |
| `text-transform` | `text-transform: uppercase;` |

## Boîte
| Propriété | Exemple |
|---|---|
| `width` / `max-width` | `max-width: 1200px;` |
| `height` | `height: 300px;` |
| `padding` | `padding: 10px 20px;` (haut/bas, gauche/droite) |
| `margin` | `margin: 0 auto;` (centre horizontalement un bloc) |
| `border` | `border: 1px solid #ccc;` |
| `border-radius` | `border-radius: 8px;` |
| `box-shadow` | `box-shadow: 0 2px 6px rgba(0,0,0,.2);` |
| `box-sizing` | `box-sizing: border-box;` |

Raccourci à 4 valeurs : `margin: haut droite bas gauche;` (sens des aiguilles d'une montre).

## Couleurs et fonds
```css
color: red;                    /* nom */
color: #ff0000;                /* hexadécimal */
color: rgb(255, 0, 0);         /* rouge, vert, bleu */
background-color: #f5f5f5;
background-image: url("../images/fond.jpg");  /* chemin relatif au fichier CSS */
background-size: cover;
```

## Unités
| Unité | Sens |
|---|---|
| `px` | Pixel (fixe) |
| `%` | Relatif au parent |
| `rem` | Relatif à la taille de police de base (recommandé) |
| `em` | Relatif à la police de l'élément |
| `vw` / `vh` | % de la largeur / hauteur de l'écran |

## Affichage
| Propriété | Effet |
|---|---|
| `display: block` | Prend toute la largeur, saute une ligne |
| `display: inline` | S'insère dans le texte |
| `display: none` | Élément masqué |
| `display: flex` | Flexbox |
| `display: grid` | Grille |

## Flexbox
```css
.conteneur {
  display: flex;
  flex-direction: row;            /* row (ligne) ou column (colonne) */
  justify-content: center;        /* axe principal : flex-start, center, space-between */
  align-items: center;            /* axe secondaire */
  flex-wrap: wrap;                /* retour à la ligne si manque de place */
  gap: 16px;
}
```

## Position
| Valeur | Effet |
|---|---|
| `static` | Par défaut |
| `relative` | Décalé par rapport à sa place normale |
| `absolute` | Placé par rapport au parent positionné |
| `fixed` | Fixe par rapport à l'écran |
| `sticky` | Colle en haut au défilement |

## Variables CSS
```css
:root { --couleur-principale: #0a4d8c; }       /* déclaration */
.bouton { background-color: var(--couleur-principale); }  /* utilisation */
```

## Media query (responsive)
```css
@media (max-width: 768px) {
  .menu { flex-direction: column; }
}
```

## Commentaire
```css
/* Ceci est un commentaire CSS */
```

## Commandes Ubuntu et raccourcis
| Commande / raccourci | Effet |
|---|---|
| `mkdir -p css && touch css/style.css` | Crée le dossier et le fichier CSS |
| `xdg-open index.html` | Ouvre la page |
| `F12` | Outils développeur du navigateur |
| `Ctrl+Shift+R` | Actualisation sans cache |
| `Ctrl+Shift+C` | Sélectionner un élément à inspecter |
| `Ctrl+Espace` (VSCode) | Suggestions de propriétés |
| `Shift+Alt+F` (VSCode) | Indenter le code |

## Liens
[[CSS - Procédure]] · [[HTML - Mémo balises]] · [[Responsive - Procédure]]