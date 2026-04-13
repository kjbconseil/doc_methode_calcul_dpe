# Documentation de la méthode de calcul 3CL-DPE 2021

## Objectif

Ce repository contient une transcription structurée en Markdown de la **méthode de calcul 3CL-DPE 2021**, telle que définie dans l'**Annexe 1 de l'arrêté du 31 mars 2021** relatif aux méthodes et procédures applicables au diagnostic de performance énergétique.

L'objectif est de disposer d'une version lisible, exploitable et navigable de cette méthode de calcul, afin de pouvoir l'implémenter dans un moteur de calcul logiciel.

## Sources officielles

Les documents sources sont publiés au **Journal Officiel de la République Française** :

1. **Arrêté du 31 mars 2021** relatif aux méthodes et procédures applicables au diagnostic de performance énergétique et aux logiciels l'établissant
   - NOR : LOGL2106175A (JO du 13 avril 2021, Texte 29 sur 114)

2. **Arrêté du 8 octobre 2021** modifiant la méthode de calcul et les modalités d'établissement du DPE
   - NOR : LOGL2118341A (JO du 14 octobre 2021, Texte 34 sur 140)
   - Remplace intégralement l'Annexe 1 (Méthode de calcul 3CL-DPE 2021)

3. **Arrêté du 25 mars 2024** modifiant les seuils des étiquettes du DPE pour les logements de petites surfaces et actualisant les tarifs annuels de l'énergie
   - NOR : TREL2330369A (JO du 20 avril 2024)
   - Entrée en vigueur : 1er juillet 2024

4. **Arrêté du 13 août 2025** modifiant le facteur de conversion de l'énergie finale en énergie primaire de l'électricité
   - NOR : ATDL2519132A (JO du 26 août 2025)
   - Entrée en vigueur : 1er janvier 2026

> La documentation intègre l'ensemble de ces modifications. L'historique des changements est détaillé dans [docs/CHANGELOG.md](docs/CHANGELOG.md).

## Contenu

Chaque fichier Markdown correspond à une section thématique de la méthode de calcul. Le sommaire complet est dans [docs/00-sommaire.md](docs/00-sommaire.md).

### Méthode 3CL (Annexe 1)

| Fichier | Section |
|---------|---------|
| [01-methode-conventionnelle.md](docs/01-methode-conventionnelle.md) | Principes de la méthode conventionnelle et expression du besoin de chauffage |
| [02-deperditions-enveloppe.md](docs/02-deperditions-enveloppe.md) | Calcul des déperditions de l'enveloppe GV |
| [03-coefficient-reduction-b.md](docs/03-coefficient-reduction-b.md) | Coefficient de réduction des déperditions b |
| [04-parois-opaques-umur.md](docs/04-parois-opaques-umur.md) | Calcul des U des parois opaques (Umur, Upb, Uph) |
| [05-parois-vitrees-portes.md](docs/05-parois-vitrees-portes.md) | Calcul des U des parois vitrées et des portes |
| [06-ponts-thermiques.md](docs/06-ponts-thermiques.md) | Calcul des déperditions par les ponts thermiques |
| [07-deperditions-renouvellement-air.md](docs/07-deperditions-renouvellement-air.md) | Déperditions par renouvellement d'air |
| [08-auxiliaires-ventilation.md](docs/08-auxiliaires-ventilation.md) | Consommations d'auxiliaires de ventilation |
| [09-apports-gratuits.md](docs/09-apports-gratuits.md) | Détermination des apports gratuits et surface Sud équivalente |
| [10-inertie.md](docs/10-inertie.md) | Détermination de l'inertie |
| [11-intermittence.md](docs/11-intermittence.md) | Modélisation de l'intermittence |
| [12-consommation-chauffage.md](docs/12-consommation-chauffage.md) | Calcul de la consommation de chauffage (Cch) |
| [13-consommation-froid.md](docs/13-consommation-froid.md) | Calcul de la consommation de froid (Cfr) |
| [14-consommation-ecs.md](docs/14-consommation-ecs.md) | Calcul de la consommation d'ECS (Cecs) |
| [15-rendements-installations.md](docs/15-rendements-installations.md) | Rendements des installations (émission, distribution, régulation) |
| [16-rendement-generation-combustion.md](docs/16-rendement-generation-combustion.md) | Rendement de génération des générateurs à combustion |
| [17-rendement-generation-ecs.md](docs/17-rendement-generation-ecs.md) | Rendement des générateurs d'ECS |
| [18-auxiliaires-installations.md](docs/18-auxiliaires-installations.md) | Consommations d'auxiliaires des installations |
| [19-eclairage-photovoltaique.md](docs/19-eclairage-photovoltaique.md) | Éclairage et production d'électricité photovoltaïque |
| [20-dpe-collectif.md](docs/20-dpe-collectif.md) | DPE dans le collectif |

### Données climatiques (Annexe 1, section 18)

| Fichier | Section |
|---------|---------|
| [21-donnees-climatiques.md](docs/21-donnees-climatiques.md) | Zones climatiques et données de référence (index) |
| [21a-donnees-climat-inf400m.md](docs/21a-donnees-climat-inf400m.md) | Données climatiques altitude < 400m |
| [21b-donnees-climat-400-800m.md](docs/21b-donnees-climat-400-800m.md) | Données climatiques altitude 400-800m |
| [21c-donnees-climat-sup800m.md](docs/21c-donnees-climat-sup800m.md) | Données climatiques altitude >= 800m |
| [21d-donnees-climat-inertie-lourde.md](docs/21d-donnees-climat-inertie-lourde.md) | Données bâtiments inertie lourde (parois anciennes) |
| [21e-facteur-solaire-coefficients-c1.md](docs/21e-facteur-solaire-coefficients-c1.md) | Facteur de couverture solaire + coefficients C1 |

### Annexes de l'arrêté DPE

| Fichier | Annexe |
|---------|--------|
| [22-etiquettes-energie-climat.md](docs/22-etiquettes-energie-climat.md) | Annexe 5 - Étiquettes énergie et climat (seuils des classes DPE) |
| [23-tarifs-energie.md](docs/23-tarifs-energie.md) | Annexe 7 - Évaluation des frais annuels d'énergie |
| [24-facteurs-conversion-energie-primaire.md](docs/24-facteurs-conversion-energie-primaire.md) | Annexe 3 - Facteurs de conversion énergie finale vers énergie primaire |
| [25-facteurs-emission-ges.md](docs/25-facteurs-emission-ges.md) | Annexe 4 - Facteurs d'émission de gaz à effet de serre |

### Changelog

| Fichier | Contenu |
|---------|---------|
| [CHANGELOG.md](docs/CHANGELOG.md) | Historique des modifications réglementaires (octobre 2021, mars 2024, août 2025) |

## Avertissement

Cette documentation est une **transcription à des fins d'implémentation logicielle**. Bien que chaque effort ait été fait pour retranscrire fidèlement les formules, tableaux et règles de la méthode officielle, **le document source du Journal Officiel fait foi** en cas de doute ou de divergence.

## Licence

Voir le fichier [LICENSE](LICENSE).
