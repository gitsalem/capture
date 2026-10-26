# Capture

Pose une capture d'écran de post (X, Threads, Bluesky…) sur un fond coloré et l'exporte en PNG, prête à partager.

**→ [gitsalem.github.io/capture](https://gitsalem.github.io/capture/)**

Tout se passe dans le navigateur : aucune image n'est envoyée nulle part. Après la première ouverture, l'outil marche aussi hors ligne.

## Utilisation

1. **Choisir une capture** dans tes photos.
2. Rogner le haut et le bas avec les curseurs **Haut** et **Bas**.
3. Choisir un **fond** parmi les vingt teintes inspirées de la gamme Apple (iPhone, iMac, MacBook Air, iPad Air).
4. **Enregistrer ou partager** ouvre la feuille de partage d'iOS. Sinon, fais un appui long sur l'aperçu pour l'enregistrer dans Photos.

Les réglages (rognage, fond) sont gardés d'une visite à l'autre. Le bouton statistiques, à côté du titre, affiche le nombre d'images traitées sur l'appareil.

### Sur iPhone

Dans Safari : bouton Partager → **Sur l'écran d'accueil**. L'outil s'ouvre alors en plein écran, comme une app.

## Rendu

- Marge de 24 pt autour de la capture, coins arrondis de 16 pt, ombre douce.
- Image au minimum carrée, jamais en paysage, capture centrée.
- Export à la résolution d'origine de la capture (@3x pour un iPhone récent).

## Fichiers

| Fichier | Rôle |
| --- | --- |
| `index.html` | L'outil complet : HTML, CSS et JavaScript, sans dépendance |
| `sw.js` | Service worker : réseau d'abord, cache en secours pour le hors ligne |
| `manifest.webmanifest`, `icon-*.png` | Installation sur l'écran d'accueil |

## Développement

Aucune compilation. Pour tester en local :

```bash
python3 -m http.server 8000
```

Puis ouvrir http://localhost:8000.

Le site est publié par GitHub Pages depuis la branche `main`.

**Après chaque modification de `index.html`**, augmenter la version du cache dans `sw.js` (`capture-v7` → `capture-v8`). Sinon, les appareils qui ont déjà installé l'app continuent d'afficher l'ancienne version.
