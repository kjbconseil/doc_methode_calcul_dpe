# 9. Calcul de la consommation de chauffage (Cch)

## Données d'entrée principales

- Rendement de génération : Rg (sans dimension)
- Rendement d'émission : Re (sans dimension)
- Rendement de distribution : Rd (sans dimension)
- Rendement de régulation : Rr (sans dimension)
- Type d'installation de chauffage : avec ou sans solaire ; base + appoint...
- Présence d'une véranda (ou assistance par ventilation) sur l'équipement

## 9.1 Installation de chauffage seule

### 9.1.1 Consommation de chauffage

La consommation de chauffage est calculée pour une consigne de température a 19°C correspondant à un comportement conventionnel (ou 21°C pour un comportement dépasseur).

Le besoin de chauffage sur le mois j, Bch_j (kWh PCI), est déterminé de la façon suivante :

```
Bch_j = (BV_j * DH_j) / 1000 + Q(rec_recup_j)/1000 + Q(pertes_gen_j)/1000
```

Avec :
| Variable | Description |
|----------|-------------|
| `BV_j` | Besoin de chauffage d'un logement par kelvin sur le mois j (W/K) (voir chapitre 2) |
| `DH_j` | Degrés heures de chauffage sur le mois j (°Ch) (différents selon le comportement choisi voir paragraphe 18.2 et 18.3) |
| `Q(rec_recup_j)` | Pertes récupérées de distribution d'ECS pour le chauffage sur le mois j (Wh) |
| `Q(pertes_gen_j)` | Pertes récupérées de stockage d'ECS pour le chauffage sur le mois j (Wh) |

### Pertes récupérées de distribution d'ECS pour le chauffage sur le mois j (Wh)

```
Q(rec_chauf_j) = 0.48 * Nref_j * (1/1000) * Q(dis_recup_j) / 8760
```

Avec :
- `Q(dis_ind_j)` : pertes de la distribution individuelle en volume chauffé pour le mois j (Wh) (voir paragraphe 15.2.1)
- `Q(dis_col_j)` : pertes de la distribution collective en volume chauffé pour le mois j (Wh) (voir paragraphe 15.2.1)

### Pertes récupérées de stockage d'ECS pour le chauffage sur le mois j (Wh)

```
Q(p_stk_rec) = 0.48 * Nref_j * Q(stk_j) / 8760
```

Avec :
- `Q(stk)` : pertes totales annuelles de stockage (Wh) (voir paragraphe 14 ou 11.6)

### Pertes récupérées de génération pour le chauffage sur le mois j (Wh)

```
Q(gen_rec_j) = 0.48 * Qpert * Q(arr) * Dper_j
```

Avec :
- `Qpert` : part des pertes par les parois égale a 0.75 pour les équipements a ventouse ou avaloirs/par ventilateur et 0.5 pour les autres
- `Q(arr)` : pertes à l'arret du générateur (Wh)
- `Dper_j` : duree pendant laquelle les pertes sont récupérées sur le mois j (h)

**Pour les générateurs assurant le chauffage uniquement** :
```
Dper_j = max(Nref_j * (1.3 + Rch(ch_j)) / (0.3 + Pn), 1790/8760)
```

**Pour les générateurs assurant l'ECS uniquement** :
```
Dper_j = Nref_j * 1790/8760
```

**Pour les générateurs assurant le chauffage ET l'ECS** :
```
Dper_j = max(Nref_j * (1.3 + Rch(ch_j)) / (0.3 + Pn) + Nref_j * 1790/8760)
```

Avec :
- `Pn` : puissance nominale du générateur (kW)
- `Rch(ch_j)` : besoin de chauffage hors pertes récupérées sur le mois j (kWh)

```
Rch(ch_j) = (BV_j * DH_j) / 1000
```

### Besoin annuel de chauffage

Le besoin annuel de chauffage (Bch) est égal à la somme des besoins mensuels (Bch_j) sur la période de chauffé :

```
Bch = SUM(Bch_j)
```

### Consommation annuelle

Les performances des équipements étant données sur une saison de chauffé complète, il n'est donc possible de calculer la consommation de chauffage (Ch, kWh PCI) que sur la saison complète de chauffé (donc sur l'entrée).



## 9.1.2 Installation classique

Ce cas correspond à une installation simple avec un unique rendement de génération, de distribution, d'émission et de régulation pour tout le bâtiment.

```
Cch = Bch * INT * Ich
```

Avec :
- `Bch` et `Cch` : besoins et consommations annuelles de chauffage (kWh PCI)
- `INT` : facteur d'intermittence
- `Ich` : inverse du rendement de l'installation :

```
Ich = 1 / (Rg * Re * Rd * Rr)
```

- `Rg, Re, Rd et Rr` sont respectivement le rendement annuel conventionnel de génération ou le coefficient de performance des pompes à chaleur (COP), le rendement d'émission, le rendement de distribution et le rendement de régulation
- L'émetteur dans ce cas est défini comme un émetteur de base



## 9.1.3 Installation avec plusieurs émissions pour même générateur

Les consommations associées a ces installations sont :

```
Cch = SUM((SA_i / SH) * INT_i * Ich_i) * Bch
```

La part de la consommation traitée par chaque émetteur est proratisée par le ratio des surfaces habitables.

Les consommations sont mensualisées de la façon suivante :

```
Cch_j = Cch * Bch_j / Bch
```



## 9.1.4 Installation avec plusieurs générateurs pour une même émission

#### 9.1.4.1 Installation de chauffage avec une chaudière ou une PAC en releve d'une chaudière bois

**Consommation annuelle de chauffage Cch1 liee à la chaudière bois (kWh PCI)** :
```
Cch1 = 0.75 * Bch * INT1 * Ich1
```

**Consommation annuelle de chauffage Cch2 liee à la PAC ou chaudière (kWh PCI)** :
```
Cch2 = 0.25 * Bch * INT2 * Ich2
```

#### 9.1.4.2 Installation de chauffage avec chaudière en releve de PAC

**Consommation Cch1 liee à la PAC (kWh PCI)** :
```
Cch1 = 0.8 * Bch * INT1 * Ich1
```

**Consommation Cch2 liee à la chaudière (kWh PCI)** :
```
Cch2 = 0.2 * Bch * INT2 * Ich2
```

#### 9.1.4.3 Les pompes à chaleur hybrides (PAC + chaudière gaz ou fioul)

Repartition du besoin de chauffage assure par chaque équipement :

| Zone | PAC | Chaudière |
|------|-----|-----------|
| <= H1 | 80 | 20 |
| H2 | 83 | 17 |
| >= H3 | 88 | 12 |

La fourniture d'ECS est considérée assuree a 100% par la chaudière.



## 9.2 Installation de chauffage avec du chauffage solaire

```
Cch = Bch * INT * (1 - Fch) * Ich
```

Avec :
- `Bch` : le besoin annuel de chauffage (kWh PCI)
- `Fch` : facteur de couverture solaire pour le chauffage, déterminé à partir du tableau du paragraphe 18.4
- `Ich` : inverse du rendement de l'installation



## 9.3 Installation de chauffage avec insert ou poele bois en appoint

**Cch1 liee au système principal de chauffage (kWh PCI)** :
```
Cch1 = 0.75 * Bch * INT1 * Ich1
```

**Cch2 liee à l'insert ou au poele (kWh PCI)** :
```
Cch2 = 0.25 * Bch * INT2 * Ich2
```



## 9.4 Installation de chauffage par insert, poele bois (ou biomasse) avec un chauffage électrique dans la salle de bains

**Cch1 liee au poele bois (kWh PCI)** :
```
Cch1 = 0.9 * Bch * INT1 * Ich1
```

**Cch2 liee au chauffage électrique de la salle de bains (kWh PCI)** :
```
Cch2 = 0.1 * Bch * INT2 * Ich2
```

Avec règles de prorata pour les cas de plusieurs salles de bain de surface S(sdb_total) et S(sdb).



## 9.5 Installation de chauffage avec en appoint un insert ou poele bois et un chauffage électrique dans la salle de bains (different du chauffage principal)

**Cch1 liee au système principal (kWh PCI)** :
```
Cch1 = 0.25 * 0.9 * Bch * INT1 * Ich1
```



## 9.6 Installation de chauffage avec chauffage solaire et insert ou poele bois en appoint

**Cch1 liee au système principal de chauffage (kWh PCI)** :
```
Cch1 = 0.75 * Bch * INT1 * (1 - Fch) * Ich1
```

**Cch2 liee à l'insert ou au poele bois (kWh PCI)** :
```
Cch2 = 0.25 * Bch * INT2 * (1 - Fch) * Ich2
```

**Production annuelle de chauffage solaire Prod(ch_sol) (kWh PCI)** :
```
Prod(ch_sol) = Bch * Fch * (0.75 * INT1 * Ich1 + 0.25 * INT2 * Ich2)
```



## 9.7 Installation de chauffage avec chaudière en releve de PAC avec insert ou poele bois en appoint

```
Cch1 = 0.8 * 0.75 * Bch * INT1 * Ich1
Cch2 = 0.2 * 0.75 * Bch * INT2 * Ich2
Cch3 = 0.25 * Bch * INT3 * Ich3
```



## 9.8 Installation de chauffage collectif avec base + appoint

La base fonctionne seule tant que la température extérieure est supérieure à une température de dimensionnement (°C). A cette température T, le besoin instantane du bâtiment est égal à la puissance utile du générateur en base :

```
T = 14 - (Pv * DH14) / Bch
```

Avec :
- `DH14` : degrés heures de base 14 sur la saison de chauffé complète (°Ch) (voir paragraphes 18.2 et 18.3)
- `Pv` : puissance emise utile par le générateur en base (kW)

```
Pv = Pn + Rd + Rv + Re
```

Le besoin de chauffage assure par la base Bch_base_j (kWhe) est calculé pour le mois j par :

```
Bch_base_j = Bch_j * (1 - DHT_j / DH14_j)
```

Avec :

```
DHT_j = Nref_j * (Test_j - Tbase) * x_j * (14 - 20 * X_j + 20 * X_j² - 5 * X_j³)
```

```
X_j = 0.5 - (T - Tbase) / (Test_j - Tbase)
```



## 9.9 Convecteur bi-jonction

**Cch1 liee au circuit collectif assurant la base (kWh PCI)** :
```
Cch1 = 0.6 * Bch * INT1 * Ich1
```

**Cch2 liee au circuit individuel assurant l'appoint (kWh PCI)** :
```
Cch2 = 0.4 * Bch * INT2 * Ich2
```



## 9.10 Chauffage avec plusieurs installations différentes et/ou indépendantes couplées

Les consommations associées a ces installations sont :

```
Cch = SUM((SA_i / SH) * INT_i * Ich_i) * Bch
```

Les consommations sont mensualisées de la façon suivante :

```
Cch_j = Cch * Bch_j / Bch
```



## 9.11 Installation de chauffage avec un générateur bi-énergie

```
Cch1 = 0.5 * Bch * INT1 * Ich1
Cch2 = 0.5 * Bch * INT2 * Ich2
```

## Sources

- **Source** : Arrêté du 31 mars 2021, Annexe 1 - Méthode de calcul 3CL-DPE 2021
- **Sections** : 9 a 9.11 (pages 56-66)
