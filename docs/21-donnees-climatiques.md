# 18. Annexe - Zones climatiques et données de référence

> Annexe 1 de l'arrêté du 31 mars 2021, section 18

## Fichiers de données

| Fichier | Contenu |
|---------|---------|
| [21a-donnees-climat-inf400m.md](21a-donnees-climat-inf400m.md) | 18.2.1 - Données climatiques altitude < 400m |
| [21b-donnees-climat-400-800m.md](21b-donnees-climat-400-800m.md) | 18.2.2 - Données climatiques altitude 400-800m |
| [21c-donnees-climat-sup800m.md](21c-donnees-climat-sup800m.md) | 18.2.3 - Données climatiques altitude >= 800m |
| [21d-donnees-climat-inertie-lourde.md](21d-donnees-climat-inertie-lourde.md) | 18.3 - Données bâtiments inertie lourde (parois anciennes) |
| [21e-facteur-solaire-coefficients-c1.md](21e-facteur-solaire-coefficients-c1.md) | 18.4 - Facteur de couverture solaire + 18.5 - Coefficients C1 |

## 18.1 Zones climatiques

Les sollicitations climatiques sont représentées par huit zones climatiques : **H1a, H1b, H1c, H2a, H2b, H2c, H2d, H3**.

### Correspondance département / zone climatique

| Département | Zone | Département | Zone | Département | Zone |
|-------------|------|-------------|------|-------------|------|
| 01 Ain | H1c | 33 Gironde | H2c | 65 Hautes-Pyrénées | H2c |
| 02 Aisne | H1a | 34 Hérault | H3 | 66 Pyrénées-Orientales | H3 |
| 03 Allier | H1c | 35 Ille-et-Vilaine | H2a | 67 Bas-Rhin | H1b |
| 04 Alpes-de-Haute-Provence | H2d | 36 Indre | H2b | 68 Haut-Rhin | H1b |
| 05 Hautes-Alpes | H1c | 37 Indre-et-Loire | H2b | 69 Rhône | H1c |
| 06 Alpes-Maritimes | H3 | 38 Isère | H1c | 70 Haute-Saône | H1b |
| 07 Ardèche | H2d | 39 Jura | H1c | 71 Saône-et-Loire | H1c |
| 08 Ardennes | H1b | 40 Landes | H2c | 72 Sarthe | H2a |
| 09 Ariège | H2c | 41 Loir-et-Cher | H2b | 73 Savoie | H1c |
| 10 Aube | H1b | 42 Loire | H1c | 74 Haute-Savoie | H1c |
| 11 Aude | H3 | 43 Haute-Loire | H1c | 75 Paris | H1a |
| 12 Aveyron | H2c | 44 Loire-Atlantique | H2a | 76 Seine-Maritime | H1a |
| 13 Bouches-du-Rhône | H3 | 45 Loiret | H1b | 77 Seine-et-Marne | H1a |
| 14 Calvados | H1a | 46 Lot | H2c | 78 Yvelines | H1a |
| 15 Cantal | H1c | 47 Lot-et-Garonne | H2c | 79 Deux-Sèvres | H2b |
| 16 Charente | H2b | 48 Lozère | H2d | 80 Somme | H1a |
| 17 Charente-Maritime | H2b | 49 Maine-et-Loire | H2b | 81 Tarn | H2c |
| 18 Cher | H2b | 50 Manche | H2a | 82 Tarn-et-Garonne | H2c |
| 19 Corrèze | H1c | 51 Marne | H1b | 83 Var | H3 |
| 20 Corse | H3 | 52 Haute-Marne | H1b | 84 Vaucluse | H2d |
| 21 Côte-d'Or | H1c | 53 Mayenne | H2a | 85 Vendée | H2b |
| 22 Côtes-d'Armor | H2a | 54 Meurthe-et-Moselle | H1b | 86 Vienne | H2b |
| 23 Creuse | H1c | 55 Meuse | H1b | 87 Haute-Vienne | H1c |
| 24 Dordogne | H2c | 56 Morbihan | H2a | 88 Vosges | H1b |
| 25 Doubs | H1c | 57 Moselle | H1b | 89 Yonne | H1b |
| 26 Drôme | H2d | 58 Nièvre | H1c | 90 Territoire de Belfort | H1b |
| 27 Eure | H1a | 59 Nord | H1a | 91 Essonne | H1a |
| 28 Eure-et-Loir | H1a | 60 Oise | H1a | 92 Hauts-de-Seine | H1a |
| 29 Finistère | H2a | 61 Orne | H1a | 93 Seine-Saint-Denis | H1a |
| 30 Gard | H3 | 62 Pas-de-Calais | H1a | 94 Val-de-Marne | H1a |
| 31 Haute-Garonne | H2c | 63 Puy-de-Dôme | H1c | 95 Val-d'Oise | H1a |
| 32 Gers | H2c | 64 Pyrénées-Atlantiques | H2c | | |

### Température extérieure de base Tbase (°C)

| Zone climatique | < 400m | 400-800m | > 800m |
|----------------|--------|----------|--------|
| H1a, H1b, H1c | -9.7 | -12.5 | -13.5 |
| H2a, H2b, H2c, H2d | -6.5 | -6.0 | -10.5 |
| H3 | -3.5 | -5.5 | -7.5 |

## Variables des tableaux climatiques

Pour chaque zone et tranche d'altitude, les données mensuelles comprennent :

| Variable | Description | Unité |
|----------|-------------|-------|
| Text | Température extérieure moyenne en période de chauffage | °C |
| Tef | Température eau froide sanitaire | °C |
| E | Ensoleillement reçu par une paroi verticale orientée au sud | kWh/m² |
| DH19 | Degrés-heures de chauffage à 19°C (comportement conventionnel) | °Ch |
| DH21 | Degrés-heures de chauffage à 21°C (comportement dépensier) | °Ch |
| Nref19 | Nombre d'heures de chauffage à 19°C | h |
| Nref21 | Nombre d'heures de chauffage à 21°C | h |
| Nref_fr28 | Nombre d'heures de refroidissement à 28°C | h |
| Textmoy_clim | Température moyenne extérieure en période de refroidissement | °C |

Pour les bâtiments à inertie lourde (section 18.3), les données incluent aussi :

| Variable | Description | Unité |
|----------|-------------|-------|
| DH14 | Degrés-heures base 14°C (rendement de génération chaudières) | °Ch |

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 18 à 18.5 (pages 120-148)
