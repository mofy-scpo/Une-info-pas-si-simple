---
stepsCompleted: ['step-01-init', 'step-02-discovery', 'step-02b-vision', 'step-02c-executive-summary', 'step-03-success', 'step-04-journeys', 'step-12-complete']
inputDocuments:
  - '_bmad-output/planning-artifacts/product-brief-Atelier-IA.md'
  - '_bmad-output/planning-artifacts/product-brief-Atelier-IA-distillate.md'
workflowType: 'prd'
briefCount: 2
researchCount: 0
brainstormingCount: 0
projectDocsCount: 0
classification:
  projectType: web_app
  domain: general
  complexity: low
  projectContext: greenfield
  notes: "Divertissement interactif personnel — success metrics humaines, persona collègue non-technicien prioritaire"
---

# Product Requirements Document - Atelier-IA

**Author:** Itadmin
**Date:** 2026-04-09

## Résumé Exécutif

"Une info, pas si simple !" est un projet web de démonstration conçu pour illustrer le workflow BMAD de bout en bout — de l'idée brute jusqu'au déploiement. Le sujet du projet (un site ludique où l'utilisateur doit réussir un mini-jeu style Geometry Dash avant d'accéder à un dashboard d'informations via APIs gratuites) est délibérément fun et léger, afin que l'attention reste focalisée sur la qualité du processus BMAD plutôt que sur la valeur commerciale du produit lui-même.

Cible principale : développeur ou passionné tech souhaitant montrer BMAD en action à des collègues, via une démo concrète et mémorable. Cible secondaire : visiteurs de portfolio GitHub cherchant un exemple de projet complet produit avec BMAD.

### Ce qui rend ce projet spécial

Le vrai différenciateur n'est pas le site en lui-même, mais ce qu'il représente : **un artefact complet du pipeline BMAD** — brief → PRD → epics → stories → implémentation → déploiement. Le projet fun et accessible (mini-jeu + APIs gratuites + GitHub Pages) est un terrain idéal pour démontrer BMAD sans la complexité d'un domaine métier sérieux. Le "gate de jeu" (obligation de valider un niveau avant d'accéder aux infos) est le mécanisme UX central — immédiatement compréhensible, surprenant, mémorable.

## Classification du Projet

- **Type :** Web App (SPA vanilla HTML/JS)
- **Domaine :** General — divertissement interactif / démo de workflow
- **Complexité :** Low
- **Contexte :** Greenfield
- **Hébergement :** GitHub Pages (zéro backend, déploiement trivial)

## Critères de Succès

### Succès Utilisateur

- L'utilisateur (collègue, visiteur portfolio) comprend immédiatement la mécanique : jouer pour accéder aux infos
- Le niveau Facile est franchissable par un non-joueur en < 30 secondes — aucun blocage lors d'une démo live
- Le dashboard affiche au minimum 6 blocs sur 7 (dégradation silencieuse si une API est indisponible)
- La réaction attendue : "C'est quoi ce truc ?" suivi d'un sourire — indicateur humain principal

### Succès Démo BMAD

- Le projet a traversé l'intégralité du pipeline BMAD dans l'ordre :
  1. `/bmad-product-brief` ✓
  2. `/bmad-create-prd` (en cours)
  3. `/bmad-create-architecture`
  4. `/bmad-create-epics-and-stories`
  5. `/bmad-dev-story`
- Chaque artefact produit (brief, PRD, architecture, epics/stories) est lisible et illustre la qualité du workflow BMAD
- Le site final est déployé sur GitHub Pages — démo locale acceptable en fallback

### Succès Technique

- SPA vanilla HTML/JS fonctionnelle, sans framework, sans dépendance npm
- Les 7 APIs gratuites sans auth répondent correctement depuis le navigateur
- Déploiement GitHub Pages réalisable en moins de 10 minutes
- Qualité de code : libre — priorité à la lisibilité pour une démo

### Résultats Mesurables

| Critère | Cible | Priorité |
|---------|-------|----------|
| Pipeline BMAD complet | 5 skills exécutés | Critique |
| Niveaux jouables | 3 (Easy/Medium/Hard) | Critique |
| APIs fonctionnelles | ≥ 6 sur 7 | Critique |
| Déploiement GitHub Pages | Réalisé | Souhaité |
| Démo locale fonctionnelle | Réalisée | Fallback |

## Périmètre Produit

### MVP — Produit Minimum Viable

- Page d'accueil avec bouton central
- Sélection de difficulté (Facile / Moyen / Difficile)
- Mini-jeu Canvas style Geometry Dash — 3 niveaux, difficulté croissante
- Écran Game Over : Réessayer / Retour à l'accueil
- Gate d'accès : 1 niveau validé minimum, reset à chaque visite
- Écran Victoire : Un autre niveau ? / Accéder aux informations ?
- Dashboard 7 blocs via APIs sans auth (Open-Meteo, WorldTimeAPI, JokeAPI, Advice Slip, Cat Facts, Open Trivia DB, Frankfurter)
- Dégradation silencieuse si API indisponible
- Esthétique "Grotesque Canvas" — formes géométriques, contours épais, couleurs saturées

### Features Post-MVP

Aucune — périmètre fermé. Ce projet est un artefact de démo BMAD, pas un produit évolutif.

### Vision

Servir de référence concrète et publique illustrant ce que le workflow BMAD produit sur un projet complet greenfield.

## Parcours Utilisateurs

### Parcours 1 — Itadmin fait la démo (chemin principal)

Itadmin ouvre son ordinateur devant ses collègues. Il navigue sur le site déployé sur GitHub Pages — ou lance `index.html` en local en fallback. La page d'accueil s'affiche : titre décalé, bouton central "Obtenir des infos". Il clique. L'écran de sélection de difficulté apparaît — il choisit **Facile** pour ne pas perdre la salle.

Le mini-jeu démarre. Son personnage carré aux yeux animés avance automatiquement. Il saute au bon moment pour éviter les obstacles grotesques. 20 secondes plus tard : victoire. L'écran lui propose "Un autre niveau ?" ou "Accéder aux informations ?". Il choisit **Accéder aux informations** — le dashboard s'affiche avec 7 blocs : météo, heure, blague du jour, conseil, fait sur les chats, question de quiz, taux de change.

Ses collègues sourient. "C'est quoi ce truc ?" — mission accomplie.

*Capacités révélées : page d'accueil, sélection de difficulté, mini-jeu Canvas, écran victoire, gate d'accès, dashboard multi-blocs.*

### Parcours 2 — Le collègue qui tente sa chance (edge case)

Un collègue veut essayer seul. Il choisit **Difficile** par défi. Le personnage avance vite, les obstacles s'enchaînent. Il échoue. Écran Game Over : **Réessayer** ou **Retour à l'accueil**. Il retente — échoue encore. Retour à l'accueil. Il recommence, choisit **Facile**, valide le niveau. Le dashboard est débloqué.

*Capacités révélées : écran Game Over, retry, retour accueil, gate conditionnel (reset à chaque visite), calibration critique du niveau Facile.*

### Parcours 3 — Visiteur portfolio GitHub (secondaire)

Un développeur tombe sur le repo GitHub. Il lit le README, voit les artefacts BMAD (brief, PRD, architecture, epics). Il comprend que c'est une démo de workflow autant qu'un site. Il clique sur le lien GitHub Pages, joue un niveau, voit le dashboard. Il repart avec une idée claire de ce que BMAD peut produire.

*Capacités révélées : déploiement GitHub Pages, artefacts BMAD lisibles dans le repo.*

### Résumé des Capacités Révélées

| Capacité | Parcours |
|----------|----------|
| Page d'accueil + bouton central | 1, 2, 3 |
| Sélection de difficulté | 1, 2 |
| Mini-jeu Canvas (3 niveaux) | 1, 2 |
| Écran Game Over + Retry / Retour accueil | 2 |
| Gate d'accès conditionnel (≥1 victoire, reset/visite) | 1, 2 |
| Écran Victoire + choix | 1, 2 |
| Dashboard 7 blocs APIs sans auth | 1, 2, 3 |
| Dégradation silencieuse si API indisponible | 1 |
| Déploiement GitHub Pages | 3 |

