# Critique comparative des propositions de design — CuisineDuFrigo

Trois propositions ont été générées par IA (Claude) à partir du brief, du persona et du wireframe.
Images archivées dans [`propositions/`](propositions/).

| | Proposition |
| --- | --- |
| A | [« Frais & vert »](propositions/proposition-A_frais.png) — clair, végétal, rassurant |
| B | [« Mode nuit gourmand »](propositions/proposition-B_nuit.png) — sombre, contrasté, ambiance soirée |
| C | [« Pop & ludique »](propositions/proposition-C_pop.png) — couleurs vives, formes très rondes |

## Direction artistique visée

L'app doit parler à **Kevin, 18 ans** : simple, rapide, pas scolaire. Le message central est **anti-gaspillage / fraîcheur des aliments**. L'interface doit rester lisible **debout devant le frigo, à une main**, et montrer d'un coup d'œil **ce qui est disponible et ce qui manque**.

## Critères et notes (sur 5)

| Critère | A — Frais & vert | B — Mode nuit | C — Pop & ludique |
| --- | :---: | :---: | :---: |
| Cohérence avec le thème (frais, anti-gaspi) | 5 | 3 | 3 |
| Lisibilité / hiérarchie | 4 | 4 | 4 |
| Contraste (WCAG AA) | 3 | 5 | 4 |
| Attrait pour le persona (18 ans) | 4 | 4 | 4 |
| Lisibilité « possédé / manquant » | 5 | 4 | 3 |
| Faisabilité en CSS (4 semaines) | 5 | 5 | 4 |
| **Total / 30** | **26** | **25** | **22** |

## Analyse

### A — « Frais & vert »
**Points forts**
- Le vert évoque directement la fraîcheur et l'anti-gaspillage : le thème se comprend sans texte.
- Code couleur très clair : vert = « tout est là », orange = « il manque » → répond au besoin n°1 du persona.
- Fond clair, cartes blanches : hiérarchie nette, facile à reproduire en CSS.

**Points faibles**
- Le texte blanc sur le vert `#2E9E5B` n'a qu'un contraste de **3.4:1** → insuffisant pour du texte de 15 px (AA demande 4.5:1).
- Style un peu « attendu », moins de personnalité que B ou C.

### B — « Mode nuit gourmand »
**Points forts**
- Meilleurs contrastes des trois (bouton **7:1**, texte secondaire **6.5:1**).
- Ambiance « soirée », cohérente avec le moment d'usage (Kevin cuisine vers 18h30).
- Look moderne qui plaît à un public jeune.

**Points faibles**
- Un fond sombre évoque peu la fraîcheur et la nourriture.
- Orange (disponible) et jaune (manquant) trop proches : la différence possédé / manquant se lit moins vite.
- Les photos de plats ressortent moins bien sur fond noir.

### C — « Pop & ludique »
**Points forts**
- Le plus original et le plus fun, identité forte.
- Contrastes corrects (bouton **5.3:1**).

**Points faibles**
- Violet + rose + jaune : trop de couleurs, rien n'évoque la cuisine ni la fraîcheur.
- Rose = « il manque » peut être perçu comme une erreur/alerte, trop dramatique.
- Rayons de 24 px et palette chargée : risque d'aspect « enfant », pas idéal pour 18 ans.

## Choix final : Proposition A — « Frais & vert »

C'est celle qui sert le mieux le **message** (anti-gaspi, fraîcheur) et la **tâche n°1** (voir d'un coup d'œil ce qui est disponible ou manquant).

### Ajustements retenus pour le design final
1. **Assombrir le vert principal** : `#2E9E5B` → `#237A46` (contraste avec le blanc **5.3:1**, conforme AA).
2. **Reprendre le meilleur de B** : prévoir un mode sombre plus tard (« Could »), en gardant le même code vert/orange.
3. **Reprendre le meilleur de C** : un peu de personnalité dans l'illustration d'accueil et l'écran « aucune recette ».
4. Garder l'orange `#F2A93B` uniquement pour « il manque X » afin que la couleur ait **un seul sens**.

### Palette finale

| Rôle | Couleur |
| --- | --- |
| Principal (boutons, « tout est là ») | `#237A46` |
| Accent (« il manque ») | `#F2A93B` |
| Fond | `#F6FAF5` |
| Surface (cartes) | `#FFFFFF` |
| Texte | `#1B2A20` |
| Texte secondaire | `#5E6F63` |
| Tags | `#E3F4E9` |

Police : **Inter** (400 / 600 / 800) · rayons 16 px · zones tactiles ≥ 48 × 48 px.

### Résultat

Le design final, avec la palette ajustée et les correctifs issus de la revue et du test utilisateur, est visible dans [`design-final.png`](design-final.png).
