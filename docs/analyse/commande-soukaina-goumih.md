# Analyse de la commande — Soukaina Goumih

- **Rôle** — Responsable sources
- **Date** — 16 novembre 2026
- **Région** — Occitanie
- **Commande** — SDIS 31, « Saison feux 2027 » ([commande.md](../commande.md))

## 1. Les questions

1. **Dans quels secteurs de Haute-Garonne les départs de feu se répètent-ils chaque été ?** Si les mêmes secteurs ressortent, le SDIS peut y mettre plus de patrouilles. Si les feux sont dispersés, il peut répartir les équipes entre plusieurs secteurs.
2. **Pour chaque seuil de danger, combien de jours faudrait-il renforcer le dispositif et combien de jours avec feu seraient couverts ?** Si un seuil plus bas couvre plus de jours avec feu et reste dans le budget, le SDIS peut l’abaisser. Si le coût dépasse le budget, il peut garder un seuil plus haut.
3. **Les feux qui démarrent les jours de danger faible se concentrent-ils dans certains secteurs ou à certaines heures ?** Si oui, le SDIS peut y maintenir une surveillance ciblée. Sinon, il peut garder sa surveillance habituelle ces jours-là.
4. **Pour un même niveau de danger, les jours avec feu sont-ils aussi fréquents en Haute-Garonne que dans les autres départements d’Occitanie et dans le reste de la France ?** Si les résultats sont proches, le SDIS peut envisager un seuil commun avec d’autres départements. Si les résultats diffèrent sur plusieurs étés, il peut étudier un seuil propre à la Haute-Garonne.

## 2. Les termes inconnus

| Terme | Ce que je crois qu’il veut dire | Ce qu’il faudrait vérifier |
|---|---|---|
| Météo des forêts | Un niveau de danger annoncé pour une journée et une zone. | Les niveaux officiels et la taille des zones. |
| Départ de feu | Un feu qui démarre et qui est recensé. | Quels types de feux sont comptés dans les données. |
| Seuil actuel | Le niveau à partir duquel le SDIS déclenche le renfort. | Le niveau utilisé et les éventuelles exceptions. |
| Dispositif renforcé | Des moyens de surveillance supplémentaires, comme des patrouilles. | Les moyens réellement mobilisés et leur coût. |
| Guet | Une surveillance qui sert à repérer rapidement un feu. | Comment le SDIS 31 organise ce guet. |

## 3. Les besoins

**La décision à éclairer**

Le SDIS 31 doit décider où placer ses moyens et à partir de quel niveau de danger les renforcer pour l’été 2027, avec le budget disponible.

**Ce qui manque dans la commande**

- Le seuil actuel et les jours où les renforts ont été activés.
- Le budget et le coût d’une journée de renfort.
- Le découpage des secteurs d’intervention et les dates exactes de la saison à étudier.
- Le périmètre de la comparaison nationale, notamment si elle inclut l’outre-mer.

## 4. Les données

| Question | Donnée idéale | Grain (une ligne = ?) | Période | Fraîcheur | Emprise géographique |
|---|---|---|---|---|---|
| Q1 — Secteurs prioritaires | Date et lieu de chaque départ de feu, avec le découpage des secteurs du SDIS. | Un départ de feu dans le relevé. Un secteur dans le découpage. | Plusieurs étés, jusqu’en 2026. | Relevé à jour jusqu’à la fin de l’été 2026 et dernier découpage disponible. | Haute-Garonne, par commune ou secteur. |
| Q2 — Choix du seuil | Niveau annoncé, nombre de départs (y compris zéro les jours couverts par le relevé), activations, coût du renfort et budget. | Un jour pour les niveaux, les feux et les renforts. Un budget par saison. | Étés pour lesquels on dispose des annonces et du relevé des feux, jusqu’en 2026. | Niveau connu avant la décision du jour. Relevé des feux et des renforts à jour en fin de saison. Dernier budget 2027 disponible. | Haute-Garonne. |
| Q3 — Jours de danger faible | Liste des jours de danger faible et date, heure et lieu des départs de feu. | Un départ de feu dans le relevé. Un jour dans les annonces. | Plusieurs étés, jusqu’en 2026. | Annonces archivées et relevé à jour jusqu’à la fin de la saison. | Haute-Garonne, par commune ou secteur. |
| Q4 — Comparaison | Niveau annoncé et présence ou absence d’un départ pour chaque jour. Identifier les jours où une donnée manque. | Un jour par département. | Mêmes étés et mêmes dates pour tous, jusqu’en 2026. | Annonces archivées et relevés des feux mis à jour sur la même période. | Haute-Garonne, autres départements d’Occitanie et reste du territoire national couvert. |

Comme responsable sources, je commencerais par vérifier ce que l’on peut récupérer auprès de Météo-France pour les niveaux de danger, dans la BDIFF pour les feux et auprès du SDIS 31 pour les renforts et les coûts.

## 5. Confrontation aux sources

Cette première comparaison reprend mes quatre questions et les fiches de l’inventaire du groupe. Les deux fiches Météo des forêts portent sur la même source, regroupée dans une colonne.

### Matrice

| Question | [BDIFF](../sources/fiche-bdiff.md) | [Météo des forêts](../sources/fiche-meteo-des-forets.md) | [EFFIS](../sources/fiche-effis.md) | [IFM Copernicus](../sources/fiche-ifm-copernicus.md) |
|---|---|---|---|---|
| Q1 — Secteurs où les feux se répètent | **partiel** — `Code_INSEE` et `Date_de_premiere_alerte` donnent la commune et l’alerte. Il manque le découpage des secteurs et la campagne 2026 (fiche, « Période » et « Clés »). | **absent** — Les colonnes `num_dep`, `niveau_j1` et `niveau_j2` donnent un danger départemental. Elles ne localisent aucun départ de feu (fiche, « Grain »). | **partiel** — La commune, la date et le contour permettent de repérer des zones touchées. Une ligne représente une surface brûlée, plusieurs lignes peuvent correspondre au même feu et les petits feux sont sous-représentés (fiche, « Grain » et « Points de vigilance »). | **absent** — `fwinx`, `latitude` et `longitude` décrivent un indice météo sur une grille. Ils ne recensent aucun départ de feu (fiche, « Grain »). |
| Q2 — Jours de renfort et jours avec feu couverts selon le seuil | **partiel** — `Date_de_premiere_alerte` et `Departement` permettent de regrouper les incendies par jour. Il manque le niveau annoncé, les activations, les coûts et le budget (fiche, « Questions de l’analyse »). | **partiel** — `niveau_j1`, `date` et `num_dep` permettent de compter les jours au-dessus d’un seuil. Il faut ajouter les feux et les données de renfort (fiche, « Grain » et « Questions »). | **partiel** — La date et le département servent à repérer des jours avec surface brûlée cartographiée. Il manque les niveaux annoncés et les coûts, et tous les départs ne sont pas représentés (fiche, « Grain » et « Points de vigilance »). | **partiel** — `fwinx` permettrait de tester des seuils de danger météo, mais la fiche indique qu’aucune table officielle vers les niveaux de la Météo des forêts n’a été trouvée. Il manque aussi les feux et les coûts (fiche, « Points qualité »). |
| Q3 — Secteurs et heures des feux les jours de danger faible | **partiel** — `Code_INSEE` et `Date_de_premiere_alerte` donnent la commune et l’heure d’alerte. Il faut le niveau annoncé et les secteurs. L’heure réelle du départ reste à vérifier (fiche, « Clés » et « Questions »). | **partiel** — `niveau_j1` identifie les jours de faible danger après décalage de `date`. Il faut un relevé des lieux et heures des feux (fiche, « Points qualité », point 1). | **partiel** — La date, la commune et le contour situent les surfaces cartographiées. La précision de l’heure réelle de départ reste à vérifier et il faut les annonces de danger (fiche, « Grain » et « Clés »). | **partiel** — `fwinx` fournit un danger météo quotidien. Il faut les feux et une correspondance validée avec le niveau « faible » de la Météo des forêts (fiche, « Grain » et « Points qualité »). |
| Q4 — Fréquence des jours avec feu au même niveau de danger selon les départements | **partiel** — `Departement` et `Date_de_premiere_alerte` permettent un comptage quotidien. L’extrait ouvert est limité à l’Occitanie, sans 2026, et sa complétude reste à vérifier (fiche, « Emprise », « Période » et « Point de vigilance »). | **partiel** — `num_dep` et `niveau_j1` couvrent 96 départements métropolitains sur trois saisons. Il manque les incendies recensés et les archives hors saison (fiche, « Emprise » et « Période »). | **partiel** — La date et le département `province` permettent des regroupements. La détection des petits feux et le lien entre surfaces et événements limitent la comparaison des départs (fiche, « Grain » et « Points de vigilance »). | **partiel** — `fwinx`, `valid_time` et les coordonnées permettent une comparaison météo. Il faut agréger par département, ajouter les feux et vérifier le rapport avec les niveaux annoncés (fiche, « Clés » et « Points qualité »). |

### Écarts avec la section 4

Pour les questions qui demandent à la fois les feux et le danger, la meilleure combinaison est la BDIFF avec la Météo des forêts. Les données réelles décrites ci-dessous sont celles des fichiers explorés.

| Question | Meilleure source | Grain | Période | Fraîcheur | Emprise |
|---|---|---|---|---|---|
| Q1 | BDIFF ; EFFIS en complément pour 2026 | Un départ et un secteur → un incendie recensé à la commune, avec l’heure d’alerte. Les secteurs restent à obtenir. | Plusieurs étés jusqu’en 2026 → BDIFF ouverte pour 2024 et 2025. EFFIS couvre 2026 avec des surfaces cartographiées. | Relevé jusqu’à la fin de l’été 2026 → BDIFF 2026 encore en saisie. Rythme de mise à jour de la version Esri non vérifié. | Haute-Garonne par commune ou secteur → communes du 31 présentes dans l’extrait Occitanie, sans rattachement aux secteurs. |
| Q2 | BDIFF + Météo des forêts | Un jour, les renforts et un budget par saison → un relevé d’alertes et un bulletin départemental à rapprocher par jour prévu. Les coûts, activations et le budget manquent. | Saisons communes jusqu’en 2026 → premier croisement possible sur les dates communes de 2024 et 2025. | Annonce connue avant la décision et bilan jusqu’en 2026 → annonces archivées disponibles, à recaler sur J+1. Feux 2026 et données financières manquants. | = Haute-Garonne dans les deux sources. |
| Q3 | BDIFF + Météo des forêts | Un feu avec lieu et heure, et un jour de danger faible → une alerte avec commune et heure, rapprochée d’un niveau départemental. | Plusieurs étés jusqu’en 2026 → deux saisons communes explorées, 2024 et 2025. | Annonces et relevé à jour en fin de saison → annonces archivées jusqu’en 2026, BDIFF limitée à 2024 et 2025 dans les extraits ouverts. | Haute-Garonne par commune ou secteur → commune pour les alertes, département pour la météo. Les secteurs manquent. |
| Q4 | BDIFF + Météo des forêts | Un jour par département → alertes à compter par jour et département, puis à croiser avec le bulletin. Il faut identifier les jours dont le relevé est incomplet. | Mêmes dates jusqu’en 2026 → dates communes des saisons 2024 et 2025 pour commencer. | Annonces et feux à jour sur la même période → météo 2024–2026 et BDIFF ouverte pour 2024–2025. La complétude des relevés reste à vérifier. | Haute-Garonne, Occitanie et reste de la France → extrait BDIFF limité à l’Occitanie ; météo couvrant les 96 départements métropolitains. |

### Décisions

Aucune source ne couvre entièrement mes questions. Je propose les décisions suivantes pour avancer.

| Question | Ce qui manque | Décision | Pourquoi | Ce que la décision coûte |
|---|---|---|---|---|
| Q1 | Le découpage des secteurs et le relevé des départs de 2026. | **collecter** — demander les secteurs et les départs au SDIS 31. | La BDIFF aide à localiser les incendies à la commune, mais il faut les secteurs pour organiser les moyens. | Du temps pour contacter le SDIS et un risque de délai ou de réponse incomplète. |
| Q2 | Les coûts, le budget, le seuil actuel et les dates d’activation. | **collecter** — demander ces informations au SDIS 31. | On peut tester le nombre de jours déclenchés selon le seuil, mais il faut les coûts pour vérifier le budget. | Une dépendance à la réponse du SDIS. En attendant, on pourra comparer les jours de renfort sans chiffrer leur coût. |
| Q3 | L’heure exacte de départ, les secteurs et le relevé 2026. | **approximer** — commencer par les communes et les heures d’alerte de 2024 et 2025, croisées avec J+1. | C’est ce que les fichiers explorés permettent d’étudier en premier. | L’heure d’alerte peut être décalée par rapport au départ. Deux saisons donnent peu de recul et la commune ne représente pas toujours un secteur du SDIS. |
| Q4 | Un export national des incendies et une couverture vérifiée des mêmes dates. | **collecter** — obtenir un extrait BDIFF plus large et vérifier les lacunes avant les calculs. | L’extrait Occitanie permet la comparaison régionale, mais il faut les autres départements pour la comparaison nationale. | Un téléchargement et des contrôles supplémentaires. Pour commencer, la comparaison commune sera limitée à 2024 et 2025 en métropole. |

