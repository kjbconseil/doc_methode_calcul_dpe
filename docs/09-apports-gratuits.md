# 6. Détermination des apports gratuits

## 6.1 Calcul de F

### Données d'entrée

- Departement
- Altitude

### Définition

F_j est la fraction des besoins de chauffage du mois j couverts par les apports gratuits, elle s'exprimé en fonction de l'inertie du bâtiment :

La formule générale est :
- Si X_j != 1 : `F_j = (1 - X_j^a) / (1 - X_j^(a+1))`
- Si X_j = 1 : `F_j = a / (a + 1)`

| Inertie | Exposant a |
|---------|-----------|
| Lourde / Tres Lourde | a = 3.6 |
| Moyenne | a = 3.0 |
| Légère | a = 2.5 |

### Calcul de X_j

```
X_j = (Ai_j + As_j) / (GV * DH_j)
```

> **Attention** : si GV * DH_j = 0, alors F_j = 1 (pas de besoin de chauffage sur le mois j)

Avec :
- `GV` : déperditions de l'enveloppe en W/K (calculées dans la partie 3)
- `DH_j` : degrés heures de chauffage sur le mois j (°Ch), déterminés à partir des tableaux des paragraphes 18.2 et 18.3 :
  - DH19 pour une consigne de chauffage a 19°C (comportement conventionnel)
  - DH21 pour une consigne de chauffage a 21°C (comportement dépasseur)
- `Ai_j` : apports internes dans le logement sur le mois j (Wh)

### Calcul des apports internes Ai_j

Le fonctionnement permanent du fonctionnement lie à l'occupation, on considéré que la puissance de chaleur degagee par l'ensemble des équipements est conventionnellement de :
- **5.7 W/m²** en occupation hors période de sommeil
- **1.1 W/m²** en inoccupation et pendant le sommeil

Le scenario conventionnel d'occupation hebdomadaire des logements est le suivant :
- De 0h a 6h et de 17h a 24h avec une période de sommeil allant de 0h a 6h et de 22h a 24h (lu-ve/sa-di, mardi, jeudi et samedi matin)
- De 0h a 19h et de 1h a 24h avec une période de sommeil allant de 0h a 6h et de 22h a 24h le mercredi
- De 0h a 24h les samedis et dimanche avec une période de sommeil allant de 0h a 6h et de 22h a 24h

Soit sur une semaine :
- 113h d'occupation dont 54h de sommeil
- 55h d'inoccupation

Les apports internes moyens dus aux équipements sur une semaine type sont donc de **3.18 W/m²**.

A ces apports il faut ajouter :
- **Ceux de l'éclairage** : qui correspondent à une puissance moyenne de 1.4 W/m² en fonctionnement. Les apports d'éclairage sont des moyennes annuelles sur toutes les zones climatiques. Cette valeur est pondérée par le nombre d'heures moyen d'éclairage (voir paragraphe 16.1, sur l'année c'est-a-dire 2173 h soit P167)
  - Les apports moyens annuels d'éclairage correspondant donc a 1.4 * 2173/8760 = **0.36 W/m²**
- **Ceux des occupants** : on considéré un apport de chaleur de 90W par adulte équivalent (variable N_adeq déterminée au paragraphe 11.1). Le nombre d'adultes équivalents est calculé en fonction de la surface habitable. Les apports de chaleur dus aux occupants sont donc a N99 * N_adeq * 90/Sh

### Formule des apports internes en période de chauffe

Les apports internes sur le mois j (en Wh) en période de chauffé sont donc :

```
Ai_j = (3.18 + 0.34) * Sh + 90 * (172/168) * N_adeq * Nref_j
```

Avec :
- `Sh` : surface habitable du logement (m²)
- `N_adeq` : nombre d'adultes équivalents (voir paragraphe 11.1)
- `3.18` : apports internes moyens des équipements (W/m²)
- `0.34` : apports moyens annuels d'éclairage (W/m²) (= 1.4 * 2173/8760)
- `90` : apport de chaleur par adulte équivalent (W)
- `172/168` : ratio heures d'occupation / heures totales par semaine
- `Nref_j` : nombre d'heures de chauffage pour le mois j, déterminés à partir des tableaux des paragraphes 18.2 et 18.3
  - Nref (19°C) pour une consigne de chauffage a 19°C (comportement conventionnel)
  - Nref (21°C) pour une consigne de chauffage a 21°C (comportement dépasseur)

Pour une année complète, Nref est évalué seulement sur la saison de chauffé avec :

```
Nref = SUM(Nref_j)
```

### Apports solaires As_j

`As_j` : apports solaires sur le mois j durant la période de chauffé (Wh) :

```
As_j = 1000 * Sse_j * E_j
```

En présence d'une véranda ou autre espace solarisé non chauffé, si ces apports solaires s'ajoutent ceux à travers cet espace, le calcul des apports solaires à travers un espace solarisé non chauffé est decrit au paragraphe 6.3.

- `Sse_j` : surface transparente sud équivalente du logement, c'est-a-dire la surface de paroi, fictive, exposee au sud, totalement transparente et sans ombrage, qui procurerait les mêmes apports solaires que les parois du logement, pour le mois j (m²) (voir partie 6.2)
- `E_j` : ensoleillement recu, sur le mois j, par une paroi verticale orientée au sud en absence d'ombrage (kWh/m²)

### En période de refroidissement

De la même manière, les apports internes sur le mois j en période de refroidissement sont donc :

```
Ai_fr_j = (3.18 + 0.34) * Sh + 90 * (172/168) * N_adeq * Nref_j
```

Avec :
- `Nref_j` : nombre d'heures de chauffage pour le mois j, déterminé à partir des tableaux des paragraphes 18.2 et 18.3
  - Nref (28°C) pour une consigne de refroidissement a 28°C (comportement conventionnel)
  - Nref (26°C) pour une consigne de refroidissement a 26°C (comportement dépasseur)

Pour une année complète, Nref est évalué uniquement sur la saison de refroidissement avec :

```
Nref = SUM(Nref_j)
```

Les apports solaires sur le mois j (As_fr_j en Wh) durant la période de refroidissement sont :

```
As_fr_j = 1000 * Sse_j * E_j * fr_j
```

Avec :
- `I_j * N_j` : ensoleillement recu en période de refroidissement, sur le mois j, par une paroi verticale orientée au sud en absence d'ombrage (kWh/m²), déterminé à partir des tableaux des paragraphes 18.2 et 18.3
  - E_j N_j (19°C) pour une consigne de chauffage a 19°C (comportement conventionnel)
  - E_j N_j (21°C) pour une consigne de chauffage a 21°C (comportement dépasseur)

- `Sse_j` : Surface transparente sud équivalente = du logement en refroidissement pour le mois j (m²)



## 6.2 Détermination de la surface Sud équivalente

### Données d'entrée

- Inclinaison des baies (verticale, pente, horizontale)
- Orientation des baies (Nord, Sud, Est, Ouest)
- Position des baies en flanc de loggia
- Nature des menuiseries (bois, PVC...)
- Type de vitrage (Simple, double...)
- Positionnement de la menuiserie (tunnel, nu intérieur...)
- Type de masque
- Masques proches (balcon, loggia...)
- Masques lointains
- Profondeur des masques proches (profondeur balcon)
- Largeur des baies
- Positionnement des masques (Nord, Sud...)
- Angle de vue des masques lointains

### Formule

La prise en compte des apports solaires exige à minima une valeur par facade des fenêtres du bâtiment. Le calcul de la surface sud équivalente se fait en sommant les valeurs de Sse pour chaque paroi vitree :

```
Sse_j = SUM(A_i * Sw_i * Sw_i * Fe_i * C1_(i,j))
```

Avec :
- `A_i` : surface de la baie i (m²)
- `Sw_i` : proportion d'énergie solaire incidente qui penetre dans le logement par la paroi vitree i
- `Fe_i` : facteur d'ensoleillement, qui traduit la réduction d'énergie solaire recue par une paroi vitree du fait des masques
- `C1_(i,j)` : coefficient d'orientation et d'inclinaison pour la paroi vitree i pour le mois j, voir paragraphe 18.5

La surface vitree des portes n'est pas prise en compte dans le calcul de Sse_j.

### 6.2.1 Détermination du facteur solaire Sw

La proportion d'énergie solaire incidente qui penetre dans le logement à travers une paroi est donnée par :

- Pour les parois en polycarbonate : **Sw = 0.4**
- Pour les doubles-fenêtres composees de deux fenêtres de facteur solaire Sw1 et Sw2, le facteur solaire de la double-fenêtre est : **Sw = Sw1 + Sw2**

Si les facteurs solaires des menuiseries sont connus et justifiés, les saisir directement.

#### Tableaux Sw par type de menuiserie

**Fenêtre ou porte-fenêtre au nu extérieur** :

| Menuiserie | Type de fenêtre | Simple vitrage | Double vitrage | Double vitrage VIR | Triple vitrage | Triple vitrage VIR |
|------------|----------------|---------------|---------------|-------------------|---------------|-------------------|
| Bois / Bois-metal | Fenêtre battante | 0.56 | 0.52 | 0.45 | 0.46 | 0.42 |
| | Fenêtre coulissante | 0.58 | 0.52 | 0.45 | 0.46 | 0.43 |
| | Porte-fenêtre battante ou coulissante sans soubassement | 0.62 | 0.55 | 0.48 | 0.49 | 0.44 |
| | Porte-fenêtre battante avec soubassement | 0.53 | 0.48 | 0.41 | 0.43 | 0.38 |
| PVC | Fenêtre battante | 0.54 | 0.48 | 0.42 | 0.43 | 0.39 |
| | Porte-fenêtre battante sans soubassement | 0.53 | 0.51 | 0.44 | 0.45 | 0.40 |
| | Porte-fenêtre battante avec soubassement | 0.50 | 0.45 | 0.39 | 0.40 | 0.36 |
| | Fenêtre coulissante | 0.53 | 0.54 | 0.46 | 0.47 | 0.43 |
| | Porte-fenêtre coulissante | 0.64 | 0.57 | 0.49 | 0.52 | 0.45 |
| Metal avec rupture de pont thermique | Fenêtre battante | 0.59 | 0.53 | 0.46 | 0.47 | 0.42 |
| | Porte-fenêtre battante | 0.63 | 0.56 | 0.48 | 0.50 | 0.45 |
| | Fenêtre coulissante | 0.65 | 0.58 | 0.50 | 0.52 | 0.46 |
| | Porte-fenêtre coulissante | 0.70 | 0.62 | 0.54 | 0.55 | 0.50 |
| Metal | Fenêtre battante | 0.61 | 0.55 | 0.48 | 0.49 | 0.44 |
| | Porte-fenêtre battante | 0.64 | 0.58 | 0.50 | 0.52 | 0.47 |
| | Fenêtre coulissante | 0.63 | 0.60 | 0.52 | 0.53 | 0.48 |
| | Porte-fenêtre coulissante | 0.64 | 0.57 | 0.49 | 0.51 | 0.48 |

(Tableaux similaires pour fenêtres/portes-fenêtres au nu intérieur ou en tunnel - voir pages 45-46)

### 6.2.2 Détermination du facteur d'ensoleillement Fe

On considéré successivement les obstacles lies au bâtiment (balcons, loggias, avancees...) et les obstacles lies à l'environnement (autres bâtiments, reliefs, vegetation...). On obtient ainsi deux coefficients, Fe1 et Fe2, dont on fait le produit :

```
Fe = Fe1 * Fe2
```

- En l'absence d'obstacles lies au bâtiment et pour les configurations non présentées ci-dessous, **Fe1 = 1**
- En l'absence d'obstacles lies à l'environnement, **Fe2 = 1**

Conventionnellement, les orientations Nord, Sud, Est et Ouest correspondent aux secteurs situes de part et d'autre de ces orientations dans un angle de 45°. Pour respectivement le Nord et le Sud, les orientations incluent les limites Nord-Est, Nord-Ouest et Sud-Est, Sud-Ouest.

#### 6.2.2.1 Masques proches

##### Baie en fond de balcon ou fond et flanc de loggias

| Avancee l (m) | Nord | Sud | Est ou Ouest |
|---------------|------|-----|-------------|
| < 1 | 0.4 | 0.5 | 0.45 |
| 1 <= l < 2 | 0.3 | 0.4 | 0.35 |
| 2 <= l < 3 | 0.2 | 0.3 | 0.25 |
| >= 3 | 0.2 | 0.2 | 0.15 |

##### Baie sous un balcon ou ouvert

| Avancee l (m) | Fe1 |
|---------------|-----|
| < 1 | 0.8 |
| 1 <= l < 2 | 0.6 |
| 2 <= l < 3 | 0.5 |
| >= 3 | 0.4 |

##### Baie masquee par une paroi latérale

Une paroi latérale est considérée faire obstacle si les angles beta et gamma sont superieurs a 30°. Les angles sont pris au centre des baies.

| Position du retour | Fe1 |
|--------------------|-----|
| Le retour ne fait pas obstacle au Sud | 0.7 |
| Le retour fait obstacle au Sud | 0.5 |

**Attention** : en présence de plusieurs types de masques proches, seul l'impact du masque le plus penalisant est pris en compte.

#### 6.2.2.2 Masques lointains

##### Obstacle d'environnement homogène

| Hauteur (°) | Orientation de la facade | | |
|-------------|---|---|---|
| | Sud | Est ou Ouest | Nord |
| < 15 | 1 | 1 | 1 |
| 15 <= h < 30 | 0.8 | 0.77 | 0.82 |
| 30 <= h < 45 | 0.3 | 0.4 | 0.6 |
| 45 <= h < 60 | 0.1 | 0.2 | 0.3 |

##### Obstacle d'environnement non homogène

```
Fe2 = 1 - SUM(Omb_i / 100)
```

Avec :
- `Omb_i` : l'ombrage cree par l'obstacle sur la paroi

La méthode d'évaluation :
1. On decoupe le champ de vision en quatre secteurs d'gaux
2. On déterminé, pour chacun d'eux, la hauteur moyenne des obstacles
3. On lit dans le tableau ci-dessous les valeurs correspondantes de l'ombrage, Omb_i

| Omb_i | Facade au Sud ou Nord | | Facade Est ou Ouest | |
|-------|---|---|---|---|
| Hauteur moyenne de l'obstacle a (°) | Pour le 2 secteurs centraux | Pour les 2 autres secteurs | Pour le secteur lateral orienté vers le sud | Pour les 2 autres secteurs |
| < 15 | 5 | 0 | 5 | 0 |
| 15 <= a < 30 | 4 | 14 | 14 | 17 | 5 |
| 30 <= a < 60 | 13 | 35 | 27 | 43 | 17 |
| 60 <= a < 90 | 35 | 40 | 59 | 43 | 25 |

Les masques lointains sont evalues au niveau de la baie la plus proche du centre de la facade avant d'appliquer à toutes les baies de cette facade.



## 6.3 Traitement des espaces tampons solarisés

Un logement donnant sur un espace tampon solarisé (véranda, loggia fermee) est influence dans son bilan énergétique par les apports solaires. Il en existe deux types.

### Apports solaires à travers un espace tampon solarisé

Les apports solaires à travers un espace tampon solarisé sont donnés sur un mois j par :

```
As(ets_j) = 1000 * Sse(veranda_j) * E_j
```

Avec :
- `I_j` : ensoleillement recu par paroi verticale orientée au sud en l'absence d'ombrage sur le mois j (kWh/(m².K))
- `Sse(veranda_j)` : surface sud équivalente representant l'impact des apports solaires associés au rayonnement solaire traversant directement l'espace tampon solarisé pour arriver dans la partie habitable du logement (apports directs) et representant l'impact de l'espace tampon solarisé sur les apports solaires à travers les baies vitrees, modélisé par une surface sud équivalente pour le mois j (Sse(véranda_j))

```
Sse(veranda_j) = Ssd_j + Ssind_j + Ssbe_j
```

- Dans le cas de baies vitrees séparant l'espace tampon solarisé de la partie habitable du logement :

```
Ssd_j = T * SUM(A_i * Sw_i * Fe_i * C1_(i,j))
```

Avec :
- `A_i` : Surface de la baie i séparant le logement de l'espace tampon solarisé (m²)
- `Sw_i` : Facteur solaire de la baie i séparant le logement de l'espace tampon solarisé
- `Fe_i` : Facteur d'ensoleillement, qui traduit la réduction d'énergie solaire recue par la baie i du fait des masques (la présence de l'espace tampon solarisé n'est pas prise en compte pour déterminer ce coefficient)
- `C1_(i,j)` : Coefficient d'orientation et d'inclinaison de la baie i séparant le logement de l'espace tampon solarisé pour le mois j, voir paragraphe 18.5
- `T` : Coefficient representant la transparence de l'espace tampon solarisé. Il correspond à l'estimation du rayonnement solaire arrivant directement dans le logement par la traverse de l'espace tampon solarisé

#### Transparence T par type de vitrage

| Menuiserie | Type de Vitrage | Transparence T |
|-----------|----------------|---------------|
| Bois / Bois metal | Simple vitrage | 0.62 |
| | Double vitrage | 0.55 |
| | Double vitrage peu émissif | 0.48 |
| | Triple vitrage | 0.49 |
| | Triple vitrage peu émissif | 0.36 |
| PVC | Simple vitrage | 0.5 |
| | Double vitrage | 0.45 |
| | Double vitrage peu émissif | 0.35 |
| | Triple vitrage | 0.4 |
| Metal avec rupture de pont thermique | Simple vitrage | 0.63 |
| | Double vitrage | 0.56 |
| | Double vitrage peu émissif | 0.48 |
| | Triple vitrage | 0.45 |
| Metal | Simple vitrage | 0.58 |
| | Double vitrage | 0.52 |
| | Double vitrage peu émissif | 0.47 |
| | Triple vitrage | 0.47 |

Pour les parois en polycarbonate, on prendra **T = 0.4**.

### Apports solaires indirects Ssind_j

```
Ssind_j = SsT_j - Ssd_j
```

Avec :
- `SsT_j` : Surface sud équivalente representant l'impact des apports solaires associés au rayonnement solaire arrivant dans la partie habitable du logement apres de multiples reflexions dans l'espace tampon solarisé (apports indirects) pour le mois j. Ssind correspond à la surface sud équivalente des apports totaux dans la véranda Ss, de laquelle il faut déduire elle des apports directs Ssd.

```
SsT_j = SUM(A_i * (0.8 * Sw_i + 0.0124) * Fe_j * C1_(i,j))
```

Avec :
- `A_i` : Surface de la baie i séparant la véranda de l'extérieur (m²)
- `Sw_i` : facteur solaire de la baie i séparant la véranda de l'extérieur (m²)
- `Fe_j` : facteur d'ensoleillement. Pour les espaces tampons solarisés, Fe_j = 1 car l'impact des masques sera multiplie
- `C1_(i,j)` : Coefficient d'orientation et d'inclinaison de la baie i séparant la véranda de l'extérieur pour le mois j, voir paragraphe 18.5

Les grandes surfaces vitrees séparant la véranda de l'extérieur seront traitées comme des portes-fenêtres avec des menuiseries au nu extérieur.

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 6 a 6.3 (pages 41-51)
