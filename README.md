# Une info, pas si simple !

> Parce que savoir la météo, ça se mérite.

---

## C'est quoi ce truc ?

Un tableau de bord d'informations. Météo, heure, blague du jour, taux de change, fait sur les chats, conseil existentiel — tout ce dont vous n'avez absolument pas besoin mais que vous consulterez quand même.

Sauf que. **Vous devrez d'abord battre un niveau de jeu pour y accéder.**

Oui, vraiment. Non, vous ne rêvez pas. Oui, c'est volontaire.

---

## Pourquoi

Parce que les dashboards classiques, c'est partout, c'est accessible d'un clic, et personne ne s'en souvient 30 secondes après. L'information perd de sa valeur quand elle est gratuite. Elle devient précieuse — et mémorable — quand on l'a **gagnée**.

Ou alors c'était juste pour faire sourire des collègues. Les deux sont vrais.

---

## Comment ça marche

1. Vous arrivez sur la page. Un bouton vous dit "Obtenir des infos".
2. Vous cliquez. Vous choisissez votre niveau de souffrance : Facile, Moyen, Difficile.
3. Vous jouez à un obstacle runner style Geometry Dash, esthétique "cartoon grotesque" — carrés aux yeux animés, couleurs qui agressent la rétine, obstacles aux formes suspectes.
4. Si vous mourez : "Réessayer" ou "Retour à l'accueil". Votre choix.
5. Si vous survivez : félicitations, vous avez mérité de savoir qu'il fait 12°C dehors.

**Un seul niveau réussi suffit.** On ne veut pas votre mort, on veut juste votre attention.

---

## Ce que vous débloquez

| Ce que vous obtenez | D'où ça vient |
|---|---|
| Météo locale | Open-Meteo |
| Heure actuelle | WorldTimeAPI |
| Blague du jour | JokeAPI |
| Conseil inutile mais sincère | Advice Slip |
| Fait sur les chats | Cat Facts |
| Question de culture générale | Open Trivia DB |
| Taux EUR/USD | Frankfurter |

Toutes les APIs sont gratuites, sans clé, sans inscription. Si l'une d'elles est en rade, son bloc disparaît sans crier. Le reste continue comme si de rien n'était. La vie continue.

---

## Stack technique

- **HTML/JS vanilla.** Pas de framework. Pas de `npm install`. Pas de `node_modules` de 400 Mo.
- **Canvas HTML5** pour le jeu. Zéro sprite externe. Tout dessiné à la main, avec amour et mauvais goût.
- **GitHub Pages** pour le déploiement. Gratuit, immédiat, démontrable depuis n'importe quel ordinateur.

---

## Déploiement

```bash
# 1. Forkez ou clonez ce repo
# 2. Activez GitHub Pages sur la branche main
# 3. C'est tout
```

Aucun backend. Aucune configuration. Aucune raison de ne pas le faire.

---

## Ce qui n'est PAS dans ce projet (et ne le sera probablement jamais)

- Authentification utilisateur
- Persistance de progression entre sessions
- Mode mobile optimisé *(le carré souffre sur téléphone, c'est assumé)*
- Toute API nécessitant une clé, une inscription ou une carte bancaire
- Mode multijoueur
- NFT du personnage carré

---

## Vision à long terme

Faire sourire. C'est largement suffisant.

Si un jour ça dépasse le cercle des collègues : peut-être un générateur de dashboards gamifiés, peut-être une plateforme communautaire, peut-être un CV interactif où le recruteur doit battre un niveau pour voir vos coordonnées.

Mais soyons honnêtes : pour l'instant, c'est un projet personnel fait pour impressionner en réunion et obtenir un "c'est quoi ce truc ?" suivi d'un sourire. Mission accomplie.

---

## Licence

Faites-en ce que vous voulez. Si vous montrez ça à quelqu'un et qu'il sourit, c'est déjà une victoire.
