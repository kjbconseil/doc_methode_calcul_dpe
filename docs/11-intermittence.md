# 8. Modélisation de l'intermittence

## Données d'entrée

- Type de bâtiment
- Type de chauffage (divisé, central)
- Type de régulation (par piece ou non)
- Équipement d'intermittence (absent, central sans minimum de température, ...)
- Type d'émetteur (air souffle, convecteurs, ...)
- Présence d'un comptage
- Hauteur moyenne sous plafond

## Définition

Le facteur d'intermittence traduit les baisses temporaires de températures, realisees pour différentes raisons : absences, ralentis de nuit et éventuellement de façon intégrale dans les pieces.

Il est égal au rapport entre les besoins reels, compte tenu d'un comportement moyen des occupants, et les besoins theoriques. Le facteur d'intermittence est donné par la formule :

```
INT = I0 / (1 + 0.1 * (G - 1))
```

Avec :

```
G = GV / (Hsp * Sh)
```

| Variable | Description |
|----------|-------------|
| `GV` | Déperditions annuelles de l'enveloppe (W/K) (déterminé en partie 3) |
| `Sh` | Surface habitable (m²) |
| `Hsp` | Hauteur moyenne sous plafond (m) |

## Valeurs I0

Les valeurs I0 sont déterminées par un tableau croisant :
- Le type de bâtiment (maison individuelle / immeuble collectif)
- Le type de chauffage (divisé / central)
- Le type de régulation (avec/sans régulation piece par piece)
- L'équipement d'intermittence

### Pour les maisons individuelles (chauffage individuel)

| Chauffage | Regulation | Émetteur | I0 pour les différents équipements d'intermittence |
|-----------|-----------|---------|------|
| | | | Absent | Central sans minimum de température | Central avec minimum de température | Par piece avec minimum de température | Central avec minimum + comptage individuel | Par piece avec comptage individuel |
| Chauffage divisé | Avec régulation piece par piece | Air souffle | 0.84 | 0.83 | 0.77 | 0.75 | 0.60 | 0.65 | 0.65 | 0.78 |
| | | Convecteur | 0.84 | 0.83 | 0.77 | 0.75 | 0.68 | 0.60 | 0.60 | 0.78 |
| | | Radiateur | 0.84 | 0.83 | 0.77 | 0.75 | 0.68 | 0.60 | 0.60 | 0.78 |
| | | Plancher chauffant | 0.91 | 0.89 | 0.86 | 0.82 | 0.64 | 0.60 | 0.60 | |
| Chauffage central | Avec régulation piece par piece | Air souffle | 0.95 | 0.89 | 0.86 | 0.82 | 0.64 | 0.60 | | |
| | Sans régulation piece par piece | Radiateur | 0.95 | 0.89 | 0.86 | 0.82 | 0.56 | 0.60 | | |

### Pour les immeubles collectifs avec chauffage individuel

(Tableau similaire avec ajustements pour le collectif - voir page 55)

### Pour les immeubles collectifs avec chauffage collectif

(Tableau avec prise en compte du comptage collectif et individuel - voir page 55)

## Règles d'intermittence

En immeuble collectif, le chauffage mixte (c'est-a-dire dont une partie est facturee collectivement et une autre individuellement) est traité au niveau de l'intermittence comme un système collectif avec comptage individuel.

Seule l'intermittence de l'appoint est prise en compte sur les installations base + appoint. Une régulation zonale sera considérée comme une régulation piece par piece.

### Types d'équipements d'intermittence

**En chauffage individuel** :
- **Absent** : pas d'équipement permettant de programmer des reduits de température
- **Central sans minimum de température** : équipements permettant une programmation seulement de la fonction marche arret et donc ne garantissant pas un minimum de température
- **Central avec un minimum de température** : équipement pouvant assurer :
  - Centralement un ralenti ou un abaissement de température fixe, non modifiable par l'occupant, même par la fonction hors gel
  - Centralement un ralenti ou un abaissement de température au choix de l'occupant
- **Piece par piece avec minimum de température** : équipement permettant d'eteindre piece par piece un ralenti ou un abaissement de température fixe, non modifiable par l'occupant

**En chauffage collectif** :
- **Absent** : pas de reduit de nuit
- **Central collectif** : possibilite de ralentis de nuit

## Règles complémentaires (Octobre 2021)

- Un plancher chauffant avec une régulation zone jour/zone nuit peut être associé à une régulation pièce par pièce
- Un poêle sera modélisé comme un radiateur/convecteur pour la détermination de l'intermittence
- Un système de chauffage divisé est un système pour lequel la génération et l'émission sont confondues. C'est le cas des convecteurs électriques, planchers chauffants électriques
- Un système de chauffage central comporte un générateur central, individuel ou collectif, et une distribution par fluide chauffant : air ou eau

## Sources

- **Source** : Arrêté du 31 mars 2021, modifié par l'arrêté du 8 octobre 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Section** : 8 (pages 55-57 version Octobre 2021)
