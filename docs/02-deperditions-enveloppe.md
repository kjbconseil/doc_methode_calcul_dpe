# 3. Calcul des déperditions de l'enveloppe GV

## Données d'entrée

- Caractéristiques de l'enveloppe (linéaires, surfaces, U)
- Surface des parois déperditives (murs, plafonds, planchers, baies, portes)
- Linéaires de ponts thermiques

## Formule principale

La somme GV des déperditions par les parois et par renouvellement d'air (W/K) s'exprime de la manière suivante :

```
GV = DPmur + DPplancher_bas + DPplancher_haut + DPmenuiserie + PT + DR
```

### Avec

| Variable | Description |
|----------|-------------|
| `PT` | Déperditions par les ponts thermiques (W/K) - voir partie 3.4 |
| `DR` | Déperditions par le renouvellement d'air (W/K) - voir partie 4 |
| `DPparoi` | Déperdition par la paroi (W/K) |

## Décomposition des déperditions par paroi

### Murs

```
DPmur = SUM(b_i * Smur_i * Umur_i)
```

### Planchers bas

```
DPplancher_bas = SUM(b_i * Spb_i * Upb_i)
```

### Planchers hauts

```
DPplancher_haut = SUM(b_i * Sph_i * Uph_i)
```

### Menuiseries (fenêtres, portes-fenêtres, portes)

```
DPmenuiserie = SUM(b_i * Smenuiserie_i * Umenuiserie_i)
```

### Variables communes

| Variable | Description |
|----------|-------------|
| `b_i` | Coefficient de réduction des déperditions pour la paroi i - voir partie 3.1 |
| `Sparoi_i` | Surface de la paroi déperditive i (m²) |
| `Uparoi_i` | Coefficient de transmission thermique de la paroi i (W/(m².K)) - voir parties 3.2 et 3.3 |

## Règles importantes

- On appelle menuiserie l'ensemble vitrage + protection solaire des fenêtres, portes-fenêtres et portes
- **Attention** : les parois donnant sur un bâtiment autre que d'habitation sont aussi considérées déperditives
- La surface prise en compte pour l'établissement du DPE est la **surface habitable** du bâtiment. Cette surface intègre les vérandas chauffées
- En présence d'un espace non habitable chauffé (par exemple un garage ou un sous-sol), cet espace est traité dans le DPE comme un espace non chauffé. Dans ce cas, le diagnostiqueur devra obligatoirement mentionner dans le rapport que cet espace ne doit pas être chauffé et intégrer ce commentaire dans la justification des écarts entre les factures et les consommations conventionnelles

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Section** : 3 (page 7)
