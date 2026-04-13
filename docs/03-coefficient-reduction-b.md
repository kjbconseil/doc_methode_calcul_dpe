# 3.1 Détermination du coefficient de réduction des déperditions b

## Données d'entrée

- Surface des parois séparant le local non chauffé des locaux chauffés : Aiu (m²)
- Surface des parois séparant le local non chauffé de l'extérieur ou du sol : Aue (m²)
- Type de local non chauffé (garage, comble, circulation...)
- Etat d'isolation des parois du local non chauffé (isolées, non isolées)

## Règles de détermination de b

### Cas simples

| Situation | Valeur de b |
|-----------|-------------|
| Paroi extérieure donnant sur l'extérieur, ou plancher sur terre-plein, vide sanitaire ou sous-sol non chauffé | **b = 1** |
| Local non chauffé non accessible (moyennement, espaces sans acces...) | Forfaitairement **b = 0.95** |
| Paroi donnant sur un bâtiment ou espace autre que d'habitation (occupation discontinue) | Consideree comme déperditive avec **b = 0.2** |

### Cas des circulations communes en collectif

Pour les circulations communes au niveau d'un appartement en bâtiment collectif d'habitation, le calcul de b se fait en considerant les parois situées au même niveau que le lot traité :
- Pour un calcul fait à l'immeuble, un seul b est pris pour toutes les circulations communes si elles ne sont pas en volume intérieur chauffe
- La méthode de caracterisation des espaces communs en volume chauffé ou non chauffé est détaillée au §17.1.1.3

### Méthode générale par tableaux

Dans les autres cas, b est déterminé à l'aide des tableaux suivants, en fonction du rapport des surfaces Aiu/Aue et du coefficient surfacique équivalent Uv_ue.

**Règles de calcul** :
- `Aiu` est la surface des parois du local non chauffé donnant sur les **locaux chauffes** (cote intérieur)
- `Aue` est la surface des parois du local non chauffé donnant sur **l'extérieur** ou en contact avec le sol (parois enterrees, terre-plein)
- Il est considéré qu'il n'y a pas d'échange entre deux locaux non chauffés distincts (sans liaison aéraulique). La surface des parois du local non chauffé donnant sur un vide sanitaire ou un autre local non chauffé n'entre donc ni dans Aiu ni dans Aue

> **Règle ajoutée (Octobre 2021)** : Dans le cas où Aue = 0, alors **b = 0**

### Tableau : Coefficient surfacique équivalent Uv_ue

| Local non chauffé | Uv_ue W/(m².K) |
|-------------------|----------------|
| **Maison individuelle** | |
| Garage | 5 |
| Cellier | 3 |
| Comble fortement ventilé | 9 |
| Comble faiblement ventilé | 3 |
| Comble très faiblement ventilé | 0.3 |
| **Logement collectif** | |
| Circulation commune sans ouverture directe sur l'extérieur | 0.0 |
| Circulation commune avec ouverture directe sur l'extérieur | 0.3 |
| Circulation commune avec bouche ou gaine de désenfumage, ouverte en permanence | 1 |
| Hall d'entrée | 3(1) ou 0.3(2) |
| Garage privé collectif | 3 |
| Autres dépendances | 3 |
| Comble fortement ventilé | 9 |
| Comble faiblement ventilé | 3 |
| Comble très faiblement ventilé | 0.3 |

*(1) Portes d'accès sans dispositif de fermeture automatique*
*(2) Portes d'accès avec dispositif de fermeture automatique*

### Vérandas et loggias non chauffées

Les espaces tampons solarisés (vérandas, loggias fermees et non chauffées) beneficient d'apports solaires qui y generent des températures superieures a celles attendues dans les espaces non solarisés.

**Rappel** : les vérandas chauffées sont traitées en surface de référence.

Dans le cas de vérandas ou loggias fermees non chauffées, les coefficients de réduction de température pris sont donnés dans le tableau ci-dessous :

| Zone climatique | Orientation de la véranda | Paroi donnant sur la véranda | b_vu |
|-----------------|--------------------------|------------------------------|------|
| H1 | Nord | Non isolé | 0.95 |
| | | Isolé | 0.85 |
| | Est / Ouest | Non isolé | 0.6 |
| | | Isolé | 0.58 |
| | Sud | Non isolé | 0.55 |
| | | Isolé | 0.63 |
| H2 | Nord | Non isolé | 0.95 |
| | | Isolé | 0.85 |
| | Est / Ouest | Non isolé | 0.6 |
| | | Isolé | 0.58 |
| | Sud | Non isolé | 0.57 |
| | | Isolé | 0.17 |
| H3 | Nord | Non isolé | 0.95 |
| | | Isolé | 0.85 |
| | Est / Ouest | Non isolé | 0.53 |
| | | Isolé | 0.53 |
| | Sud | Non isolé | 0.4 |
| | | Isolé | 0.55 |

**Règles d'orientation** :
- Les orientations Nord integrent les limites Nord-Est et Nord-Ouest
- Les orientations Sud integrent les limites Sud-Est et Sud-Ouest
- L'orientation de la véranda pour en connaitre est celle de la facade principale (avec la plus grande surface de vitrages verticaux). S'il existe plusieurs facades d'orientation predominante, c'est-a-dire qu'au moins deux facades d'orientation predominent de façon égale les surfaces vitrees les plus importantes, b_vu est la moyenne des b_vu sur ces orientations

### Détermination de b par les tableaux Aiu/Aue

Les valeurs de b en fonction du rapport Aiu/Aue et de Uv_ue sont données dans des tables selon que :
- Aiu est **non isolée** ou **isolée**
- Aue est **non isolée** ou **isolée**

Les données ne figurant pas dans le tableau peuvent être obtenues par interpolation ou extrapolation en traçant des droites entre les valeurs les plus proches présentes dans le tableau.

**Isolation des parois** :
- Pour les bâtiments d'avant 1975, la paroi est considérée comme non isolée
- Pour les bâtiments construits à partir de 1975 :
  - Les murs sont considérés comme isolés par l'extérieur
  - Les plafonds sont considérés comme isolés par l'extérieur
  - Les planchers sur terre-plein sont considérés isolés par l'extérieur (en sous-face) à partir de 2001

On en déduit la valeur de b en fonction des différents cas suivants :
- 2S/P est arrondi à l'entier le plus proche
- Valeurs de Ue (W/(m².K)) selon Upb et 2S/P

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Section** : 3.1 (pages 8-11)
