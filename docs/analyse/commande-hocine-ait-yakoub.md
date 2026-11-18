# Analyse de la commande - Hocine Ait Yakoub

## 1. Les questions

Quatre questions dont la réponse aiderait la direction à trancher.

1. Quelles communes ou zones de la Haute-Garonne concentrent le plus de départs de feu et de surfaces brûlées sur les dix dernières saisons ? Si quelques zones concentrent l'essentiel des feux, la direction y renforce les moyens en priorité ; si les feux sont dispersés, elle garde une répartition homogène.
2. Pour chaque niveau de la Météo des forêts, quelle part des jours a connu au moins un départ de feu en Haute-Garonne ? Si cette part augmente nettement à partir d'un niveau donné, la direction place le seuil de déclenchement à ce niveau ; sinon, l'indice seul ne suffit pas et elle doit le combiner à d'autres critères.
3. Pour chaque seuil possible, combien de jours le dispositif renforcé aurait-il été déclenché sans feu (fausses alertes), et combien de feux seraient partis en dessous du seuil (feux manqués) ? La direction choisit le seuil qui limite les feux manqués tout en restant dans le nombre de jours de renforcement que le budget permet.
4. La relation entre le niveau de l'indice et les départs de feu est-elle la même en Haute-Garonne que dans les autres départements d'Occitanie et en France ? Si elle est comparable, la direction peut reprendre un seuil régional ou national ; si elle diffère, elle fixe un seuil propre au département.

## 2. Les termes inconnus

| Terme | Ce que je crois qu'il veut dire | Ce qu'il faudrait vérifier |
|---|---|---|
| Départ de feu | Un feu qui démarre, quelle que soit la surface finalement brûlée | Si les sources comptent tous les départs ou seulement les feux au-delà d'une surface minimale |
| Feu de forêt | Un feu qui touche une forêt ou une zone naturelle | La définition officielle (forêt, lande, maquis, garrigue ?) et si les feux agricoles sont inclus |
| Météo des forêts | L'indice publié par Météo-France qui annonce le danger de feu | Ses niveaux, son grain (département ou zone), sa date de création et l'existence d'un historique |
| Danger élevé | Un des niveaux de la Météo des forêts | À quel niveau exact il correspond dans l'échelle officielle |
| Indice au plus bas | Le niveau le plus faible de l'échelle | Le nom de ce niveau et sa fréquence l'été |
| Dispositif renforcé | Patrouilles, guet et moyens supplémentaires mis en place les jours à risque | Son contenu exact, son coût par jour et sa zone d'application |
| Seuil actuel | Le niveau de l'indice à partir duquel le SDIS déclenche aujourd'hui le dispositif | Sa valeur, qui n'est pas donnée dans la commande |
| Moyens humains et financiers | Personnels, véhicules et budget de la lutte contre les feux | Le budget disponible et l'unité de répartition (centre de secours, commune, zone) |
| Département | Le territoire de la Haute-Garonne | Code INSEE ou territoire couvert par le SDIS 31 : coïncident-ils ? |
| Été / saison feux | La période de risque, approximativement de juin à septembre | Les dates retenues par le SDIS et par les sources |

## 3. Les besoins

La décision à éclairer, en une phrase : où concentrer les moyens du SDIS 31 et à partir de quel niveau de la Météo des forêts déclencher le dispositif renforcé, avec un budget qui ne permet pas de renforcer partout ni tout l'été.

Ce qui manque dans la commande pour y répondre (une information, une précision, une hypothèse à confirmer) :
- le seuil actuel de déclenchement ;
- le coût d'une journée de dispositif renforcé et le nombre de jours que le budget permet ;
- l'unité géographique à laquelle les moyens sont répartis (centre de secours, commune, massif) ;
- la période exacte de la saison feux à étudier ;
- la profondeur d'historique disponible pour la Météo des forêts (à vérifier) ;
- la fiabilité du recensement des feux : un feu non déclaré dans les sources fausserait l'analyse du seuil.

## 4. Les données

Pour chaque question, la donnée qu'il vous faudrait idéalement pour répondre.

| Question | Donnée idéale | Grain (une ligne = ?) | Période | Fraîcheur | Emprise géographique |
|---|---|---|---|---|---|
| 1 | Liste des départs de feu avec date, commune, surface brûlée et cause | Un départ de feu | 10 dernières saisons au moins | Annuelle, saison 2026 incluse | Haute-Garonne, au niveau commune |
| 2 | Niveau quotidien de la Météo des forêts croisé avec le nombre de départs de feu du jour | Un jour × une zone de l'indice | Toutes les saisons où l'indice existe | Quotidienne, saison 2026 incluse | Haute-Garonne |
| 3 | Même donnée que la question 2, plus le coût journalier du dispositif renforcé et le budget annuel | Un jour × une zone de l'indice | Toutes les saisons où l'indice existe | Quotidienne pour l'indice, annuelle pour le budget | Haute-Garonne |
| 4 | Niveau quotidien de l'indice et départs de feu pour tous les départements | Un jour × un département | Toutes les saisons où l'indice existe | Quotidienne, saison 2026 incluse | Occitanie (13 départements) et France |

## 5. Confrontation aux sources

Sources de l'inventaire du groupe (`docs/sources/inventaire.md`) : BDIFF (fiche de Soukaina), Météo des forêts (ma fiche et celle de Samy), EFFIS (fiche de Maha), IFM / FWI Copernicus (ma fiche).

### Matrice

| Question | BDIFF | Météo des forêts | EFFIS | IFM / FWI Copernicus |
|---|---|---|---|---|
| 1 | **partiel** : la commune de chaque incendie est connue (`Code_INSEE`, rubrique « Grain »), mais seules 2024 et 2025 ont été ouvertes (rubrique « Période »), loin des dix saisons voulues, et la fiche ne cite ni colonne de surface ni colonne de cause. | **absent** : une ligne = un département × une date de publication (`num_dep`, `date`) ; aucun feu, aucun détail infra-départemental. | **partiel** : contour et commune de chaque surface brûlée de 2000 à 2026 (rubriques « Grain » et « Période »), mais ce sont des surfaces vues par satellite, pas des départs de feu ; petits feux sous-représentés (« Points de vigilance ») ; 37 enregistrements seulement en Haute-Garonne (« Volumétrie »). | **partiel** : donnée indirecte. `fwinx` donne un danger météo par point de grille de 0,25° (13 points en Haute-Garonne), pas des feux ni des surfaces. |
| 2 | **partiel** : donne les jours avec incendie (`Date_de_premiere_alerte`, `Departement`), mais pas le niveau de danger ; 2024 et 2025 seulement ; exhaustivité non vérifiée, Esri signale des lignes manquantes (« Point de vigilance »). | **partiel** : donne le niveau du jour (`niveau_j1` décalé d'un jour, par `num_dep`), mais pas les feux ; trois saisons (2024 à 2026), de fin mai ou juin à fin septembre ou début octobre seulement (rubrique « Période »). | **partiel** : donne la date des surfaces brûlées (rubrique « Grain »), mais pas des départs de feu ; les petits feux manquent, ce qui fausse le comptage des jours avec feu. | **partiel** : `fwinx` quotidien par point de grille ; c'est une valeur continue, pas les 4 niveaux de la Météo des forêts ; seule la période juin à septembre 2025 a été vérifiée dans le fichier. |
| 3 | **partiel** : mêmes raisons qu'en Q2 ; aucune donnée sur le coût du dispositif ou le budget (rubrique « Questions de l'analyse » : « les activations, coûts et le budget nécessitent des données du SDIS »). | **partiel** : permet de tester chaque seuil (`niveau_j1`, `niveau_j2`), mais ne contient ni les feux, ni le coût, ni le budget. | **partiel** : mêmes raisons qu'en Q2 ; aucune donnée de coût. | **partiel** : peut servir de proxy du niveau sur une période plus longue (lien fort avec la Météo des forêts en Haute-Garonne à l'été 2025 : `fwinx` moyen de 4,8 au niveau 1, 15,5 au niveau 2, 31,5 au niveau 3), mais aucune donnée de coût. |
| 4 | **partiel** : les fichiers ouverts sont filtrés sur l'Occitanie (rubrique « Volumétrie » : 885 enregistrements) ; les couches complètes (1 367 et 2 539 enregistrements) n'ont pas été ouvertes, la comparaison nationale n'est donc pas encore possible. | **partiel** : emprise complète pour la comparaison (96 départements, `num_dep`, rubrique « Emprise »), mais pas les feux et trois saisons seulement. | **partiel** : 78 départements français, dont 12 sur 13 en Occitanie (rubrique « Emprise ») ; surfaces et non départs ; années non comparables avant et après 2019 (rubrique « Période »). | **partiel** : couvre toute la France, mais sans code département (rubrique « Clés ») : il faut une jointure spatiale, et Paris (75), les Hauts-de-Seine (92) et la Seine-Saint-Denis (93) ne contiennent aucun point de grille. |

Aucune question n'a de source « complet ». Aucune cellule n'est « inconnu » : chaque degré a été justifié à partir des fichiers ou des fiches.

### Écarts avec la section 4

| Question | Meilleure source | Grain | Période | Fraîcheur | Emprise |
| -------- | ---------------- | ----- | ------- | --------- | ------- |
| 1 | BDIFF | = (un incendie recensé, `Code_INSEE`) | dix dernières saisons → 2024 et 2025 | annuelle, saison 2026 incluse → annuelle, 2026 en cours de saisie et non diffusée | Haute-Garonne à la commune → = (exhaustivité non vérifiée) |
| 2 | Météo des forêts croisée avec la BDIFF | un jour × une zone de l'indice → un jour × un département (la zone de l'indice est le département) | toutes les saisons de l'indice → saisons communes 2024 et 2025, de juin à septembre seulement | quotidienne, 2026 incluse → Météo des forêts jusqu'au 5 octobre 2026, BDIFF sans 2026 | = (Haute-Garonne) |
| 3 | Météo des forêts croisée avec la BDIFF | = (comme Q2) | comme Q2 | quotidienne pour l'indice, annuelle pour le budget → indice comme Q2, budget et coût absents | = (Haute-Garonne) |
| 4 | Météo des forêts croisée avec la BDIFF | = (un jour × un département) | comme Q2 | comme Q2 | Occitanie et France → Météo des forêts = (96 départements), BDIFF ouverte sur l'Occitanie seulement |

### Décisions

| Question | Ce qui manque | Décision | Pourquoi | Ce que la décision coûte |
|---|---|---|---|---|
| 1 | Un historique des départs de feu sur dix saisons, à la commune | **collecter** | La BDIFF a le bon grain (`Code_INSEE`) et existe sur une période plus longue que l'extrait ouvert : il faut récupérer l'export du portail BDIFF quand il sera accessible, ou les couches des années précédentes. EFFIS peut compléter pour les grands feux, sans remplacer la BDIFF. | Du temps de collecte, et un risque si le portail reste inaccessible : la question se limiterait alors à 2024 et 2025. |
| 2 | Des saisons communes plus nombreuses entre les feux et le niveau de danger, et le niveau pour les feux hors saison | **renoncer** (reformuler) | On réduit la question à ce que les sources permettent : le croisement BDIFF × Météo des forêts sur 2024 et 2025, de juin à septembre, avec la date de publication décalée d'un jour. | Seulement deux saisons, avec très peu de jours aux niveaux 3 et 4 (un seul jour au niveau 3 et aucun au niveau 4 en Haute-Garonne en 2024). Les feux hors saison sont exclus, alors qu'ils sont nombreux (85 % des surfaces EFFIS en Occitanie). |
| 3 | Le seuil actuel, le coût d'une journée de dispositif renforcé et le budget disponible | **collecter** | Aucune source du défi ne les contient. Il faut les demander à la direction du SDIS 31. | Une dépendance à la réponse de la direction. Sans elle, on présentera les fausses alertes et les feux manqués pour chaque seuil, sans les traduire en jours de renfort finançables. |
| 4 | Les feux de tous les départements français sur les mêmes dates | **collecter** | Les couches BDIFF complètes existent (1 367 et 2 539 enregistrements), mais n'ont été ouvertes que sur l'Occitanie : il faut les récupérer en entier. | Un volume plus important à traiter, et une couverture à vérifier pour chaque département avant de comparer. |

**Piste à discuter en groupe :** pour allonger l'historique des questions 2 à 4, approximer le niveau de la Météo des forêts avec l'IFM Copernicus, disponible sur une période plus longue d'après sa page. Ce proxy mesure mal la sécheresse de la végétation et l'occupation des sols, que les prévisionnistes ajoutent pour fixer le niveau. Il demande aussi un traitement en Python (NetCDF, jointure spatiale).
