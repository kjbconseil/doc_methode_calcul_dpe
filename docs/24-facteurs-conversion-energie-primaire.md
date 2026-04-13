# Facteurs de conversion des énergies finales en énergie primaire

> Annexe 3 de l'arrêté du 31 mars 2021, modifiée par l'arrêté du 13 août 2025

Les facteurs de conversion de l'énergie finale (exprimée en kilowattheures de pouvoir calorifique inférieur) en énergie primaire sont les suivants :

| Énergie | Facteur de conversion |
|---------|----------------------|
| Électricité | **1,9** |
| Autres énergies | 1 |

## Application

La consommation d'énergie primaire (CEP) du logement est obtenue en multipliant chaque consommation d'énergie finale par le facteur de conversion correspondant, puis en sommant le tout :

```
CEP = SUM(Cef_i * coef_ep_i) / Sref
```

Avec :
- `Cef_i` : consommation d'énergie finale pour l'énergie i (kWh)
- `coef_ep_i` : facteur de conversion en énergie primaire pour l'énergie i
- `Sref` : surface de référence du logement (m²)

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 3
- **Modifié par** : Arrêté du 13 août 2025 (NOR : ATDL2519132A), en vigueur au 1er janvier 2026
- **Ancienne valeur** : 2,3 pour l'électricité (arrêté du 31 mars 2021 initial)
