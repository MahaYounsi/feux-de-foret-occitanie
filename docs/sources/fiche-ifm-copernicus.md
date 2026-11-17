# Fiche d'identité — Indices de danger feu historiques (Copernicus EWDS)

**Explorée par** — Maha Younsi, le 17 novembre 2026
**Périmètre du projet** — Occitanie, avec un focus sur la Haute-Garonne (31)
**Fichiers ouverts** — **aucun fichier de données pour l'instant** : le téléchargement demande un compte (voir « Mode d'accès »). Cette fiche s'appuie sur le catalogue de l'Early Warning Data Store (métadonnées et formulaire de téléchargement). Les rubriques qui dépendent du contenu d'un fichier sont marquées « non vérifiée ».

| Rubrique | Valeur |
|---|---|
| Propriétaire et système | **Copernicus Emergency Management Service (CEMS)**, produit par le **CEPMMT (ECMWF)** pour le **Centre commun de recherche (JRC)** de la Commission européenne, dans le cadre du système européen EFFIS. Jeu « Fire danger indices historical data from the Copernicus Emergency Management Service » (`cems-fire-historical-v1`), DOI 10.24381/cds.0e89c522. Les indices sont calculés à partir de la **réanalyse météorologique ERA5**, et non à partir des données de Météo-France. |
| Mode d'accès et format | **Formulaire web ou API** de l'Early Warning Data Store, avec **compte obligatoire** (l'API renvoie « authentication required » sans identifiant). Formats proposés : **GRIB** ou **NetCDF4** (indiqué comme expérimental). On choisit la variable, l'année, le mois, le jour, la grille (originale, 0,25° ou 0,5°) et une zone géographique. |
| Grain (une ligne = ?) | **Non vérifiée**, aucun fichier ouvert. D'après le formulaire : une valeur par maille de grille et par jour sélectionné. |
| Emprise géographique | **Mondiale** d'après les métadonnées. Le formulaire permet de découper une zone (pas de 0,05°), donc d'extraire l'Occitanie ou la France. |
| Période réellement couverte | **Non vérifiée** dans un fichier. Les métadonnées annoncent du **3 janvier 1940 au 14 novembre 2026**. Deux versions existent : « consolidated » (consolidée) et « intermediate » (provisoire, pour la période la plus récente). |
| Date de dernière mise à jour affichée sur la fiche | **16 novembre 2026** (catalogue EWDS). Jeu publié le 30 septembre 2019. |
| Fréquence de mise à jour | **Quotidienne** d'après les métadonnées du catalogue. |
| Volumétrie | **Non vérifiée** : aucun fichier téléchargé. Elle dépendra de la zone, de la période et des variables choisies. |
| Clés disponibles | **Latitude, longitude et date** (d'après le formulaire ; non vérifiée dans un fichier). **Pas de code département** : il faudra une jointure spatiale avec les contours des départements (Admin Express) pour agréger par département et croiser avec la Météo des forêts ou la BDIFF. |
| Données personnelles | **Aucune** : indices météorologiques calculés sur une grille (description du jeu). |
| Licence | **CC-BY 4.0** (catalogue EWDS), citation de la source obligatoire. |
| Questions de l'analyse | **Q3, Q4 et Q6** sur une période beaucoup plus longue que la Météo des forêts (3 saisons seulement), en croisant avec la BDIFF. **Q9** : situer la saison 2026 par rapport aux décennies précédentes. Variable utile : `fire_weather_index` (indice canadien FWI), plus ses composantes (`fine_fuel_moisture_code`, `duff_moisture_code`, `drought_code`, `initial_fire_spread_index`, `build_up_index`, `fire_daily_severity_rating`). |

## Points de vigilance

- **Ce n'est pas l'indice de la direction** : la Météo des forêts publie des niveaux de 1 à 4, établis par Météo-France à partir de son propre IFM, de la sécheresse de la végétation et de la surface forestière. Copernicus fournit une valeur continue calculée avec ERA5. La correspondance entre `fire_weather_index` et l'IFM de Météo-France reste **à vérifier**.
- **Traduire en niveaux** : pour répondre à la direction, il faudra définir des seuils de FWI équivalents aux niveaux de la Météo des forêts, par exemple en comparant les deux sur les saisons 2024 à 2026.
- **Format technique** : GRIB et NetCDF demandent des bibliothèques spécifiques (xarray, cfgrib, netCDF4). À coordonner avec Sami (pipeline).

## Reste à faire

1. Créer un compte sur l'Early Warning Data Store et accepter la licence CC-BY.
2. Télécharger un premier échantillon : `fire_weather_index`, zone Occitanie, juillet 2025, NetCDF, version consolidée.
3. Ouvrir le fichier et compléter les rubriques « non vérifiée » : grain, période, volumétrie, clés.

## Liens consultés

- [Fiche du jeu sur l'Early Warning Data Store](https://ewds.climate.copernicus.eu/datasets/cems-fire-historical-v1)
- [Métadonnées du catalogue (API)](https://ewds.climate.copernicus.eu/api/catalogue/v1/collections/cems-fire-historical-v1)
