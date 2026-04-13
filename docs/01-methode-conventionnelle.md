# 1. La méthode conventionnelle

## Objectif

Le DPE a pour principal objectif d'informer sur la performance énergétique des bâtiments. Il affiche le bilan annuel des consommations de chauffage, d'eau chaude sanitaire, de refroidissement, d'éclairage et des auxiliaires. Il conduit aussi à une estimation des émissions de gaz à effet de serre associée aux consommations des 5 usages précédents.

## Principes fondamentaux

Les informations communiquées par le DPE doivent permettre de comparer objectivement les différents bâtiments entre eux. Pour cela, la méthode utilise des **conditions climatiques moyennes** et un **comportement conventionnel des occupants**.

### Hypothèses conventionnelles principales

- La consommation d'une maison individuelle occupée par une famille de 3 personnes, la consommation de cette même maison ne sera pas la même si elle est occupée par une famille de 5 personnes
- De plus, que l'on chauffé a 19°C ou 21°C, les consommations du même bâtiment peuvent significativement fluctuer
- Le DPE est fait principalement par une méthode de calcul des consommations conventionnelles, s'appuyant sur une utilisation standardisée du bâtiment pour des conditions climatiques moyennes du lieu

### Critères de la méthode conventionnelle

- On présume un système de chauffage dans le bâtiment ainsi que les expositions mobiles et les cheminées à foyer ouvert. Toute la surface habitable du logement est considérée chauffée en permanence pendant la période de chauffe
- Les besoins de chauffage sont calculés mensuellement à partir de degrés heures base 19 pour des météos représentatives du climat des 8 zones climatiques de la France métropolitaine. Les degrés heures sont égaux à la somme, pour toutes les heures de la saison de chauffage pendant lesquelles la température extérieure est inférieure a 19°C. Le pronostic prend en compte une inoccupation de 7 jours en décembre (dernière semaine) pendant la période de chauffé ainsi qu'un rabat des températures a 11°C pendant la journée en semaine
- Le besoin d'ECS est forfaitaire selon la surface habitable du bâtiment et la zone climatique. Dans le calcul du besoin d'ECS, une semaine d'absence est comptée au mois de décembre
- Les besoins de refroidissement sont calculés mensuellement sur les périodes ou la température extérieure dépasse 28°C



# 2. Expression du besoin de chauffage

## Définition

**BV_j** : besoin mensuel de chauffage d'un logement, divisé par l'écart moyen de température entre l'intérieur et l'extérieur durant la période de chauffage. Son calcul se fait à partir du coefficient GV en tenant compte des apports de chaleur dus à l'occupation et au rayonnement solaire. Il est exprimé en watts par kelvin (W/K).

## Formule principale

```
BV_j = GV * (1 - F_j)
```

### Variables

| Variable | Description | Référence |
|----------|-------------|-----------|
| `GV` | Déperditions de l'enveloppe en W/K | voir partie 3 |
| `F_j` | Fraction des besoins de chauffage couverts par les apports gratuits sur le mois j | voir partie 6.1 |

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 1 (page 6) et 2 (page 6)
