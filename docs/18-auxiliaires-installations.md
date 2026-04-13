# 15. Calcul des consommations d'auxiliaires des installations de chauffage, de refroidissement et d'ECS

## Formules principales

### Consommation des auxiliaires de chauffage

```
Caux_ch = Caux_gen_ch + Caux_dist_ch
```

Avec :
- `Caux_gen_ch` : consommation annuelle des auxiliaires de génération de l'installation de chauffage (Wh) : `Caux_gen_ch = Q(aux_g_ch)`
- `Q(aux_g_ch)` : consommation annuelle des auxiliaires de génération de l'installation de chauffage (Wh)
- `Caux_dist_ch` : consommation annuelle des auxiliaires de distribution de l'installation de chauffage (Wh)

### Consommation des auxiliaires d'ECS

```
Caux_ecs = Caux_gen_ecs + Caux_dist_ecs
```

Avec :
- `Caux_gen_ecs` : consommation annuelle de génération de l'installation d'ECS (Wh) : `Caux_gen_ecs = Q(aux_g_ecs)`
- `Q(aux_g_ecs)` : consommation annuelle de génération de l'installation d'ECS (kWh)
- `Caux_dist_ecs` : consommation annuelle des auxiliaires de distribution de l'installation d'ECS (Wh)
- `Caux_dist_ecs = Q(c,j) + Q(circ,j)`
- `Q(c,j)` : consommation annuelle du circulateur de bouclage (Wh)
- `Q(trac)` : consommation annuelle du traceur (Wh)

**Important** : Les consommations des auxiliaires de distribution de chauffage et d'ECS sont prises nulles pour les installations individuelles en l'absence de circulation externe au générateur.

### Consommation des auxiliaires de refroidissement

Pour les installations de refroidissement, les consommations de génération sont prises en compte dans le SEER (EER). Seules les consommations des auxiliaires de distribution sont donc a comptabiliser :

```
Caux_fr = Caux_dist_fr
```



## 15.1 Consommation des auxiliaires de génération

### Détermination des puissances par défaut des auxiliaires

```
P(aux_g) = G + H * P_n   (W)
```

Dans cette equation :
- Pour les chaudières gaz ou fioul : si P_n > 400 kW alors P_n = 400 kW
- Pour les générateurs d'air chaud : si P_n > 300 kW alors P_n = 300 kW
- Pour les chaudières bois : si P_n > 70 kW alors P_n = 70 kW

| Type de générateur | G (W) | H (W/kW) |
|-------------------|-------|---------|
| Chaudière au gaz ou au fioul | 20 | 1.6 |
| Chaudière bois atmospherique | 0 | 0 |
| Chaudière bois assistee par ventilateur | 73.3 | 10.5 |
| Générateur d'air chaud | 0 | 4 |
| Radiateur gaz | 40 | 0 |
| Chauffe eau gaz | 0 | 0 |
| Accumulateur gaz | 0 | 0 |

**Règles** :
- Les consommations de génération sont nulles dans les cas suivants (Q(aux_g) = 0) :
  - Pour les installations avec une production de chaleur (chauffage et/ou ECS) par PAC, les consommations des auxiliaires de génération sont prises en compte dans le SCOP (COP). Elles seront donc ignorees
  - Pour les installations avec une production de chaleur (chauffage et/ou ECS) par un réseau de chaleur urbain, les consommations des auxiliaires de génération sont prises conventionnellement nulles

### 15.1.1 Consommation des auxiliaires de génération de chauffage

La consommation annuelle des auxiliaires de génération Q(aux_g_ch) (kWh) est :

```
Q(aux_gen_ch) = (P(aux_g_ch) * Bch_g) / P(n_ch)
```

Avec :
- `P(n_ch)` : puissance nominale du générateur de l'installation de chauffage (W)
- `P(aux_g_ch)` : puissance des auxiliaires de génération de l'installation de chauffage (W)
- `Bch_g` : besoin d'énergie annuel assure par le générateur pour le chauffage (Wh)

### 15.1.2 Consommation des auxiliaires de génération d'ECS

```
Q(aux_gen_ecs) = (P(aux_g_ecs) * Becs_g) / P(n_ecs)
```



## 15.2 Consommation des auxiliaires de distribution

### 15.2.1 Puissance des circulateurs de chauffage et de refroidissement

Pertes de charge du réseau (kPa) :

```
delta_P(reseau) = 0.15 * Lres + delta_Pem
```

Avec :
- 0.115 kPa/m de pertes de charge linéaires
- `Lres` : longueur du réseau le plus defavorise (m)
- `delta_Pem` : la perte de charge de l'émetteur (kPa)

| Type d'émetteur | delta_Pem (kPa) | |
|----------------|---|---|
| | Chauffage | Refroidissement |
| Radiateurs | 30 si boucle monotube | Non applicable |
| | 10 sinon | |
| Plancher/plafond chauffant/refroidissant | 15 | 15 |
| Autres cas | 35 | 35 |

Calcul de la longueur du réseau le plus defavorise :

```
Lres = 5 + f_lm * Niv * sqrt(25 * Sh / Niv)
```

Avec :
- `Niv` : nombre de niveaux du bâtiment
- `Sh` : surface habitable du bâtiment (m²)
- `f_lm` :

| | f_lm | |
|---|---|---|
| Émetteur | Chauffage | Refroidissement |
| Plancher | 0.158 | 0.156 |
| Autre | 0.802 | 1 |

**Temperature nominale de dimensionnement** : delta_tm

| Temperature de distribution du chauffage | delta_tm |
|----------------------------------------|---------|
| Moyenne / Basse | 7.5°C |
| Haute | 15°C |

Pour le refroidissement, delta_tm = 4°C.

**Puissance nominale du circulateur en chauffage** (P_ci) :

```
P_ci = 10^-3 * (GV) * (20 - T_base) * ratio
```

**Puissance nominale du circulateur en froid** (P_cf) :

```
P_cf = 10^-3 * (GV) * (34 - 26) + 0.03 * Sh + 0.25 * Sfenv
```

Avec :
- `Sfenv` : Surface des fenêtres et portes-fenêtres

### 15.2.2 Consommation des auxiliaires de distribution de chauffage

```
Caux_dist_ch = P(circ_ch) * Nref
```

Avec :
- `P(circ_ch)` : puissance du circulateur de l'installation de chauffage (W)
- `Nref` : nombre d'heures annuel de chauffage (voir paragraphes 18.2 et 18.3)

### 15.2.3 Consommation des auxiliaires de distribution de froid

```
Caux_dist_fr = P(circ_fr) * Nref
```

### 15.2.4 Consommation des auxiliaires de distribution d'ECS

Les consommations des auxiliaires de distribution pour une installation d'ECS individuelle sont nulles.

Les pertes de distribution (kWh) sont données par :

```
Q(dis_indiv) = (0.5 * Lvc / Sh) * Becs
Q(dis_collect) = 0.112 * Becs
Q(dis_solaire) = 0.039 * Becs
```

Avec :
- `Lvc` : longueur du réseau d'ECS en volume chauffé (m)
- `Becs` : besoin annuel d'eau chaude sanitaire (Wh)

```
Lvc = 2 * (0.5 * Sh + Rd(ecs))
```

#### Prise en compte du bouclage pour l'ECS

Débit au depart de la boucle (m3/h) pour une chute de température de 5°C :

```
q(bc) = Q(dis) / 5815
```

Longueur par défaut du bouclage de l'ECS (en m) :

```
L_bl = 4 * sqrt(Sh / Niv) + 5 * (Niv - 0.5)
```

La perte de charge dans le bouclage (kPa) :
```
delta_Pb = 0.2 * L_bl + 10
```

La puissance hydraulique du bouclage (W) :
```
P_hydr = (q(bc) * delta_Pb) / 3.6
```

L'efficacité du circulateur est :
```
Eff(circ) = (q(bc)^0.77) / 15.3
```

La puissance électrique du circulateur (W) :
```
P(circ_b) = max(20, P_hydr / Eff(circ))
```

La consommation électrique des circulateurs sur une heure (Wh/h) :
```
Q(circ_b) = P(circ_b)
```

La consommation annuelle du circulateur de bouclage (Wh) :
```
Q(bc_b) = 8760 * P(circ_b)
```

#### Prise en compte du tracage pour l'ECS

La consommation annuelle du traceur (Wh) :
```
Q(trac) = 0.14 * Becs
```

Les auxiliaires des installations d'ECS solaire ne sont pas pris en compte.

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 15 a 15.2 (pages 94-99)
