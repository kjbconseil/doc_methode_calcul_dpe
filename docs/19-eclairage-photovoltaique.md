# 16. Calcul de la consommation d'éclairage et de la production d'électricité

## 16.1 Consommation d'éclairage (Cecl)

La consommation d'éclairage est forfaitaire dans les bâtiments d'habitation. La puissance d'éclairage conventionnelle est prise égale a **1.4 W/m²**.

### Formule

Consommation d'éclairage conventionnelle (kWh/m²/an) :

```
Cecl = SUM(Cecl_j)
```

```
Cecl_j = C * Pecl * Nh_j / 1000
```

Avec :
- `C` : coefficient correspondant au taux d'utilisation de l'éclairage en l'absence d'éclairage naturel. Il prend la valeur de **0.9** pour une commande de l'éclairage par interrupteur (considéré dans les logements)
- `Pecl` : puissance d'éclairage conventionnelle, égale a **1.4 W/m²**
- `Nh_j` : nombre d'heures de fonctionnement de l'éclairage sur le mois j (h)

### Nombre moyen d'heures d'éclairage par jour par mois et zone climatique

| Mois | H1a | H1b | H1c | H2a | H2b | H2c | H2d | H3 |
|------|-----|-----|-----|-----|-----|-----|-----|-----|
| Janvier | 7 | 6 | 6 | 7 | 7 | 6 | 6 | 6 |
| Février | 6 | 6 | 5 | 6 | 6 | 5 | 5 | 5 |
| Mars | 5 | 5 | 5 | 5 | 5 | 4 | 4 | 4 |
| Avril | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 |
| Mai | 2 | 2 | 2 | 2 | 2 | 2 | 2 | 2 |
| Juin | 1 | 1 | 1 | 1 | 1 | 1 | 2 | 2 |
| Juillet | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| Aout | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| Septembre | 4 | 4 | 4 | 4 | 4 | 4 | 3 | 3 |
| Octobre | 6 | 6 | 6 | 6 | 6 | 6 | 5 | 5 |
| Novembre | 6 | 6 | 6 | 6 | 6 | 6 | 5 | 5 |
| Décembre | 7 | 7 | 7 | 7 | 7 | 7 | 6 | 6 |
| **Total** | 51 | 49 | 50 | 51 | 51 | 53 | 51 | 51 |



## 16.2 Production d'électricité

Seule la production d'électricité renouvelable par des capteurs photovoltaiques est prise en compte. Cependant, la présence de production d'électricité eolienne ou par cogeneration devra être mentionnee.

### Formule

La production d'électricité par des capteurs photovoltaiques Ppv (en kWh/m²/an) s'exprimé de la manière suivante :

```
Ppv = SUM(Ppv_j)
```

```
Ppv_j = SUM(N_m * Scapteurs_m * r * Ppv_j * C * I_c) / Sh
```

Avec :
| Variable | Description |
|----------|-------------|
| `Scapteurs_m` | Surface des panneaux photovoltaiques i orientées et inclines de la même manière (m²). Si la surface des panneaux n'est pas connue et ne peut être mesurée : `Scapteurs_m = 1.6 * Nbm` |
| `1.6` | Surface par défaut d'un module photovoltaique (m²) |
| `Nbm` | Nombre de modules |
| `r` | Rendement moyen des modules = **17%** |
| `I_(c,j)` | Ensoleillement en kWh/m² pour le mois j (voir partie 18.2) |
| `C` | Coefficient de perte = **0.86** |
| `I_c` | Coefficient de pondération prenant en compte l'alteration par rapport à l'orientation optimale (180° au Sud) des panneaux photovoltaiques |

### Coefficient d'inclinaison des panneaux photovoltaiques

| Orientation | Inclinaison par rapport à l'horizontal | | | | |
|------------|---|---|---|---|---|
| | <= 15° | 15° <= 45° | 45° <= 75° | >= 75° |
| Est | 1 | 0.96 | 0.84 | 0.79 |
| Sud-Est | 1 | 1.03 | 0.94 | 0.71 |
| Sud | 1 | 1.07 | 0.97 | 0.73 |
| Sud-Ouest | 1 | 1.03 | 0.94 | 0.71 |
| Ouest | 1 | 0.96 | 0.83 | 0.59 |

### Part d'énergie photovoltaique autoconsommee

De façon forfaitaire, une part de la production de photovoltaique est considérée autoconsommee. Cette production d'électricité autoconsommee est déduite de la consommation d'énergie finale électrique utilisée pour le calcul des émissions énergétiques et gaz à effet de serre.

La part d'énergie photovoltaique autoconsommee annuellement est déterminée de la façon suivante :

```
Celec_ac = Celec_tot - Tap
```

Avec :
- `Celec_ac` : électricité photovoltaique autoconsommee (kWhe/(m².an))
- `Celec_tot` : consommation totale annuelle d'électricité pour les 5 usages reglementaires et les usages mobiliers (kWhe/(m².an)) (tous or desirees)
- `Tap` : taux d'autoproduction, correspondant au rapport entre la production d'électricité autoconsommee et la consommation d'énergie (tous usages) du bâtiment (%)

```
Tap = 1 / (Tce + Tapl)
```

- `Tce` : taux de couverture, correspondant au ratio entre la production totale du site et la consommation annuelle (tous usages) (%)
- `Ppv` : production totale d'électricité photovoltaique (kWhe/(m².an))
- `Tapl` : coefficient de calage representant le taux d'autoproduction maximum pouvant être atteint lorsque la production d'électricité renouvelable augmente

```
Tapl = SUM(Tapl_j * Celec_tot_j) / Celec_tot
```

### Repartition de l'électricité autoconsommee par usage

| Usage de l'électricité i | Tapl_j |
|-------------------------|--------|
| Chauffage | 0.03 |
| Refroidissement | 0.25 |
| ECS | 0.09 |
| Éclairage | 0.50 |
| Auxiliaires de ventilation | 0.50 |
| Auxiliaires de distribution | 0.10 |
| Autres usages | 0.45 |

Si un usage n'est pas électrique : `Tapl_j = 0`

L'électricité « autoconsommee » Celec_ac est repartie conventionnellement par usage de l'électricité : au prorata des valeurs Tapl_j et Celec_tot_j :

```
Celec_ac_j = Celec_ac * (Tapl_j * Celec_tot_j) / (Tapl * Celec_tot)
```

### Consommations des autres usages

| | Cum (kWhe/(m².an)) |
|---|---|
| Maison individuelle | 19 |
| Immeuble collectif | 27 |

**En maison individuelle** : Ccom_ecl = 0
**En immeuble collectif** : Ccom_ecl = 1.1 kWhe/(m².an)

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 16 a 16.2 (pages 100-103)
