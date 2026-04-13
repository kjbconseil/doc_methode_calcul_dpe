# Documentation de la méthode de calcul 3CL-DPE 2021

## Objectif

Ce repository contient une transcription structuree en Markdown de la **méthode de calcul 3CL-DPE 2021**, telle que définie dans l'**Annexe 1 de l'arrêté du 31 mars 2021** relatif aux méthodes et procedures applicables au diagnostic de performance énergétique.

L'objectif est de disposer d'une version lisible, exploitable et navigable de cette méthode de calcul, afin de pouvoir l'implementer dans un moteur de calcul logiciel.

## Sources officielles

Les documents sources sont publiés au **Journal Officiel de la République Française** :

1. **Arrêté du 31 mars 2021** relatif aux méthodes et procédures applicables au diagnostic de performance énergétique et aux logiciels l'établissant
   - NOR : LOGL2106175A (JO du 13 avril 2021, Texte 29 sur 114)
   - [Télécharger le PDF sur Légifrance](https://www.legifrance.gouv.fr/download/pdf?id=doxMrRr0wbfJVvtWjfDP4rj1eH6w-xJoB6-2bmLS9gg=)

2. **Arrêté du 8 octobre 2021** modifiant la méthode de calcul et les modalités d'établissement du DPE
   - NOR : LOGL2118341A (JO du 14 octobre 2021, Texte 34 sur 140)
   - Remplace intégralement l'Annexe 1 (Méthode de calcul 3CL-DPE 2021)

> La documentation ci-dessous intègre les modifications d'octobre 2021. Les changements sont détaillés dans [docs/CHANGELOG-octobre-2021.md](docs/CHANGELOG-octobre-2021.md).

## Contenu

Chaque fichier Markdown correspond à une section thematique de la méthode de calcul :

| Fichier | Section |
|---------|---------|
| [00-sommaire.md](docs/00-sommaire.md) | Index general |
| [01-méthode-conventionnelle.md](docs/01-méthode-conventionnelle.md) | Principes de la méthode conventionnelle et expression du besoin de chauffage |
| [02-déperditions-enveloppe.md](docs/02-déperditions-enveloppe.md) | Calcul des déperditions de l'enveloppe GV |
| [03-coefficient-reduction-b.md](docs/03-coefficient-reduction-b.md) | Coefficient de reduction des déperditions b |
| [04-parois-opaques-umur.md](docs/04-parois-opaques-umur.md) | Calcul des U des parois opaques (Umur, Upb, Uph) |
| [05-parois-vitrees-portes.md](docs/05-parois-vitrees-portes.md) | Calcul des U des parois vitrees et des portes |
| [06-ponts-thermiques.md](docs/06-ponts-thermiques.md) | Calcul des déperditions par les ponts thermiques |
| [07-déperditions-renouvellement-air.md](docs/07-déperditions-renouvellement-air.md) | Déperditions par renouvellement d'air |
| [08-auxiliaires-ventilation.md](docs/08-auxiliaires-ventilation.md) | Consommations d'auxiliaires de ventilation |
| [09-apports-gratuits.md](docs/09-apports-gratuits.md) | Détermination des apports gratuits et surface Sud equivalente |
| [10-inertie.md](docs/10-inertie.md) | Détermination de l'inertie |
| [11-intermittence.md](docs/11-intermittence.md) | Modélisation de l'intermittence |
| [12-consommation-chauffage.md](docs/12-consommation-chauffage.md) | Calcul de la consommation de chauffage (Cch) |
| [13-consommation-froid.md](docs/13-consommation-froid.md) | Calcul de la consommation de froid (Cfr) |
| [14-consommation-ecs.md](docs/14-consommation-ecs.md) | Calcul de la consommation d'ECS (Cecs) |
| [15-rendements-installations.md](docs/15-rendements-installations.md) | Rendements des installations (émission, distribution, régulation) |
| [16-rendement-génération-combustion.md](docs/16-rendement-génération-combustion.md) | Rendement de génération des générateurs a combustion |
| [17-rendement-génération-ecs.md](docs/17-rendement-génération-ecs.md) | Rendement des générateurs d'ECS |
| [18-auxiliaires-installations.md](docs/18-auxiliaires-installations.md) | Consommations d'auxiliaires des installations |
| [19-éclairage-photovoltaique.md](docs/19-éclairage-photovoltaique.md) | Éclairage et production d'électricité photovoltaique |
| [20-dpe-collectif.md](docs/20-dpe-collectif.md) | DPE dans le collectif |
| [21-donnees-climatiques.md](docs/21-donnees-climatiques.md) | Zones climatiques et donnees annexes |

## Avertissement

Cette documentation est une **transcription à des fins d'implementation logicielle**. Bien que chaque effort ait ete fait pour retranscrire fidèlement les formules, tableaux et regles de la méthode officielle, **le document source du Journal Officiel fait foi** en cas de doute ou de divergence. Certains tableaux de valeurs numeriques volumineux (donnees climatiques mensuelles, coefficients C1 par zone) sont références mais non intégralement reproduits ici : se reporter aux pages 117-148 de l'annexe officielle.

## Licence

Voir le fichier [LICENSE](LICENSE).
