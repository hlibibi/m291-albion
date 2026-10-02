# Brief — CuisineDuFrigo

> Fichier de spécification officiel du projet M291.
> Auteur : Albion (SM-C2b) · Version 1.0 · 02.10.2026

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
| Must | Saisie d'ingrédients sous forme de tags (ajout / suppression) |
| Must | Filtrage des recettes selon les ingrédients saisis |
| Must | Tri par pourcentage d'ingrédients possédés + badge « il manque X » |
| Must | Fiche détail : ingrédients (possédés / manquants), temps, étapes |
| Should | Suggestions pendant la saisie (autocomplétion) |
| Should | Favoris (stockés en local dans le navigateur) |
| Could | Filtre par temps de préparation (< 15 min, < 30 min) |

### Exclus (hors projet)

- Comptes utilisateurs / connexion
- Scan du frigo ou photo d'ingrédients
- IA générative de recettes
- Liste de courses, quantités et conversions
- API externe de recettes

## 6. Données

Données **inventées**, stockées dans un fichier JSON local (~20 fiches).

```json
{
  "id": 1,
  "nom": "Pâtes poulet-courgette",
  "temps": 20,
  "difficulte": "facile",
  "ingredients": ["pâtes", "poulet", "courgette", "ail", "huile d'olive"],
  "etapes": [
    "Cuire les pâtes.",
    "Couper le poulet et la courgette en dés.",
    "Faire revenir le tout avec l'ail dans l'huile.",
    "Mélanger avec les pâtes."
  ]
}
```

## 7. Écrans

| Code | Écran | Rôle |
| --- | --- | --- |
| E1 | Accueil | Point d'entrée, bouton principal |
| E2 | Mon frigo | Saisie des ingrédients |
| E3 | Résultats | Liste des recettes filtrées |
| E4 | Détail recette | Ingrédients + étapes + favori |
| E5 | Favoris | Recettes enregistrées |

→ Wireframes : [`mon_app/Design/wireframes/`](mon_app/Design/wireframes/)

## 8. Contraintes

- **Mobile first** (360–414 px), utilisable à une main.
- Technologies : HTML, CSS, JavaScript (pas de framework imposé).
- Accessibilité : contrastes AA, zones tactiles ≥ 44 px, textes ≥ 16 px.
- Pas de dépendance payante.

## 9. Critères de réussite

- Kevin trouve une recette en **moins de 3 interactions** après la saisie.
- Il voit **immédiatement** ce qui lui manque.
- L'app fonctionne hors connexion une fois chargée.

## 10. Planning (4 semaines)

| Semaine | Objectif |
| --- | --- |
| 1 | Structure HTML des 5 écrans + données JSON |
| 2 | Saisie des tags + logique de filtrage |
| 3 | Fiche détail + favoris + cas limites |
| 4 | Design final, accessibilité, tests, corrections |

## 11. Revue croisée

| | |
| --- | --- |
| Relu par | _(nom du binôme)_ |
| Date | _(à compléter)_ |
| Remarques | _(à compléter)_ |
