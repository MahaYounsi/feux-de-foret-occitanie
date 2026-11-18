# Fiche source - Archives de la Météo des forêts

Fiche remplie par Samy Bouaouni.
Page : https://www.data.gouv.fr/datasets/archives-de-la-meteo-des-forets

| Rubrique | Valeur |
|---|---|
| Propriétaire et système | Météo-France. Système : « Indice de danger intégré » (indice forêt météo + sécheresse de la végétation, relevés ONF), calculé chaque jour (PDF, p. 1 et 3). |
| Mode d'accès (export, API, téléchargement) et format | Téléchargement sur data.gouv.fr : 3 fichiers csv.gz, un par année. Séparateur virgule en 2024 et 2025, point-virgule en 2026. L'API associée donne seulement J+1 et J+2, pas l'archive. |
| Grain (une ligne = ?) | Un département × un jour d'émission, avec `niveau_j1` (lendemain) et `niveau_j2` (surlendemain). 5 colonnes : `date`, `num_dep`, `niveau_j1`, `niveau_j2`, `nom_dep`. Exactement 96 lignes par jour dans les 3 fichiers. |
| Emprise géographique | 96 départements de métropole, Corse comprise (2A, 2B), dont les 13 d'Occitanie et la Haute-Garonne. Pas d'outre-mer. |
| Période réellement couverte par les données | 2024 : du 3 juin au 30 sept. (120 jours). 2025 : du 3 juin au 30 sept. (120 jours). 2026 : du 28 mai au 5 oct. (131 jours). Aucun jour manquant dans ces saisons, rien en dehors. Rien avant 2024. |
| Date de dernière mise à jour affichée sur la fiche | 5 octobre 2026 (autre page : 5 août 2026). Ce n'est pas la période couverte. |
| Fréquence de mise à jour | Une émission par jour en saison (vérifié, aucun trou). Le jeu n'est pas mis à jour chaque jour : « fréquence non respectée » sur la page, fichiers du 24 juin, 25 juin et 5 oct. 2026. |
| Volumétrie | 35 616 lignes (11 520 + 11 520 + 12 576). Fichiers de 40, 43 et 50 Ko compressés (441 à 470 Ko décompressés, taille affichée sur la page). |
| Clés disponibles (sur quoi pourra-t-on joindre ?) | `num_dep` = code département, mais écrit `1` en 2024 et 2025 et `01` en 2026 ; `2A` et `2B` pour la Corse. À mettre sur 2 caractères pour joindre au `code` du geojson. Ne pas joindre sur le nom (« Territoire-de-Belfort » ici, « Territoire de Belfort » dans le geojson). `date` : jour d'émission, heure UTC variable (16h00 en 2024, environ 14h50 ensuite). |
| Données personnelles | Aucune : date, code et nom de département, 2 niveaux. Aucune valeur vide. |
| Licence | Licence Ouverte 2.0 (page du jeu de données). La page de l'API affiche « non renseignée ». |
| Questions de votre analyse auxquelles elle pourrait répondre | Questions 2, 3 et 4 (jours au-dessus du seuil), croisées avec une source de feux : elle ne contient aucun feu. Pas la question 1 (départements seulement), ni le budget. |

## Non vérifié, et pourquoi

- Sens de `niveau_j1` (lendemain) et `niveau_j2` (surlendemain), et correspondance 1 faible, 2 modéré, 3 élevé, 4 très élevé : vient de la documentation, pas des données.
- Fin de la saison 2026 : le fichier s'arrête au 5 octobre, qui est aussi la date de mise à jour ; on ne sait pas si la saison continue.

## Ce que la fiche change pour notre analyse

- Indice départemental : pas de localisation à la commune (question 1).
- 3 saisons seulement (2024 à 2026) : pas de 10 ans d'historique. Le niveau 4 existe, mais il est rare (en J+1 : 1 ligne en 2024, 29 en 2025, 99 en 2026 sur les 96 départements).
- Niveaux = prévisions, pas du danger observé.
- Pour le pipeline : le niveau du jour D vient de `niveau_j1` de l'émission de D-1 ou de `niveau_j2` de celle de D-2. Il faut aussi unifier les 3 fichiers (séparateur, code département, nom de colonne : `nom_dep` en 2024 et 2026, `dep_nom` en 2025).
- Haute-Garonne, jours au niveau 3 ou 4 en J+1 : 1 en 2024, 10 en 2025, 35 en 2026. Le seuil change donc fortement le nombre de jours à renforcer (question 4).