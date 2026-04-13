# 18. Annexe - Zones climatiques et données de référence

## 18.1 Zones climatiques

Les sollicitations climatiques sont representees par huit zones climatiques : **H1a, H1b, H1c, H2a, H2b, H2c, H2d, H3**.

### Correspondance departement / zone climatique

| Departement | Zone | Departement | Zone | Departement | Zone |
|-------------|------|-------------|------|-------------|------|
| 01 Ain | H1c | 33 Gironde | H2c | 65 Hautes-Pyrenees | H2c |
| 02 Aisne | H1a | 34 Herault | H3 | 66 Pyrenees-Orientales | H3 |
| 03 Allier | H1c | 35 Ille-et-Vilaine | H2a | 67 Bas-Rhin | H1b |
| 04 Alpes-de-Haute-Provence | H2d | 36 Indre | H2b | 68 Haut-Rhin | H1b |
| 05 Hautes-Alpes | H1c | 37 Indre-et-Loire | H2b | 69 Rhone | H1c |
| 06 Alpes-Maritimes | H3 | 38 Isere | H1c | 70 Haute-Saone | H1b |
| 07 Ardeche | H2d | 39 Jura | H1c | 71 Saone-et-Loire | H1c |
| 08 Ardennes | H1b | 40 Landes | H2c | 72 Sarthe | H2a |
| 09 Ariege | H2c | 41 Loir-et-Cher | H2b | 73 Savoie | H1c |
| 10 Aube | H1b | 42 Loire | H1c | 74 Haute-Savoie | H1c |
| 11 Aude | H3 | 43 Haute-Loire | H1c | 75 Paris | H1a |
| 12 Aveyron | H2c | 44 Loire-Atlantique | H2a | 76 Seine-Maritime | H1a |
| 13 Bouches-du-Rhone | H3 | 45 Loiret | H1b | 77 Seine-et-Marne | H1a |
| 14 Calvados | H1a | 46 Lot | H2c | 78 Yvelines | H1a |
| 15 Cantal | H1c | 47 Lot-et-Garonne | H2c | 79 Deux-Sevres | H2b |
| 16 Charente | H2b | 48 Lozere | H2d | 80 Somme | H1a |
| 17 Charente-Maritime | H2b | 49 Maine-et-Loire | H2b | 81 Tarn | H2c |
| 18 Cher | H2b | 50 Manche | H2a | 82 Tarn-et-Garonne | H2c |
| 19 Correze | H1c | 51 Marne | H1b | 83 Var | H3 |
| 20 Corse | H3 | 52 Haute-Marne | H1b | 84 Vaucluse | H2d |
| 21 Cote-d'Or | H1c | 53 Mayenne | H2a | 85 Vendee | H2b |
| 22 Cotes-d'Armor | H2a | 54 Meurthe-et-Moselle | H1b | 86 Vienne | H2b |
| 23 Creuse | H1c | 55 Meuse | H1b | 87 Haute-Vienne | H1c |
| 24 Dordogne | H2c | 56 Morbihan | H2a | 88 Vosges | H1b |
| 25 Doubs | H1c | 57 Moselle | H1b | 89 Yonne | H1b |
| 26 Drome | H2d | 58 Nievre | H1c | 90 Territoire de Belfort | H1b |
| 27 Eure | H1a | 59 Nord | H1a | 91 Essonne | H1a |
| 28 Eure-et-Loir | H1a | 60 Oise | H1a | 92 Hauts-de-Seine | H1a |
| 29 Finistere | H2a | 61 Orne | H1a | 93 Seine-Saint-Denis | H1a |
| 30 Gard | H3 | 62 Pas-de-Calais | H1a | 94 Val-de-Marne | H1a |
| 31 Haute-Garonne | H2c | 63 Puy-de-Dome | H1c | 95 Val-d'Oise | H1a |
| 32 Gers | H2c | 64 Pyrenees-Atlantiques | H2c | | |

### Temperature extérieure de base Tbase (°C)

| Zone climatique | < 400m | 400 < < 800m | > 800m |
|----------------|--------|-------------|--------|
| H1a, H1b, H1c | -9.7 | -12.5 | -13.5 |
| H2a, H2b, H2c, H2d | -6.5 | -6 | -10.5 |
| H3 | -3.5 | -5.5 | -7.5 |

## 18.2 Sollicitations exterieures

### Ensoleillement E (en kWh/m²)

Les données d'ensoleillement E sont fournies par zone climatique et par mois (voir tableaux du document source pages 118-140).

Ces données couvrent :
- **Données a moins de 400m d'altitude** (section 18.2.1)
- **Données entre 400m et 800m d'altitude** (section 18.2.2)
- **Données a plus de 800m d'altitude** (section 18.2.3)

Pour chaque zone climatique, les données mensuelles comprennent :
- Degrés heures de chauffage DH (a 19°C et 21°C)
- Nombre d'heures de chauffage Nref (a 19°C et 21°C)
- Temperature extérieure moyenne Text
- Temperature d'eau froide sanitaire T(ef)
- Ensoleillement E (kWh/m²)
- Nombre d'heures de refroidissement Nref_fr (a 28°C et 26°C)

### 18.3 Cas des bâtiments construits de parois anciennes a tres forte inertie

Des données spécifiques sont fournies pour les bâtiments a tres forte inertie, avec les mêmes decompositions par altitude.

## 18.4 Facteur de couverture solaire

Les facteurs de couverture solaire peuvent être saisis directement quand ils sont connus et peuvent être justifiés.

Les valeurs sont données dans le document source par zone climatique (voir page 140).

## 18.5 Coefficients d'orientation et d'inclinaison des parois vitrees : C1

Les coefficients C1 sont donnés par zone climatique (H1a, H1b, H1c, H2a, H2b, H2c, H2d, H3) et par mois, en fonction de :
- L'**orientation** (Sud, Ouest, Nord, Est)
- L'**inclinaison** (< 25°, 25°-75°, > 75°, horizontal)

(Tableaux détaillés pages 141-148 du document source)

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 18 a 18.5 (pages 117-148)
