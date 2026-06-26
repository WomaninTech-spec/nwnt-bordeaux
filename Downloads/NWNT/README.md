# No Women No Tech · Bordeaux

Landing page de l'association NWNT Bordeaux.

## Stack

HTML/CSS statique — une seule page, zéro dépendance, zéro framework.  
Les témoignages sont chargés en live depuis Airtable.

## Structure

```
NWNT/
├── index.html                          # La page entière
└── NWNT Bordeaux — Deck […]_files/    # Images et logos
```

## Airtable (témoignages)

Renseigner les deux variables en haut de `index.html` :

```js
const AIRTABLE_API_KEY = 'patXXXXXXXXXXXXXX';
const AIRTABLE_BASE_ID = 'appXXXXXXXXXXXXXX';
```

Table attendue : **Témoignages**  
Champs : `Prénom` · `Rôle` · `Entreprise` · `Texte` · `Afficher` (checkbox) · `Photo` (optionnel)

Cocher `Afficher` suffit pour publier un témoignage.

## Mise à jour du contenu

Tout est dans `index.html`, organisé en sections commentées :

| Section | Ce qu'on y modifie |
|---|---|
| `#partners` | Ajouter / éditer les partenaires |
| `#testimonials` | Clé Airtable |
| `#event` | Date et liens Summer Party |
| `#join` | Tarifs cotisation |
| `#board` | Membres du bureau |

## Déploiement

Connecté à Netlify via ce repo.  
Chaque push sur `main` redéploie automatiquement.

```bash
git add Downloads/NWNT/index.html
git commit -m "update"
git push
```
