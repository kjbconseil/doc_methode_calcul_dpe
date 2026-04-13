# 3.4 Calcul des déperditions par les ponts thermiques

## Données d'entrée

- Type d'isolation (ITI, ITE, ITR)
- Nombre de niveaux
- Nombre d'appartements
- Retour d'isolation autour des menuiseries (avec ou sans)
- Hauteur moyenne sous plafond
- Linéaires de pont thermique
- Position des menuiseries (nu extérieur, nu intérieur, tunnel)

## Formule principale

```
PT = SUM(k_pb(m,i) * l_pb(m,i)) + SUM(k_pi(m,i) * l_pi(m,i)) + SUM(k_rf(m,i) * b_rf(m,i))
     + SUM(k_ph(m,i) * l_ph(m,i)) + SUM(k_men(m,i) * l_men(m,i))
```

### Variables

| Variable | Description |
|----------|-------------|
| `k_pb(m,i)` | Valeur du pont thermique de la liaison plancher bas / mur (W/(m.K)) |
| `k_pi(m,i)` | Valeur du pont thermique de la liaison plancher intermédiaire / mur (W/(m.K)) |
| `k_refend` | Valeur du pont thermique de la liaison refend/mur (W/(m.K)) |
| `k_ph(m,i)` | Valeur du pont thermique de la liaison plancher haut / mur (W/(m.K)) |
| `k_men(m,i)` | Valeur du pont thermique de la liaison menuiserie / mur (W/(m.K)) |
| `l_pb(m,i)` | Longueur du pont thermique plancher bas / mur (m), il prend en compte les seuils des portes et porte-fenêtres |
| `l_pi(m,i)` | Longueur du pont thermique plancher intermédiaire / mur (m) |
| `l_ph(m,i)` | Longueur du pont thermique plancher haut / mur (m) |
| `l_rf(m,i)` | Longueur du pont thermique refend/mur (m) |
| `l_men(m,i)` | Longueur du pont thermique menuiserie / mur (m) |

## Calcul de la longueur des refends

En immeuble collectif d'habitation, la longueur totale forfaitaire du pont thermique refend/mur est :

```
l_rf(m,i) = 2 * Hsp * (Nb_app - Niv)
```

### Avec

| Variable | Description |
|----------|-------------|
| `Hsp` | Hauteur moyenne sous plafond (m) |
| `Nb_app` | Nombre d'appartements |
| `Niv` | Nombre de niveaux |

## Règles sur l'isolation

- Si le coefficient de transmission thermique U ou l'etat d'isolation d'une paroi est inconnu :
  - Pour les bâtiments d'avant 1975, la paroi est considérée comme non isolée
  - Pour les bâtiments construits à partir de 1975 :
    - Les murs sont considérés comme isolés par l'extérieur
    - Les plafonds sont considérés comme isolés par l'extérieur
    - Les planchers sur terre-plein sont considérés isolés par l'extérieur (en sous-face) à partir de 2001

- **ITI** : Isolation Thermique par l'Interieur
- **ITE** : Isolation Thermique par l'Exterieur
- **ITR** : respectivement isolation thermique intérieure, extérieure et repartie

- Si les valeurs des ponts thermiques sont connues et justifiees, les saisir directement pour le calcul, à l'exception des ponts thermiques négligés dans les valeurs par défaut
- Les ponts thermiques des parois au niveau des circulations communes ne sont pas pris en compte
- Aucun coefficient de réduction des températures (b) n'est applique aux ponts thermiques



## 3.4.1 Plancher bas / mur

Valeur du pont thermique de la liaison Plancher bas / Mur (W/(m.K))

| k_pb(m,i) | Plancher bas | | | |
|-------------|-------------|---|---|---|
| | Non isolé | ITI | ITE | ITI + ITE |
| **Mur extérieur** | | | | |
| Non isolé | 0.39 | 0.43 | 0.8 | 0.47 |
| ITI | 0.31 | 0.06 | 0.71 | 0.09 |
| ITE | 0.49 | 0.48 | 0.54 | 0.48 |
| ITR | 0.31 | 0.1 | 0.45 | 0.1 |
| ITI + ITE | 0.31 | 0.06 | 0.45 | 0.08 |
| ITE + ITR | 0.31 | 0.08 | 0.45 | 0.08 |
| ITI + ITR | 0.33 | 0.1 | 0.43 | 0.1 |

**Règles** :
- Pour les murs, s'il n'est pas possible de distinguer le type d'isolation (ITI, ITE...), prendre par défaut ITI
- Pour les planchers bas, s'il n'est pas possible de distinguer le type d'isolation (ITI, ITE...), prendre par défaut ITE
- Pour un plancher bas, ITR correspond à une isolation sous-chape et ITI à une isolation en sous-face
- Les planchers en feuille polystyrene sont traités comme des planchers avec ITE
- Les planchers bas en ossature (bois ou autre materiau), quand ils sont isolés entre les ossatures, sont considérés en ITE

## 3.4.2 Plancher intermédiaire / mur

Valeur du pont thermique de la liaison Plancher intermédiaire / Mur (W/(m.K))

| Mur extérieur | k_pi(m,i) |
|---------------|-----------|
| Non isolé | 0.86 |
| ITI | 0.92 |
| ITE | 0.24 |
| ITR | 0.24 |
| ITI + ITE | 0.13 |
| ITI + ITR | 0.34 |
| ITE + ITR | 0.11 |

**Règles** :
- Seuls les murs et planchers constitues d'un materiau lourd (beton, brique, ...) sont considérés ici. Pour les autres cas le pont thermique est pris nul
- Les ponts thermiques des planchers intermédiaires en ossature légère (ossature bois ou autre materiau) / murs sont négligés
- Lorsque le plancher intermédiaire ne separe que deux niveaux du lot faisant l'objet du DPE, il faut prendre en compte dans les calculs seulement la moitie de la valeur tabulée ci-dessus

## 3.4.3 Plancher haut / mur

Valeur du pont thermique de la liaison Plancher haut / Mur (W/(m.K))

**Terrasse ou plancher haut lourd** :

| k_ph(m,i) | Plancher haut | | | |
|-------------|-------------|---|---|---|
| | Non isolé | ITI | ITE | ITI + ITE |
| **Mur extérieur** | | | | |
| Non isolé | 0.3 | 0.83 | 0.4 | 0.4 |
| ITI | 0.27 | 0.07 | 0.75 | 0.07 |
| ITE | 0.55 | 0.76 | 0.58 | 0.58 |
| ITR | 0.4 | 0.3 | 0.48 | 0.3 |
| ITI + ITE | 0.27 | 0.07 | 0.58 | 0.07 |
| ITE + ITR | 0.27 | 0.07 | 0.48 | 0.07 |
| ITI + ITR | 0.4 | 0.3 | 0.48 | 0.3 |

**Règles** :
- Pour les murs, s'il n'est pas possible de distinguer le type d'isolation (ITI, ITE...), prendre par défaut ITI
- Pour les planchers hauts, s'il n'est pas possible de distinguer le type d'isolation (ITI, ITE...), prendre par défaut ITI
- Pour un plancher haut, ITR correspond à une isolation sous plancher haut et ITE à une isolation sur plancher haut
- Les ponts thermiques des planchers hauts en ossature légère sont négligés

## 3.4.4 Refend / mur

Valeur du pont thermique de la liaison Refend/Mur (W/(m.K))

| Mur extérieur | k_rf(m,i) |
|---------------|-----------|
| Non isolé | 0.23 |
| ITI | 0.42 |
| ITE | 0.13 |
| ITR | 0.2 |
| ITI + ITE | 0.13 |
| ITE + ITR | 0.2 |
| ITI + ITR | 0.15 |

**Règles** :
- Les ponts thermiques des parois sur circulations sont négligés pour les appartements et les immeubles
- Lorsque le refend ne separe que deux volumes du même lot faisant l'objet du DPE, il faut prendre en compte dans les calculs seulement la moitie de la valeur tabulée ci-dessus

## 3.4.5 Menuiserie / mur

Valeur du pont thermique de la liaison Menuiserie / Mur (W/(m.K))

On entend par menuiserie les fenêtres, portes ou portes-fenêtres.

| k_men(m,i) | Menuiserie | | | |
|-------------|------------|---|---|---|
| | Au nu intérieur | En tunnel | Au nu extérieur |
| | lp<5 | lp>10 | | lp<5 | lp>10 |
| **Mur** | | | | | |
| Non isolé | 0.43 | 0.29 | 0.31 | 0.19 | 0.38 | 0.25 |
| ITI avec retour d'isolant | 0.22 | 0.18 | 0.16 | 0.11 | 0 | 0 |
| ITI sans retour d'isolant | 0.43 | 0.29 | 0.31 | 0.19 | 0 | 0 |
| ITE avec retour d'isolant | 0 | 0 | 0.19 | 0.15 | 0.25 | 0.3 |
| ITE sans retour d'isolant | 0 | 0 | 0.45 | 0.4 | 0.9 | 0.8 |
| ITR | | | | | | |
| ITI+ITR avec retour d'isolant | 0 | 0 | 0.15 | 0.13 | 0 | 0 |
| ITI+ITR sans retour d'isolant | 0 | 0 | 0.31 | 0.19 | 0 | 0 |
| ITI+ITE sans retour d'isolant | 0.2 | 0.2 | 0.2 | 0.19 | 0 | 0 |
| ITI+ITE avec retour d'isolant | 0 | 0 | 0.19 | 0.15 | 0.2 | 0.3 |
| ITE+ITR sans retour d'isolant | 0 | 0 | 0.3 | 0.2 | 0.3 | 0.2 |

### Avec

- `lp` est la largeur approximative (arrondir à la valeur la plus proche apparaissant dans le tableau) du dormant de la menuiserie (cm)

**Règles** :
- Pour les murs, s'il n'est pas possible de distinguer le type d'isolation (ITI, ITE...), prendre par défaut ITI
- Ces valeurs de pont thermique sont valables pour les appuis, tableaux et le linteau de la menuiserie
- Les ponts thermiques au niveau des seuils de porte et de porte-fenêtre ne sont pas pris en compte
- Les ponts thermiques avec les parois en ossature bois sont négligés
- Les ponts thermiques au niveau des fenêtres de toit sont négligés

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 3.4 a 3.4.5 (pages 31-36)
