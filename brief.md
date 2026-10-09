# Brief — CuisineDuFrigo

> Fichier de spécification officiel du projet M291.
> Auteur : Albion (SM-C2b)

## 1. Le projet en une phrase

CuisineDuFrigo propose des recettes à partir des ingrédients que l'utilisateur a déjà chez lui, pour éviter le gaspillage.

## 2. Utilisateur cible

**Kevin, 18 ans**, étudiant en colocation, budget serré, débutant en cuisine. Il cherche sur son téléphone, debout devant le frigo, une idée rapide.
→ Détails : [`mon_app/Design/persona.md`](mon_app/Design/persona.md)

## 3. Problème à résoudre

Les sites de recettes partent d'un nom de plat. Kevin, lui, part de ce qu'il a. Résultat : il ne trouve pas d'idée, commande à manger et jette des ingrédients.

## 4. Tâche principale (flow n°1)

Entrer une liste d'ingrédients → voir les recettes possibles → ouvrir une recette.
→ Détails : [`mon_app/Design/user-flow.md`](mon_app/Design/user-flow.md)

## 5. Périmètre

### Inclus (MVP — 4 semaines)

| Priorité | Fonctionnalité |
| --- | --- |
| Must | Saisie d'ingrédients sous forme de tags : champ + bouton « + » (48 × 48 px), validation par Entrée, plusieurs ingrédients d'un coup séparés par des virgules |
| Must | Filtrage des recettes selon les ingrédients saisis |
| Must | Tri par pourcentage d'ingrédients possédés, puis par temps de préparation (le plus rapide d'abord) en cas d'égalité |
| Must | Badge sur chaque carte : « Tout est là ✓ » ou « Il manque : ail » (nom de l'ingrédient manquant) |
| Must | Fiche détail : ingrédients (possédés / à acheter), temps, étapes |
| Should | Suggestions pendant la saisie (autocomplétion dès 2 lettres) |
| Should | Favoris (stockés en local dans le navigateur) |
| Could | Filtre par temps de préparation (< 15 min, < 30 min) |
| Could | Fonctionnement hors connexion une fois l'app chargée |

### Exclus (hors projet)

- Comptes utilisateurs / connexion
- Scan du frigo ou photo d'ingrédients
- IA générative de recettes
- Liste de courses, quantités et conversions
- API externe de recettes

## 6. Données

Données **inventées**, stockées dans des fichiers JSON locaux.

- **`recettes.json`** : **30 à 40 fiches**, construites surtout avec des ingrédients courants (pâtes, riz, œufs, poulet, tomate, oignon, fromage…) pour limiter les cas « aucune recette trouvée ».
- **`ingredients.json`** : liste de référence des ingrédients, générée à partir des fiches. Elle sert aux **suggestions** pendant la saisie.

```json
{
  "id": 1,
  "nom": "Pâtes poulet-tomate",
  "temps": 15,
  "difficulte": "facile",
  "ingredients": ["pâtes", "poulet", "tomate", "ail"],
  "etapes": [
    "Cuire les pâtes 10 min.",
    "Couper le poulet en dés et le saisir.",
    "Ajouter la tomate et l'ail.",
    "Mélanger avec les pâtes."
  ]
}
```

### Règles de comparaison des ingrédients

- **Ingrédients de base** : sel, poivre, huile, eau, sucre et farine sont **toujours considérés comme présents**. Ils n'apparaissent jamais comme « manquants » et sont listés à part sur la fiche (« + sel, poivre, huile »).
- **Normalisation** avant comparaison : minuscules, sans accents, au singulier, espaces supprimés (« Courgettes » = « courgette »).
- **Ingrédient inconnu** : ajouté quand même en tag, la recherche continue avec les autres.

## 7. Écrans

| Code | Écran | Rôle |
| --- | --- | --- |
| E1 | Accueil | Point d'entrée, titre « Cuisine avec ce que tu as déjà », bouton principal |
| E2 | Mon frigo | Saisie des ingrédients |
| E3 | Résultats | Liste des recettes filtrées |
| E4 | Détail recette | Ingrédients + étapes + favori |
| E5 | Favoris | Recettes enregistrées |

→ Wireframes : [`mon_app/Design/wireframes/`](mon_app/Design/wireframes/) · Design final : [`mon_app/Design/design-final.png`](mon_app/Design/design-final.png)

## 8. Contraintes

- **Mobile first** (360–414 px), utilisable à une main.
- Technologies : HTML, CSS, JavaScript (pas de framework imposé).
- Accessibilité (WCAG 2.2 AA) : contrastes ≥ 4,5:1, **zones tactiles ≥ 48 × 48 px**, textes ≥ 16 px, navigation complète au clavier avec focus visible, `alt` sur les images.
- Pas de dépendance payante.

→ Audit et tests : [`mon_app/Design/tests-utilisateurs.md`](mon_app/Design/tests-utilisateurs.md)

## 9. Critères de réussite

- Kevin trouve une recette en **moins de 3 interactions** après la saisie.
- Il voit **immédiatement** ce qui lui manque, sans ouvrir la fiche.
- Au test 5 secondes, l'idée « cuisiner avec ce qu'on a déjà » est comprise.
- 100 % des textes respectent les contrastes WCAG AA.

## 10. Planning (4 semaines)

| Semaine | Objectif |
| --- | --- |
| 1 | Structure HTML des 5 écrans + données JSON (recettes et ingrédients) |
| 2 | Saisie des tags (bouton « + », virgules, normalisation) + logique de filtrage et de tri |
| 3 | Fiche détail + favoris + cas limites + **styles du design final et contrastes** |
| 4 | Navigation clavier et focus, test utilisateur sur l'app en ligne (s16), corrections |

## 11. Revue croisée

| | |
| --- | --- |
| Relu par | Kevin |
| Date | 02.10.2026 |
| Avis global | Brief solide, prêt pour commencer le code après les corrections 1 à 4. |

**Points forts**
- Le problème est clair et concret : on part du frigo, pas d'un nom de plat.
- Le périmètre est bien découpé (Must / Should / Could) et la liste « Exclus » évite que le projet grossisse.
- L'exemple de fiche JSON aide à comprendre la structure des données.
- Le planning sur 4 semaines est réaliste.

**À corriger**
1. **Ingrédients de base** : sel, poivre, huile, eau vont compter comme « manquants » partout. Décider s'ils sont considérés comme toujours présents.
2. **Orthographe des ingrédients** : « courgette » et « Courgettes » doivent être reconnus comme identiques. Préciser la comparaison (minuscules, sans accents, singulier).
3. **Autocomplétion** : préciser d'où viennent les suggestions (liste d'ingrédients dédiée ou tirée des fiches recettes).
4. **Critère « hors connexion »** : absent du périmètre et du planning. L'ajouter en « Could » ou l'enlever.
5. **Seulement 20 recettes** : risque fréquent de « aucune recette trouvée ». Prévoir 30 à 40 fiches ou des ingrédients très courants.

**Questions**
- À pourcentage égal, quelle recette s'affiche en premier ? La plus rapide ?
- La semaine 4 (design, accessibilité, tests, corrections) n'est-elle pas trop chargée ?
