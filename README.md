# nwnt-bordeaux

Landing page for No Women No Tech Bordeaux — a community of women in tech, officially structured as an association in March 2026.

**Live:** https://womanintech-spec.github.io/nwnt-bordeaux/

---

## Stack

Single-file static HTML/CSS. No framework, no build step, no dependencies.  
Testimonials load live from Airtable via the REST API.

## Project structure

```
Downloads/NWNT/
├── index.html          # Entire page — edit this file
└── […]_files/         # Images and logos
.github/
└── workflows/
    └── deploy-nwnt.yml # GitHub Pages auto-deploy
```

## Airtable setup

Fill in the two variables at the top of `index.html`:

```js
const AIRTABLE_API_KEY = 'patXXXXXXXXXXXXXX'; // read-only token
const AIRTABLE_BASE_ID = 'appXXXXXXXXXXXXXX';
```

Expected table name: **Témoignages**  
Fields: `Prénom` · `Rôle` · `Entreprise` · `Texte` · `Afficher` (checkbox) · `Photo` (attachment, optional)

Checking `Afficher` on a record publishes it immediately.

## Updating content

Everything lives in `index.html` in clearly marked sections:

| Section | What to edit |
|---|---|
| `#partners` | Add or update partners |
| `#event` | Summer Party date and links |
| `#join` | Membership pricing |
| `#board` | Bureau members |

## Deploy

Pushes to `main` trigger an automatic GitHub Pages deploy (~2 min).

```bash
git add Downloads/NWNT/index.html
git commit -m "update"
git push
```
