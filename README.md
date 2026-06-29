# No Women No Tech · Bordeaux

**Live →** [nowomannotech.fr](https://womanintech-spec.github.io/nwnt-bordeaux/) *(custom domain en cours)*

Une communauté de femmes dans la tech à Bordeaux — 225+ membres, 40+ événements, 4 ans d'existence. Structurée en association loi 1901 en mars 2026.

---

## Ce que c'est

Landing page vitrine de l'association NWNT Bordeaux. Une seule page HTML/CSS, zéro dépendance, zéro framework. Rapide, maintenable, deployée automatiquement via GitHub Actions sur GitHub Pages.

Les témoignages des membres sont chargés en live depuis Airtable — avec fallback sur des placeholders si la clé n'est pas renseignée.

---

## Stack

| Quoi | Pourquoi |
|---|---|
| HTML/CSS statique | Maintenable par n'importe qui, sans installation |
| Google Fonts (Unbounded + Space Grotesk) | Identité visuelle forte, chargement CDN |
| Airtable REST API | Témoignages gérés par l'équipe sans toucher au code |
| GitHub Actions | Deploy automatique à chaque push sur `main` |
| GitHub Pages | Hébergement gratuit, HTTPS inclus |

---

## Structure du repo

```
/                              ← racine du repo (home bTeslar)
├── README.md                  ← ce fichier
├── .github/
│   └── workflows/
│       └── deploy-nwnt.yml    ← pipeline GitHub Pages
└── Downloads/
    └── NWNT/
        ├── index.html         ← toute la landing page
        └── NWNT Bordeaux — Deck Membres & Partenaires 2026_files/
            ├── *.jpg          ← photos du bureau et des événements
            └── nwnt-logo-*.png
```

> La racine du repo est le home directory — le workflow GitHub Actions pointe explicitement sur `Downloads/NWNT/` comme source Pages.

---

## Modifier le contenu

Tout est dans `index.html`. Les sections sont commentées :

| Balise | Contenu |
|---|---|
| `#hero` | Accroche, chips, stats badge |
| `#timeline` | Les 4 ans d'impact + KPIs |
| `#events` | Formats d'événements |
| `#partners` | Partenaires (French Tech Bdx, Le Wagon, etc.) |
| `#event` | Summer Party — date, liens, lieu |
| `#testimonials` | Chargés depuis Airtable (ou placeholders) |
| `#board` | Bureau : photos, rôles, bios |
| `#join` | Tarifs cotisation + CTA HelloAsso |
| `#press` | Presse & médias |

---

## Airtable — témoignages en live

Deux variables à renseigner en haut de `index.html` :

```js
const AIRTABLE_API_KEY = 'patXXXXXXXXXXXXXX';
const AIRTABLE_BASE_ID = 'appXXXXXXXXXXXXXX';
```

**Générer un token** → airtable.com/create/tokens · scope requis : `data.records:read`

**Trouver le Base ID** → URL de la base Airtable : `airtable.com/appXXXXXXXXXXXXXX/...`

Structure attendue de la table `Témoignages` :

| Champ | Type |
|---|---|
| `Prénom` | Single line text |
| `Rôle` | Single line text |
| `Entreprise` | Single line text |
| `Texte` | Long text |
| `Afficher` | Checkbox — cocher = publié immédiatement |
| `Photo` | Attachment (optionnel) |

Si les variables sont vides ou si la table ne contient aucun enregistrement visible, des placeholders s'affichent automatiquement.

---

## Déployer

```bash
# Modifier index.html puis :
git add Downloads/NWNT/index.html
git commit -m "update"
git push
```

GitHub Actions redéploie en ~2 minutes. Pas de build, pas de node_modules, pas de pipeline complexe.

---

## Domaine custom

Les domaines `nowomannotech.fr` / `.org` / `.com` sont enregistrés séparément.

Pour brancher un domaine sur GitHub Pages :
1. **GitHub** → Settings → Pages → Custom domain → `nowomannotech.fr`
2. **Registrar** → Ajouter les enregistrements A de GitHub + CNAME `www`

```
A  @  185.199.108.153
A  @  185.199.109.153
A  @  185.199.110.153
A  @  185.199.111.153
CNAME  www  womanintech-spec.github.io
```

---

## Contacts

| Rôle | Nom |
|---|---|
| Co-présidente | Vanessa Portois Wermter |
| Co-présidente | Caroline Ramade |
| Trésorière | Sarah Jarsallé |
| Secrétaire générale · Ops | Elise Rabiot |
| Secrétaire adjointe · Plaidoyer & tech | Barbara Teslar |
| Secrétaire adjointe · Members | Ségolène Chauvet |
| Email | nowomennotech@gmail.com |
| HelloAsso | [Adhésion 2026](https://www.helloasso.com/associations/no-women-no-tech/adhesions/adhesion-nwnt-2026) |
