# Tests utilisateurs & audit d'accessibilité — CuisineDuFrigo

> Atelier e2-7 · M291 · Semaine 8
> Maquette testée : [`propositions/proposition-A_frais.png`](propositions/proposition-A_frais.png) + [`wireframes/wireframe.png`](wireframes/wireframe.png)
> Fiche d'observation : [`fiche-observation.md`](fiche-observation.md)

---

## 1. Scénario de test

> « Tu as des pâtes, du poulet et des tomates : trouve une recette que tu peux faire avec tout ça et ouvre sa fiche. »

- **Durée max :** 5 minutes (chronomètre)
- **Tâche réussie si :** le testeur arrive sur la fiche détail d'une recette marquée « Tout est là ✓ »

## 2. Protocole

1. Installer le testeur devant la maquette, sans rien expliquer de l'app.
2. Test 5 secondes : montrer l'écran d'accueil 5 s, puis demander « C'est une appli pour… ? »
3. Lire le scénario une seule fois, lancer le chronomètre.
4. Demander au testeur de **penser à voix haute** (Think Aloud).
5. Observer **en silence** : ne pas guider, ne pas pointer, ne pas justifier.
6. Noter hésitations, remarques et temps dans le tableau ci-dessous.

## 3. Résultats du test

| | |
| --- | --- |
| **Testeur** | Kevin |
| **Observateur** | Albion |
| **Date** | 09.10.2026 |
| **Support** | image de la maquette (proposition A) sur téléphone |
| **Phrase du test 5 secondes** | « C'est un truc de cuisine. » |
| **Test de localisation** | réussi : appui direct sur le bouton vert « Voir les recettes » |
| **Temps mis** | immédiat, sans hésitation |
| **Aide donnée** | non |

### Analyse

**Test 5 secondes : compris à moitié.** Kevin a reconnu le domaine (la cuisine), mais pas la vraie promesse de l'app : partir **de ce qu'on a déjà** dans son frigo pour éviter le gaspillage. Sur l'accueil, le grand titre « Pas d'idée ce soir ? » parle de recettes en général, et l'idée du frigo n'arrive que dans le petit texte en dessous, qui n'est pas lu en 5 secondes.

**Test de localisation : réussi.** Le bouton principal vert est trouvé tout de suite. Sa couleur, sa taille (pleine largeur, 56 px de haut) et sa position en bas de l'écran fonctionnent.

**Limite du test.** Sur l'image, les ingrédients étaient déjà ajoutés en tags : le test n'a donc pas vérifié **l'étape de saisie**, qui est la plus à risque selon l'évaluation experte ci-dessous. Elle sera testée en s16 sur l'app en ligne, avec un champ vide.

### Hésitations observées

Aucune hésitation observée sur la tâche de localisation.

### Remarques dites à voix haute

- « C'est un truc de cuisine. » (test 5 secondes)

### Évaluation experte (parcours cognitif) — en attendant le test réel

Avant le test avec un camarade, j'ai parcouru moi-même le flow écran par écran en me mettant à la place de Kevin (persona). Pour chaque étape, je me suis posé la question : « Est-ce qu'il sait quoi faire, et est-ce qu'il comprend ce qui s'est passé ? »

| Écran | Risque d'hésitation identifié | Gravité |
| --- | --- | :---: |
| E1 Accueil | « Récemment » : on ne sait pas si c'est une recherche ou une recette déjà faite. | faible |
| E2 Mon frigo | Il n'y a pas de bouton « Ajouter » à côté du champ : l'utilisateur ne sait pas s'il faut appuyer sur Entrée ou sur une suggestion. | **forte** |
| E2 Mon frigo | Réflexe probable : taper « pâtes, poulet, tomates » d'un coup avec des virgules. La maquette prévoit un seul ingrédient à la fois. | **forte** |
| E2 Mon frigo | La croix ✕ des tags est trop petite (~12 px) : risque de rater la suppression. | moyenne |
| E3 Résultats | « Il manque 1 » ne dit pas **quoi** : il faut ouvrir la fiche pour le savoir. | **forte** |
| E3 Résultats | Le badge et la barre de progression disent la même chose : doublon qui charge la carte. | faible |
| E4 Détail | Les ingrédients manquants en gris barré peuvent être lus comme « à ne pas utiliser » plutôt que « à acheter ». | moyenne |

**Hypothèses à vérifier pendant le test réel :**
1. Le testeur va-t-il taper plusieurs ingrédients séparés par des virgules ?
2. Va-t-il ouvrir une recette « Il manque 1 » juste pour savoir ce qui manque ?

---

## 4. Audit des contrastes (WCAG 2.2 AA)

Seuils : **4,5:1** pour le texte courant, **3:1** pour le grand texte (≥ 24 px, ou ≥ 19 px en gras).
Mesures calculées avec la formule de luminance relative WCAG.

### Bouton principal

| Version | Couleurs | Ratio mesuré | Résultat |
| --- | --- | :---: | :---: |
| Proposition A (initiale) | blanc `#FFFFFF` sur vert `#2E9E5B` | **3,41:1** | ❌ échec (texte 15 px) |
| **Palette finale** | blanc `#FFFFFF` sur vert `#237A46` | **5,32:1** | ✅ AA |

### Autres couples de couleurs

| Élément | Texte / fond | Ratio | Résultat |
| --- | --- | :---: | :---: |
| Texte principal sur fond | `#1B2A20` / `#F6FAF5` | 14,24:1 | ✅ |
| Texte principal sur carte | `#1B2A20` / `#FFFFFF` | 15,01:1 | ✅ |
| Texte secondaire (initial) | `#6B7D70` / `#F6FAF5` | 4,15:1 | ❌ |
| Texte secondaire (final) | `#5E6F63` / `#F6FAF5` | 5,07:1 | ✅ |
| Texte secondaire (final) sur carte | `#5E6F63` / `#FFFFFF` | 5,34:1 | ✅ |
| Badge « Il manque X » | `#1B2A20` / `#F2A93B` | 7,52:1 | ✅ |
| Tags d'ingrédients | `#1B2A20` / `#E3F4E9` | 13,14:1 | ✅ |
| Lien « Modifier » | `#237A46` / `#F6FAF5` | 5,05:1 | ✅ |
| Logo « CuisineDuFrigo » (initial) | `#2E9E5B` / `#F6FAF5` | 3,23:1 | ⚠️ OK seulement en grand texte |

**Bilan :** avec la palette finale, 100 % des textes atteignent AA. La proposition A d'origine échouait sur le bouton principal et le texte secondaire.

## 5. Cibles tactiles

Minimum WCAG 2.2 AA : **24 × 24 px** · standard visé en cours : **48 × 48 px**.

| Élément | Taille sur la maquette | Résultat | Correction |
| --- | --- | :---: | --- |
| Bouton « Qu'est-ce que je cuisine ? » | 244 × 56 px | ✅ | — |
| Bouton « Voir les recettes » | 252 × 56 px | ✅ | — |
| Carte recette (E3) | 260 × 120 px | ✅ | — |
| Onglets Accueil / Favoris | 150 × 58 px | ✅ | — |
| **Croix ✕ d'un tag** | ~12 × 12 px | ❌ | zone cliquable 48 × 48 px autour de la croix |
| **Lignes de suggestions** | ~20 px de haut | ❌ | 48 px de haut par suggestion |
| Flèche retour ← | ~20 × 20 px | ⚠️ | zone 48 × 48 px |
| Cœur ♥ favori (E4) | ~22 × 22 px | ⚠️ | zone 48 × 48 px |

## 6. Navigation au clavier & focus

L'app n'est pas encore codée : ce test se fera sur la version HTML. Ce qui est prévu :

| Écran | Ordre du Tab | Activation |
| --- | --- | --- |
| E1 | bouton principal → recherches récentes → onglets | Entrée |
| E2 | retour → champ → suggestions (flèches ↑↓) → croix des tags → « Voir les recettes » | Entrée / Espace |
| E3 | retour → « Modifier » → cartes recettes | Entrée |
| E4 | retour → cœur favori → (lecture) | Entrée / Espace |

- **Focus visible :** contour `3px solid #1B2A20` décalé de 2 px (`outline-offset: 2px`), visible sur le vert comme sur le blanc.
- **Pas de piège :** la liste de suggestions se ferme avec Échap.
- **Images :** chaque photo de recette aura un `alt` (ex. `alt="Pâtes poulet-tomate dans une assiette"`). Les illustrations décoratives auront `alt=""`.

---

## 7. Correctifs prioritaires

### Tirés de l'audit

| # | Problème | Correctif chiffré |
| --- | --- | --- |
| A1 | Bouton principal à 3,41:1 | vert `#2E9E5B` → `#237A46` = **5,32:1** |
| A2 | Croix des tags ~12 px | zone tactile portée à **48 × 48 px** |

### Tirés de l'évaluation experte

| # | Problème | Correctif prévu |
| --- | --- | --- |
| E1 | Saisie d'un seul ingrédient à la fois, pas de bouton « Ajouter » | bouton « + » de 48 × 48 px à droite du champ, et découpage automatique sur les virgules (« pâtes, poulet » → 2 tags) |
| E2 | « Il manque 1 » sans préciser quoi | badge remplacé par « Il manque : ail » directement sur la carte |

### Tirés du test utilisateur

| # | Friction observée | Correctif prévu |
| --- | --- | --- |
| T1 | Test 5 s : « un truc de cuisine », l'idée « avec ce que j'ai dans mon frigo » n'est pas perçue | titre de l'accueil « Pas d'idée ce soir ? » → **« Cuisine avec ce que tu as déjà »**, en 24 px gras, pour que la promesse soit lue en premier |
| T2 | La saisie des ingrédients n'a pas pu être testée (tags déjà remplis sur l'image) | test s16 sur l'app en ligne en partant d'un **champ vide**, pour vérifier les hypothèses 1 et 2 de l'évaluation experte |

**Ce qui est conservé :** le bouton principal vert (trouvé immédiatement) garde sa couleur, sa taille et sa position.
