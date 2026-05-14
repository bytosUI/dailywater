# DailyWater

Petite app web pour suivre ton hydratation quotidienne (8 verres / 2L par jour),
pensée pour accompagner un jeûne intermittent.

## Structure

- `index.html` — page principale
- `manifest.json` — manifeste PWA (rend l'app installable)
- `service-worker.js` — cache hors-ligne
- `icon.svg` — icône de l'app

Les données sont stockées dans le `localStorage` du navigateur (rien n'est envoyé sur un serveur).

## Tester en local

Un service worker exige un vrai serveur (pas un `file://`). Depuis le dossier :

```sh
python3 -m http.server 8080
```

Puis ouvre `http://localhost:8080` dans Safari.

## Héberger en ligne (option recommandée : GitHub Pages)

1. Crée un repo GitHub (ex. `dailywater`) et pousse-y le contenu du dossier.
2. Dans le repo → **Settings → Pages**.
3. **Source** : `Deploy from branch`, branche `main`, dossier `/ (root)`.
4. Patiente ~1 min. GitHub te donne une URL du type `https://<ton-pseudo>.github.io/dailywater/`.

Autres options gratuites équivalentes : Netlify, Vercel, Cloudflare Pages (drag-and-drop du dossier).

## Installer sur l'iPhone

1. Ouvre l'URL dans **Safari** (pas Chrome — sur iOS seul Safari sait installer une PWA).
2. Bouton **Partager** (carré avec flèche vers le haut).
3. **Ajouter à l'écran d'accueil**.
4. Une icône goutte d'eau apparaît sur ton home screen, lancée en plein écran comme une vraie app.

L'app continue de fonctionner même sans connexion une fois ouverte une première fois.

## Mettre à jour

Après modification des fichiers, incrémente la version dans `service-worker.js` :

```js
const CACHE = 'dailywater-v2'; // v1 → v2
```

Sinon le navigateur servira l'ancienne version depuis le cache.
