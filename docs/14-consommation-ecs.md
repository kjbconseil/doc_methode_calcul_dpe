# 11. Calcul de la consommation d'ECS (Cecs)

## Données d'entrée

- Temperature d'eau froide
- Type de bâtiment
- Surface de référence
- Nombre de logements d'un immeuble collectif

## 11.1 Calcul du besoin d'ECS

Les besoins journaliers moyens par personne (adulte équivalent) sur une année sont en moyenne de 56 a 73 litres a 40°C. Le scenario d'utilisation conventionnel du DPE s'appuie sur un comportement conventionnel, qui correspond à une consommation de 56 l/j/pers d'eau chaude a 40°C, contre 73 l/j/pers pour un comportement dépasseur. Cela correspond environ à une variation du besoin de +40% entre le profil conventionnel de consommation et le profil dépasseur.

On considéré conventionnellement que le logement est inoccupe 7 jours par an (du 24 au 30 décembre inclus).

### Nombre d'adultes équivalents N_adeq

#### Logements individuels

On definit la surface de référence moyenne d'un logement (m²) comme suit :

```
Sref_moy = Sref / Nb_log
```

Avec :
- `Sref` : surface de référence totale de la maison individuelle (m²)
- `Nb_log` : nombre de logements (= 1 pour le traitement d'une maison individuelle contenant un seul logement)

Calcul du coefficient d'occupation maximal N_max :

- Si `Sref_moy < 30m²` :
  ```
  N_max = 1
  ```
- Si `30m² <= Sref_moy <= 70m²` :
  ```
  N_max = 1.75 - 0.01875 * (70 - Sref_moy)
  ```
- Si `Sref_moy >= 70m²` :
  ```
  N_max = 0.025 * Sref_moy
  ```

Calcul du nombre d'adultes équivalent N_adeq :

- Si `N_max <= 1.75` :
  ```
  N_adeq = Nb_log * N_max
  ```
- Si `N_max > 1.75` :
  ```
  N_adeq = Nb_log * (1.75 + 0.3 * (N_max - 1.75))
  ```

#### Logements collectifs

On definit la surface de référence moyenne d'un logement (m²) comme suit :

```
Sref_moy = Sref / Nb_log
```

Avec :
- `Sref` : surface de référence totale de l'immeuble (m²)
- `Nb_log` : nombre de logements (>= 1 pour le traitement d'un appartement)

Cette surface moyenne permet de déterminer le N_max pour un logement moyen :

- Si `Sref_moy < 10m²` :
  ```
  N_max = 1
  ```
- Si `10m² <= Sref_moy <= 50m²` :
  ```
  N_max = 1.75 - 0.01875 * (50 - Sref_moy)
  ```
- Si `Sref_moy >= 50m²` :
  ```
  N_max = 0.035 * Sref_moy
  ```

Calcul du nombre d'adultes équivalent N_adeq :

- Si `N_max <= 1.75` :
  ```
  N_adeq = Nb_log * N_max
  ```
- Si `N_max > 1.75` :
  ```
  N_adeq = Nb_log * (1.75 + 0.3 * (N_max - 1.75))
  ```

### Besoin mensuel d'ECS (Becs_j)

La quantité de chaleur Becs_j (Wh) nécessaire sur le mois j pour preparer l'eau chaude sanitaire est obtenue selon la formule suivante :

**Pour un comportement conventionnel** :
```
Becs_j = 1.163 * N_adeq * 56 * (40 - T(ef_j)) * nj
```

**Pour un comportement dépasseur** :
```
Becs_j = 1.163 * N_adeq * 79 * (40 - T(ef_j)) * nj
```

Avec :
- `T(ef_j)` : température moyenne d'eau froide sanitaire sur le mois j (°C). La température d'eau froide est une donnée climatique mensuelle pour chacune des 8 zones climatiques (voir parties 18.2 et 18.3)
- `nj` : nombre de jours d'occupation sur le mois j

| Mois | nj |
|------|-----|
| Janvier | 31 |
| Février | 28 |
| Mars | 31 |
| Avril | 30 |
| Mai | 31 |
| Juin | 30 |
| Juillet | 31 |
| Aout | 31 |
| Septembre | 30 |
| Octobre | 31 |
| Novembre | 30 |
| Décembre* | 24 |

*Dans l'approche conventionnelle une absence d'une semaine est comptée en décembre.

### Besoin annuel

```
Becs = SUM(Becs_j)
```

## 11.2 Calcul des consommations d'ECS

### Données d'entrée

- Rendement de génération : Rg (sans dimension)
- Rendement de distribution : Rd (sans dimension)
- Rendement de stockage : Rs (sans dimension)
- Type d'installation d'ECS : avec ou sans solaire ; base + appoint...
- Puissance nominale des générateurs : Pn (W)

### Formule

La consommation annuelle d'eau chaude sanitaire Cecs (kWh PCI) s'exprimé de la manière suivante :

```
Cecs = Becs * Iecs
```

Avec :
- `Becs` : besoin annuel d'ECS (kWh)
- `Iecs` : inverse du rendement de l'installation :

```
Iecs = 1 / (Rs * Rd * Rg)
```

- `Rs` : rendement de stockage
- `Rd` : rendement de distribution
- `Rg` : rendement de génération

La consommation d'ECS sur un mois j peut être déduite de la consommation annuelle :

```
Cecs_j = (Becs_j / Becs) * Cecs
```

## 11.3 Un seul système d'ECS avec solaire

```
Cecs = Becs * (1 - Fecs) * Iecs
```

Avec :
- `Becs` : besoin en eau chaude sanitaire (kWh)
- `Fecs` : facteur de couverture solaire, déterminé à partir du tableau du paragraphe 18.4
- `Iecs` : inverse du produit des rendements

La production d'ECS solaire Prod(ecs_solaire) (kWh PCI) serait alors :

```
Prod(ecs_solaire) = Becs * Fecs * Iecs
```

## 11.4 Plusieurs systèmes d'ECS (limite a 2 systèmes différents par logement)

```
Cecs1 = 0.5 * Becs * Iecs1      Cecs2 = 0.5 * Becs * Iecs2
```

## 11.5 Rendement de distribution de l'ECS

### 11.5.1 Installation individuelle

| Rendement de distribution Rd | Production en volume habitable | |
|------------------------------|------|------|
| | Pieces alimentées contigues | Pieces alimentées non contigues |
| | 0.93 | 0.87 |
| Production hors volume habitable | 0.87 | 0.81 |

Les pieces considérées sont les salles de bain et les cuisines. S'il existe plusieurs salles de bain en plus de la cuisine, il faut vérifier leur contiguite verticale ou horizontale.

### 11.5.2 Installation collective

| Rendement de distribution Rd | Majorite des logements |
|------------------------------|---|
| | Pieces alimentées contigues | Pieces alimentées non contigues |
| Réseau collectif non isolé | 0.28 | 0.26 |
| Réseau collectif isolé sans tracage | 0.55 | 0.52 |
| Réseau collectif isolé avec tracage | | 0.81 |

## 11.6 Rendement de stockage de l'ECS

L'ensemble de ce paragraphe ne s'applique pas aux chauffe-eau thermodynamiques, traités en partie 14.2.

Le rendement de stockage est calculé annuellement.

S'il n'y a pas de stockage : `Q(p_stk) = 0`

### 11.6.1 Pertes de stockage des ballons d'accumulation

La présence d'un ballon de preparation de l'ECS est responsable de pertes de stockage (Q(stk) (Wh)) :

```
Q(stk) = 67662 * V^0.55
```

Avec :
- `Vs` : volume du ballon de stockage (litres)

### 11.6.2 Pertes des ballons électriques

```
Q(p_stk) = 8592 + (45/24) * Vs * Cr
```

Avec :
- `Vs` : volume du ballon de stockage (litres)
- `Cr` : coefficient de perte du ballon de stockage (Wh/(l.°C.jour))

| Coefficient de perte (Cr) | Volume du ballon (litres) | | | |
|--------------------------|---|---|---|---|
| | <= 100 | 100 < <= 200 | 200 < <= 300 | > 300 |
| Chauffe-eau horizontal | 0.39 | 0.33 | 0.3 | 0.3 |
| Chauffe-eau vertical (autre ou inconnu) | 0.32 | 0.23 | 0.22 | 0.22 |
| Chauffe-eau vertical (Catégorie B ou 2 étoiles) | 0.37 | 0.22 | 0.2 | 0.18 |
| Chauffe-eau vertical (Catégorie C ou 3 étoiles) | 0.25 | 0.2 | 0.18 | 0.16 |

### 11.6.3 Rendement de stockage Rs

**Pour les ballons électriques verticaux de catégorie C ou 3+** :
```
Rs = 1 / (1 + (Q(p_stk) * Rd) / Becs)
```

**Pour les autres ballons électriques** :
```
Rs = 1 / (1 + Q(p_stk) / (Rd * Becs))
```

Avec :
- `Q(p_stk)` : pertes de stockage (Wh)
- `Rd` : rendement de distribution
- `Becs` : besoin annuel d'ECS (Wh)

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 11 a 11.6 (pages 69-74)
