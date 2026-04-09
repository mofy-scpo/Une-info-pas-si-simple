---
title: "Product Brief : Une info, pas si simple !"
status: "complete"
created: "2026-04-09"
updated: "2026-04-09"
inputs: ["conversation utilisateur", "recherche web APIs gratuites sans auth", "recherche web clones Geometry Dash HTML/JS"]
---

# Product Brief : Une info, pas si simple !

## Résumé exécutif

"Une info, pas si simple !" est un site web ludique à page unique qui renverse le modèle traditionnel du tableau de bord d'informations : pour accéder à la météo, à l'heure, à la blague du jour ou au taux de change, il faut d'abord **mériter ses données** en survivant à un mini-jeu inspiré de Geometry Dash.

Le concept est immédiatement compréhensible : un bouton central invite l'utilisateur à "accéder aux infos". Ce clic déclenche un niveau de jeu — un obstacle runner en scrolling latéral à l'esthétique grotesque et cartoon — que l'utilisateur doit valider pour déverrouiller le tableau de bord. Trois niveaux de difficulté sont proposés (Facile / Moyen / Difficile) ; **un seul suffit pour débloquer l'accès**. À la victoire, deux choix : "Un autre niveau ?" ou "Accéder aux informations ?"

Projet personnel à fort potentiel de démo, "Une info, pas si simple !" est conçu pour impressionner des collègues tout en étant déployable en quelques minutes sur GitHub Pages — sans backend, sans configuration, sans contrainte.

---

## Le problème (ou plutôt : le prétexte)

Les tableaux de bord d'informations, c'est partout. Météo, heure, actualités — tout est accessible d'un clic, sans friction, sans effort, sans fun. Le résultat ? Des sites que personne ne montre avec enthousiasme, et que personne ne mémorise.

"Une info, pas si simple !" pose une question provocatrice : **et si accéder à une information basique devenait une micro-aventure ?** L'information perd de sa valeur quand elle est gratuite. Elle devient précieuse — et mémorable — quand on l'a gagnée.

---

## La solution

Un site HTML/JS pur, déployé sur GitHub Pages, structuré autour d'une boucle de gameplay :

1. **Page d'accueil** — Titre percutant + bouton central unique : "Obtenir des infos"
2. **Sélection du niveau** — L'utilisateur choisit sa difficulté : Facile, Moyen ou Difficile
3. **Mini-jeu** — Obstacle runner en scrolling latéral, style Geometry Dash, esthétique "Grotesque Canvas" : formes géométriques aux contours noirs épais, couleurs saturées (vert acide, rose flashy, jaune cassé), personnage carré avec yeux animés, obstacles aux formes irrégulières — le tout en Canvas HTML5, sans sprites externes
4. **Game Over** — L'utilisateur choisit : "Réessayer" ou "Retour à l'accueil"
5. **Gate d'accès** — 1 niveau validé minimum requis pour accéder au dashboard (condition réinitialisée à chaque visite)
6. **Écran de victoire** — Deux choix clairs : "Un autre niveau ?" ou "Accéder aux informations ?"
7. **Tableau de bord** — 7 blocs d'informations récupérées en temps réel via APIs publiques sans authentification. Si une API est indisponible, son bloc est silencieusement ignoré et les autres s'affichent normalement.

| Bloc | API | Contenu affiché |
|------|-----|-----------------|
| Météo | Open-Meteo | Température et conditions locales |
| Heure | WorldTimeAPI | Heure actuelle (timezone configurable) |
| Blague du jour | JokeAPI | Blague aléatoire (FR/EN) |
| Conseil du jour | Advice Slip | Conseil aléatoire |
| Fait sur les chats | Cat Facts | Anecdote féline |
| Culture générale | Open Trivia DB | Question quiz + réponse révélable |
| Taux de change | Frankfurter | Taux EUR/USD et quelques autres |

Toutes les APIs sont **gratuites, sans authentification**, sans limite bloquante pour un usage personnel.

---

## Ce qui rend ce projet différent

- **Le gate de jeu** : conditionner l'accès à l'information à la réussite d'un niveau est un mécanisme UX rare, immédiatement mémorable et socialement partageable
- **Zéro dépendance backend** : HTML/JS pur, APIs publiques, hébergement GitHub Pages — rien à configurer, rien à maintenir, démontrable depuis n'importe quel ordinateur
- **L'esthétique décalée** : le style grotesque/cartoon crée un contraste drôle avec la sobriété habituelle des dashboards et renforce l'identité du projet
- **La tension narrative** : même sur un niveau Facile, la mécanique crée un instant de suspense et de satisfaction qu'aucun dashboard statique ne peut offrir

---

## À qui ça s'adresse

**Utilisateur principal : le créateur et ses collègues**
Développeur ou passionné tech souhaitant démontrer un projet fun, créatif et techniquement solide. Les collègues — même non-techniques — sont immédiatement captés par le jeu avant de s'amuser des informations révélées.

**Utilisateur secondaire : visiteur de portfolio GitHub**
Tout développeur ou recruteur découvrant le projet cherche quelque chose d'original — "Une info, pas si simple !" remplit ce rôle comme carte de visite créative et mémorable.

---

## Critères de succès

Pour ce projet personnel, le succès se mesure simplement :

- Le jeu est jouable et fonctionnel sur les 3 niveaux de difficulté
- L'accès au tableau de bord est bien conditionné à la victoire du gate
- Les APIs répondent sans erreur ; les blocs indisponibles sont ignorés proprement
- Le déploiement GitHub Pages fonctionne en moins de 10 minutes
- **Indicateur humain clé** : la réaction des collègues — "C'est quoi ce truc ?" suivi d'un sourire = mission accomplie

---

## Périmètre v1

### Dans le périmètre
- SPA (Single Page Application) en HTML/JS vanilla — aucun framework
- Mini-jeu Geometry Dash-like avec sélection de difficulté (Facile / Moyen / Difficile)
- Esthétique "Grotesque Canvas" — formes géométriques, contours épais, couleurs saturées
- Écran Game Over avec choix : Retry ou Retour à l'accueil
- Tableau de bord avec 7 blocs d'informations via APIs sans auth
- Dégradation silencieuse si une API est indisponible
- Condition d'accès : 1 niveau validé minimum, reset à chaque visite
- Hébergement et déploiement GitHub Pages

### Hors périmètre v1
- Authentification utilisateur ou persistance de progression entre sessions
- Éditeur de niveaux personnalisés
- Toute API nécessitant une clé ou une inscription (ex : NASA APOD)
- Compatibilité tactile / mobile optimisée
- Mode multijoueur ou classement en ligne

---

## Vision à terme

Si le concept séduit au-delà du cercle des collègues, "Une info, pas si simple !" pourrait évoluer vers :
- Un générateur de dashboards gamifiés personnalisables (choix des APIs, design des niveaux)
- Une plateforme communautaire où des créateurs soumettent leurs propres niveaux
- Un format réplicable : le "gate de jeu" appliqué à d'autres contextes — CV interactif, landing page, portfolio

Mais pour l'instant : **faire sourire**. C'est largement suffisant.
