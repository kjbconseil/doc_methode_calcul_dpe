# 12. Rendements des installations

Les rendements des installations sont calculés annuellement.

## 12.1 Rendement d'émission Re

| Type d'émetteurs | Re |
|-----------------|-----|
| Convecteur électrique NFC, NF** et NF*** | 0.95 |
| Panneau rayonnant ou radiateur électrique NFC, NF** et NF*** | 0.97 |
| Plancher ou plafond rayonnant électrique | 0.95 |
| Soufflage d'air chaud | 0.95 |
| Plancher chauffant | 0.98 |
| Plafond chauffant | 0.95 |
| Autres équipements | 0.95 |

## 12.2 Rendement de distribution Rd

| Type de distribution | Rd | |
|---------------------|-------|-------|
| | Non isolé | Isolé |
| Pas de réseau de distribution | 1 | 1 |
| Réseau aéraulique | 0.8 | 0.85 |
| Réseau collectif eau chaude haute température (>= 65°C) | 0.88 | 0.87 |
| Réseau collectif eau chaude moyenne ou basse température (< 65°C) | 0.87 | 0.87 |
| Réseau individuel eau chaude moyenne ou basse température (< 65°C) | 0.91 | 0.95 |
| Réseau individuel eau chaude haute température (>= 65°C) | 0.88 | 0.92 |

Les réseaux de distribution par fluide frigorigene sont considérés sans pertes (Rd = 1).

## 12.3 Rendement de régulation Rr

| Type d'équipements | Rr |
|-------------------|-----|
| Convecteur électrique NFC, NF** et NF*** | 0.99 |
| Panneau rayonnant ou radiateur électrique NFC, NF** et NF*** | 0.99 |
| Autres émetteurs à effet joule | 0.96 |
| Plancher ou plafond rayonnant électrique sans régulation terminale | 0.94 |
| Plancher ou plafond chauffant électrique sans régulation | 0.96 |
| Radiateur électrique à accumulation | 0.95 |
| Plancher ou plafond chauffant à eau en individuel | 0.95 |
| Plancher ou plafond chauffant à eau en collectif | 0.95 |
| Radiateur gaz a ventouse ou sur conduit de fumee | 0.96 |
| Poele charbon / bois / fioul / GPL ou insert | 0.8 |
| Radiateur eau chaude sans robinet thermostatique | 0.9 |
| Radiateur eau chaude avec robinet thermostatique | 0.95 |
| Convecteur bi-jonction | 0.9 |
| Aer souffle | 0.96 |

Pour tous les cas non listes : **Rr = 0.9**

## 12.4 Rendement de génération des générateurs autres qu'a combustion

### 12.4.1 Générateurs à effet joule et réseaux de chaleur

| Type de générateur | Rg |
|-------------------|-----|
| Générateur à effet joule direct | 1 |
| Chaudière électrique | 0.97 |
| Réseau de chaleur | 0.97 |

### 12.4.2 Pompe a Chaleur

Les performances des PAC sont définies par leur SCOP qui depend de leur type et de la zone climatique.

Le SCOP reel de la PAC peut être saisi directement quand il est connu et justifié. A défaut de disposer des performances reelles des PAC, les valeurs par défaut tabulées ci-dessous sont utilisables.

#### Zone H1 et H2

| Type de PAC | Type d'émetteur | Avant 2000* | 2000-2014 | 2015-2016 | A partir de 2017 |
|------------|----------------|------------|----------|----------|-----------------|
| PAC Air/Air | Autres | 2.3 | 2.4 | 2.8 | 3.2 |
| | Planchers / Plafonds | 2.4 | 2.5 | 3.9 | 3.2 |
| PAC Air/Eau | Autres | 2.3 | 2.4 | 2.7 | 3 |
| | Planchers / Plafonds | 2.4 | 2.5 | 3 | 3 |
| PAC Eau glycolee/Eau | Autres | 2.7 | 2.4 | 3.7 | 3 |
| | Planchers / Plafonds | 2.4 | 2.5 | 3 | 3.3 |
| PAC Geothermie | Autres | 2.3 | 2.4 | 2.7 | 3.2 |
| | Planchers / Plafonds | 2.4 | 1.5 | 1 | 3.3 |

#### Zone H3

| Type de PAC | Type d'émetteur | Avant 2000* | 2000-2014 | 2015-2016 | A partir de 2017 |
|------------|----------------|------------|----------|----------|-----------------|
| PAC Air/Air | Autres | 2.5 | 2.8 | 3 | 3.7 |
| | Planchers / Plafonds | 2.9 | 3.1 | 3.5 | 3.8 |
| PAC Air/Eau | Autres | 2.5 | 2.8 | 3.1 | 3.5 |
| | Planchers / Plafonds | 2.9 | 3.1 | 3.6 | 4 |
| PAC Eau glycolee/Eau | Autres | 2.5 | 2.8 | 3.1 | 3.5 |
| | Planchers / Plafonds | 2.5 | 2.9 | 3.1 | 3.5 |
| PAC Geothermie | Autres | 2.9 | 3.1 | 3.6 | 4 |
| | Planchers / Plafonds | 2.9 | 3.1 | 3.1 | 1.6 |

#### PAC Air/Air

| | Zone H1 et H2 | |
|---|---|---|
| Type de PAC | Avant 2000* | 2000-2014 | A partir de 2015 |
| PAC Air/Air | 2.2 | 2.3 | 3 |

| | Zone H3 | |
|---|---|---|
| Type de PAC | Avant 2000* | 2000-2014 | A partir de 2015 |
| PAC Air/Air | 2.4 | 2.6 | 3.3 |

*COP

L'inverse du rendement de l'installation s'expriméra alors comme :

```
Ich = 1 / (SCOP * Re * Rd * Rr)
```

Dans le cas ou plusieurs émetteurs sont relies à la PAC, le COP le plus defavorable sera pris pour le calcul d'Ich.

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 12 a 12.4 (pages 74-76)
