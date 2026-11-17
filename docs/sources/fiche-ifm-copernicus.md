# Fiche d'identité — Indice Forêt Météo (IFM / FWI), Copernicus

- **Explorée par :** Hocine Ait Yakoub (responsable qualité), 2026-11-17
- **Page de la source :** https://ewds.climate.copernicus.eu/datasets/cems-fire-historical-v1 (« Fire danger indices historical data from the Copernicus Emergency Management Service »)
- **Fichier ouvert :** un extrait téléchargé le 2026-11-17 : variable *Fire weather index*, réanalyse, jeu consolidé, version 4.1, du 1er juin au 30 septembre 2025, rectangle Nord 51.5 / Sud 41 / Ouest -5.5 / Est 10, grille 0.25° × 0.25°, format NetCDF4.

> **Le mot « canadien » :** le FWI (Fire Weather Index) est une méthode de calcul conçue par le Service canadien des forêts, devenue la référence internationale. Les données sont bien celles de la France : la méthode est appliquée à la météo de chaque point de la grille. L'IFM de Météo-France est le nom français de cet indice, et la documentation de la Météo des forêts indique que Météo-France s'en sert pour établir ses niveaux de danger.

| Rubrique | Valeur |
|---|---|
| Propriétaire et système | Copernicus Emergency Management Service (CEMS), pour le système européen d'information sur les feux de forêt (EFFIS). Données calculées par le Centre européen de prévision météorologique à moyen terme (ECMWF), à partir de la réanalyse météo ERA5. Attributs du fichier : `institution = European Centre for Medium-Range Weather Forecasts`. |
| Mode d'accès (export, API, téléchargement) et format | Téléchargement par formulaire sur l'Early Warning Data Store (EWDS) : compte gratuit obligatoire, acceptation de la licence, puis demande placée en file d'attente avant le téléchargement. Une API existe aussi (code proposé par le formulaire) : non testée. Formats proposés : GRIB ou NetCDF4, marqué « Experimental ». Le fichier reçu est un NetCDF4 (HDF5), converti depuis du GRIB2. |
| Grain (une ligne = ?) | Une valeur = un point de grille de 0,25° × 0,25° (environ 28 km × 20 km en France) × un jour. Variable `fwinx`, sans unité (`units = Numeric`), dimensions `valid_time × latitude × longitude`. |
| Emprise géographique | Terres émergées du monde entier d'après la page. Dans l'extrait : 43 latitudes × 63 longitudes = 2 709 points, de 41° à 51,5° Nord et de -5,5° à 10° Est. Ce rectangle déborde sur les pays voisins (Espagne, Royaume-Uni, Belgique, Allemagne, Suisse, Italie) : il faut le découper sur les limites de la France. |
| Période réellement couverte par les données | Dans le fichier ouvert : du 2025-06-01 au 2025-09-30, 122 jours consécutifs, sans trou. La page annonce une couverture de 1940 à aujourd'hui, et le formulaire propose les années 1940 à 2026 : **non vérifiée dans un fichier**, seul l'extrait 2025 a été téléchargé. |
| Date de dernière mise à jour affichée sur la fiche | 2026-11-16, d'après la page EWDS. |
| Fréquence de mise à jour | Quotidienne d'après la page, prolongée à mesure que la réanalyse ERA5 est disponible. Le formulaire distingue un jeu « Consolidated » et un jeu « Intermediate » : le délai entre les deux est **non vérifié**. |
| Volumétrie | Extrait ouvert : 2 709 points × 122 jours = 330 498 valeurs, 655 Ko. Volume complet (toutes les années, toute la France) : **non vérifié**, aucun téléchargement complet n'a été fait. |
| Clés disponibles (sur quoi pourra-t-on joindre ?) | Latitude, longitude et date (`valid_time`). **Il n'y a pas de code département ni de code commune.** Pour joindre avec la Météo des forêts ou BDIFF, il faut rattacher chaque point de grille à un département (avec le GeoJSON des départements fourni avec la Météo des forêts, par exemple). Test fait : la Haute-Garonne contient 13 points de grille. |
| Données personnelles | Aucune : des valeurs météo calculées sur une grille. |
| Licence | CC-BY (affichée sur la page et à accepter dans le formulaire). Citation de la source obligatoire. |
| Questions de mon analyse auxquelles elle pourrait répondre | Q2, Q3 et Q4 sur une période beaucoup plus longue que la Météo des forêts, à condition de traduire l'indice en niveaux comparables. En partie Q1 : la grille de 25 km distingue des zones à l'intérieur de la Haute-Garonne (13 points), mais elle mesure un danger météo, pas des feux. |

## Points qualité relevés

1. **Ce n'est pas le même indicateur que la Météo des forêts.** Le FWI est une valeur continue (de 0 à 43 en Haute-Garonne à l'été 2025), alors que la Météo des forêts publie 4 niveaux établis par des prévisionnistes, qui ajoutent la sécheresse de la végétation et l'occupation des sols. Aucune table de passage officielle entre FWI et niveaux n'a été trouvée.
2. **Test exploratoire : le lien avec la Météo des forêts est fort.** En Haute-Garonne, du 1er juin au 30 septembre 2025, j'ai comparé le FWI moyen du département avec le niveau de la Météo des forêts du même jour (`niveau_j1` décalé d'un jour), sur 119 jours communs. FWI moyen de 4,8 les jours de niveau 1 (68 jours), de 15,5 au niveau 2 (41 jours) et de 31,5 au niveau 3 (10 jours). Corrélation de rang de Spearman : 0,81. Le FWI pourrait donc servir à **reconstituer un historique avant 2024**, mais c'est une hypothèse à valider en groupe, pas une donnée de la source.
3. **Environ 18 % de valeurs vides dans l'extrait.** Elles correspondent à la mer (la source ne couvre que les terres). C'est normal, mais il faut les exclure et non les traiter comme des zéros.
4. **Les petits départements n'ont aucun point de grille.** Paris (75), les Hauts-de-Seine (92) et la Seine-Saint-Denis (93) ne contiennent aucun point à 0,25° : il faut une autre règle d'agrégation (point le plus proche, moyenne pondérée par la surface). Ça ne touche pas l'Occitanie, mais ça compte pour la comparaison nationale (Q4).
5. **Grille interpolée.** La grille 0,25° est une interpolation de la grille d'origine (environ 31 km d'après la page). La valeur d'un point n'est pas une mesure de station météo.
6. **Format peu pratique et marqué « Experimental ».** NetCDF4 ou GRIB, lisibles avec Python (`xarray`) mais pas avec un tableur. Il faut un compte et une file d'attente : à prévoir dans le pipeline (extraction non automatique sans l'API).
7. **Heure de référence de la valeur quotidienne :** `valid_time` est à 00:00 chaque jour, mais l'heure exacte à laquelle l'indice est calculé n'est **pas vérifiée**. C'est à confirmer dans la documentation avant tout croisement fin avec les dates des feux.

## Rubriques non vérifiées

- **Période complète (1940 à aujourd'hui) et volumétrie totale :** seul l'extrait 2025 a été téléchargé.
- **API :** non testée.
- **Délai entre jeu intermédiaire et jeu consolidé :** non trouvé.
- **Heure de calcul de l'indice quotidien :** non trouvée dans le fichier.
