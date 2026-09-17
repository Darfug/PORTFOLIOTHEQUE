# Vitrine alternance, Mastère Direction Artistique, BRASSART Lille

Page vitrine envoyée aux agences, studios et annonceurs pour leur faire découvrir
les étudiants DA4 et DA5 en recherche d'alternance. Site statique, hébergement
gratuit, contenu modifiable depuis le navigateur.

## Contenu

| Fichier | Rôle | À publier ? |
|---|---|---|
| `index.html` | La vitrine publique | oui |
| `etudiants.json` | Toutes les données : référentiel de filtres et fiches | oui |
| `images/` | Les visuels d'accroche, WebP 1600 px | oui |
| `assets/` | Logos BRASSART blanc et noir, favicon | oui |
| `_headers` | Force le `noindex` sur tout le site (Cloudflare Pages) | oui |
| `admin.html` | L'outil d'édition | non, à garder sur votre machine |

## Mise en ligne, une seule fois

1. Créez un dépôt GitHub privé, par exemple `vitrine-alternance`.
2. Déposez-y `index.html`, `etudiants.json`, `_headers` et les dossiers `images/` et `assets/`.
   Ne déposez pas `admin.html`.
3. Sur Cloudflare Pages, créez un projet connecté à ce dépôt. Aucune commande
   de build, dossier de sortie à la racine.
4. Vous obtenez une adresse du type `vitrine-alternance.pages.dev`. C'est le lien
   à envoyer aux entreprises.

## Le token d'édition

Dans GitHub : Settings, Developer settings, Personal access tokens,
Fine-grained tokens.

- Accès limité au seul dépôt de la vitrine
- Permission `Contents` en lecture et écriture, rien d'autre
- Durée de vie 1 an, à renoter dans votre agenda

Ouvrez `admin.html` depuis votre disque, renseignez le dépôt et le token une fois.
Ils restent stockés dans ce navigateur.

## Modifier le contenu

1. Ouvrir `admin.html`, cliquer sur « Charger les données ».
2. Ajouter une fiche, envoyer les visuels, basculer un étudiant en « Placé ».
3. Cliquer sur « Publier en ligne ». La page est à jour une minute plus tard.

Un étudiant passé en « Placé » disparaît de la grille mais alimente le compteur
« Déjà placés cette année » affiché en haut de page.

## Envoyer un lien ciblé

Deux paramètres se combinent dans l'adresse :

- `?src=nom_entreprise` identifie le destinataire et se propage vers les liens
  de portfolio, ce qui permet de savoir qui a cliqué
- les filtres sont dans l'adresse : sélectionnez les profils voulus sur la page,
  cliquez sur « Copier ce lien filtré », vous obtenez une vitrine sur mesure

Exemple : `...pages.dev/?src=agence_martin&specialite=Motion%20design`

## Aperçu en local

La page charge un fichier JSON, un double-clic sur `index.html` ne suffit pas.
Depuis le dossier :

```
python3 -m http.server 8000
```

puis ouvrez `http://localhost:8000`.

## Avant la première diffusion

- Autorisation écrite de diffusion signée par chaque étudiant, portant sur le nom,
  les visuels et le lien du portfolio
- Vérifier que les travaux affichés ne contiennent pas de commande client sous NDA
- Renseigner l'email de contact réel dans l'en-tête depuis `admin.html`
- Retirer les huit fiches de démonstration

## Charte graphique

La page applique la charte BRASSART :

| Élément | Valeur |
|---|---|
| Couleur principale | magenta `#C61063` |
| Couleur de la filière Direction Artistique | `#FF451D`, utilisée pour les filtres actifs et les années |
| Typographie | Gotham, avec Montserrat en substitut web libre |
| Logotype | version blanche sur fond magenta et sur fond noir |

Gotham est une police sous licence, non diffusable sur un site public. La page
la charge en priorité si elle est installée sur le poste, et bascule sinon sur
Montserrat, dont le dessin géométrique en est proche. Si l'école dispose d'une
licence web Gotham, il suffit de remplacer l'appel Google Fonts par le kit
correspondant, les variables CSS sont déjà en place en haut du fichier.
