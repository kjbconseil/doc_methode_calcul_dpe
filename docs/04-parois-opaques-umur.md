# 3.2 Calcul des U des parois opaques

## Données d'entrée

- Caractéristiques des parois (type, épaisseur, mitoyennete, materiaux traditionnels)
- Caractéristiques isolation (épaisseur, résistance, année d'isolation)
- Nombre d'appartements
- Retour d'isolation autour des menuiseries (avec ou sans)
- Hauteur moyenne sous plafond

## Règles generales

- On considéré qu'un logement est chauffé par effet joule lorsque la chaleur est fournie par une résistance électrique
- Une paroi opaque (hors plancher bas) est considérée comme un mur des lors que l'angle par rapport à l'horizontal est supérieur ou égal a 75°. Dans les autres cas, il s'agit d'un plancher haut



## 3.2.1 Calcul des Umur

### Schéma de calcul

Le calcul suit un arbre de decision :
1. Si Umur est connu (saisie directe) -> utiliser cette valeur
2. Sinon, déterminer le type de mur -> chercher Umur0 (non isolé) dans les tableaux
3. Si Umur0 non trouve dans les tableaux (Connu 1 = Non) -> Umur0 = 2.5
4. Si Umur0 trouve -> Umur0 = MAX(Umur0_tab, Umur_tab) (avec Umur_tab du tableau par année d'isolation)
5. Verifier présence d'isolation :
   - Si isolation connue avec **résistance isolant** :
     ```
     Umur = 1 / (1/Umur0 + R_isolation)
     ```
   - Si isolation connue avec **épaisseur isolant** :
     ```
     Umur = 1 / (1/Umur0 + e/0.04)
     ```
   - Si isolation inconnue mais paroi isolée -> déterminer selon l'année d'isolation

**Année d'isolation** :
- Si année de construction <= 74, alors Année d'isolation = 75-77
- Sinon Année d'isolation = Année de construction

### 3.2.1.2 Calcul des Umur0

Umur0 est le coefficient de transmission thermique du mur non isolé (W/(m².K)).

#### Tableaux des Umur0 par type de mur et épaisseur

**Murs en pierre de taille et moellons** :

Épaisseur nominale (en cm) :

| Épaisseur | <= 20 | 25 | 30 | 35 | 40 | 45 | 50 | 55 | >= 60 |
|-----------|-------|----|----|----|----|----|----|----|----|
| Murs en pierre de taille et moellons, meuliere, bossage, galets, murs avec remplissage (tout-venant) | 2.40 | | | | | | 1.10 | 1.00 | 0.90 |
| Murs avec remplissage (tout-venant) | | | | | | | | | 1.05 |

> **Note** : Les valeurs intermédiaires non présentes dans le tableau peuvent être obtenues par interpolation ou extrapolation.

**Briques pleines et assimilées** :

| Épaisseur (cm) | 1-8 | 7.5 | 30 | 40 | 60 | >= 70 |
|----------------|-----|-----|----|----|----|-------|
| Briques pleines | 2.75 | 1.65 | 1.35 | 1.25 | 1.15 | 1.15 |

**Mur en gravier ou beton de cailloux** :

| Épaisseur (cm) | 1-8 | 7.5 | 30 | 40 | 60 | >= 70-80 |
|----------------|-----|-----|----|----|----|---------|
| Valeur | 2.75 | 1.65 | 1.35 | 1.25 | 1.15 | 1.15 |

**Murs en pans de bois** :

| Épaisseur (cm) | < 6 | 10 | 15 | 18 | >= 21 | >= 32 |
|----------------|-----|----|----|----|----|-------|
| Sans remplissage (tout-venant) | 1 | 2.7 | 2.55 | 1.98 | 1.55 | 1.28 |
| Avec remplissage (tout-venant) | | 1.7 | | | | |

**Briques creuses** :

| Épaisseur (cm) | <= 10 | 15 | 20 | >= 25 |
|----------------|-------|----|----|-------|
| Briques creuses | 2.5 | 1.9 | | |
| Murs bois + briques | 3.5 | 1.2 | 0.65 | 0.58 |

**Murs en beton plein (banche)** :

| Épaisseur (cm) | <= 7 | 12 | 15 | 20 | 25 | 30 | 35 | >= 40 |
|----------------|------|----|----|----|----|----|----|-------|
| Beton plein | 1.8 | 3.35 | 3.55 | 2.75 | 1.5 | 1.25 | 2 | 1.63 |

**Blocs de beton creux** :

| Épaisseur (cm) | <= 20 | 25 | >= 25 |
|----------------|-------|----|-------|
| Blocs beton creux | 1.9 | 2.45 | 1.5 |

**Blocs de beton plein** :

| Épaisseur (cm) | <= 10 | 15 | 20 | 25 | 30 | 35 | >= 40 |
|----------------|-------|----|----|----|----|----|----|
| Blocs beton plein | 2.5 | 2.75 | 1.65 | 2.4 | 1.5 | 2.05 | |

**Murs en beton de machefer** :

| Épaisseur (cm) | <= 15 | 20 | 25 | 30 | >= 35 |
|----------------|-------|----|----|----|----|
| Valeur | 2.15 | 1.25 | 1.45 | 1.45 | 1.65 |

**Murs en beton banche** :

| Épaisseur (cm) | <= 15 | 22.5 | 25 | 30 | 35 | >= 40 |
|----------------|-------|------|----|----|----|------|
| Beton banche | 2.5 | 2.75 | 1.65 | 2.4 | 1.5 | 2.05 |

**Murs en beton cellulaire** :

| Épaisseur (cm) | 13 | 17.5 | 20 | 22.5 | 25 | 27.5 | 30 | 33.6 | 37.5 |
|----------------|-----|------|-----|------|-----|------|-----|------|------|
| Construction >= 2013 | 0.69 | 0.55 | 0.42 | 0.37 | 0.55 | 0.49 | 0.42 | 0.38 | 0.22 |
| Construction < 2013 | 0.69 | 0.55 | 0.53 | 0.46 | 0.42 | | 0.38 | 0.22 | |

> **Attention** : Les valeurs exactes de chaque épaisseur doivent être vérifiées avec le document officiel (tableaux pages 14-15 de l'annexe).

**Murs sandwich beton/isolant/beton (sans isolation rapportée)** :

| Épaisseur (cm) | < 5 | >= 5 a < 25 | >= 25 |
|----------------|-----|-------------|-------|
| Valeur | 0.9 | 0.48 | 0.48 |

**Murs en ossature bois (sans isolation rapportée)** :

| Épaisseur (cm) | 10 | 15 | 20 | 25 | 30 | 35 | 40 | >= 45 |
|----------------|----|----|----|----|----|----|----|----|
| Valeur | 0.46 | 0.35 | 0.26 | 0.31 | 0.17 | 0.31 | 0.18 | 0.13 |

### Cloison de platre

```
Umur0 = 1.33 W/(m².K)
```

### Parois anciennes avec enduit

Pour les parois dites "anciennes", c'est-a-dire constituees de materiaux traditionnels a savoir pierre, terre, mur a colombage, brique ancienne, la présence d'un enduit saillant n'est pas considérée comme une isolation. Cependant, un enduit saillant apporte une correction d'isolation qu'il faut prendre en compte en consideration :

```
Umur0 = 1 / (1/Umur0_sans_enduit + R_enduit)
```

Avec :
- `R_enduit = 0.7 m².K/W`

### Cas particuliers

- Les murs en parois de verre sont traités comme des parois vitrees (voir paragraphe 3.3)
- Pour les murs non répertoriés, saisir directement les coefficients de transmission thermique quand ils sont justifiés
- Pour les murs doubles ou de composants multiples connus et justifiés, saisir directement le U du mur calcule



## 3.2.2 Calcul des Uplancher bas (Upb)

### Schéma de calcul

Si le plancher donné sur l'extérieur ou un local non chauffé (hors sous-sol) :
1. Saisir Upb directement si connu
2. Sinon, déterminer le type de plancher -> chercher Upb0 dans les tableaux
3. Si Upb0 > 2 -> Upb0 = 2
4. Verifier la présence d'isolation :
   - Avec **résistance isolant** :
     ```
     Upb = 1 / (1/Upb0 + R_isolation)
     ```
   - Avec **épaisseur isolant** :
     ```
     Upb = 1 / (1/Upb0 + e/0.042)
     ```
   - Isolation inconnue -> déterminer selon l'année

### 3.2.2.1 Calcul des Upb sur vide sanitaire / sous-sol / terre-plein

**Vide sanitaire / sous-sol / extérieur** :
- Valeurs Upb en fonction de Upb0 et 2S/P (périmètre), selon :
  - Le plancher est sur vide sanitaire ou sous-sol non chauffe
  - Le plancher donné sur terre-plein
  - Batiment construit avant 2001 / à partir de 2001

Variables du tableau :
- `P` : périmètre du plancher deperdtif du bâtiment ou du lot sur terre-plein, vide sanitaire ou sous-sol non chauffé (m)
- `S` : surface du plancher du bâtiment ou du lot sur terre-plein, vide sanitaire ou sous-sol non chauffé (m²)
- `2S/P` est arrondi à l'entier le plus proche

### 3.2.2.2 Calcul des Upb0

Upb0 est le coefficient de transmission thermique du plancher bas non isolé (W/(m².K)).

| Type de plancher | Upb0 |
|------------------|------|
| Plafond avec ou sans remplissage | 1.45 W/(m².K) |
| Plancher entre solives bois avec ou sans remplissage | 1.45 W/(m².K) |
| Bardeaux et remplissage | 1.2 W/(m².K) |
| Plancher bois sur solives bois | 1.2 W/(m².K) |
| Plancher bois sur solives métalliques | 2 W/(m².K) |
| Voutains en briques ou moellons | 1.75 W/(m².K) |
| Voutains sur solives métalliques | 2.5 W/(m².K) |
| Planchers entre solives métalliques, terre cuite, poutrelles beton | 2 W/(m².K) |
| Dalle beton | 2.5 W/(m².K) |
| Plancher a entrevous (solant Upb0 < 0.45 W/(m².K)) | Upb0 = 0.45 |

Pour les planchers bas non répertoriés, saisir directement les coefficients de transmission thermique Upb0 quand ils sont justifiés. Les données des règles Th-U peuvent être utilisées.



## 3.2.3 Calcul des Uplancher haut (Uph)

### Schéma de calcul

Même logique que pour Umur et Upb :
1. Saisir Uph directement si connu
2. Sinon, déterminer le type de plafond -> chercher Uph0 dans les tableaux
3. Si Uph0 > 2.5 -> Uph0 = 2.5
4. Verifier la présence d'isolation :
   - Avec **résistance isolant** :
     ```
     Uph = 1 / (1/Uph0 + R_isolation)
     ```
   - Avec **épaisseur isolant** :
     ```
     Uph = 1 / (1/Uph0 + e/0.034)
     ```

### 3.2.3.2 Calcul des Uph0

Uph0 est le coefficient de transmission thermique du plancher haut non isolé (W/(m².K)).

| Type de plancher haut | Uph0 |
|-----------------------|------|
| Plafond avec ou sans remplissage | 2.5 W/(m².K) |
| Plafond entre solives bois avec ou sans remplissage métallique | 2 W/(m².K) |
| Plafond sous solives métalliques | 1.2 W/(m².K) |
| Plafond entre solives métalliques, poutrelles cuivre, entrevous | 2.5 W/(m².K) |
| Plafond bois sur solives bois | 1.65 W/(m².K) |
| Plancher bois sur solives métalliques | 1.45 W/(m².K) |
| Dalle beton | 2.5 W/(m².K) |
| Plafond lourd (type entrevous, bois...) | 3.5 W/(m².K) |

**Cas particuliers** :
- Combles aménagés sous rampant : Uph0 < 2.5 W/(m².K)
- Toiture en chaume : Uph0 = 0.24 W/(m².K)
- Plafond en plaque de platre : Uph0 = 2.5 W/(m².K)

**Attention** : Les valeurs par défaut des caractéristiques des parois dependent des années de construction dans certains cas. Pour les bâtiments ayant fait l'objet d'extension, les valeurs par défaut des caractéristiques des parois peuvent être différentes entre l'extension et le bâtiment originel.

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 3.2.1 a 3.2.3 (pages 12-21)
