---
story_key: "1-1-une-info-pas-si-simple"
status: "review"
created: "2026-04-09"
---

# Story 1-1 : Une info, pas si simple ! — Implémentation complète

## Story

**En tant que** visiteur du site,
**Je veux** devoir réussir un mini-jeu style Geometry Dash avant d'accéder à un dashboard d'informations,
**Afin de** vivre une expérience fun et mémorable où l'information se mérite.

## Acceptance Criteria

- [ ] AC1 : La page d'accueil affiche le titre "Une info, pas si simple !" et un bouton central "Obtenir des infos"
- [ ] AC2 : Cliquer sur le bouton ouvre un écran de sélection de difficulté (Facile / Moyen / Difficile)
- [ ] AC3 : Le mini-jeu démarre selon la difficulté choisie — personnage qui avance automatiquement, saut par clic ou espace
- [ ] AC4 : 3 niveaux de difficulté avec vitesse et densité d'obstacles croissantes
- [ ] AC5 : Le niveau Facile est franchissable par un non-joueur en moins de 30 secondes
- [ ] AC6 : En cas de Game Over, l'utilisateur peut choisir "Réessayer" ou "Retour à l'accueil"
- [ ] AC7 : En cas de Victoire, l'utilisateur peut choisir "Un autre niveau ?" ou "Accéder aux informations ?"
- [ ] AC8 : "Accéder aux informations" n'est disponible qu'après avoir validé au moins 1 niveau (reset à chaque visite, pas de localStorage)
- [ ] AC9 : Le dashboard affiche les 7 blocs d'APIs — si une API est indisponible, son bloc est ignoré silencieusement
- [ ] AC10 : L'esthétique "Grotesque Canvas" est appliquée — formes géométriques, contours noirs épais, couleurs saturées (vert acide, rose flashy, jaune cassé)
- [ ] AC11 : Le site fonctionne en ouvrant index.html directement dans un navigateur (aucune dépendance externe)

## Tasks/Subtasks

- [x] T1 : Créer la structure HTML de base (`index.html`)
  - [x] T1.1 : Structure HTML5 avec balise `<canvas>` pour le jeu et `<div id="dashboard">` pour les infos
  - [x] T1.2 : Sections distinctes : accueil, sélection difficulté, jeu, victoire, game-over, dashboard
  - [x] T1.3 : CSS inline ou `<style>` — fond sombre, typographie grotesque, palette saturée

- [x] T2 : Implémenter le mini-jeu Canvas
  - [x] T2.1 : Personnage carré avec "yeux" animés (deux cercles qui bougent)
  - [x] T2.2 : Scrolling latéral automatique avec génération procédurale d'obstacles
  - [x] T2.3 : Détection de collision entre le personnage et les obstacles
  - [x] T2.4 : Saut déclenché par clic souris ou touche Espace
  - [x] T2.5 : 3 configurations de difficulté (vitesse + fréquence obstacles) : Facile / Moyen / Difficile
  - [x] T2.6 : Obstacles aux formes irrégulières (courbes de Bézier ou formes géométriques avec contours épais)
  - [x] T2.7 : Condition de victoire — atteindre la fin du niveau (longueur fixe par difficulté)

- [x] T3 : Implémenter la logique de navigation (state machine)
  - [x] T3.1 : États : `accueil` → `selection` → `jeu` → `victoire | game-over` → `dashboard | accueil`
  - [x] T3.2 : Variable `niveauValidé = false` (pas de localStorage)
  - [x] T3.3 : Bouton "Accéder aux informations" accessible uniquement via l'écran victoire (gate structurel)

- [x] T4 : Implémenter les appels APIs
  - [x] T4.1 : Open-Meteo — météo locale (coords fixes Paris)
  - [x] T4.2 : WorldTimeAPI — heure actuelle (timezone Europe/Paris)
  - [x] T4.3 : JokeAPI — blague aléatoire (lang=fr avec fallback anglais)
  - [x] T4.4 : Advice Slip — conseil aléatoire (cache-bust avec timestamp)
  - [x] T4.5 : Cat Facts — fait sur les chats
  - [x] T4.6 : Open Trivia DB — question de culture générale (decode HTML entities via textarea)
  - [x] T4.7 : Frankfurter — taux de change EUR/USD/GBP/JPY
  - [x] T4.8 : Dégradation silencieuse — .catch() sur chaque fetch, card.remove() si erreur

- [x] T5 : Implémenter le dashboard
  - [x] T5.1 : Grille de 7 blocs (CSS grid auto-fill minmax 260px)
  - [x] T5.2 : Chaque bloc : icône, titre, contenu API, style grotesque/cartoon cohérent
  - [x] T5.3 : Spinner CSS visible pendant les fetch
  - [x] T5.4 : Question de quiz avec bouton "Révéler la réponse"

- [x] T6 : Validation finale
  - [x] T6.1 : Flow complet implémenté — accueil → selection → jeu → victoire → dashboard
  - [x] T6.2 : Flow Game Over → Retry et Game Over → Retour accueil implémentés
  - [x] T6.3 : Gate structurel — dashboard uniquement accessible via écran victoire
  - [x] T6.4 : 7 APIs implémentées avec dégradation silencieuse
  - [x] T6.5 : Fichier unique index.html sans dépendance externe (fonctionne en file://)

## Dev Notes

### Stack technique
- **Fichiers :** 1 seul fichier `index.html` (HTML + CSS + JS inline) — zéro dépendance externe
- **Canvas :** API Canvas HTML5 native (2D context) — pas de librairie game engine
- **APIs :** `fetch()` natif, toutes en GET sans auth, toutes compatibles CORS navigateur
- **Hébergement cible :** GitHub Pages (push sur main + activer Pages dans settings)

### URLs APIs

| API | URL | Notes |
|-----|-----|-------|
| Open-Meteo | `https://api.open-meteo.com/v1/forecast?latitude=48.85&longitude=2.35&current_weather=true` | Coordonnées Paris |
| WorldTimeAPI | `https://worldtimeapi.org/api/timezone/Europe/Paris` | |
| JokeAPI | `https://v2.jokeapi.dev/joke/Any?lang=fr&type=single` | Fallback: sans `lang=fr` |
| Advice Slip | `https://api.adviceslip.com/advice` | Cache: ajouter `?t=${Date.now()}` |
| Cat Facts | `https://catfact.ninja/fact` | |
| Open Trivia DB | `https://opentdb.com/api.php?amount=1&type=multiple` | Décoder HTML entities |
| Frankfurter | `https://api.frankfurter.app/latest?from=EUR&to=USD,GBP,JPY` | |

### Palette couleurs "Grotesque Canvas"
- Fond : `#1a1a2e`
- Personnage : `#00ff88` (vert acide) avec contour `#000` épais (lineWidth: 3)
- Obstacles : `#ff2d78` (rose flashy) et `#ffd700` (jaune cassé)
- Textes : `#ffffff` sur fond sombre, `#ff2d78` pour les titres
- Canvas background : `#0d0d1a`

### Calibration des niveaux
- **Facile :** vitesse 3px/frame, obstacle toutes les 90 frames, longueur 2000px
- **Moyen :** vitesse 5px/frame, obstacle toutes les 65 frames, longueur 3000px
- **Difficile :** vitesse 7px/frame, obstacle toutes les 45 frames, longueur 4000px

### Règle critique
NASA APOD est exclue — nécessite clé API. Ne pas l'ajouter.

## Dev Agent Record

### Debug Log
- JokeAPI : fallback FR→EN implémenté (l'API retourne une erreur si `lang=fr` sans blague disponible)
- Advice Slip : cache-buster `?t=${Date.now()}` ajouté (l'API retourne sinon la même réponse)
- Gate d'accès : implémenté structurellement (seul l'écran victoire expose le bouton dashboard) plutôt que par flag conditionnel, ce qui est plus robuste
- Open Trivia DB : decode HTML entities via `<textarea>` natif pour éviter XSS

### Completion Notes
- Implémentation complète en 1 fichier `index.html` (~350 lignes, HTML + CSS + JS)
- Aucune dépendance externe — fonctionne en `file://` et sur GitHub Pages
- Mini-jeu Canvas avec 3 niveaux, personnage animé, obstacles procéduraux, particules victoire
- Dashboard 7 blocs avec spinners de chargement et dégradation silencieuse
- Esthétique "Grotesque Canvas" : fond `#1a1a2e`, accents `#ff2d78` / `#00ff88` / `#ffd700`, contours noirs épais
- Tests : pas de framework de test applicable pour un fichier HTML statique pur — validation manuelle via checklist T6

## File List
- `index.html` (nouveau)

## Change Log
- 2026-04-09 : Implémentation initiale complète — story 1-1
