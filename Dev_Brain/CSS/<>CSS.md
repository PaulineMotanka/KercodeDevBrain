---
tags: [css, web, front, procedure]
---



## Résumé
CSS décrit **l'apparence** d'une page HTML : couleurs, polices, tailles, espaces, disposition. Le principe : je **sélectionne** un élément, puis je lui applique des **propriétés**.



## Définitions clés
- **CSS** (Cascading Style Sheets) : feuilles de style en cascade.
- **Sélecteur** : désigne les éléments à styler (`p`, `.carte`, `#menu`).
- **Propriété** : ce que je change (`color`, `margin`).
- **Valeur** : le réglage (`red`, `20px`).
- **Déclaration** : `propriété: valeur;`
- **Règle** : sélecteur + `{ déclarations }`.
- **Classe** : étiquette réutilisable (`class="carte"` → `.carte`).
- **Cascade / spécificité** : règles de priorité quand plusieurs règles visent le même élément.
- **Modèle de boîte** : chaque élément est une boîte (contenu, padding, bordure, margin).
- **Flexbox** : système de disposition en ligne ou en colonne.

## Anatomie d'une règle

```css
selecteur {
  propriete: valeur;   /* déclaration */
}

.carte {               /* sélecteur de classe */
  color: #333;         /* couleur du texte */
  padding: 16px;       /* espace intérieur */
}
```

## Schéma : le modèle de boîte

```text
+--------------------------------------+
|              MARGIN                  |  espace extérieur (transparent)
|   +------------------------------+   |
|   |           BORDER             |   |  bordure
|   |   +----------------------+   |   |
|   |   |       PADDING        |   |   |  espace intérieur
|   |   |   +--------------+   |   |   |
|   |   |   |   CONTENU    |   |   |   |  texte, image
|   |   |   +--------------+   |   |   |
|   |   +----------------------+   |   |
|   +------------------------------+   |
+--------------------------------------+
```
> Analogie photo : contenu = la photo, padding = le passe-partout, border = le cadre, margin = la distance avec le tableau voisin.

## Procédure

### 1. Créer le fichier CSS
```bash
mkdir -p css                # dossier dédié aux styles
touch css/style.css         # fichier de styles
```

### 2. Lier le CSS dans le `<head>` du HTML
```html
<link rel="stylesheet" href="css/style.css">  <!-- chemin relatif depuis index.html -->
```

### 3. Remise à zéro de base (en haut de style.css)
```css
* {
  margin: 0;
  box-sizing: border-box;   /* width inclut padding et bordure : plus simple à calculer */
}

body {
  font-family: Arial, sans-serif;  /* police + famille de secours */
  line-height: 1.5;                /* hauteur de ligne lisible */
  color: #222;
}
```

### 4. Cibler avec une classe, puis styler
Dans le HTML :
```html
<article class="carte">
  <h2 class="carte__titre">Titre</h2>
  <p>Texte</p>
</article>
```
Dans le CSS :
```css
.carte {
  background-color: #f5f5f5;
  padding: 16px;                 /* intérieur */
  margin-bottom: 24px;           /* extérieur */
  border: 1px solid #ccc;
  border-radius: 8px;            /* coins arrondis */
}

.carte__titre {
  font-size: 1.5rem;             /* rem : relatif à la taille de base */
  color: #0a4d8c;
}
```

### 5. Disposer des éléments avec Flexbox
```css
.menu {
  display: flex;                  /* éléments côte à côte */
  justify-content: space-between; /* répartition sur l'axe principal */
  align-items: center;            /* alignement sur l'axe secondaire */
  gap: 16px;                      /* espace entre les éléments */
}
```

### 6. Tester et ajuster avec les outils développeur
- `F12` dans le navigateur → onglet **Inspecteur**.
- Cliquer un élément : voir ses règles CSS et sa boîte.
- Modifier une valeur en direct pour tester, puis **reporter dans VSCode** (rien n'est sauvegardé dans le navigateur).

## Ordre de priorité (cascade)
1. Style en ligne `style="..."` (à éviter)
2. `#id`
3. `.classe`
4. `balise`

À spécificité égale, la **dernière règle écrite** gagne.

## ATTENTION
- Oublier le `;` en fin de déclaration → la suivante est ignorée.
- Oublier le `.` devant une classe (`carte` ≠ `.carte`).
- Mauvais chemin dans `href` du `<link>` → aucun style appliqué.
- Cache du navigateur : forcer l'actualisation avec `Ctrl+Shift+R`.
- Tout styler avec des `id` ou en `style=""` : pas réutilisable.
- Utiliser `px` partout : préférer `rem`/`%` pour le responsive.
- Confondre `margin` (extérieur) et `padding` (intérieur).



## Liens
[[CSS - Mémo]] · [[HTML - Procédure]] · [[Responsive - Procédure]] · [[Accessibilité RGAA]]
