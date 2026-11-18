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
