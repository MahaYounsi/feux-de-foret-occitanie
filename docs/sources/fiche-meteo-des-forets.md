# Fiche d'identité — Archives de la Météo des forêts

- **Explorée par :** Hocine Ait Yakoub (responsable qualité), 2026-11-17
- **Page de la source :** https://www.data.gouv.fr/datasets/archives-de-la-meteo-des-forets
- **Fichiers ouverts :** `mdf_2024.csv.gz`, `mdf_2025.csv.gz`, `mdf_2026.csv.gz`, `donnees-expertisees-meteodesforets-departements-20251218.geojson`, `donnees-expertisees-presentation-meteodesforets-20260909.pdf`

| Rubrique | Valeur |
|---|---|
| Propriétaire et système | Météo-France. Le niveau est établi par les prévisionnistes à partir de l'Indice de danger intégré (IFM complété par l'état de sécheresse de la végétation et l'occupation des sols du département), d'après la documentation PDF. Publié sur data.gouv.fr. |
| Mode d'accès (export, API, téléchargement) et format | Téléchargement de fichiers sur data.gouv.fr : un fichier CSV compressé (`.csv.gz`) par saison, plus un contour des départements (GeoJSON) et une présentation (PDF). Une API Météo des forêts existe aussi sur data.gouv.fr : non explorée. |
| Grain (une ligne = ?) | Un département × une date de publication. Chaque ligne donne deux prévisions : `niveau_j1` (danger prévu pour le lendemain) et `niveau_j2` (pour le surlendemain). Niveaux de 1 à 4 : faible, modéré, élevé, très élevé. |
| Emprise géographique | 96 départements : l'Hexagone et la Corse (`2A`, `2B`), dont les 13 départements d'Occitanie. Pas d'outre-mer. Vérifié dans les trois fichiers et dans le GeoJSON (96 contours). |
| Période réellement couverte par les données | Dates de publication : du 2024-06-03 au 2024-09-30 (120 jours), du 2025-06-03 au 2025-09-30 (120 jours), du 2026-05-28 au 2026-10-05 (131 jours). Aucun jour manquant dans ces intervalles. Pas d'archive pour 2023, alors que l'outil existe depuis 2023 selon la documentation. Rien hors saison (hiver, début de printemps). |
| Date de dernière mise à jour affichée sur la fiche | 5 octobre 2026 (fichier de la saison 2026 sur data.gouv.fr). |
| Fréquence de mise à jour | Une publication par jour pendant la saison (vérifié : un jeu de 96 lignes par jour, sans trou). data.gouv.fr signale « fréquence de mise à jour non respectée » pour le jeu de données. |
| Volumétrie | 35 616 lignes au total : 11 520 (2024), 11 520 (2025), 12 576 (2026). Environ 450 Ko par fichier décompressé, 40 à 50 Ko compressé. Volume très léger. |
| Clés disponibles (sur quoi pourra-t-on joindre ?) | Code département (`num_dep`) et date. Avec BDIFF : par département (déduit du code commune) et par jour, à condition de décaler la date (voir points qualité 1 et 3). Avec le GeoJSON : `num_dep` = `code`. |
| Données personnelles | Aucune. Les colonnes sont une date, un code et un nom de département, et deux niveaux de danger. |
| Licence | Licence Ouverte / Open Licence version 2.0 (Etalab). |
| Questions de mon analyse auxquelles elle pourrait répondre | Q2 (part des jours avec feu par niveau), Q3 (fausses alertes et feux manqués selon le seuil) et Q4 (comparaison Haute-Garonne, Occitanie, France), une fois croisée avec un historique des feux. Elle ne répond pas à Q1 : le niveau est donné pour tout le département, pas pour une commune ou un massif. |

## Points qualité relevés

1. **La colonne `date` est la date de publication, pas le jour concerné.** `niveau_j1` porte sur le lendemain et `niveau_j2` sur le surlendemain. Exemple vérifié : la ligne publiée le 2026-07-09 donne `niveau_j1 = 4` pour la Haute-Garonne, c'est-à-dire le rouge du 10 juillet 2026. Sans ce décalage, le croisement avec les feux serait faux d'un jour.
2. **Deux prévisions pour un même jour, qui peuvent différer.** Pour le 10 juillet 2026 en Haute-Garonne : niveau 3 dans la publication du 8 juillet (`niveau_j2`), niveau 4 dans celle du 9 juillet (`niveau_j1`). Il faut décider laquelle retenir et consigner la décision dans le journal.
3. **Le format change d'une année à l'autre :**
   - séparateur `,` en 2024 et 2025, `;` en 2026 ;
   - colonne du nom du département : `nom_dep` (2024, 2026) mais `dep_nom` (2025) ;
   - code département sur un caractère (`1`, `9`) en 2024 et 2025, sur deux caractères (`01`, `09`) en 2026 : à normaliser avant toute jointure ;
   - heure de publication : 16:00 UTC en 2024, 14:50 UTC en 2025 et 2026.
4. **Historique court :** trois saisons seulement (2024 à 2026), d'environ quatre mois chacune. Un feu survenu hors de ces périodes n'a pas de niveau associé.
5. **Peu de jours aux niveaux élevés, et très inégaux selon les années.** En Haute-Garonne (`niveau_j1`) : 2024 : 104 jours au niveau 1, 15 au niveau 2, 1 au niveau 3, 0 au niveau 4 ; 2025 : 69 / 41 / 10 / 0 ; 2026 : 26 / 70 / 31 / 4. Pour juger un seuil à 3 ou à 4, l'échantillon est faible.
6. **La documentation et les données ne concordent pas :** le PDF annonce une publication « à compter du 3 juin », alors que la saison 2026 commence le 28 mai et finit le 5 octobre.
7. **Complétude et cohérence :** aucune valeur vide, aucun doublon (département, date), niveaux toujours compris entre 1 et 4 dans les trois fichiers.

## Rubriques non vérifiées

- **API Météo des forêts :** non explorée dans le temps de l'exercice, seuls les fichiers téléchargeables ont été ouverts.
