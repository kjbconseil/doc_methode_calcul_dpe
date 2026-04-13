# 10. Calcul de la consommation de froid (Cfr)

Les besoins et consommation en froid sont calculés pour un comportement conventionnel (consigne de refroidissement a 28°C) et pour un comportement dépasseur (consigne de refroidissement a 26°C).

Quel que soit le comportement, la méthode de calcul suivante s'applique.

## 10.1 Calcul du besoin annuel de froid

```
Bfr = SUM(Bfr_j)
```

Avec :
- `Bfr` : besoin annuel de refroidissement (kWh)
- `Bfr_j` : besoin de refroidissement sur le mois j (kWh)

## 10.2 Calcul du besoin mensuel de froid

Le besoin mensuel de refroidissement depend du ratio de bilan thermique R(util_j) sur le mois j :

```
R(util_j) = (Ai_fr_j + As_fr_j) / (GV * (Text(moy_clim_j) - Tint) * Nref_j)
```

Avec :
| Variable | Description |
|----------|-------------|
| `Ai_fr_j` | Apports internes sur le mois j sur la période de refroidissement (Wh) - calculés au paragraphe 6.1 |
| `As_fr_j` | Apports solaires sur le mois j sur la période de refroidissement (Wh) - calculés au paragraphe 6.1 |
| `GV` | Transfert thermique à travers l'enveloppe et le renouvellement d'air (W/K). Le GV prend en compte les échanges de chaleur par le renouvellement d'air. Ces échanges sont calculés sur la période de refroidissement de la même façon que pour la période de chauffage |
| `Tint` | Temperature de consigne en froid (°C) égale a 28°C ou 26°C selon le comportement traité |
| `Text(moy_clim_j)` | Temperature extérieure moyenne sur le mois j pendant les périodes de climatisation (°C) |

### Besoin mensuel de refroidissement Bfr_j

Si `1/futi_j >= R(util_j)` alors :
```
Bfr_j = 0
```

Sinon :
```
Bfr_j = ((Ai_fr_j + As_fr_j) / 1000 - futi_j * (GV / 1000) * (Tint - Text(moy_clim_j))) * Nref_j
```

Avec :
- `Nref_j` : nombre d'heures de refroidissement pour le mois j, déterminé à partir des tableaux des paragraphes 18.2 et 18.3
  - Nref (28°C) pour une consigne de refroidissement a 28°C (comportement conventionnel)
  - Nref (26°C) pour une consigne de refroidissement a 26°C (comportement dépasseur)
- `futi_j` : facteur d'utilisation des apports sur le mois j

### Facteur d'utilisation futi_j

Si `R(util_j) != 1` :
```
futi_j = (1 - R(util_j)^(-a)) / (1 - R(util_j)^(-(a+1)))
```

Si `R(util_j) = 1` :
```
futi_j = a / (a + 1)
```

Avec :
```
a = 1 + tau / 15
```

- `tau` : constante de temps de la zone pour le refroidissement (h)

```
tau = C(th) / (3600 * GV)
```

- `C(th)` : Capacite thermique intérieure efficace de la zone (J/K)

| Inertie | C(th) (J/K) |
|---------|-------------|
| Légère | 110 000 * Sref |
| Moyenne | 165 000 * Sref |
| Lourde ou tres lourde | 260 000 * Sref |

## 10.3 Les consommations de refroidissement

### Données d'entrée

- Performance de l'installation de refroidissement (SEER ou année d'installation)
- Zone climatique
- Surface de référence
- Surface de référence refroidie

### Formule

La consommation de refroidissement est :

```
Cfr = 0.9 * Bfr / EER
```

Avec :
- `0.9` : coefficient d'intermittence pour le froid
- `EER` : coefficient d'efficacité énergétique. Il représente la performance de l'installation de refroidissement :

```
EER = 0.95 * SEER
```

### SEER : coefficient d'efficacité énergétique saisonnier

| SEER | Avant 2008 | 2008-2014 | À partir de 2015 |
|------|-----------|----------|-----------------|
| Zone H1 et H2 | 3.6 | 6.5 | 6.7 |
| Zone H3 | 3.25 | 5.7 | 7.5 |

*EER = coefficient SEER si disponible

Si le coefficient SEER du système de refroidissement est connu et justifié, le saisir directement.

La consommation de refroidissement est déterminée pour le logement entier. Si seule une partie du logement est refroidie, alors la consommation de refroidissement du logement est obtenue en multipliant la consommation de froid calculée pour le logement entier par le rapport de la surface de référence de la partie refroidie a celle du logement.

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 10 a 10.3 (pages 66-68)
