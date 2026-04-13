# Facteurs de conversion des énergies finales en émissions de gaz à effet de serre

> Annexe 4 de l'arrêté du 31 mars 2021, renvoyant à l'annexe 4.1 de l'arrêté du 15 septembre 2006

Les facteurs de conversion des énergies finales en émissions de gaz à effet de serre sont exprimés en kg éqCO2 par kWh PCI d'énergie finale.

## Tableau des facteurs d'émission (annexe 4, partie 1.1)

| Énergie | Facteur (kg éqCO2/kWh PCI) |
|---------|---------------------------|
| Gaz naturel | 0.227 |
| Fioul domestique | 0.324 |
| Charbon | 0.385 |
| Gaz propane ou butane | 0.272 |
| Autres combustibles fossiles | 0.324 |
| Bois - Bûches | 0.03 |
| Bois - Granulés (pellets) ou briquettes | 0.03 |
| Bois - Plaquettes forestières | 0.024 |
| Bois - Plaquettes d'industrie | 0.024 |
| Électricité renouvelable produite sur site et autoconsommée | 0 |
| Électricité (hors autoconsommation) - Chauffage | 0.079 |
| Électricité (hors autoconsommation) - ECS | 0.065 |
| Électricité (hors autoconsommation) - Refroidissement | 0.064 |
| Électricité (hors autoconsommation) - Éclairage | 0.069 |
| Électricité (hors autoconsommation) - Auxiliaires | 0.064 |

Pour les **réseaux de chaleur et de froid**, les facteurs d'émission sont spécifiques à chaque réseau et définis dans l'annexe 7 de l'arrêté du 15 septembre 2006 (voir aussi annexe 13 de l'arrêté DPE habitation). Les valeurs sont disponibles sur le site de l'arrêté « contenu CO2 des réseaux ».

## Application

Les émissions de gaz à effet de serre (EGES) du logement sont obtenues en multipliant chaque consommation d'énergie finale par le facteur d'émission correspondant, puis en sommant le tout :

```
EGES = SUM(Cef_i * coef_ges_i) / Sref
```

Avec :
- `Cef_i` : consommation d'énergie finale pour l'usage i (kWh PCI)
- `coef_ges_i` : facteur d'émission GES pour l'énergie et l'usage i (kg éqCO2/kWh PCI)
- `Sref` : surface de référence du logement (m²)

Le résultat en kg éqCO2/(m².an) détermine la classe climat du logement (voir [22-etiquettes-energie-climat.md](22-etiquettes-energie-climat.md)).

## Équivalence en kilomètres parcourus (annexe 6)

Les émissions annuelles de GES du bien sont exprimées en nombre de kilomètres parcourus en voiture en divisant la quantité annuelle d'émissions (en kg éqCO2) par **0,193**.

## Sources

- **Source** : Annexe 4.1 de l'arrêté du 15 septembre 2006, modifiée par l'arrêté du 31 mars 2021 (NOR : LOGL2107220A, Art. 1 §9)
- **Annexe 6** : Expression des émissions en kilomètres parcourus
- **Annexe 13** : Contenu CO2 des réseaux de chaleur et de froid
