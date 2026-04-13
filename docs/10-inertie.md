# 7. Détermination de l'inertie

## 7.1 Plancher haut lourd

Un plancher haut est lourd si :
- Plancher sous toiture (terrasse, combles perdus, rampant lourd) non isolé par l'extérieur et sans faux plafond (*) et constitue de :
  - Beton plein de plus de 8 cm
  - Poutrelles et hourdis beton ou terre cuite
- Sous-face de plancher intermédiaire sans isolant et sans faux plafond (*) constitue de :
  - Beton plein de plus de 15 cm
  - Poutrelles et hourdis beton ou sans curer

(*) Ne sont concernes que les faux plafonds possedant une lame d'air non ventilée ou l'isolement ventilé (enceinte ou 1 500 mm² d'ouverture par m² de surface), couvrant plus de la moitie de la surface du plafond de niveaux concernes.

Un plancher haut dont l'inertie est inconnue est considéré par défaut a **inertie légère**.

## 7.2 Plancher bas lourd

Un plancher bas est lourd si :
- Face supérieure de plancher intermédiaire avec un revetement non isolant constitue de :
  - Beton plein de plus de 15 cm avec isolation
  - Chape ou dalle de beton de 4 cm ou plus sur entrevous lourds (beton, terre cuite), ou beton cellulaire armee ou sur dalles alvéolées en beton
- Plancher bas non isolé ou avec un isolant thermique en sous-face et un revetement non isolant constitue de :
  - Beton plein de plus de 10 cm d'épaisseur
  - Chape ou dalle de beton de 4 cm ou plus sur entrevous lourds (beton, terre cuite), ou beton cellulaire arme ou sur dalles alvéolées en beton
  - Dalle de beton de 5 cm ou plus sur entrevous en materiaux isolant
  - Autres planchers dans un materiau lourd (pierre, brique ancienne, terre, ...) sans revetement isolant

Un plancher bas (autre que sur terre-plein) dont l'inertie est inconnue est considéré par défaut a **inertie lourde**.

## 7.3 Paroi verticale lourde

Une paroi verticale est dite lourde si elle remplit l'une ou l'autre des conditions suivantes :
- Lorsque les murs de facade, de pignon et de refends mitoyens sont non isolés ou isolés par l'extérieur avec un materiau constitutif :
  - Beton plein (bancher, bloc, préfabriqué) de 7 cm ou plus
  - Bloc agglomere beton 11 cm ou plus
  - Bloc perfoure en beton (ou autres materiaux lourds) : 10 cm ou plus
  - Bloc creux beton 11 cm ou plus
  - Brique pleine ou perforee 10.5 cm ou plus
- Tout materiau ancien lourd (pierre, brique ancienne, terre, pisee...)

### Conditions spécifiques pour les refends

- Murs exterieurs a isolation reportee de 30 cm minimum, avec un cloisonnement realise en bloc de beton, en brique pleinière enduite ou en carreau de platre de 5 cm minimum ou en beton cellulaire de 7 cm minimum
- Environ les trois quarts (en surface), des doublages interieurs des murs exterieurs et des murs de cloisonnements (parois interieures), font 5 cm minimum et sont realises en bloc de beton, brique enduite ou carreau de platre
- Lorsque la taille moyenne des locaux est inférieure a 30 m² :
  - Environ les trois quarts des murs de cloisonnement intérieur lourds, realises en :
    - Beton plein de 7 cm minimum
    - Bloc de beton creux ou perfore (ou autres materiaux lourds) de 10 cm minimum
    - Brique pleine ou perforee de 10.5 cm minimum
    - Autre brique de 15 cm minimum avec un enduit platre sur chaque face

Les murs inconnus sont considérés à l'**inertie légère**.

## 7.4 Inertie du bâtiment

La classe d'inertie est déterminée par la combinaison plancher bas / plancher haut / paroi verticale :

| Plancher bas | Plancher haut | Paroi verticale | Classe d'inertie |
|-------------|--------------|----------------|-----------------|
| Lourd | Lourd | Lourde | **Tres lourde** |
| Lourd | Lourd | - | **Lourde** |
| Lourd | - | Lourde | **Lourde** |
| Lourd | Lourd | - | **Lourde** |
| - | Lourd | - | **Moyenne** |
| Lourd | - | - | **Moyenne** |
| - | - | Lourde | **Moyenne** |
| - | - | - | **Légère** |

> `-` signifie que la paroi n'est **pas** lourde (ou que l'information n'est pas pertinente)

En présence de plusieurs types de murs, de planchers hauts ou de planchers bas, l'inertie de la paroi a considerer dans le tableau ci-dessus est donnée par celle des surfaces majoritaires.

### Pour un bâtiment de plusieurs niveaux (immeuble ou maison)

La démarche est la suivante :
1. Determiner l'inertie de chaque niveau
2. Considerer que l'inertie du bâtiment est celle la plus représentative en surface habitable
3. Pour les situations d'égalité, la règle est la suivante :

| Inertie des niveaux | | | Inertie bâtiment |
|--------------------|---|---|-----------------|
| Lourde | Moyenne | Légère | |
| X | X | X | Moyenne |
| X | X | | Lourde |
| X | | X | Moyenne |

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Section** : 7 (pages 52-53)
