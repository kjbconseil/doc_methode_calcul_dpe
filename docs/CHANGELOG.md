# Changelog réglementaire - Méthode 3CL-DPE

Historique des modifications apportées à la méthode de calcul DPE par les arrêtés successifs.

## Mars 2024 - Petites surfaces et tarifs d'énergie

**Arrêté du 25 mars 2024** modifiant les seuils des étiquettes du diagnostic de performance énergétique pour les logements de petites surfaces et actualisant les tarifs annuels de l'énergie.

- NOR : TREL2330369A
- Publié au Journal Officiel le 20 avril 2024, Texte 15 sur 101
- Entrée en vigueur : 1er juillet 2024

### Modifications

- **Surface de référence** : le terme « surface habitable » (Sh) est remplacé par « surface de référence » (Sref) dans l'ensemble de la méthode. La surface de référence inclut la surface habitable + vérandas chauffées + locaux chauffés d'occupation humaine (h >= 1,80 m)
- **Seuils d'étiquettes petites surfaces** : nouveaux seuils CEP/EGES pour les logements dont Sref <= 40 m², par interpolation linéaire (voir [22-etiquettes-energie-climat.md](22-etiquettes-energie-climat.md))
- **Tarifs d'énergie** : mise à jour de l'annexe 7 avec les prix 2022-2023 (voir [23-tarifs-energie.md](23-tarifs-energie.md))
- **Attestation de reclassement** : les DPE réalisés entre le 1er juillet 2021 et le 30 juin 2024 pour des logements <= 40 m² peuvent obtenir une attestation de nouvelle étiquette via l'Observatoire DPE-Audit de l'ADEME

---

## Octobre 2021 - Mise à jour de la méthode 3CL-DPE 2021

**Arrêté du 8 octobre 2021** modifiant la méthode de calcul et les modalités d'établissement du diagnostic de performance énergétique.

- NOR : LOGL2118341A
- Publié au Journal Officiel le 14 octobre 2021, Texte 34 sur 140
- Entrée en vigueur : au lendemain de sa publication

L'Art. 2, 2° remplace intégralement l'Annexe « Méthode de calcul 3CL-DPE 2021 » par une version mise à jour.

### Section 1 - La méthode conventionnelle

- Ajout de la mention « ou indirecte » après « directe » concernant les déperditions par les parois vitrées
- Ajout d'un paragraphe détaillant les limites du calcul conventionnel (différences avec les consommations réelles)

### Section 3.1 - Coefficient de réduction des déperditions b

- **Nouvelle règle** : « Dans le cas où Aue = 0, alors b = 0 »
- **Tableau Uv_ue modifié** pour le logement collectif :

| Local non chauffé (collectif) | Uv_ue Mars 2021 | Uv_ue Octobre 2021 |
|-------------------------------|-----------------|-------------------|
| Circulation commune sans ouverture directe sur l'extérieur | 0.5 | **0.0** |
| Circulation commune avec ouverture directe sur l'extérieur | 5 | **0.3** |
| Circulation commune avec bouche/gaine de désenfumage | variable | **1** |
| Hall d'entrée | 3 | **3(1) ou 0.3(2)** |

*(1) Portes d'accès sans dispositif de fermeture automatique*
*(2) Portes d'accès avec dispositif de fermeture automatique*

- **Tableau b_vu des vérandas modifié** : les valeurs ont été recalculées pour toutes les zones climatiques

| Zone | Orientation | Paroi | b_vu Mars 2021 | b_vu Octobre 2021 |
|------|------------|-------|---------------|------------------|
| H1 | Nord | Non isolé | 0.85 | **0.95** |
| H1 | Nord | Isolé | 0.65 | **0.85** |
| H1 | Est/Ouest | Non isolé | 0.6 | **0.6** |
| H1 | Est/Ouest | Isolé | 0.4 | **0.58** |
| H1 | Sud | Non isolé | 0.55 | **0.55** |
| H1 | Sud | Isolé | 0.18 | **0.63** |
| H2 | Nord | Non isolé | 0.85 | **0.95** |
| H2 | Nord | Isolé | 0.65 | **0.85** |
| H2 | Est/Ouest | Non isolé | 0.58 | **0.6** |
| H2 | Est/Ouest | Isolé | 0.5 | **0.58** |
| H2 | Sud | Non isolé | 0.55 | **0.57** |
| H2 | Sud | Isolé | 0.35 | **0.17** |
| H3 | Nord | Non isolé | 0.95 | **0.95** |
| H3 | Nord | Isolé | 0.85 | **0.85** |
| H3 | Est/Ouest | Non isolé | 0.55 | **0.53** |
| H3 | Est/Ouest | Isolé | 0.5 | **0.53** |
| H3 | Sud | Non isolé | 0.6 | **0.4** |
| H3 | Sud | Isolé | 0.55 | **0.55** |

### Section 3.2 - Parois opaques

- Ajout des toitures en bac acier traitées comme des combles aménagés sous rampants : Uph0 = 2.5 W/(m².K)

### Section 4 - Déperditions par renouvellement d'air

- **Ventilation par ouverture des fenêtres** : Qvarep_conv passé de **2.60** à **1.2** m³/(h.m²)
- **Nouveau type ajouté** : « Ventilation naturelle par conduit avec entrées d'air hygro » : Qvarep_conv = 2.23, Smea_conv = 4
- **Nouvelle règle pour Q4Pa_conv** : Pour les bâtiments construits avant 1948 et dont les menuiseries possèdent des joints, Q4Pa_conv = 2.5 m³/(h.m²). Cette condition est respectée si les menuiseries représentant plus de 50% de la surface totale possèdent des joints.

### Section 6.1 - Apports gratuits

- **Scénario d'occupation modifié** :
  - Ancien : 113h d'occupation, 55h d'inoccupation
  - Nouveau : **133h d'occupation** dont 56h de sommeil, **36h d'inoccupation** (sur 168h = 1 semaine)
- **Formule Ai_j mise à jour** avec le nouveau ratio d'occupation :
  ```
  Ai_j = ((3.18 + 0.34) * Sh + 90 * (132/168) * N_adeq) * Nref_j
  ```
  (le ratio 172/168 de Mars est remplacé par **132/168**)

### Section 7.4 - Inertie du bâtiment

- Ajout d'un nouveau critère pour paroi verticale lourde : **Mur sandwich (béton / isolant / béton)**
- **Tableau d'inertie modifié** - ajout d'une ligne :
  - `- | Lourd | Lourde → Lourde` (plancher bas non lourd, plancher haut lourd, paroi verticale lourde = Lourde)

### Section 8 - Intermittence

- **Nouvelle règle** : Un plancher chauffant avec une régulation zone jour/zone nuit peut être associé à une régulation pièce par pièce
- **Nouvelle règle** : Un poêle sera modélisé comme un radiateur/convecteur pour la détermination de l'intermittence

### Sections 9 à 17 - Consommations

- Structure et formules globalement inchangées
- Ajustements mineurs de rédaction et clarifications

### Art. 1 de l'arrêté (modifications de l'arrêté DPE du 31 mars 2021)

Ces modifications portent sur les annexes de l'arrêté DPE (non la méthode 3CL elle-même) :

1. Protection solaire : exception pour les baies orientées Sud, Est et Ouest dont la surface est strictement inférieure à 0.7 m² et si celles-ci représentent moins de 10% de la surface totale de baie
2. Recommandations : remplacement de « en dernier étage » par « possédant un plafond déperdif »
3. Collectif avec chauffage mixte : dans le cas où un bâtiment est équipé d'un système de chauffage collectif et d'un système de chauffage individuel, les calculs sont réalisés pour chacun des systèmes puis additionnés
4. Tableau nj (jours d'occupation par mois) ajouté explicitement à l'annexe 14
5. Tableaux des tarifs de l'Électricité et du gaz naturel ajoutés (1er janvier 2021)
