# 13. Rendement de génération des générateurs à combustion

## 13.1 Inserts et poeles

### Données d'entrée

- Type de générateur
- Type de cascade
- Présence d'une régulation
- Type d'émetteur
- Type de combustible bois

### Rendements Rg des inserts et poeles

| Type de générateur | Rg |
|-------------------|-----|
| Cuisiniere, Foyer ferme, Poele buche, insert installé avant 1990 | 0.5 |
| Cuisiniere, Foyer ferme, Poele buche, insert installé entre 1990 et 2004 | 0.60 |
| Cuisiniere, Foyer ferme, Poele buche, insert installé à partir de 2005 sans label flamme verte | 0.65 |
| Cuisiniere, Foyer ferme, Poele buche, insert installé de 2005 a 2009 avec label flamme verte | 0.65 |
| Cuisiniere, Foyer ferme, Poele buche, insert installé de 2007 a 2017 avec label flamme verte | 0.70 |
| Cuisiniere, Foyer ferme, Poele buche, insert installé à partir de 2018 avec label flamme verte | 0.75 |
| Poele a granules installé avant 2012 ou sans label flamme verte | 0.8 |
| Poele a granules flamme verte installé entre 2012 et 2019 | 0.85 |
| Poele a granules flamme verte installé à partir de 2020 | 0.87 |
| Poele fioul GPL ou charbon | 0.72 |

Les poeles a bois bouilleur installées à partir de 2012 sont traités comme des chaudières bois installées entre 2004 et 2012.



## 13.2 Chaudières et autres générateurs à combustion

### Données d'entrée

- Type de générateur
- Nombre de générateurs
- Departement
- Type de cascade
- Puissance nominale générateur (kW)
- Présence d'une régulation
- Type d'émetteur
- Année d'installation des émetteurs
- Type de combustible bois
- Rendement à pleine charge
- Rendement a charge intermédiaire
- Type de bruleur

### 13.2.1 Profil de charge des générateurs

Le profil de charge conventionnel donné pour chaque intervalle de taux de charge le coefficient de pondération correspondant.

#### Profil de charge conventionnel

| Taux de charge Tch_j | De 0% a 10% | De 10% a 20% | De 20% a 30% | De 30% a 40% | De 40% a 50% | De 50% a 60% | De 60% a 70% | De 70% a 80% | De 80% a 90% | De 90% a 100% |
|----------------------|-------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|--------------|---------------|
| Coeff_pond_j | 0.1 | 0.25 | 0.2 | 0.15 | 0.1 | 0.1 | 0.05 | 0.025 | 0.025 | 0 |

Ce profil de charge est donné sur une période de chauffé et non mensuellement. Le calcul du rendement de génération se fera donc sur toute la saison de chauffé et non mensuellement.

Pour les calculs les taux de charge sont pris en milieux de classe (5%, 15%, 25%, ..., 85%, 95%).

Le coefficient de pondération Coeff_pond_j est associé au taux de charge Tch_j, qui correspond à l'intervalle [Tch_j - 5%; Tch_j + 5%].

### 13.2.1.2 Présence de N générateurs à combustion indépendants

Les taux de charge doivent être pondérés par un coefficient Cdimref qui permet de prendre en compte les charges partielles.

**Pour un seul générateur à combustion de puissance installée Pn_inst** :

```
Cdimref = 1000 * Pn_inst / (GV * (19 - Tbase))
```

**Pour N générateurs à combustion** :

```
Cdimref = 1000 * (Pn_inst_1 + Pn_inst_2 + ... + Pn_inst_N) / (GV * (19 - Tbase))
```

Avec :
- `Pn_inst` : puissance installée de générateur à combustion (kW)
- `GV` : déperditions totales du bâtiment (W/K)
- `Tbase` : température extérieure de base (°C)

Le coefficient Coeff_pond_j est alors affecte au taux de charge Tch_j_dim_syst et aura :

```
Coeff_pond_j_dim_syst = Coeff_pond_j
```

```
Tch_j_dim = Min(Tch_j / Cdimref, 1)
```

Si Pn/GV > 1, alors sous-dimensionnement de l'installation.

### 13.2.1.3 Cascade de deux générateurs à combustion

La répartition de la puissance relative du générateur i est :

```
Prel(gen_1) = Pn(gen_1) / (Pn(gen_1) + Pn(gen_2))
Prel(gen_2) = Pn(gen_2) / (Pn(gen_1) + Pn(gen_2))
```

#### 13.2.1.3.1 Cascade avec priorite

Le générateur 1 sera le plus performant ou a défaut le plus puissant. Il sera considéré comme prioritaire si aucune information complementaire n'est disponible.

```
CTch_dim_syst(gen_1) = min(Prel(gen_1), Tch_dim_syst)
CTch_dim_syst(gen_2) = min(Prel(gen_2), Tch_dim_syst - CTch_dim_syst(gen_1))
```

Avec le taux de charge final suivant :

```
Tch_j_final(gen_1) = min(CTch_dim_syst(gen_1) / Prel(gen_1))
Tch_j_final(gen_2) = min(1, CTch_dim_syst(gen_2) / Prel(gen_2))
```

#### 13.2.1.3.2 Cascade sans priorite (même contribution au taux de charge)

```
CTch_dim_syst(gen_1) = Prel(gen_1) * Tch_dim_syst
CTch_dim_syst(gen_2) = Prel(gen_2) * Tch_dim_syst
```

### 13.2.1.4 Pertes au point de fonctionnement

- `Qp_j` (kW) : pertes au point de fonctionnement « e » (taux de charge e = Tch_j_final)
- `Qp_0` : pertes à l'arret (kW)
- `Rpn et Rpint` : respectivement les rendements à pleine charge et a charge intermédiaire
- `Pn` : puissance nominale du générateur (kW)

### Coefficient de conversion PCI/PCS

| Energies | Coefficient de conversion k(PCI/PCS) |
|---------|------|
| Électricité | 1 |
| Gaz naturel | 1.11 |
| GPL | 1.09 |
| Fioul | 1.07 |
| Bois | 1.08 |
| RCU | 1 |
| Charbon | 1.04 |

### 13.2.1.5 Chaudières basse température et condensation

Pour les chaudières basse température et condensation, le point de fonctionnement correspond à un fonctionnement a 15% de charge.

**Entre 0 et 15% de charge** :
```
Qp_e = (|Qp_100 - 0.15 * Qp_0| * e) / 0.15 + 0.15 * Qp_0
```

**Entre 15 et 30% de charge** :
```
Qp_e = (|Qp_100 - Qp_30| * e) / 0.3 + Qp_30 - Qp_100
Qp_30 = 0.3 * Pn * (100 - Rpint) / Rpint
Qp_100 = Pn * (100 - Rpn) / Rpn
```

**Entre 30 et 100% de charge** :
```
Qp_e = (|Qp_100 - Qp_30| * e + 0.3) / 2
```

**Pour les chaudières basse température** (avec régulation) :
```
Qp_30 = 0.3 * Pn * (100 - (R_pint + 0.1 * (40 - T/onc_30))) / (R_pint + 0.1 * (40 - T/onc_30))
Qp_100 = Pn * (100 - (R_pn + 0.1 * (70 - T/onc_100))) / (R_pn + 0.1 * (70 - T/onc_100))
```

**Pour les chaudières à condensation** (avec régulation) :
```
Qp_30 = 0.3 * Pn * (100 - (R_pint + 0.2 * (33 - T/onc_30))) / (R_pint + 0.2 * (33 - T/onc_30))
Qp_100 = Pn * (100 - (R_pn + 0.1 * (70 - T/onc_100))) / (R_pn + 0.1 * (70 - T/onc_100))
```

### Temperatures de fonctionnement Tfonc_100 et Tfonc_30

`Tfonc_100` (°C) est la température de fonctionnement de la chaudière a 100% de charge. Elle est donnée dans les tableaux suivants en fonction des types d'émetteur et des différentes périodes de leur installation :

**Chaudières à condensation** :

| Temperature de distribution / Type d'émetteur | Avant 1981 | Entre 1981 et 2000 | Apres 2000 |
|----------------------------------------------|-----------|-------------------|-----------|
| Basse / Plancher basse température | 60 | 35 | 35 |
| Moyenne / Radiateur à chaleur douce | 80 | 70 | 60 |
| Haute / Autres émetteurs | 80 | 70 | 70 |

**Chaudières basse température** :

| Temperature de distribution / Type d'émetteur | Avant 1981 | Entre 1981 et 2000 | Apres 2000 |
|----------------------------------------------|-----------|-------------------|-----------|
| Basse / Plancher basse température | 32 | 24.5 | 24.5 |
| Moyenne / Radiateur à chaleur douce | 38 | 35 | 32 |
| Haute / Autres émetteurs | 38 | 35 | 35 |

`Tfonc_30` (°C) : température de fonctionnement de la chaudière a 30% de charge, selon le type d'installation :

**Pour une chaudière standard jusqu'en 1990** :

| Temperature de distribution / Type d'émetteur | Avant 1981 | Entre 1981 et 2000 | Apres 2000 |
|----------------------------------------------|-----------|-------------------|-----------|
| Basse / Plancher basse température | 53 | 50 | 50 |
| Moyenne / Radiateur à chaleur douce | 59 | 56 | 53 |
| Haute / Autres émetteurs | 59 | 56 | 56 |

**Pour une chaudière standard depuis 1991** :

| Temperature de distribution / Type d'émetteur | Avant 1981 | Entre 1981 et 2000 | Apres 2000 |
|----------------------------------------------|-----------|-------------------|-----------|
| Basse / Plancher basse température | 49.5 | 45 | 45 |
| Moyenne / Radiateur à chaleur douce | 53.5 | 52.5 | 49.5 |
| Haute / Autres émetteurs | 55.5 | 52.5 | 52.5 |

### 13.2.2 Valeurs par défaut des chaudières gaz et fioul

Les tableaux donnent les valeurs par défaut des Rpn, Rpint et Qp0 en fonction du type, de l'anciennete et de la puissance nominale.

(Tableaux détaillés pages 85 - voir le document source pour les valeurs exactes par type)

### 13.2.2.1 Générateurs d'air chaud

**Entre 0 et 50% de charge** :
```
Qp_e = (|Qp_100 - 0.15 * Qp_0| * e) / 0.5 + 0.15 * Qp_0
```

**Entre 50 et 100% de charge** :
```
Qp_e = (|Qp_100 - Qp_50| * e) / 0.5 + 2 * Qp_50 - Qp_100
Qp_50 = 0.5 * Pn * (100 - R_pint) / R_pint
Qp_100 = Pn * (100 - R_pn) / R_pn
```

```
Pn * (1.75 - 0.55 * Log(Pn))
```

**Rendements par défaut** :
- Si les équipements sont **anciens (avant 2006)** : R_pn = 77%, R_pint = 74%
- Si les équipements sont **neufs (a partir de 2006)** :
  - Pour un générateur standard : R_pn = 84%, R_pint = 77%
  - Pour un générateur à condensation : R_pn = 90%, R_pint = 83%

### 13.2.2.3 Chaudières bois

Les chaudières au charbon sont traitées comme des chaudières bois buche.

Le point de fonctionnement w des chaudières bois correspond a 50% de charge.

**Entre 0 et 50% de charge** :
```
Qp_e = (|Qp_100 - 0.15 * Qp_0| * e) / 0.5 + 0.15 * Qp_0
```

**Entre 50 et 100% de charge** :
```
Qp_e = (|Qp_100 - Qp_50| * e) / 0.5 + 2 * Qp_50 - Qp_100
Qp_50 = 0.5 * Pn * (100 - R_pint) / R_pint
Qp_100 = Pn * (100 - R_pn) / R_pn
```

(Tableaux détaillés des rendements par type de chaudière bois, par anciennete et puissance - voir page 88)

### 13.2.2.4 Calcul des puissances nominales

Lorsque les puissances des générateurs à combustion individuels ne sont pas connues et pour les recommandations :

```
Pch = (1.2 * GV * (19 - Tbase)) / (1000 * 0.95²)
```

Avec :
- `Pch` : puissance nominale du générateur pour le chauffage (kW)
- `Tbase` : température extérieure de base selon la zone climatique et l'altitude (°C) (voir paragraphe 18.1)
- `GV` : déperditions à travers l'enveloppe et par renouvellement d'air (W/K)

La puissance nécessaire pour la production d'eau chaude sanitaire (Pecs) depend du type de production et du volume de stockage :

| Type de production d'ECS | Volume de stockage (l) | Puissance de dimensionnement (kW) |
|--------------------------|----------------------|----------------------------------|
| Instantanee | Vs = 0 | Pecs = 21 |
| Semi-instantanee | 0 < Vs <= 20 | Pecs = 21 - (18 * Vs) |
| Semi-accumulation | 20 < Vs <= 150 | Pecs = 5 - 1.751 + ... |
| Accumulation | 150 + Vs | Pecs = ... |

La puissance de dimensionnement du générateur est :
```
Pdim = max(Pch, Pecs)
```

### 13.2.3 Puissances moyennes fournies et consommees

Le rendement conventionnel annuel moyen de génération de chauffage est :

```
Rg(ch_PCI) = Pmfou / (Pmcons + 0.45 * Qp_0 + Pveil)
```

Avec :
- `Pveil` : puissance de la veilleuse (kW)
- `Qp_0` : Pertes à l'arret (kW)

Pour le calcul des consommations, la conversion en PCI du rendement donné :

```
Rg(ch_PCI) = k(PCI/PCS) * Rg(ch_PCS)
```

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 13 a 13.2 (pages 77-90)
