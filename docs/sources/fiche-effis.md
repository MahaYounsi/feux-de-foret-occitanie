# Fiche d'identité — EFFIS, surfaces brûlées cartographiées par satellite

**Explorée par** — Maha Younsi, le 17 novembre 2026
**Périmètre du projet** — Occitanie, avec un focus sur la Haute-Garonne (31)
**Fichiers ouverts** — l'ensemble des enregistrements « France » de la base des surfaces brûlées, récupérés par l'API publique d'EFFIS (7 197 enregistrements, réponse JSON), et la documentation EFFIS (page « Data and services », licence, méthode de cartographie). Les téléchargements en Shapefile et SpatiaLite n'ont pas pu être ouverts (voir « Mode d'accès »).

| Rubrique | Valeur |
|---|---|
| Propriétaire et système | **EFFIS** (European Forest Fire Information System), composante du **Copernicus Emergency Management Service**, géré par le **Centre commun de recherche (JRC)** de la Commission européenne. Les surfaces brûlées sont cartographiées à partir d'**images satellites** (MODIS, puis Sentinel-2 depuis 2018), puis vérifiées visuellement (documentation EFFIS). |
| Mode d'accès et format | **API REST publique sans compte**, réponse **JSON** paginée, avec le contour de chaque surface brûlée (multipolygone). Également proposés sur la page « Data and services » : base complète en **Shapefile** ou **SpatiaLite** (ZIP). **Non ouverts** : le serveur de téléchargement présentait un **certificat de sécurité expiré** le 17/11/2026. Les données historiques détaillées et les extraits de la base des feux sont fournis **sur demande** via un formulaire. |
| Grain (une ligne = ?) | **Une surface brûlée cartographiée** : identifiant, date du feu, commune, département (`province`), surface en hectares, part de chaque type d'occupation du sol (feuillus, conifères, végétation naturelle, zones agricoles, etc.), contour. Constaté : 7 197 identifiants uniques. Un même feu peut apparaître en plusieurs surfaces le même jour dans la même commune (exemple : deux lignes à Arguenos le 31/10/2026). |
| Emprise géographique | Europe, Moyen-Orient et Afrique du Nord ; filtre par pays. Pour la France : **78 départements** ont au moins une surface brûlée. Occitanie : **12 départements sur 13**, le **Gers n'a aucun enregistrement**. |
| Période réellement couverte | Pour la France, dates de feu du **5 juillet 2000 au 10 novembre 2026**. **Saison 2026 incluse** (1 740 enregistrements en France). Le nombre d'enregistrements augmente fortement à partir de **2019** (de 8 à 92 par an avant, de 260 à 1 740 après), ce qui correspond au passage à Sentinel-2, qui détecte des feux plus petits. Les années ne sont donc **pas comparables entre elles** sans précaution. |
| Date de dernière mise à jour affichée sur la fiche | Pas de date globale affichée sur la page. Dans les données, la dernière modification d'un enregistrement date du **16 novembre 2026**. |
| Fréquence de mise à jour | **En continu** : la page présente une base « real-time updated » (mise à jour en temps réel). La fréquence exacte n'est **pas documentée**. |
| Volumétrie | France : **7 197** enregistrements, **22 champs**, environ **46 Mo** de JSON avec les contours. Occitanie : **2 016** enregistrements. Haute-Garonne : **37** enregistrements, **921 ha** au total (le plus grand : 126 ha). Surface médiane : 16 ha ; 97 enregistrements à 0 ha. |
| Clés disponibles | **Nom de la commune** et **nom du département** (en texte, **pas de code INSEE**) ; **coordonnées** (centre et contour) ; **date du feu**. Pour joindre la BDIFF ou la Météo des forêts, passer par une **jointure spatiale** avec les contours des communes (Admin Express) plutôt que par les noms, à cause des homonymes et des accents. Les dates sont en heure locale avec le décalage horaire (par exemple `+01:00`). |
| Données personnelles | **Aucune** : pas de nom de personne ni de coordonnée de contact dans les 22 champs. |
| Licence | **Creative Commons Attribution 4.0 (CC BY 4.0)** pour le contenu appartenant à l'Union européenne : citer la source et indiquer les modifications (page de licence EFFIS). |
| Questions de l'analyse | **Q1** (secteurs où se concentrent les feux) : localisation précise par contour, communes touchées en Haute-Garonne. **Q7** (exposition comparée des départements) : surfaces par département, avec la part forêt / autre végétation. **Q9** (2026 exceptionnelle ?) : **seule source explorée qui couvre déjà 2026**, alors que la BDIFF 2026 n'est pas publiée. **Q4** (feux les jours de danger faible) : voir le constat ci-dessous sur les feux hors saison. |

## Constat important pour la direction

En Occitanie, **1 718 surfaces brûlées sur 2 016 (85 %) ont eu lieu hors de la période juin-septembre**, surtout de janvier à avril. Or la Météo des forêts n'est publiée que de fin mai à début octobre.

| Mois | Janv. | Févr. | Mars | Avr. | Mai | Juin | Juil. | Août | Sept. | Oct. | Nov. | Déc. |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Occitanie | 300 | 519 | 530 | 250 | 7 | 43 | 105 | 94 | 56 | 39 | 24 | 49 |
| Haute-Garonne | 3 | 12 | 6 | 3 | 0 | 2 | 0 | 2 | 0 | 5 | 0 | 4 |

Ces feux de fin d'hiver se trouvent surtout dans les départements de montagne (Lozère : 629, Hautes-Pyrénées : 417, Ariège : 254) et en Haute-Garonne dans des communes pyrénéennes (Arguenos, Gouaux-de-Larboust, Artigue). Cela pourrait expliquer que des chefs de centre aient combattu des feux « des jours où l'indice était au plus bas », ou en l'absence d'indice. **Hypothèse à vérifier** : brûlages pastoraux (écobuages) ; la cause n'est pas dans EFFIS et devra être recoupée avec la BDIFF.

## Points de vigilance

- **Ce ne sont pas des départs de feu** : EFFIS cartographie des **surfaces brûlées vues par satellite**. Les petits feux sont absents ou sous-représentés : la documentation indique un seuil d'environ **30 ha** avant 2018 ; Sentinel-2 permet ensuite de descendre en dessous, sans seuil précis documenté.
- **Toute végétation** : une surface peut être à 100 % « autre végétation naturelle » (landes, prairies), sans forêt. Pour coller à la définition de « feu de forêt » du glossaire, il faudra filtrer avec les champs d'occupation du sol (178 enregistrements n'en ont pas).
- **Ruptures dans le temps** : ne pas comparer 2026 aux années 2000-2018 sans tenir compte du changement de satellite.
- **Pas de code INSEE** : prévoir une jointure spatiale (à coordonner avec Hocine pour Admin Express).

## Liens consultés

- [EFFIS, page « Data and services »](https://forest-fire.emergency.copernicus.eu/applications/data-and-services)
- [API des surfaces brûlées, France](https://api.effis.emergency.copernicus.eu/rest/2/burntareas/current/?country=FR&format=json)
- [Licence des données EFFIS](https://forest-fire.emergency.copernicus.eu/about-effis/data-license)
- [Méthode de cartographie (Rapid Damage Assessment)](https://forest-fire.emergency.copernicus.eu/about-effis/technical-background/rapid-damage-assessment)
