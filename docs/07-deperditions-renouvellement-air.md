# 4. Calcul des déperditions par renouvellement d'air

## Données d'entrée

- Type de bâtiment
- Surface des parois déperditives hors plancher bas
- Surface de référence
- Nombre de niveaux
- Hauteur moyenne sous plafond
- Type de ventilation
- Année de construction ou de l'installation
- Zone climatique

## Formule principale

Les déperditions DR par renouvellement d'air par degre d'écart entre l'intérieur et l'extérieur (W/K) sont données par la formule suivante :

```
DR = Hvent + Hperm
```

### Déperdition par ventilation

```
Hvent = 0.34 * Qvarep_conv * Sref
```

Avec :
- `Qvarep_conv` : débit d'air extrait conventionnel par unite de surface de référence (m³/(h.m²)) (voir tableau par type de ventilation ci-apres)
- `Sref` : surface de référence (m²)
- `0.34` : chaleur volumique de l'air (Wh/(m³.K))

### Déperdition par infiltrations (perméabilité)

```
Hperm = 0.34 * Qvinf
```

Avec :

- `Qvinf` : débit d'air du aux infiltrations liees au vent (m³/h) :

```
                    Hsp * Sref * n_50 * e
Qvinf = -----------------------------------------------
         1 + (f/e) * ((Qvasouf_conv - Qvarep_conv) / (Hsp * Sref))²
```

### Variables

| Variable | Description |
|----------|-------------|
| `Hsp` | Hauteur moyenne sous plafond (m) |
| `Sref` | Surface de référence (m²) |
| `n_50` | Renouvellement d'air sous 50 Pascals (h⁻¹) |
| `Qvasouf_conv` | Débit volumique conventionnel a souffler (m³/(h.m²)) (voir tableau) |
| `Qvarep_conv` | Débit volumique conventionnel a reprendre (m³/(h.m²)) (voir tableau) |
| `e` et `f` | Coefficients de protection prenant les valeurs tabulées ci-dessous |

### Coefficients de protection e et f

| Coefficient | Plusieurs facades exposees | Une seule facade exposee |
|-------------|---------------------------|-------------------------|
| e | 0.07 | 0.02 |
| f | 15 | 20 |

Une facade exposee est une facade donnant sur l'extérieur.

### Renouvellement d'air sous 50 Pascals (n50)

```
n50 = Q4Pa / ((4/50)^(2/3) * Hsp * Sref)
```

```
Q4Pa = Q4Pa_conv + 0.45 * Smea_conv * Sref
```

### Permeabilite Q4Pa_conv

```
Q4Pa_conv = Q4Pa_conv_val * Sdep
```

Avec :
- `Sdep` : surface des parois déperditives hors plancher bas (m²)
- `Q4Pa_conv` : valeur conventionnelle de la perméabilité sous 4Pa (m³/(h.m²))

### Valeurs de Q4Pa_conv par période

| | Appartement/Immeuble | | Maison | |
|---|---|---|---|---|
| | Avant 1948 | 1948-1974 | 1975- >2012 | Avant 1948 | 1948-1974 | 1975- >2012 |
| Q4Pa_conv | 4.6 | 2 | 1.5 | 1 | 3.3 | 2.3 | 1 | 1.3 | 0.8 |

**Règles spéciales** :
- Pour les bâtiments qui ont fait l'objet d'une mesure d'étanchéité à l'air moins de deux ans avant le diagnostic, la valeur mesurée de Q4Pa_conv peut être saisie
- Pour les maisons construites avant 1948 avec une isolation des murs et/ou du plafond (isolation de plus de 50% des surfaces), Q4Pa_conv = 2 m³/(h.m²)
- Pour les maisons construites entre 1948 et 1974 avec une isolation des murs et/ou du plafond (isolation de plus de 50% des surfaces), Q4Pa_conv = 1.9 m³/(h.m²)
- **(Octobre 2021)** Pour les bâtiments ou logements construits avant 1948 et dont les menuiseries possèdent des joints, Q4Pa_conv = 2.5 m³/(h.m²). Cette condition est respectée si les menuiseries représentant plus de 50% de la surface totale possèdent des joints

### Débits conventionnels par type de ventilation

| Type de ventilation | Qvarep_conv (m³/(h.m²)) | Qvasouf_conv (m³/(h.m²)) | Smea_conv (m³/(h.m²)) |
|--------------------|------------------------|--------------------------|---------------------|
| Ventilation par ouverture des fenêtres | 1.2 | 1.2 | 0 |
| Ventilation par entrées d'air hautes et basses | 2.23 | 0 | 4 |
| VMC SF Auto réglable < 1982 | 1.97 | 0 | 2 |
| VMC SF Auto réglable de 1982 a 2000 | 1.65 | 0 | 2 |
| VMC SF Auto réglable de 2001 a 2012 | 1.50 | 0 | 2 |
| VMC SF Auto réglable apres 2012 | 1.32 | 0 | 2 |
| VMC SF Hygro A < 2001 | 1.50 | 0 | 2 |
| VMC SF Hygro A de 2001 a 2012 | 1.44 | 0 | 2 |
| VMC SF Hygro A apres 2012 | 1.16 | 0 | 2 |
| VMC SF Gaz < 2001 | 1.59 | 0 | 2 |
| VMC SF Gaz de 2001 a 2012 | 1.53 | 0 | 2 |
| VMC SF Gaz apres 2012 | 1.22 | 0 | 2 |
| VMC SF Hygro B < 2001 | 1.36 | 0 | 1.5 |
| VMC SF Hygro B de 2001 a 2012 | 1.24 | 0 | 1.5 |
| VMC SF Hygro B apres 2012 | 1.09 | 0 | 1.5 |
| VMC Basse pression Auto réglable | 1.97 | 0 | 2 |
| VMC Basse pression Hygro A | 1.30 | 0 | 2 |
| VMC Basse pression Hygro B | 1.24 | 0 | 1.5 |
| VMC DF individuelle avec échangeur <= 2012 | 0.60 | 0.6 | 0 |
| VMC DF individuelle avec échangeur apres 2012 | 0.26 | 0.26 | 0 |
| VMC DF collective avec échangeur <= 2012 | 0.75 | 0.75 | 0 |
| VMC DF collective avec échangeur apres 2012 | 0.46 | 0.46 | 0 |
| VMC DF sans échangeur <= 2012 | 1.65 | 1.65 | 0 |
| VMC DF sans échangeur apres 2012 | 1.32 | 1.32 | 0 |
| Ventilation naturelle par conduit | 2.23 | 0 | 4 |
| Ventilation hybride < 2001 | 1.52 | 0 | 3 |
| Ventilation hybride de 2001 a 2012 | 1.33 | 0 | 3 |
| Ventilation hybride apres 2012 | 1.17 | 0 | 3 |
| Ventilation hybride avec entrees d'air hygro < 2001 | 1.52 | 0 | 2 |
| Ventilation hybride avec entrees d'air hygro de 2001 a 2012 | 1.33 | 0 | 2 |
| Ventilation hybride avec entrees d'air hygro apres 2012 | 1.17 | 0 | 2 |
| Ventilation mecanique sur conduit existant < 2012 | 2.24 | 0 | 4 |
| Ventilation mecanique sur conduit existant apres 2012 | 1.97 | 0 | 4 |
| Ventilation naturelle par conduit avec entrées d'air hygro | 2.23 | 0 | 3 |
| Puits climatique sans échangeur < 2012 | 0.99 | 0.99 | 0 |
| Puits climatique sans échangeur apres 2012 | 0.79 | 0.79 | 0 |
| Puits climatique avec échangeur <= 2012 | 0.36 | 0.36 | 0 |
| Puits climatique avec échangeur apres 2012 | 0.16 | 0.16 | 0 |

### Cas des VMC par insufflation

Les VMC par insufflation sont traitées comme des VMC simple flux autoreglables et avec les mêmes caractéristiques selon les années d'installation.

### Cas des puits climatiques

Le puits climatique est considéré comme une VMC double flux faisant recircler dans le logement de l'air à une température proche de celle du sol.

Par hypothese la température moyenne en sortie de puits canadien est de 12°C. La température moyenne extérieure d'Octobre a Avril est de 8°C.

La modélisation du puits climatique est donc comparable a celle d'une VMC double flux avec une correction sur les températures : *P correction = Tbase-12 / Tbase-8 = 0.6 applicable pour obtenir les valeurs pertinentes dans le tableau.*

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Section** : 4 (pages 37-39)
