# 17. DPE dans le collectif

## 17.1 Génération d'un DPE à l'immeuble collectif d'habitation

### 17.1.1 Collecte des données d'entrée

#### 17.1.1.1 Règles d'échantillonnage

La réalisation d'un DPE sur un immeuble collectif d'habitation necessite la visite de l'ensemble des logements du bâtiment pour la détermination des caractéristiques des installations dans chaque logement.

A défaut de pouvoir visiter l'ensemble des appartements, le diagnostiqueur etablit le DPE de l'immeuble sur la base de la visite d'un échantillon de logements. La description de l'enveloppe et des équipements au niveau de l'immeuble sera obtenue par extrapolation à partir des données relevees dans l'échantillon.

**Règles obligatoires de visite** (au minimum) :
- Un logement de chaque typologie (T1, T2, T3...)
- Un logement sur chaque type de plancher (sous-sol, dalle, vide sanitaire, terre-plein...)
- Un logement en étage intermédiaire
- Un logement sous toiture (comble, terrasse, rampant, toiture...)

**Règles de taille d'échantillon** :
- Pour un immeuble de 11 a 100 logements : au minimum un nombre de logements supérieur ou égal a 10% du nombre total d'appartements de l'immeuble
- Pour un immeuble de plus de 100 logements : au minimum 10 logements, et un nombre de logements supérieur ou égal a 5% du nombre total d'appartements de l'immeuble

#### 17.1.1.2 Cas particulier : immeuble gere de manière homogène

On entend par immeuble gere de manière homogène :
- Un immeuble appartenant à un propriétaire unique attestant de la présence de systèmes (installations de chauffage, de refroidissement, de production d'ECS et de ventilation) et menuiseries similaires dans l'ensemble des logements
- La puissance des équipements ne fait pas partie du critère d'homogeneite

#### 17.1.1.3 Caracterisation des espaces communs en volume chauffé ou non chauffe

Pour caracteriser les espaces communs (couloirs, escaliers...) en volume chauffé ou en volume non chauffé, les règles suivantes doivent être appliquees :

- Tout d'abord, un « volume intérieur » est un local horizontal ou vertical, depourvu de parois donnant sur l'extérieur à l'exception de celles ayant le même niveau d'isolation que les parois du même type du bâtiment et dont la liaison donnant sur l'extérieur ou sur des locaux non chauffés (n>8) est inférieure a celui donnant sur des locaux chauffés (ratio)
- Consideres comme chauffes, les « volumes interieurs » qui ne possedent pas d'ouvertures permanentes sur l'extérieur (trappe, gaine de désenfumage) et dont les acces vers l'extérieur et vers des locaux non chauffés ou a occupation discontinue sont respectivement munis de sas et de dispositifs de fermeture automatique, ainsi que les espaces equipes d'émetteurs
- Consideres comme non chauffes, les « volumes interieurs » ne repondant pas au moins à une des conditions ci-dessus

### 17.1.2 Définition d'un appartement "moyen"

```
Sref(moy) = Sref / Nb_log
```

Avec :
- `Sref` : surface de référence totale de l'immeuble (m²)
- `Nb_log` : nombre de logements de l'immeuble

Les appartements « moyens » equipes d'un même type d'installation sont appeles sous-ensemble de l'immeuble. L'appartement peut donc appartenir a plusieurs sous-ensembles selon l'installation considérée.

A chaque appartement « moyen », on associé les caractéristiques du type de système observe, puis sur le nombre d'appartements de l'échantillon equipes de ce type de système :

```
Pn(moy_systeme) = SUM(Pn(systeme_appartement) * Sref(systeme_appartement)) / SUM(Sref(systeme_appartement))
```



## 17.2 Génération d'un DPE à l'appartement

### 17.2.1 Génération d'un DPE à l'appartement

#### 17.2.1.1 Calcul des consommations de chauffage, de refroidissement, d'ECS et d'auxiliaires

Le calcul des besoins de chauffage, de refroidissement et d'ECS s'effectue toujours à l'échelle de l'appartement.

Le calcul du besoin de chauffage s'appuie sur l'enveloppe de l'appartement, en considerant ou non les espaces communs comme des espaces chauffes.

**Traitement des usages individuels** :

En cas de système individuel de chauffage, refroidissement et/ou d'ECS, le calcul des consommations est realise à partir du besoin de l'appartement et des caractéristiques du système individuel, selon la méthode developpee dans les chapitres précédents.

**Traitement des usages collectifs** :

En cas de système collectif de chauffage, de refroidissement et/ou d'ECS, les deux cas suivants sont a distinguer :
- Dans le cas des générateurs autres qu'a combustion, les consommations de l'appartement sont calculées à partir des caractéristiques du générateur de l'immeuble (effet joule, PAC, réseau de chaleur)
- Dans le cas des générateurs à combustion, les consommations de l'appartement sont calculées en considerant un générateur individuel virtuel, appele « générateur équivalent », identique au générateur collectif mais avec des caractéristiques pondérés par le rapport de la surface de référence de l'appartement a celle de l'immeuble

#### Tableau des equivalences installation individuelle vs collective

| Caractéristiques de l'installation individuelle équivalente | Valeur |
|---|---|
| Puissance nominale Pn | = x * Pn du générateur collectif |
| Rendement à pleine charge Rpn | = Rpn du générateur collectif |
| Rendement a charge intermédiaire Rpint | = Rpint du générateur collectif |
| Puissance de la veilleuse Pveil | = x * Pveil du générateur collectif |
| Pertes à l'arret QPO | Calcul à partir de la puissance nominale Pn du générateur équivalente |
| Pertes de stockage du ballon d'ECS Q(p_stk) | = x * Q(p_stk) du ballon d'ECS collectif |
| Rendement de génération Rg | Calcul à partir des caractéristiques de l'installation individuelle équivalente |
| Rendement d'émission Re | Re de l'installation collective |
| Rendement de régulation Rr | = Rr de l'installation collective |
| Rendement de distribution Rd | = Rd de l'installation collective |
| Intermittence INT | = INT de l'installation collective |
| Consommation des auxiliaires de génération | Calcul à partir des puissances nominales Pn et des puissances des auxiliaires de génération de chauffage (ou ECS) de l'appartement |
| Consommation des auxiliaires de distribution de chauffage | = x * consommation des auxiliaires de distribution de chauffage calculée à l'échelle de l'immeuble |
| Consommation des auxiliaires de distribution d'ECS | Calculee à l'immeuble avec le besoin d'ECS de l'appartement |



### 17.2.2 Génération des DPE des appartements à partir des données de l'immeuble

#### 17.2.2.1 Détermination de la méthode applicable

Les modalites de calcul des consommations de chauffage et des consommations d'ECS des appartements sont déterminées selon l'arbre de decision suivant :

**Pour la consommation de chauffage** :
- **Méthode 1** : Repartition des consommations de chauffage de l'immeuble au prorata de la surface de référence
- **Méthode 2** : Repartition des consommations de l'immeuble en fonction du besoin de chauffage et de la part d'individualisation des frais de chauffage

**Pour la consommation d'ECS** :
- **Méthode 1** : Repartition des consommations d'ECS entre les appartements au prorata du besoin d'ECS
- **Méthode 2** : Calcul des consommations de chaque appartement avec attribution d'un système « par défaut » pour les appartements non visites (le système le moins performant de ceux observes dans l'échantillon)

#### 17.2.2.2 Chauffage collectif avec individualisation des frais (Méthode 2)

```
Cch_ap_j = (1 - coef_FC) * (Sref_ap_j / Sref) * Cch + coef_FC * Cle_ap_j * Cch
```

```
Caux_ch_ap_j = (1 - coef_FC) * (Sref_ap_j / Sref) * Caux_ch + coef_FC * Cle_ap_j * Caux_ch
```

Avec :
- `Sref_ap_j` : surface de référence de l'appartement j
- `Sref` : surface de référence totale de l'immeuble
- `Cch` : consommation annuelle totale de chauffage de l'immeuble
- `Caux_ch` : consommation annuelle des auxiliaires de chauffage totale de l'immeuble
- `coef_FC` : coefficient d'individualisation des frais de chauffage
- `Cle_ap_j` : clé de répartition

En cas de chauffage individuel : **coef_FC = 1**

**Cle de répartition** basee sur le besoin de chauffage (Cle_ap_j) :

```
Cle_ap_j = Bch_ap_j / SUM(Bch_ap_j)
```



### 17.3 Chauffage collectif alimentant plusieurs immeubles

Pour un groupe d'immeubles alimentes par une installation collective unique, l'installation de chauffage est traitée comme un réseau de chaleur local.

### 17.4 Immeuble collectif mixte

Le besoin de chauffage des locaux tertiaires sera calculé de la même manière que pour les logements.

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 17 a 17.4 (pages 104-116)
