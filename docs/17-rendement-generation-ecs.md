# 14. Rendement des générateurs d'ECS

## Données d'entrée

- Type de production
- Puissance nominale
- Rendement à pleine charge et a charge intermédiaire
- Pertes à l'arret
- Volume de stockage
- Isolation de la distribution
- Type de distribution
- Temperature de distribution
- Type d'alimentation

## 14.1 Générateurs à combustion

### Conventions de calcul

La consommation conventionnelle de la production d'eau chaude sanitaire suppose une absence de consommation pendant 1 semaine au mois de décembre.

Il est donc considéré dans la suite de façon conventionnelle :
- Nombre annuel d'heures de fonctionnement de l'ECS = **1790h**
- Nombre d'heures de vacances = **168h**
- Duree de fonctionnement de l'ECS ramenee à la période de vacances = **105h**
- Les générateurs de production d'ECS ne sont pas maintenus en température

### 14.1.1 Production d'ECS seule instantanee par chauffe-eau gaz

Le rendement conventionnel annuel moyen de génération d'ECS a pour expression :

```
Rg = 1 / ((1/Rg) * (1790 + Q(0)/Becs) + (v970 + Pveil/Becs))
```

Avec :
- `Becs` : énergie annuelle a fournir par le générateur pour l'ECS en Wh
- `Pveil` : puissance de la veilleuse (W)
- `Qp_0` : pertes à l'arret du générateur (W)
- `R_pn` : rendement à pleine charge du générateur

**Valeurs par défaut** :

| Anciennete | Pn <= 10 kW | | Pn > 10 kW | |
|-----------|---|---|---|---|
| | Rendement PCI % | Qp0 en % puissance nominale Pn | Rendement PCI % | Qp0 en % puissance nominale Pn | Puissance veilleuse (W) |
| Avant 1981 | 70.5% | 4.0% | 70.5% | 4.0% | 150 |
| 1981-1989 | 75.0% | 3.0% | 75.0% | 2.0% | 120 |
| 1990-2000 | 83.0% | 1.2% | 82.0% | 1.2% | 120 |
| 2001-2015 | 83.0% | 1.0% | 84.0% | 1.0% | 100 |
| Apres 2015 | 83.0% | 1.0% | 84.0% | 0.6% | |

### 14.1.2 Production mixte par chaudière gaz, fioul, bois

```
Rg = Rs = 1 / ((1790 * Qp_e + Q(stk)) / Becs) + (v970 + 0.5 * Pveil / Becs)
```

Avec :
- `Qp_e` : pertes à l'arret de la chaudière (W)
- `Becs` : énergie annuelle a fournir par le générateur pour l'ECS en Wh
- `R_pn` : rendement a 100% de charge
- `Q(stk)` : pertes de stockage (Wh)

### 14.1.3 Accumulateur gaz

```
Rg = Rs = 1 / ((8592 * Qp_e + Q(stk)) / Becs + (v970 + Pveil / Becs))
```

Avec :
- `R_pn` : rendement a 100% de charge
- `Becs` : besoin annuel a fournir par le générateur pour l'ECS (Wh)
- `Q(stk)` : pertes de stockage (Wh)
- `Pveil` : puissance de la veilleuse (W)
- `Qp_0` : pertes à l'arret de la chaudière (W)

```
Qp_0 = 1.5 + Pn / 100
```

Les caractéristiques par défaut sont similaires a celles des chauffe-eau gaz.

## 14.2 Chauffe-eau thermodynamique à accumulation

Les performances des chauffe-eau thermodynamiques sont définies par des COP qui dependent du type d'installation et de la zone climatique.

| COP | Zone H1 et H2 | | |
|-----|------|------|------|
| | Avant 2000 | 2010-2014 | A partir de 2015 |
| CET sur air extérieur ou ambiant (sur local non chauffe) | 2 | 2.5 | 2.8 |
| CET sur air extrait | 2.3 | 2.5 | 2.8 |
| PAC double service | 2 | 2.1 | 2.3 |

| COP | Zone H3 | | |
|-----|------|------|------|
| | Avant 2000 | 2010-2014 | A partir de 2015 |
| CET sur air extérieur ou ambiant (sur local non chauffe) | 2.3 | 2.5 | 2.8 |
| CET sur air extrait | 2.3 | 2.5 | 2.8 |
| PAC double service | 2.3 | 2.4 | 2.6 |

Pour le chauffe-eau thermodynamique, la performance des ballons est prise en compte dans le COP.

Ainsi :
```
Iecs = 1 / (Rd * COP)
```

## 14.3 Réseau de chaleur

Les rendements de stockage et de génération sont remplaces par le rendement d'échange de la sous-station :
- Si l'installation est isolée : `Rs * Rg = 0.9`
- Sinon : `Rs * Rg = 0.75`

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 14 a 14.3 (pages 91-93)
