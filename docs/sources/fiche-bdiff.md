# Fiche d’identité — BDIFF, feux de forêt 2024 et 2025

**Explorée par** — Soukaina Goumih, le 17 novembre 2026  
**Périmètre du projet** — Occitanie, avec un focus sur la Haute-Garonne (31)  
**Fichiers ouverts** — deux réponses JSON des couches 2024 et 2025 filtrées sur les 13 départements d’Occitanie. Les couches sont une diffusion adaptée de la BDIFF par Esri France. La page de recherche du portail BDIFF a renvoyé une erreur HTTP 503 lors de l’exploration, ce qui a empêché de récupérer son export CSV.

| Rubrique | Valeur |
|---|---|
| Propriétaire et système | BDIFF, diffusée par l’IGN sur data.gouv.fr. Les fichiers ouverts proviennent de couches ArcGIS publiées par Esri France, qui cite l’IGN et Géorisques. |
| Mode d’accès et format | Le portail BDIFF documente un export CSV UTF-8 dans un ZIP après filtrage. Accès utilisé pour cette fiche : API ArcGIS REST, réponse JSON sans géométrie, une couche par année. |
| Grain (une ligne = ?) | Un incendie recensé correspond à un enregistrement. Les attributs comprennent la commune, le département et l’horodatage de la première alerte. |
| Emprise géographique | La documentation des couches annonce la France métropolitaine et les DOM. Les fichiers ouverts ont été filtrés sur l’Occitanie, dont la Haute-Garonne. La couverture exhaustive des départements est **non vérifiée**, car la présence d’un territoire dans la documentation ne garantit pas qu’il contient des enregistrements exhaustifs. |
| Période réellement couverte | En Occitanie, dates de première alerte constatées du 1er janvier au 29 décembre **2024** et du 10 janvier au 31 décembre **2025**. Les extrêmes indiquent la première et la dernière alerte du fichier, sans établir l’exhaustivité du relevé. Le portail BDIFF indique que **2026 est en cours de saisie** et que cette campagne n’est pas diffusée publiquement. |
| Date de dernière mise à jour affichée sur la fiche | **13 décembre 2025** sur la fiche BDIFF de data.gouv.fr. Les métadonnées ArcGIS des deux couches indiquent une modification le **27 août 2026**. |
| Fréquence de mise à jour | **Annuelle** pour la BDIFF d’après data.gouv.fr. Fréquence de mise à jour des couches ArcGIS **non vérifiée**, faute de calendrier indiqué dans leurs fiches consultées. |
| Volumétrie | **413** enregistrements en Occitanie pour 2024 et **472** pour 2025, soit **885** au total dans les deux JSON ouverts (38 champs par enregistrement). Sur l’ensemble de chaque couche, l’API renvoie **1 367** et **2 539** enregistrements, respectivement. |
| Clés disponibles | `Code_INSEE` pour joindre un référentiel de communes. Pour la météo, utiliser `Departement` et le jour local dérivé de `Date_de_premiere_alerte`. Convertir l’horodatage UTC en heure locale de l’Occitanie avant d’en extraire le jour et le croiser avec le **jour prévu** J+1. |
| Données personnelles | Aucun nom de personne ni coordonnée de contact dans les champs observés. La couche comporte un champ de décompte des décès. La présence éventuelle d’informations indirectement identifiantes dans les autres attributs est **non vérifiée**, faute de revue complète de leur contenu. |
| Licence | La fiche BDIFF indique **Licence Ouverte 2.0**. Les métadonnées des couches ArcGIS renvoient aux [mentions légales de la BDIFF](https://bdiff.agriculture.gouv.fr/mentions-legales). Une licence distincte pour la version ArcGIS est **non vérifiée**, faute de mention explicite dans ses métadonnées. |
| Questions de l’analyse | **Q1 — Secteurs prioritaires** : repérer les communes touchées plusieurs étés, puis joindre le découpage du SDIS 31 pour remonter aux secteurs. **Q2 — Choix du seuil** : compter, après croisement avec la Météo des forêts, les jours avec incendie recensé qui auraient été couverts par chaque seuil. Les activations, coûts et le budget nécessitent des données du SDIS. **Q3 — Jours de danger faible** : repérer les communes et créneaux d’alerte en croisant avec la météo. L’heure exacte de départ reste à vérifier. **Q4 — Comparaison** : agréger les incendies par jour et département, puis comparer à niveau de danger égal sur les mêmes dates. Pour la comparaison nationale, utiliser l’emprise commune aux deux jeux de données. |

## Point de vigilance

Commencer le croisement avec les deux saisons communes, **2024 et 2025**. Les métadonnées Esri signalent que certaines lignes de la BDIFF n’ont pas pu être intégrées. Un jour sans incendie recensé doit rester distinct d’un jour dont la couverture n’est pas vérifiée.

## Liens consultés

- [Fiche officielle BDIFF sur data.gouv.fr](https://www.data.gouv.fr/datasets/base-de-donnees-sur-les-incendies-de-forets-en-france-bdiff/)
- [Documentation de l’export BDIFF](https://bdiff.agriculture.gouv.fr/aide/recherche)
- [Couche ArcGIS 2024](https://services.arcgis.com/d3voDfTFbHOCRwVR/ArcGIS/rest/services/G%C3%A9orisques___Les_feux_de_For%C3%AAt__2024_/FeatureServer/16)
- [Couche ArcGIS 2025](https://services.arcgis.com/d3voDfTFbHOCRwVR/ArcGIS/rest/services/G%C3%A9orisques___Les_feux_de_For%C3%AAt__2025_/FeatureServer/13)
