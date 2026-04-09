---
title: "Product Brief Distillate : Une info, pas si simple !"
type: llm-distillate
source: "product-brief-Atelier-IA.md"
created: "2026-04-09"
purpose: "Contexte token-efficient pour création de PRD ou implémentation directe"
---

# Distillate — Une info, pas si simple !

## Identité du projet

- Nom du site : "Une info, pas si simple !" (le nom exact est important, c'est l'accroche centrale)
- Type : SPA (Single Page Application) HTML/JS vanilla — aucun framework JS
- Hébergement cible : GitHub Pages (déploiement trivial, zéro backend)
- Public : projet perso à montrer à des collègues ; valeur portfolio secondaire
- Ambiance générale : fun, décalé, légèrement absurde — pas un projet sérieux, c'est voulu

---

## APIs retenues (toutes sans authentification)

| API | URL de base | Ce qu'elle fournit | Notes |
|-----|------------|-------------------|-------|
| Open-Meteo | `https://api.open-meteo.com/v1/forecast` | Météo (temp, conditions) | Géoloc ou coords fixes |
| WorldTimeAPI | `https://worldtimeapi.org/api/timezone` | Heure actuelle par timezone | Aucune clé |
| JokeAPI | `https://v2.jokeapi.dev/joke/Any` | Blague aléatoire FR/EN | Filtres de catégorie disponibles |
| Advice Slip | `https://api.adviceslip.com/advice` | Conseil aléatoire | Réponse JSON simple |
| Cat Facts | `https://catfact.ninja/fact` | Fait aléatoire sur les chats | Aucune clé |
| Open Trivia DB | `https://opentdb.com/api.php?amount=1` | Question de culture générale | Encode HTML à décoder |
| Frankfurter | `https://api.frankfurter.app/latest` | Taux de change EUR/USD etc. | Aucune clé |

**Règle critique :** NASA APOD est explicitement exclue — nécessite une clé API, même gratuite. Ne pas re-proposer.

**Comportement si API indisponible :** dégradation silencieuse — le bloc est ignoré, les autres s'affichent normalement. Pas de message d'erreur visible pour l'utilisateur.

---

## Flow utilisateur complet (UX précis)

```
[Page d'accueil]
  └─ Bouton central "Obtenir des infos"
       └─ [Écran sélection difficulté]
            ├─ Facile
            ├─ Moyen
            └─ Difficile
                 └─ [Mini-jeu démarre]
                      ├─ VICTOIRE
                      │    └─ [Écran victoire]
                      │         ├─ "Un autre niveau ?" → retour à sélection difficulté
                      │         └─ "Accéder aux informations ?" → [Dashboard] (si ≥1 niveau validé)
                      └─ GAME OVER
                           ├─ "Réessayer" → relance le même niveau
                           └─ "Retour à l'accueil" → [Page d'accueil]
```

**Gate d'accès :** L'option "Accéder aux informations" n'est disponible qu'après avoir validé au moins 1 niveau. Condition resetée à chaque visite (pas de localStorage, pas de cookie).

---

## Mini-jeu — Spécifications

- **Genre :** Obstacle runner scrolling latéral, style Geometry Dash
- **Mécanique core :** personnage qui avance automatiquement, saut déclenché par clic/espace pour éviter les obstacles
- **Niveaux :** 3 niveaux de difficulté (Facile / Moyen / Difficile) — vitesse et densité d'obstacles croissantes
- **Calibration Facile :** doit être franchissable par un non-joueur en < 30 secondes — critère clé pour les démos live
- **Technologie :** Canvas HTML5 vanilla — pas de librairie game engine (Phaser.js non requis)
- **Références open source disponibles sur GitHub :**
  - `Pixelikas/Geometry-Dash-Clone` — HTML/CSS/JS pur
  - `willmil11/GeometryDash` — HTML vanilla
  - `jonalma/geometry-dash-remake` — éducatif
  - CodePen : `codepen.io/exitandjump/pen/YQwOJe`

---

## Esthétique — Style "Grotesque Canvas"

- **Approche :** formes géométriques dessinées en Canvas, sans sprites externes ni assets image
- **Contours :** traits noirs épais (stroke) sur toutes les formes
- **Palette :** couleurs saturées légèrement "fausses" — vert acide, rose flashy, jaune cassé, fond sombre
- **Personnage :** carré avec "yeux" animés (deux cercles qui bougent)
- **Obstacles :** formes irrégulières via courbes de Bézier pour l'aspect grotesque
- **Objectif esthétique :** cartoon/absurde sans nécessiter de ressources graphiques dessinées à la main
- L'esthétique grotesque/cartoon doit idéalement s'étendre au dashboard (icônes fun, cohérence visuelle)

---

## Contraintes techniques

- **Aucun backend** — tout doit fonctionner en fichiers statiques servis par GitHub Pages
- **Aucun framework JS** — vanilla uniquement (HTML + CSS + JS)
- **Aucune dépendance npm** — pas de build step, pas de bundler
- **APIs appelées côté client** (fetch depuis le navigateur) — attention aux éventuels problèmes CORS (toutes les APIs listées le supportent)
- **Déploiement :** push sur branche `main` ou `gh-pages` + activation GitHub Pages dans les settings du repo

---

## Idées capturées hors périmètre v1 (pour versions futures)

- Bouton "Défie tes collègues" — partage du lien GitHub Pages après victoire
- Personnage réagissant visuellement aux données météo (sourire si beau temps, etc.)
- Éditeur de niveaux personnalisés
- Générateur de dashboards gamifiés (choix des APIs par l'utilisateur)
- Plateforme communautaire de niveaux
- README soigné sur GitHub comme pièce de portfolio à part entière

---

## Idées rejetées et pourquoi

| Idée | Raison du rejet |
|------|----------------|
| NASA APOD API | Nécessite une clé API (même gratuite) — complexifie inutilement |
| Persistance localStorage | Hors périmètre v1 — reset à chaque visite voulu |
| Compatibilité mobile/tactile | Hors périmètre v1 — démo sur ordinateur suffisante |
| Framework JS (React, Vue...) | Complexité inutile pour un SPA simple sur GitHub Pages |
| Mise en ligne complexe | GitHub Pages choisi précisément pour sa simplicité |

---

## Risques identifiés

- **Calibration du niveau Facile** : si trop difficile pour des non-joueurs, l'effet de démo tombe à plat — à tester en priorité
- **Latence des APIs** : prévoir un état de chargement visible (spinner ou animation) pour éviter l'effet "dashboard cassé" lors des démos
- **CORS** : vérifier que chaque API accepte les requêtes depuis un domaine GitHub Pages (`*.github.io`)
