# Matrice questions × sources — Occitanie

Version 0, 18 novembre 2026. Construite à partir des sections 1 (questions) et 5 (confrontation aux sources) des quatre analyses individuelles :

| Membre | Analyse | Branche |
|---|---|---|
| Maha Younsi | `docs/analyse/commande-maha-younsi.md` | `analyse/confrontation-maha-younsi` |
| Hocine Ait Yakoub | `docs/analyse/commande-hocine-ait-yakoub.md` | `analyse/commande-hocine-ait-yakoub` |
| Samy Bouaouni | `docs/analyse/commande-samy-bouaouni.md` | `analyse/confrontation-samy-bouaouni` |
| Soukaina Goumih | `docs/analyse/commande-soukaina-goumih.md` | `analyse/confrontation-soukaina-goumih` |

Sources : celles de l'[inventaire du groupe](../sources/inventaire.md). Les deux fiches Météo des forêts ([Hocine](../sources/fiche-meteo-des-forets.md), [Samy](../sources/fiche-archives-meteo-des-forets.md)) portent sur la même source et sont regroupées dans une colonne. Samy n'a confronté ses questions qu'à la Météo des forêts : ses degrés n'apparaissent que dans cette colonne.

Degrés : **complet** (répond au grain, sur la période et sur l'emprise voulus) · **partiel** (répond en partie) · **absent** (rien d'utile) · **inconnu** (non vérifié dans le fichier ou sa documentation). Chaque décision est numérotée dans le [journal des décisions](journal-des-decisions.md).

---

## 1. Questions retenues

Les 21 questions des quatre analyses ont été fusionnées en 9 questions. La colonne « Posée par » garde la trace des questions d'origine.

| # | Question retenue | Posée par | Décision éclairée |
|---|---|---|---|
| G1 | Dans quelles communes ou quels secteurs de la Haute-Garonne les départs de feu se concentrent-ils, et se répètent-ils d'une saison à l'autre ? | Maha Q1 · Hocine Q1 · Samy Q1 · Soukaina Q1 | Où placer les moyens |
| G2 | À quels mois, jours et heures les départs de feu sont-ils les plus fréquents dans le 31 ? | Maha Q2 | Quand renforcer |
| G3 | Pour chaque niveau de la Météo des forêts, quelle part des jours a connu au moins un départ de feu ? | Maha Q3 · Hocine Q2 · Samy Q2 | Choix du seuil |
| G4 | Quelle part des feux part les jours de danger faible, et ces feux se concentrent-ils dans certains secteurs ou à certaines heures ? | Maha Q4 · Soukaina Q3 | Surveillance ciblée hors dispositif |
| G5 | Pour chaque seuil possible : combien de jours de dispositif renforcé, combien de fausses alertes, combien de feux hors dispositif, et est-ce compatible avec le budget ? | Maha Q5 · Hocine Q3 · Samy Q4 · Soukaina Q2 | Choix du seuil sous contrainte budgétaire |
| G6 | Le lien entre le niveau de danger et les départs de feu est-il le même dans le 31, dans les autres départements d'Occitanie et en France ? | Maha Q6 · Hocine Q4 · Samy Q3 · Soukaina Q4 | Seuil propre au 31 ou commun |
| G7 | Le 31 est-il plus ou moins touché que les autres départements, rapporté à sa surface boisée ? | Maha Q7 | Niveau d'investissement, mutualisation |
| G8 | Quelles sont les causes principales des départs de feu ? | Maha Q8 | Prévention ciblée ou surveillance |
| G9 | L'été 2026 a-t-il été exceptionnel par rapport aux saisons précédentes ? | Maha Q9 | Dimensionner 2027 sur 2026 ou non |

---

## 2. Matrice

Sous chaque degré retenu, en italique : le degré donné par chaque membre qui a posé la question.

| # | [BDIFF](../sources/fiche-bdiff.md) | Météo des forêts | [EFFIS](../sources/fiche-effis.md) | [IFM Copernicus](../sources/fiche-ifm-copernicus.md) |
|---|---|---|---|---|
| **G1** | **partiel** — `Code_INSEE` localise à la commune, mais seulement 2024-2025 au lieu de dix saisons, et **seulement 5 incendies dans le 31** (1 en 2024, 4 en 2025, vérifié dans les couches le 18/11) ; pas de secteurs SDIS. *Maha, Hocine, Soukaina : partiel* | **absent** — `num_dep`, `niveau_j1` : un niveau par département, aucun feu ni lieu (fiches, « Grain »). *Maha, Hocine, Samy, Soukaina : absent* | **partiel** — `commune` et contour depuis 2000, mais des surfaces vues par satellite, pas des départs ; 37 surfaces dans le 31 ; petits feux sous-représentés (fiche, « Grain », « Volumétrie », « Points de vigilance »). *Maha, Hocine, Soukaina : partiel* | **absent** — **divergence tranchée** (D-012) : `fwinx`, `latitude`, `longitude`, `valid_time` décrivent un danger météo sur 13 points de grille dans le 31 ; le fichier ne contient aucun feu. *Maha, Soukaina : absent · Hocine : partiel (« donnée indirecte »)* |
| **G2** | **partiel** — `Date_de_premiere_alerte` : heure d'alerte en UTC, pas l'heure de départ ; 2 saisons, 5 feux dans le 31. *Maha : partiel* | **absent** — aucun feu ; `date` = publication. *Maha : absent* | **partiel** — `firedate` utile pour les mois ; heure non exploitable (26 % à 00:00, le reste vers midi). *Maha : partiel* | **absent** — `valid_time` n'est pas un départ. *Maha : absent* |
| **G3** | **partiel** — jours avec feu par `Departement` et jour local de `Date_de_premiere_alerte`, sans niveau de danger ; 2024-2025 ; lignes non intégrées signalées par Esri (fiche, « Point de vigilance ») ; trop peu de feux dans le 31 pour un taux par niveau. *Maha, Hocine : partiel* | **partiel** — `niveau_j1` décalé d'un jour, par `num_dep` ; 3 saisons, de fin mai ou juin à fin septembre ou début octobre ; niveaux **prévus**, pas observés ; dans le 31, 1 seul jour au niveau 3 et aucun au niveau 4 en 2024. *Maha, Hocine, Samy : partiel* | **partiel** — dates des surfaces brûlées, pas des départs ; peu de jours avec surface dans le 31, surtout hors saison. *Maha, Hocine : partiel* | **partiel** — `fwinx` continu, pas les 4 niveaux ; lien fort avec les niveaux dans le 31 à l'été 2025 (corrélation 0,81 ; valeur moyenne 4,8 au niveau 1, 15,5 au niveau 2, 31,5 au niveau 3), sans table officielle ; seul l'été 2025 a été vérifié. *Maha, Hocine : partiel* |
| **G4** | **partiel** — `Code_INSEE` et heure d'alerte ; `Surface_parcourue` existe (vérifié), unité à confirmer ; pas de secteurs. *Maha, Soukaina : partiel* | **partiel** — `niveau_j1 = 1` repère les jours faibles, après décalage de `date`, mais rien hors saison. *Maha, Soukaina : partiel* | **partiel** — commune, date et `area_ha`, mais 85 % des surfaces d'Occitanie hors juin-septembre, donc sans niveau. *Maha, Soukaina : partiel* | **partiel** — danger quotidien, correspondance avec le niveau 1 non validée. *Maha, Soukaina : partiel* |
| **G5** | **partiel** — feux sous le seuil comptables sur 2024-2025 ; ni activations, ni coûts, ni budget (fiche, « Questions de l'analyse »). *Maha, Hocine, Soukaina : partiel* | **partiel** — nombre de jours par seuil directement calculable (31, niveau ≥ 3 : 1 / 10 / 35 jours en 2024 / 2025 / 2026) ; pas de feux, pas de coûts. *Maha, Hocine, Samy, Soukaina : partiel* | **partiel** — surfaces sous le seuil, sans petits feux ; aucun coût. *Maha, Hocine, Soukaina : partiel* | **partiel** — jours au-dessus d'un seuil de FWI ; peut servir à allonger l'historique ; aucun coût. *Maha, Hocine, Soukaina : partiel* |
| **G6** | **partiel** — extrait ouvert limité à l'Occitanie (885 incendies) ; les couches complètes (1 367 incendies en 2024, 2 539 en 2025) existent mais n'ont pas été ouvertes. *Maha, Hocine, Soukaina : partiel* | **partiel** — 96 départements métropolitains chaque jour, 3 saisons, pas de feux. *Maha, Hocine, Samy, Soukaina : partiel* | **partiel** — 78 départements, dont 12 sur 13 en Occitanie (Gers absent) ; surfaces et non départs ; rupture en 2019. *Maha, Hocine, Soukaina : partiel* | **partiel** — France entière, mais sans code département : jointure spatiale à faire ; aucun point de grille à Paris (75), dans les Hauts-de-Seine (92) et en Seine-Saint-Denis (93). *Maha, Hocine, Soukaina : partiel* |
| **G7** | **partiel** — nombre de feux et `Surface_foret` par département ; pas de surface boisée totale. *Maha : partiel* | **absent** *Maha : absent* | **partiel** — `area_ha`, `broadlea`, `conifer`, `mixed` ; pas de surface boisée totale. *Maha : partiel* | **absent** *Maha : absent* |
| **G8** | **partiel** — **tranché** (« inconnu » chez Maha) : la colonne `Nature` existe, avec 5 catégories (Malveillance, Involontaire (travaux), Involontaire (particulier), Accidentelle, Naturelle). Remplie pour 71 % des feux d'Occitanie en 2024 et 84 % en 2025, mais **vide pour les 5 feux du 31**. La colonne `Connaissance` est toujours vide. | **absent** *Maha : absent* | **absent** — aucun des 22 champs ne décrit une cause. *Maha : absent* | **absent** *Maha : absent* |
| **G9** | **partiel** — 2024-2025 en référence ; **2026 non diffusée** (fiche, « Période »). *Maha : partiel* | **partiel** — danger prévu bien plus fort en 2026 (35 jours au niveau ≥ 3 dans le 31), mais c'est un danger, pas des feux. *Maha : partiel* | **partiel** — seule source avec 2026 : 12 surfaces dans le 31 en 2026, contre 9 en 2025 et 3 en 2024. *Maha : partiel* | **inconnu** — 2026 et l'historique long annoncés, mais seul l'été 2025 a été ouvert. *Maha : inconnu* → vérification demandée à Hocine (D-010) |

### Divergences entre membres

| Cellule | Degrés donnés | Retour au fichier | Degré retenu |
|---|---|---|---|
| G1 × IFM Copernicus | Maha, Soukaina : absent · Hocine : partiel | Les variables du fichier sont `fwinx`, `latitude`, `longitude` et `valid_time` : un danger météo, aucun feu ni surface. La question porte sur les départs de feu. | **absent** (D-012). L'idée de Hocine est gardée comme question nouvelle (section 4). |
| G8 × BDIFF | Maha : inconnu | Couches BDIFF 2024 et 2025 interrogées le 18/11 : colonne `Nature` présente, vide pour les 5 feux du 31. | **partiel** (D-009) |
| G1, G2, G3 × BDIFF | partiel pour tous | Couches interrogées le 18/11 : 5 incendies dans le 31 sur 2024-2025. Le degré ne change pas, mais la question ne tient pas au grain du 31 seul. | **partiel** (D-004) |

Pour toutes les autres cellules notées par plusieurs membres, les degrés concordent. Les **décisions**, elles, divergent sur G1 et G3 : voir D-002 et D-004 dans le journal.

---

## 3. Lecture par question : les manques

**Aucune question n'a de source « complet ».** Les manques principaux :

- **Données internes du SDIS 31** (G1, G5) : secteurs d'intervention, seuil actuel, jours d'activation, coût d'une journée de renfort, budget. Aucune source publique ne les contient.
- **Assez de feux dans le 31** (G1, G2, G3, G8) : la BDIFF n'en compte que 5 sur deux saisons. Il faut soit élargir l'échelle à l'Occitanie, soit obtenir les interventions du SDIS 31, soit récupérer la BDIFF sur des années plus anciennes.
- **Un historique long qui associe niveaux et feux** (G3, G5) : 2 saisons communes (2024-2025) entre la BDIFF et la Météo des forêts, au lieu des dix saisons demandées par Hocine et Samy.
- **Les feux hors saison** (G4) : la Météo des forêts n'a pas de niveau hors de fin mai à début octobre, alors que la majorité des surfaces brûlées d'Occitanie le sont en hiver.
- **Les feux des autres départements** (G6) : l'extrait BDIFF ouvert est limité à l'Occitanie.
- **La surface boisée** (G7) : aucune source de l'inventaire ne la donne.
- **Les feux 2026 recensés au sol** (G9) : BDIFF 2026 non diffusée.

## 4. Lecture par source : ce qui sert, ce qui reste à interroger

Aucune source n'est sans question : aucune n'est à écarter.

| Source | Questions servies | Questions que la source permettrait de poser, et qu'on n'a pas posées |
|---|---|---|
| BDIFF | G1 à G9, toutes en partiel | `Moyens_de_premiere_intervention`, `SurfaceFeuArriveeSecour`, `Origine_de_l_alerte` : **les feux attaqués tôt restent-ils plus petits ?** Utile pour la décision « où placer les moyens ». Également `Hygrometrie`, `Vitesse_moyenne_du_vent`, `Temperature` : conditions météo relevées au moment du feu. |
| Météo des forêts | G3 à G6, G9 | `niveau_j2` : **la prévision à J+2 est-elle assez fiable pour organiser le dispositif deux jours à l'avance ?** |
| EFFIS | G1 à G7, G9 | Parts d'occupation du sol (`broadlea`, `othernatlc`, `agriareas`…) : **quelle part des surfaces brûlées est réellement de la forêt ?** Utile pour la définition de « feu de forêt ». |
| IFM Copernicus | G3 à G6, G9 | **Peut-on reconstituer un niveau de danger avant 2024**, pour avoir plus de saisons ? Et, d'après la remarque de Hocine sur G1 : **dans quelles parties du 31 le danger météo est-il le plus souvent élevé ?** (13 points de grille, une lecture plus fine que le niveau départemental). |

**Sources de la liste du défi absentes de l'inventaire**, alors qu'elles combleraient un manque : Statistiques nationales des SDIS (interventions, G1, G6), BD Forêt V2 (G7), Admin Express (jointures EFFIS et IFM avec les communes et les départements).
