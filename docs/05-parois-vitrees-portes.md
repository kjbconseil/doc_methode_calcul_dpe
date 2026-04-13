# 3.3 Calcul des U des parois vitrees et des portes

## Données d'entrée

- Type de vitrage (simple, double...)
- Épaisseur lame d'air
- Présence d'une couche peu émissive
- Gaz de remplissage
- Inclinaison vitrage
- Type de menuiserie
- Type de volets
- Type de porte

## Règles generales

- Les grandes surfaces vitrees des vérandas chauffées seront traitées comme des portes-fenêtres avec des menuiseries au/ou extérieur
- Les parois en brique de verre sont traitées comme des parois vitrees avec :
  - Brique de verre pleine : **Uv = 3.5 W/(m².K)**
  - Brique de verre creuse : **Uv = 2 W/(m².K)**
- Les parois en polycarbonate sont traitées comme des parois vitrees avec : **Uv = 5 W/(m².K)**

## Définition de l'inclinaison des baies

- Paroi verticale = angle par rapport à l'horizontal >= 75°
- Paroi horizontale = angle par rapport à l'horizontal < 75°

## Demarche de calcul

Le coefficient U des fenêtres est connu : saisir Uw et caracteriser les occultations pour déterminer Ujn.

Si Uw est inconnu, alors suivre la démarche suivante :
1. **Détermination de Ug** à partir du type de vitrage
2. **Détermination de Uw** à partir de Ug, du type de paroi vitree et de la menuiserie
3. **Détermination de Ujn** à partir de Uw et du type de fermeture
4. Si présence de protections solaires : Ubaie = Ujn. Sinon : Ubaie = Uw

### Variables

| Variable | Description |
|----------|-------------|
| `Ug` | Coefficient de transmission thermique du vitrage (W/(m².K)) |
| `Uw` | Coefficient de transmission thermique de la fenêtre ou de la porte-fenêtre (vitrage + menuiserie) (W/(m².K)) |
| `Ujn` | Coefficient de transmission thermique de la fenêtre ou de la porte-fenêtre avec les protections solaires (W/(m².K)) |



## 3.3.1 Détermination de la performance du vitrage Ug

### Simple vitrage et survitrage

Pour un simple vitrage, quelle que soit l'épaisseur du verre :
```
Ug = 5.8 W/(m².K) pour un vitrage vertical ou horizontal
```

Le Ug d'un survitrage est déterminé en apportant une majoration de 0.1 W/(m².K) au Ug du double vitrage rempli à l'air sec ayant la même épaisseur de lame d'air. Les épaisseurs des lames d'air pour le survitrage sont plafonnees a 20mm. C'est-a-dire que toute lame d'air d'un survitrage d'épaisseur supérieure a 20mm sera traitée dans les calculs comme une lame d'air de 20mm d'épaisseur.

### Double vitrage vertical

**Remplissage air sec ou inconnu** :

| Épaisseur lame d'air (mm) | Vitrage non traité | Vitrage peu émissif |
|---------------------------|-------------------|-------------------|
| 6 | 3.3 | 2.05 |
| 8 | 3.1 | 1.5 |
| 10 | 2.8 | 1.6 |
| 12 | 2.6 | 1.45 |
| 14 | 2.6 | 1.3 |
| 16 | 2.5 | 1.3 |
| 18 | 2.7 | 1.4 |
| 20 | 2.7 | 1.4 |

**Remplissage Argon ou Krypton** :

| Épaisseur lame d'air (mm) | Vitrage non traité | Vitrage peu émissif |
|---------------------------|-------------------|-------------------|
| 6 | 2.9 | 2.0 |
| 8 | 2.9 | 1.7 |
| 10 | 2.8 | 1.5 |
| 12 | 2.6 | 1.3 |
| 14 | 2.6 | 1.3 |
| 16 | 2.5 | 1.1 |
| 18 | 2.6 | 1.1 |
| 20 | 2.6 | 1.1 |

### Double vitrage horizontal

(Même structure de tableaux avec valeurs legerement différentes - voir page 23)

### Triple vitrage vertical

**Remplissage air sec ou inconnu** :

| Épaisseur lame d'air (mm) | Vitrage non traité | Vitrage peu émissif |
|---------------------------|-------------------|-------------------|
| 6 | 2.3 | 1.7 |
| 8 | 2.1 | 1.5 |
| 10 | 2.0 | 1.2 |
| 12 | 1.8 | 1.0 |
| 14 | 1.8 | 1.0 |
| 16 | 1.8 | 0.9 |
| 18 | 1.7 | 0.6 |
| 20 | 1.7 | 0.6 |

**Remplissage Argon ou Krypton** :

| Épaisseur lame d'air (mm) | Vitrage non traité | Vitrage peu émissif |
|---------------------------|-------------------|-------------------|
| 6 | 2.0 | 1.6 |
| 8 | 2.0 | 1.2 |
| 10 | 1.8 | 1.0 |
| 12 | 1.8 | 0.8 |
| 14 | 1.7 | 0.8 |
| 16 | 1.6 | 0.7 |
| 18 | 1.4 | 0.6 |
| 20 | 1.4 | 0.6 |

**Attention** : Si la valeur de l'épaisseur de la lame d'air n'est pas dans le tableau présenté, prendre la valeur directement inférieure si elle y figure.

**Attention** : Si un triple vitrage à des épaisseurs de lame d'air différentes, considerer que c'est un triple vitrage dont l'épaisseur de chaque lame d'air est la moitie de l'épaisseur totale des deux lames d'air (ou la valeur consignee dans les tableaux précédents la plus proche de la moitie de l'épaisseur).

**Par défaut**, les doubles et triples vitrages installés à partir de 2006 sont tous considérés remplis à l'Argon ou au Krypton.

Si le Ug d'un vitrage est connu et justifié, le saisir directement.



## 3.3.2 Coefficients Uw des fenêtres / portes-fenêtres

Les baies sans ouverture possible (ni battantes ni coulissantes) seront traitées comme battantes dans tous la suite.

### Menuiserie métallique a rupture de pont thermique

| Ug | Fenêtre battante | Fenêtre coulissante | Porte-Fenêtre battante | Porte-Fenêtre coulissante |
|----|-----------------|--------------------|-----------------------|--------------------------|
| 0.5 | 1.3 | 1.4 | 1.0 | 1.2 |
| 0.6 | 1.4 | 1.5 | 1.2 | 1.3 |
| 0.7 | 1.5 | 1.6 | 1.3 | 1.4 |
| ... | ... | ... | ... | ... |
| 6 | 6.0 | 6.0 | 6.0 | 6.1 |

### Menuiserie métallique sans rupture de pont thermique

| Ug | Fenêtre battante | Fenêtre coulissante | Porte-Fenêtre battante | Porte-Fenêtre coulissante |
|----|-----------------|--------------------|-----------------------|--------------------------|
| 0.5 | 1.8 | 2.0 | 1.6 | 1.5 |
| ... | ... | ... | ... | ... |
| 6 | 6.4 | 6.4 | 6.0 | 6.4 |

### Menuiserie PVC

| Ug | Fenêtre battante | Fenêtre coulissante | Porte-Fenêtre battante | Porte-Fenêtre coulissante | Porte-Fenêtre battante avec soubassement |
|----|-----------------|--------------------|-----------------------|--------------------------|------|
| 0.5 | 0.8 | 1.3 | 0.8 | 1.1 | 0.8 |
| ... | ... | ... | ... | ... | ... |

### Menuiserie bois ou bois metal

Dans tous les calculs, les menuiseries mixtes bois metal prendront les caractéristiques du bois.

| Ug | Fenêtre battante | Fenêtre coulissante | Porte-Fenêtre battante | Porte-Fenêtre coulissante | Porte-Fenêtre battante avec soubassement |
|----|-----------------|--------------------|-----------------------|--------------------------|------|
| 0.6 | 1.2 | 1.2 | 0.9 | 1.3 | 1.2 |
| ... | ... | ... | ... | ... | ... |

### Traitement des doubles fenêtres

```
Ue = 1 / (1/Uw1 + 1/Uw2 + 0.07)
```

Ou Uw1 et Uw2 sont respectivement le coefficient de transmission thermique des fenêtres 1 et 2 (W/(m².K)).

Chaque fenêtre du complexe doit donc être caracterisee pour déterminer la performance de la double-fenêtre.

Si le Uw d'une menuiserie est connu et justifié, le saisir directement.



## 3.3.3 Coefficients Ujn des fenêtres/portes-fenêtres

La présence de volets aux fenêtres et portes-fenêtres leur apporte un supplement d'isolation avec une résistance additionnelle deltaR.

### Resistance additionnelle deltaR par type de fermeture

| Fermetures | deltaR (m².K/W) |
|-----------|----------------|
| Jalousie accordeon, fermeture a lames orientables y compris les venitiens exterieurs tout metal, volets battants ou persiennes avec ajours fixes | 0.08 |
| Fermeture sans ajours en position deployee, volets roulants alu | 0.15 |
| Volets roulants PVC ou bois (e <= 12 mm) | 0.19 |
| Persienne coulissante et volet battant PVC ou bois (e <= 22 mm) | 0.19 |
| Volets roulants PVC ou bois (e > 12 mm) | 0.25 |
| Persienne coulissante et volet battant PVC ou bois (e > 22 mm) | 0.25 |
| Fermeture isolée sans ajours en position deployee | 0.25 |

Note : e est l'épaisseur du tablier

### Formule Ujn

Les Ujn associés à des Uw non presents dans les tableaux peuvent être obtenus par interpolation ou extrapolation avec les deux Uw tabulées les plus proches.

Si le Ujn d'une menuiserie est connu et justifié, le saisir directement.



## 3.3.4 Coefficients U des portes

Si le coefficient U des portes est connu et justifié, le saisir directement. Sinon, prendre les valeurs tabulées ci-dessous :

| Nature de la menuiserie | Type de porte | Uporte W/(m².K) |
|------------------------|--------------|-----------------|
| Porte simple en bois ou PVC | Porte opaque pleine | 3.5 |
| | Porte avec moins de 30% de vitrage simple | 4 |
| | Porte avec 30-60% de vitrage simple | 4.5 |
| | Porte avec double vitrage | 3.5 |
| Porte simple en metal | Porte opaque pleine | 5.8 |
| | Porte avec vitrage simple | 5.8 |
| | Porte avec moins de 30% de double vitrage | 5.5 |
| | Porte avec 30-60% de double vitrage | 4.8 |
| Toute menuiserie | Porte opaque pleine isolée | 1.5 |
| | Porte précédée d'un SAS | 1.5 |
| | Porte isolée avec double vitrage | 1.5 |

**Attention** : une porte vitree avec plus de 60% de vitrage est traitée comme une porte-fenêtre avec soubassement.

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 3.3 a 3.3.4 (pages 21-31)
