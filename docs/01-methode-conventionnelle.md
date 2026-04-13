# 1. La méthode conventionnelle

## Objectif

Le DPE a pour principal objectif d'informer sur la performance énergétique des bâtiments. Il affiche le bilan annuel des consommations de chauffage, d'eau chaude sanitaire, de refroidissement, d'éclairage et des auxiliaires. Il conduit aussi à une estimation des émissions de gaz à effet de serre associée aux consommations des 5 usages précédents.

## Principes fondamentaux

Les informations communiquées par le DPE doivent permettre de comparer objectivement les différents bâtiments entre eux. Prenons le cas d'une maison individuelle occupée par une famille de 3 personnes, la consommation de cette même maison ne sera pas la même si elle est occupée par une famille de 5 personnes. De plus, selon que l'on chauffe à 19°C ou 21°C, les consommations du même bâtiment peuvent significativement fluctuer. Il est dès lors nécessaire dans l'établissement de ce diagnostic de s'affranchir du comportement des occupants afin d'avoir une information sur la qualité énergétique du bâtiment. C'est la raison pour laquelle l'établissement du DPE est fait principalement par une méthode de calcul des consommations conventionnelles. Elle s'appuie sur une utilisation standardisée du bâtiment pour des conditions climatiques moyennes du lieu.

### Critères de la méthode conventionnelle

- On présume un système de chauffage dans le bâtiment ainsi que les équipements mobiles et les cheminées à foyer ouvert. Toute la surface habitable du logement est considérée chauffée en permanence pendant la période de chauffe
- Les besoins de chauffage sont calculés mensuellement à partir de degrés heures base 19 pour des météos représentatives du climat des 8 zones climatiques de la France métropolitaine. Les degrés heures sont égaux à la somme, pour toutes les heures de la saison de chauffage pendant laquelle la température extérieure est inférieure à 19°C. Ils prennent en compte une inoccupation de 7 jours en décembre (dernière semaine) pendant la période de chauffe ainsi qu'un réduit des températures à **16°C** pendant la journée en semaine
- Le besoin d'ECS est forfaitaire selon la surface habitable du bâtiment et la zone climatique. Dans le calcul du besoin d'ECS, une semaine d'absence est comptée au mois de décembre
- Les besoins de refroidissement sont calculés mensuellement sur les périodes où la température extérieure est supérieure à 28°C

Ces caractéristiques du calcul conventionnel peuvent être responsables de différences importantes entre les consommations réelles facturées et celles calculées avec la méthode conventionnelle. En effet, tout écart entre les hypothèses du calcul conventionnel et le scénario réel d'utilisation du bâtiment entraîne des différences au niveau des consommations. De plus, certaines caractéristiques impactant les consommations du bâtiment ne sont connues que de façon limitée (par exemple : les rendements des chaudières qui dépendent de leur dimensionnement et de leur entretien, la qualité de mise en œuvre du bâtiment, le renouvellement d'air dû à la ventilation, etc.).

# 2. Expression du besoin de chauffage

## Définition

**BV_j** : besoins mensuels de chauffage d'un logement, divisés par l'écart moyen de température entre l'intérieur et l'extérieur durant la période de chauffage. Son calcul se fait à partir du coefficient GV en tenant compte des apports de chaleur dus à l'occupation et au rayonnement solaire. Il est exprimé en watts par kelvin (W/K).

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

- **Source** : Arrêté du 31 mars 2021 modifié par l'arrêté du 8 octobre 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 1 (page 6) et 2 (page 6)
