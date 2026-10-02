# Grille de roast e2-1

**Nom :** Albion
**Date :** 25.09.2026

**Barème :** 1 = cassé · 3 = moyen · 5 = ça va (ces pages n'auront jamais 5 partout).

| Capture | Lisibilité | Navigation | Feedback | Cohérence | Accessibilité | Phrase précise |
|---|:-:|:-:|:-:|:-:|:-:|---|
| 01 mur de texte | 1 | 2 | 2 | 2 | 1 | Tout le texte, titres compris, est en 11px gris `#888` sur blanc (contraste 3.5:1, sous le minimum AA de 4.5:1) et affiché inline : aucune hiérarchie, impossible de repérer le titre de l'article. |
| 02 labyrinthe | 3 | 1 | 1 | 2 | 2 | L'action principale n'a pas de bouton : la page décrit en texte un chemin de 6 niveaux (Menu › Espace › Plus › Options › Avancé › Liste) et les 3 liens mènent tous vers `#`. |
| 03 silence | 2 | 3 | 1 | 3 | 1 | Le bouton « ok » est gris `#ddd` sur fond `#ddd` (contraste 1:1, invisible) et son clic ne fait rien : ni confirmation, ni message d'erreur, ni chargement. Les champs n'ont pas de label. |
| 04 carnaval | 1 | 2 | 2 | 1 | 1 | Promo et prix normal ne se distinguent que par rouge vs vert (illisible pour un daltonien), sur un texte vert `#0f0` sur jaune `#ff0` (contraste 1.3:1) et 5 polices différentes. |

## La pire, pour la présentation

Capture n° **03 silence** parce que c'est la seule où l'utilisateur ne peut **pas du tout** accomplir sa tâche : le bouton est invisible (contraste 1:1), le clic ne renvoie aucun feedback, les champs n'ont pas de label, et la mention « en cliquant vous acceptez tout » en `#ccc` 11px lui fait accepter des conditions qu'il ne peut même pas lire. Les autres pages sont laides ou pénibles, celle ci est bloquante et trompeuse.
