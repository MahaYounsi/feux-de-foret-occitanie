# Inventaire des sources — Occitanie

Mise en commun du 17 novembre 2026, à partir des fiches du groupe.

| Source | Explorée par | Pertinente pour nos questions ? | Ce que nous avons découvert |
|---|---|---|---|
| [BDIFF](fiche-bdiff.md) | Soukaina Goumih | Oui, pour repérer les communes où les feux se répètent. En la croisant avec la météo, on pourra aussi étudier les jours avec feu selon le niveau de danger. | Les extraits ouverts contiennent 885 incendies recensés en Occitanie sur 2024 et 2025. Le portail officiel était inaccessible, donc une version republiée par Esri a été utilisée. Cette version signale des lignes manquantes. Les données BDIFF 2026 sont encore en cours de saisie. |
| Météo des forêts — [fiche de Hocine](fiche-meteo-des-forets.md) et [fiche de Samy](fiche-archives-meteo-des-forets.md) | Hocine Ait Yakoub et Samy Bouaouni | Oui, pour comparer les niveaux de danger avec les feux observés et tester différents seuils de renfort. | Les fichiers couvrent 2024 à 2026, avec 35 616 lignes pour les 96 départements métropolitains. Chaque bulletin prévoit le lendemain et le surlendemain. Il faut utiliser la date prévue pour faire le croisement avec les feux. |
| [EFFIS](fiche-effis.md) | Maha Younsi | Oui, pour localiser les surfaces brûlées et regarder ce qui s’est passé en 2026. | La fiche relève 2 016 surfaces cartographiées en Occitanie, de 2000 à novembre 2026. Les petits feux sont moins bien représentés et un même feu peut avoir plusieurs surfaces. Le changement de satellites complique la comparaison entre les années. |
| [IFM / FWI Copernicus](fiche-ifm-copernicus.md) | Hocine Ait Yakoub | Oui, comme complément pour étudier le danger météo sur une période plus longue, si on arrive à traiter les données. | Hocine a ouvert un extrait de l’été 2025. Le format NetCDF demande un traitement avec Python. L’indice est calculé à partir d’une réanalyse météo. Le lien avec les quatre niveaux de la Météo des forêts reste à vérifier. |

## Quelles questions de nos analyses n’ont encore aucune source ?

Il nous manque surtout le budget, le coût d’une journée de renfort, le seuil actuel et les dates où le dispositif a été activé. Il faudra aussi demander les secteurs d’intervention du SDIS 31 pour savoir où répartir les moyens.

Pour les jours de faible danger et la comparaison entre départements, on a des sources à croiser. Il faut encore vérifier que les périodes et les territoires correspondent et repérer les données manquantes. L’extrait BDIFF ouvert couvre l’Occitanie ; la comparaison nationale demandera un export plus large.

Pour 2026, EFFIS apporte déjà des surfaces brûlées, mais il nous manque encore un relevé complet des départs de feu, notamment les petits feux.

## Quelle source nous a surpris, et pourquoi ?

EFFIS nous a surpris parce que la fiche de Maha montre beaucoup de surfaces brûlées hors de l’été, surtout dans les départements de montagne. Il faudra regarder si ces dates entrent dans notre période d’étude. Quand aucun bulletin météo n’est disponible, on laissera le niveau comme manquant.

On a aussi remarqué qu’une même journée peut avoir deux prévisions différentes dans la Météo des forêts. Il faudra choisir ensemble si on utilise celle du lendemain (J+1) ou celle du surlendemain (J+2).

## Quelle source semble utile mais inexploitable dans le temps du projet ?

L’IFM Copernicus semble le plus long à exploiter. Un extrait a pu être ouvert, mais traiter tout l’historique et le relier aux niveaux de la Météo des forêts demanderait plus de travail. On doit encore décider si c’est faisable dans le temps disponible. Les valeurs de réanalyse demandent aussi de vérifier ce qu’on peut en déduire sur les annonces faites à l’époque.

EFFIS et la BDIFF ont posé des problèmes d’accès, mais les API ou les versions republiées ont permis d’explorer leurs données.

## À revoir ensemble

Hocine et Samy ont exploré la même source météo. On devra choisir une fiche de référence en gardant les contributions de chacun.

Pour commencer, on peut proposer de croiser la BDIFF et la météo sur 2024 et 2025, aux dates communes. Il faudra harmoniser les codes département et vérifier la couverture des relevés avant de compter les jours sans feu.
