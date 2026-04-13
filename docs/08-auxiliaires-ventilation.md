# 5. Calcul des consommations d'auxiliaires de ventilation

## Données d'entrée

- Type de VMC
- Type de bâtiment
- Surface habitable

## Formule principale

La consommation annuelle d'auxiliaires de ventilation (kWhe/an) est donnée par la formule :

```
Caux_v = 8760 * Pvent_moy / 1000
```

### Avec

- `Pvent_moy` : puissance moyenne des auxiliaires (W)

## Puissance Pvent_moy en maison individuelle

| Pvent_moy | jusqu'a 2012 | Apres 2012 |
|-----------|-------------|------------|
| Simple Flux Auto | 15 W THC | 15 W THC |
| Simple Flux Hygro | 50 W THC | 15 W THC |
| Double Flux | 80 W THC | 35 W THC |

Les puissances d'auxiliaires tabulées ci-dessus pour les VMC double flux integrent les puissances de soufflage et de l'extraction.

## Puissance Pvent_moy en immeuble collectif

```
Pvent_moy = Pvent * Qvarep_conv * Sh
```

Avec :
- `Qvarep_conv` : débit d'air extrait conventionnel par unite de surface habitable (m³/(h.m²)) (voir chapitre 4)
- `Sh` : surface habitable (m²)
- `Pvent` : puissance des auxiliaires (kh/(m³/h)) :

| | Pvent | |
|---|---|---|
| | jusqu'a 2012 | Apres 2012 |
| Simple Flux Auto réglable | 0.46 W THC/(m³/h) | 0.25 W THC/(m³/h) |
| Simple Flux Hygro réglable | 0.46 W THC/(m³/h) | 0.25 W THC/(m³/h) |
| Double Flux Auto réglable | 1.1 W THC/(m³/h) | 0.5 W THC/(m³/h) |

Les puissances d'auxiliaires des VMC basse pression sont les mêmes que pour les VMC classiques.

Les puissances d'auxiliaires tabulées ci-dessus pour les VMC double flux integrent les puissances de soufflage et de l'extraction.

## Ventilation hybride

On considéré que le système bascule d'un mode mecanique à un mode naturel et inversement. Les consommations d'auxiliaires sont liees pendant le mode de fonctionnement mecanique.

Par défaut la duree de fonctionnement de l'extracteur mecanique est prise pour le mode grand débit.

| | Ratio du temps d'utilisation en grand débit (en h/semaine) |
|---|---|
| Collectif | 28 |
| Individuel | 14 |

Les consommations d'auxiliaires pour une VMC hybride correspondent aux consommations d'une VMC classique autoreglable d'avant 2012 multipliees par le ratio du temps d'utilisation :

| | Ratio du temps d'utilisation du mode mecanique |
|---|---|
| Collectif | 0.167 |
| Individuel | 0.083 |

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Section** : 5 (pages 40-41)
