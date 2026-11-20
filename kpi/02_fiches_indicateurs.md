# Fiches d'indicateurs

Projet feux-de-foret-occitanie · Statut : à remplir

Chaque membre remplit **sa** section uniquement, pour éviter les conflits de fusion. Le jeu d'indicateurs v0 est rédigé en groupe à la fin.

<!-- Gabarit d'une section : recopier ces rubriques dans votre section.

### Fiche : <nom de l'indicateur>

| Rubrique | Contenu |
|---|---|
| 1. Question et objectif | |
| 2. Formule : numérateur, dénominateur, unité | |
| 3. Paramètres (ce qui peut changer la valeur) | |
| 4. Périmètre, période, granularité, fréquence | |
| 5. Source et champs | |
| 6. Lignes utilisables (part des lignes où tous les champs de la formule sont renseignés) | |
| 7. Proxy et biais (sens du biais : surestimation ou sous-estimation) | |
| 8. Décision éclairée (ce que la valeur change pour le SDIS) | |
| 9. Propriétaire (qui calcule, qui relit) | |

**Changement de paramètre :** paramètre, nouvelle valeur ; ce qui change dans la fiche (décision comprise) ; ce qui ne change pas.

**RACER (une phrase par critère) :**
- Relevant :
- Accepted :
- Credible :
- Easy :
- Robust :

**Détournement (K4) :** par qui, comment, avec quel effet.
**Garde-fou :** indicateur qui ne mesure pas la même chose.
**Risque résiduel :** ce que le garde-fou ne voit pas.

**Second indicateur (garde-fou) :** formule et source.

**Pre-mortem :**

| Rang | Raison d'échec | Probabilité | Gravité | Garde-fou |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | (pas exigé) |

**Rôle de chaque indicateur :** KPI principal, KPI secondaire, garde-fou, contexte, écarté (avec la raison).
-->

## Maha Younsi

Objectif suivi : [01_objectif_maha-younsi.md](01_objectif_maha-younsi.md) (D1, question G1). Statut : brouillon, à relire par le groupe.

### Fiche : part des départs de feu dans les secteurs prioritaires

| Rubrique | Contenu |
|---|---|
| 1. Question et objectif | **Question G1 :** dans quelles communes ou quels secteurs du 31 les départs de feu se concentrent-ils, et se répètent-ils d'une saison à l'autre ? **Objectif :** d'ici le 30 septembre 2027, faire passer de [a %] à [b %] la part des départs de feu du 31 survenus dans des secteurs prioritaires désignés avant le 1er mars 2027 et limités à [x %] des communes, sans hausse de la surface médiane parcourue par les feux hors de ces secteurs. |
| 2. Formule : numérateur, dénominateur, unité | **Numérateur :** nombre de départs de feu du 31, du 1er mars au 30 septembre, dont la commune (`Code_INSEE`) appartient à un secteur prioritaire. **Dénominateur :** nombre de départs de feu du 31 sur la même période. **Unité :** %. |
| 3. Paramètres | **R**, la règle de désignation des secteurs. Règle de base : commune touchée au moins une fois la saison précédente ; variante : au moins deux fois. **x %**, le plafond de communes prioritaires. **La période :** 1er mars au 30 septembre, ou toute l'année. **La maille :** la commune, ou les secteurs du SDIS 31 s'il les fournit. |
| 4. Périmètre, période, granularité, fréquence | **Périmètre :** la Haute-Garonne pour l'objectif ; l'Occitanie pour la valeur indicative et quand le 31 compte trop peu de feux (D-004). **Période :** du 1er mars au 30 septembre 2027, comparée à la saison 2025 (secteurs tirés de 2024). **Granularité :** un départ de feu, rattaché à une commune. **Fréquence :** une valeur par saison avec la BDIFF (publication annuelle) ; un suivi mensuel n'est possible qu'avec les interventions du SDIS 31. |
| 5. Source et champs | BDIFF, couches Géorisques 2024 (FeatureServer/16) et 2025 (FeatureServer/13), voir la [fiche BDIFF](../docs/sources/fiche-bdiff.md). Champs : `Code_INSEE` (commune), `Departement`, `Date_de_premiere_alerte` (date, en UTC, convertie en heure locale). Garde-fou : `Surface_parcourue`. |
| 6. Lignes utilisables | **100 %** : 885 sur 885 incendies d'Occitanie en 2024-2025 ont à la fois `Code_INSEE` et `Date_de_premiere_alerte`. Dans le 31 : 5 sur 5. Le champ `SurfaceFeuArriveeSecour` est vide sur les 885 lignes : il n'est pas utilisable. |
| 7. Proxy et biais | **« Secteur prioritaire » → commune.** Les secteurs du SDIS 31 ne sont pas connus (à demander). Biais : un feu parti dans la commune voisine d'un secteur compte « hors secteur », la part est **sous-estimée**. **« Départ de feu » → incendie recensé dans la BDIFF, daté par la première alerte.** Les petits feux éteints vite peuvent manquer. Si la surveillance renforcée fait détecter et recenser plus de petits feux dans les secteurs prioritaires, la part est **surestimée** (biais de détection). |
| 8. Décision éclairée | **Part élevée** (au moins [b %]) : les feux se répètent aux mêmes endroits. Le SDIS garde ses secteurs et y concentre patrouilles et guet. **Part faible** : les feux changent de place d'une saison à l'autre. Une liste fixe de secteurs ne sert pas : le SDIS passe à des moyens mobiles, déclenchés selon le niveau de la Météo des forêts (D2), ou change de règle de désignation. |
| 9. Propriétaire | **Porte l'indicateur et le présente à la direction :** Maha Younsi. **Calcule :** Samy Bouaouni (pipeline). **Relit :** Hocine Ait Yakoub (qualité). Répartition proposée, à valider en groupe. |

**Changement de paramètre.** Calcul sur l'Occitanie, feux de 2025, secteurs tirés des feux de 2024 :

| Règle R | Communes prioritaires | Part des feux 2025 (toute l'année) | Part des feux 2025 (1er mars au 30 septembre) |
|---|---|---|---|
| Au moins 1 feu en 2024 | 284 | 43 % (202 sur 472) | 43 % (156 sur 365) |
| Au moins 2 feux en 2024 | 77 | 18 % (85 sur 472) | 18 % (67 sur 365) |

- **Ce qui change** quand on passe de « 1 feu » à « 2 feux » :
  - la liste est presque 4 fois plus courte ;
  - elle ne couvre plus que 18 % des feux ;
  - avec cette règle, la lecture penche vers des moyens mobiles plutôt que vers des secteurs fixes ;
  - la cible [b %] doit être fixée à nouveau.
- **Ce qui ne change pas :**
  - la formule, la source, le dénominateur et le garde-fou ;
  - la période ne change presque rien : 43 % et 18 % dans les deux cas.
- La règle doit donc être fixée **avant** la saison, pas choisie après coup.

**RACER (une phrase par critère) :**
- **Relevant :** il mesure directement si les moyens concentrés sont là où les feux partent, ce qui est la question D1.
- **Accepted :** à confirmer avec la direction, qui doit accepter la commune comme maille ou fournir ses propres secteurs, avec les définitions du glossaire (« départ de feu »).
- **Credible :** oui si la règle R, le plafond et la période sont écrits avant la saison. Mais avec 4 ou 5 feux par saison dans le 31, deux lecteurs peuvent conclure différemment : d'où le seuil plancher.
- **Easy :** le calcul est simple (deux champs, 100 % renseignés), mais la BDIFF n'est publiée qu'une fois par an. La valeur 2027 n'arrive qu'après la saison, sauf avec les données d'intervention du SDIS 31.
- **Robust :** fragile. On peut le gonfler en élargissant les secteurs ou en choisissant la règle après coup, et il varie beaucoup avec peu de feux (voir K4).

**Détournement (K4) :**
- **Par qui :** celui qui désigne les secteurs prioritaires (l'équipe d'analyse ou l'état-major du SDIS).
- **Comment :** il ajoute en cours de saison, ou après, les communes où des feux viennent de partir.
- **Effet :** la part approche 100 % sans que les moyens aient été placés à l'avance.

**Garde-fous :**
- **Règle fixée à l'avance :** la liste des secteurs est versionnée dans le dépôt avant le 1er mars 2027 et n'est plus modifiée.
- **Volume :** le nombre de communes prioritaires et le nombre de feux de la saison sont affichés à côté de la part.
- **Seuil plancher :** sous [10, à valider] départs de feu dans la saison, la part du 31 n'est pas lue ; on lit celle de l'Occitanie.
- Aucun de ces garde-fous ne mesure la localisation des feux, comme le fait l'indicateur.

**Risque résiduel :**
- **Un feu dans un secteur prioritaire n'a pas forcément été mieux combattu.** L'indicateur et ses garde-fous montrent où partent les feux, pas si la présence des moyens a réduit leur nombre ou leur taille.
- **Si la surveillance dissuade les départs dans les secteurs prioritaires, la part baisse alors que la stratégie fonctionne.**

**Second indicateur (garde-fou) : surface médiane parcourue par les départs de feu hors secteurs prioritaires.**
- **Formule :** médiane de `Surface_parcourue` (m², unité à confirmer dans la documentation BDIFF) des départs de feu du 31, du 1er mars au 30 septembre, dont la commune n'est pas prioritaire.
- **Rôle :** contrepoids. Il se dégrade si le reste du territoire est délaissé, et il mesure la gravité, pas la localisation.
- **Médiane plutôt que moyenne :** un seul très grand feu fait passer la moyenne des feux de 2025 partis dans des communes déjà touchées en 2024 à 717 010 m², contre une médiane de 1 175 m².
- **Valeur indicative en Occitanie, en 2025 :**
  - médiane de 1 447 m² pour les 270 feux hors des communes touchées en 2024 ;
  - médiane de 1 175 m² pour les 202 feux dans ces communes.
- **Lignes utilisables :** 885 sur 885.

**Pre-mortem.** Dans un an, l'indicateur a échoué : le SDIS a pris une mauvaise décision à cause de lui.

| Rang | Raison d'échec | Probabilité | Gravité | Garde-fou |
|---|---|---|---|---|
| 1 | Trop peu de feux dans le 31 : la part vaut 0 % ou 100 % par hasard, et le SDIS garde ou abandonne ses secteurs à tort. | élevée (5 feux en 2 ans dans la BDIFF) | élevée | Seuil plancher, volume affiché à côté de la part, lecture à l'échelle de l'Occitanie, et demande des interventions du SDIS 31 |
| 2 | La direction lit une part élevée comme la preuve que concentrer les moyens réduit les feux, alors qu'elle dit seulement où ils partent (corrélation lue comme une cause). | moyenne | élevée | Afficher le contrepoids (surface médiane hors secteurs) et écrire dans chaque rendu ce que l'indicateur ne mesure pas |
| 3 | Les secteurs sont désignés sur une saison qui ne ressemble pas à 2027 (2026 très chargée en danger, feux hors saison, 37 % en Occitanie). | moyenne | moyenne | (pas exigé) |

**Rôle de chaque indicateur :**

| Indicateur | Rôle | Raison |
|---|---|---|
| Part des départs de feu dans les secteurs prioritaires | KPI principal | Répond à D1 : les moyens sont-ils là où partent les feux ? |
| Taux de répétition : part des communes touchées une saison qui le sont à nouveau la saison suivante | KPI secondaire | Explique et prépare le principal : sans répétition, aucune liste de secteurs ne peut marcher. Occitanie : 102 des 284 communes touchées en 2024 le sont à nouveau en 2025 (36 %). |
| Surface médiane parcourue hors secteurs prioritaires | Garde-fou | Contrepoids : se dégrade si le reste du territoire est délaissé. |
| Nombre de départs de feu de la saison | Garde-fou | Volume et seuil plancher : sous [10, à valider] feux, la part n'est pas lue. |
| Nombre de jours de niveau 3 ou plus dans le 31 | Contexte | Explique une saison chargée, sans guider le choix des secteurs. |
| Part des départs de feu hors saison de la Météo des forêts | Contexte | Rappelle que 37 % des feux (Occitanie) partent hors saison. On le note, on ne le pilote pas. |
| Surface parcourue à l'arrivée des secours | Écarté | Champ `SurfaceFeuArriveeSecour` vide sur les 885 lignes : infaisable. |
| Nombre total de feux en Occitanie | Écarté | Si la valeur double, aucune décision du SDIS 31 ne change : c'est une métrique de vanité. |
| Classement des communes du 31 par nombre de feux, sans plafond | Écarté | Avec 5 feux en 2 ans, il stigmatiserait quelques communes sans base solide. |

## Hocine Ait Yakoub

<!-- Fiche de Hocine Ait Yakoub -->

## Samy Bouaouni

Objectif suivi : [01_objectif_samy-bouaouni.md](01_objectif_samy-bouaouni.md) (D2, question [G à confirmer]). Statut : brouillon, à relire par le groupe.

### Fiche : taux de feux déclenchés sur des jours à indice bas

| Rubrique | Contenu |
|---|---|
| 1. Question et objectif | **Question :** à partir de quel niveau de la Météo des forêts le SDIS doit-il déclencher son dispositif ? **Objectif :** d'ici la fin de la saison 2027, faire passer de [a %] à [b %] la part des départs de feu du 31 survenus un jour d'indice inférieur à N, N étant fixé avant le début de la saison, sans que le nombre de jours déclenchés dépasse [budget, à demander]. |
| 2. Formule : numérateur, dénominateur, unité | **Numérateur :** nombre de départs de feu du 31, dans la période couverte par l'indice, survenus un jour D dont l'indice (`niveau_j1` de l'émission de la veille) est inférieur à N. **Dénominateur :** nombre de départs de feu du 31 sur la même période. **Unité :** %. |
| 3. Paramètres | **N**, le niveau de déclenchement : 2, 3 ou 4 (valeur d'essai : 3). **L'horizon de l'indice :** `niveau_j1` (lendemain) ou `niveau_j2` (surlendemain). **La date retenue pour un feu :** la première alerte, convertie en heure locale. **La période :** la saison de l'indice, car il n'existe pas en dehors. **La maille :** le département, imposé par l'indice. |
| 4. Périmètre, période, granularité, fréquence | **Périmètre :** la Haute-Garonne pour l'objectif ; l'Occitanie quand le 31 compte trop peu de feux (D-004). **Période :** saisons 2024, 2025 et 2026 pour les valeurs de départ, saison 2027 pour l'objectif. **Granularité :** un département pour un jour. **Fréquence :** une valeur par saison, car la BDIFF est publiée une fois par an. Le garde-fou (jours déclenchés) peut se suivre chaque mois si l'archive est mise à jour. |
| 5. Source et champs | **Indice :** Archives de la Météo des forêts, voir la [fiche](../docs/sources/fiche-archives-meteo-des-forets.md). Champs : `date`, `num_dep` (= 31), `niveau_j1`. **Feux :** BDIFF, voir la [fiche BDIFF](../docs/sources/fiche-bdiff.md). Champs : `Date_de_premiere_alerte`, `Departement`, `Code_INSEE`, repris de la fiche de Maha, non vérifiés par moi. **Jointure :** le département (`num_dep` sur 2 caractères, `31`) et le jour calendaire. |
| 6. Lignes utilisables | **Indice : 100 %.** 35 616 lignes sur 35 616 ont `date`, `num_dep`, `niveau_j1` et `niveau_j2` renseignés. Dans le 31 : 371 jours (120 + 120 + 131), sans trou. **Feux :** d'après la fiche de Maha, 885 sur 885 incendies d'Occitanie en 2024-2025 ont `Code_INSEE` et `Date_de_premiere_alerte`, dont 5 dans le 31. Mais 37 % des feux d'Occitanie partent hors saison de la Météo des forêts : sans niveau, ils sortent du calcul. **Part utilisable de la formule complète :** non vérifiée, le croisement n'est pas fait. |
| 7. Proxy et biais | **« Jour à indice bas » → jour dont le niveau prévu la veille est inférieur à N.** Le niveau est une prévision à J+1, pas un danger observé : le taux juge la prévision, le sens du biais n'est pas établi. **« Départ de feu » → incendie recensé dans la BDIFF, daté par la première alerte.** Un feu qui dure plusieurs jours n'a qu'un jour, donc la date retenue change le taux. 9 départs de feu sur 10 sont d'origine humaine (PDF de la Météo des forêts) : un feu humain un jour d'indice bas n'est pas une erreur de l'indice, le taux **surestime** alors ses défauts. |
| 8. Décision éclairée | **Taux élevé** (au moins [b %]) : des feux échappent au dispositif. Le SDIS abaisse N pour déclencher plus souvent. **Taux faible :** N reste ou est relevé, à condition de vérifier le nombre de jours déclenchés (second indicateur) par rapport au budget. **Sous le seuil plancher :** le taux du 31 n'est pas lu, on lit celui de l'Occitanie. |
| 9. Propriétaire | **Porte l'indicateur :** Samy Bouaouni. **Calcule :** Samy Bouaouni (pipeline). **Relit :** Hocine Ait Yakoub (qualité). Répartition reprise de la fiche de Maha, à valider en groupe. |

**Faisabilité.** Pour l'indice : faisable, vérifié dans les 3 fichiers. Pour les feux : le champ existe dans la BDIFF d'après la fiche du groupe, mais je n'ai pas fait le croisement. Avec 5 feux dans le 31 en 2024-2025, le taux du 31 est sous le plancher : seule la lecture à l'échelle de l'Occitanie est possible.

**Changement de paramètre.** Calcul sur la Haute-Garonne, avec `niveau_j1` : jours déclenchés, c'est-à-dire d'indice supérieur ou égal à N.

| N | 2024 (sur 120 jours) | 2025 (sur 120 jours) | 2026 (sur 131 jours) |
|---|---|---|---|
| 2 | 16 | 51 | 105 |
| 3 | 1 | 10 | 35 |
| 4 | 0 | 0 | 4 |

- **Ce qui change** quand on passe de N = 3 à N = 2 :
  - les « jours à indice bas » ne sont plus que les jours de niveau 1, donc le numérateur diminue et le taux baisse ou reste ;
  - la décision « abaisser N » devient moins probable ;
  - les jours déclenchés passent de 10 à 51 en 2025 et de 35 à 105 en 2026 ;
  - la cible [b %] doit être fixée à nouveau.
- **Ce qui ne change pas :**
  - le dénominateur (tous les feux de la période), la source, le grain et la définition d'un feu.
- N doit donc être fixé **avant** la saison, pas choisi après coup.

**RACER (une phrase par critère) :**
- **Relevant :** il mesure directement la part des feux qui échappent au dispositif, ce qui est la question D2.
- **Accepted :** à confirmer avec la direction, qui doit valider N et la définition d'un feu, avec les définitions du glossaire (« départ de feu »).
- **Credible :** oui si N, l'horizon et la date retenue sont écrits avant la saison. Mais avec 5 feux dans le 31 en 2 ans, deux lecteurs peuvent conclure différemment : d'où le seuil plancher.
- **Easy :** l'indice se lit facilement (3 fichiers à unifier), mais la BDIFF n'est publiée qu'une fois par an. La valeur 2027 n'arrive qu'après la saison, sauf avec les interventions du SDIS 31.
- **Robust :** fragile. On peut le faire baisser en abaissant N, et il varie beaucoup avec peu de feux (voir K4).

**Détournement (K4) :**
- **Par qui :** celui qui fixe N et qui est jugé sur le taux (l'équipe d'analyse ou l'état-major du SDIS).
- **Comment :** il abaisse N à 2, après coup, pour qu'aucun feu ne tombe sous N.
- **Effet :** le taux tombe vers 0, alors que le dispositif tourne presque tout le temps (105 jours sur 131 en 2026 pour N = 2 en Haute-Garonne).

**Garde-fous :**
- **Règle fixée à l'avance :** N, l'horizon, la date retenue et la définition d'un feu sont versionnés dans le dépôt avant le début de la saison et ne sont plus modifiés.
- **Contrepoids :** le nombre de jours déclenchés par saison (second indicateur) est comparé au budget [à demander].
- **Volume :** le nombre de départs de feu de la saison est affiché à côté du taux.
- **Seuil plancher :** sous [10, à valider] départs de feu dans la saison, le taux du 31 n'est pas lu ; on lit celui de l'Occitanie (règle du groupe, fiche de Maha).
- Seul le contrepoids mesure autre chose que l'indicateur (la charge du dispositif) ; le volume et le seuil plancher disent seulement si le taux est lisible.

**Risque résiduel :**
- **Un jour déclenché sans feu n'est pas forcément une fausse alerte :** le dispositif a pu fonctionner.
- **Le taux et ses garde-fous jugent la prévision de l'indice, pas l'efficacité du dispositif.** Les 37 % de feux hors saison de la Météo des forêts (Occitanie, fiche de Maha) restent invisibles.

**Second indicateur (garde-fou) : nombre de jours déclenchés par saison.**
- **Formule :** nombre de jours dont `niveau_j1` est supérieur ou égal à N, en Haute-Garonne, par saison (et par mois pour le suivi). Unité : jours.
- **Rôle :** contrepoids. Il se dégrade si N est abaissé pour améliorer le taux, et il mesure la charge du dispositif, pas les feux.
- **Horizon :** les comptes diffèrent selon l'horizon (en 2026 pour N = 3 : 35 jours avec `niveau_j1`, 23 avec `niveau_j2`), donc il est fixé à l'avance.
- **Seuil d'alerte :** le nombre de jours renforçables par été [à demander à la direction]. Au-delà : relever N ou cibler.
- **Valeur indicative en Occitanie** (13 départements, départements-jours de niveau supérieur ou égal à N) :

| N | 2024 (sur 1 560) | 2025 (sur 1 560) | 2026 (sur 1 703) |
|---|---|---|---|
| 2 | 403 | 651 | 1 202 |
| 3 | 77 | 177 | 518 |
| 4 | 1 | 7 | 48 |

- **Lecture :** en 2026 pour N = 3, la Haute-Garonne (35 jours) est proche de la moyenne des 13 départements (518 ÷ 13 = 40), l'Aude est loin devant (107).
- **Lignes utilisables :** 371 sur 371 en Haute-Garonne, 4 823 sur 4 823 pour les 13 départements d'Occitanie.
- **Proxy :** aucun, tous les termes ont un champ.

**Pre-mortem.** Dans un an, l'indicateur a échoué : le SDIS a pris une mauvaise décision à cause de lui.

| Rang | Raison d'échec | Probabilité | Gravité | Garde-fou |
|---|---|---|---|---|
| 1 | Trop peu de feux dans le 31 et 3 saisons seulement : le taux vaut 0 % ou 100 % par hasard, et N est fixé sur du bruit. Les saisons diffèrent beaucoup (1 jour de niveau 3 ou plus en 2024, 10 en 2025, 35 en 2026). | élevée (5 feux en 2 ans dans le 31, fiche de Maha) | élevée | Seuil plancher, volume affiché à côté du taux, lecture à l'échelle de l'Occitanie |
| 2 | N abaissé au minimum pour améliorer le taux : le dispositif est déclenché presque tout le temps (N = 2 : 105 jours sur 131 en 2026) et le budget est dépassé. | moyenne | élevée | Le second indicateur : jours déclenchés comparés au budget [à demander] |
| 3 | Jours mal alignés : le niveau du jour D est lu dans la mauvaise émission, ou les 3 fichiers sont lus différemment (séparateur, code `1` au lieu de `01`, `dep_nom` et `nom_dep`). Un feu est rattaché au mauvais jour ou département. | moyenne | moyenne | (pas exigé) Contrôle par échantillon et test de 96 lignes par jour, sans jour manquant (vérifié sur les 3 fichiers) |

**Rôle de chaque indicateur :**

| Indicateur | Rôle | Raison |
|---|---|---|
| Taux de feux déclenchés sur des jours à indice bas | KPI principal | Répond à D2 : à partir de quel niveau déclencher. Lisible seulement à l'échelle de l'Occitanie. |
| Part des jours déclenchés sans départ de feu | KPI secondaire | Explique et prépare le principal : dit combien de jours déclenchés l'ont été pour rien. Demande le croisement avec la BDIFF. |
| Nombre de jours déclenchés par saison | Garde-fou | Contrepoids : se dégrade si N est abaissé pour améliorer le taux. Calculable avec l'archive seule. |
| Nombre de départs de feu de la saison | Garde-fou | Volume et seuil plancher : sous [10, à valider] feux, le taux du 31 n'est pas lu. |
| Moment de la saison (mois) | Contexte | Explique sans guider l'action : en 2025, 9 des 10 jours de niveau 3 ou plus du 31 sont en août. On le note, on ne le pilote pas. |
| Corrélation entre feux et température | Écarté | Si elle double, personne ne fait rien de différent : l'indice contient déjà la température, l'humidité, le vent et les précipitations (PDF de la Météo des forêts). |
| Niveau moyen de l'indice par saison | Écarté | Si la valeur double, personne ne fait rien de différent : la décision porte sur un seuil N, et une moyenne cache les jours de pointe (4 jours de niveau 4 en 2026 dans le 31). |


## Soukaina Goumih

Objectif suivi dans [01_objectif_soukaina-goumih.md](01_objectif_soukaina-goumih.md) (D2, question G4). Fiche proposée pour relecture.

### Fiche : part des départs de feu sous le seuil de renfort

| Rubrique | Contenu |
|---|---|
| 1. Question et objectif | **G4.** Quelle part des feux survient un jour de danger faible ? Pour D2, comparer la couverture des seuils de renfort. Au 30 septembre 2027, viser dans le 31 une réduction d'au moins [x points de pourcentage] par rapport à `N = 3` sur les mêmes jours et feux, sans hausse de la part de jours de renfort sans feu recensé ni dépassement du budget. Fixer la cible avec le SDIS après avoir mesuré la référence locale. |
| 2. Formule : numérateur, dénominateur, unité | **Numérateur** — feux recensés en saison avec un niveau J+1 apparié strictement inférieur à `N`. **Dénominateur** — tous les feux recensés en saison avec un niveau J+1 apparié dans le même périmètre. **Unité** — %. Chaque incendie est compté une fois, même si plusieurs feux partagent un jour et un département. Avec zéro feu apparié, afficher « non calculable ». |
| 3. Paramètres | Seuil de référence `N = 3` et variantes `N = 2` ou `N = 4`. Un jour est classé en renfort simulé si son niveau prévu est supérieur ou égal à `N`. La prévision est le J+1 émis la veille. L'horodatage de première alerte est converti de l'UTC vers `Europe/Paris` avant d'en extraire la date. Fixer ces règles et la fenêtre saisonnière avant la comparaison. |
| 4. Périmètre, période, granularité, fréquence | Haute-Garonne pour D2, Occitanie pour le repère historique (D-004). Saisons communes 2024 et 2025 pour le repère, saison 2027 avec bilan au 30 septembre pour l'objectif. Un feu est apparié à une seule prévision au grain département × jour. Suivi mensuel si le SDIS fournit un relevé d'intervention à jour, sinon bilan après publication des données annuelles. |
| 5. Source et champs | [BDIFF](../docs/sources/fiche-bdiff.md), couches Géorisques 2024 (`FeatureServer/16`) et 2025 (`FeatureServer/13`) : `Departement` et `Date_de_premiere_alerte`. [Archives de la Météo des forêts](../docs/sources/fiche-archives-meteo-des-forets.md), CSV 2024 et 2025 : `num_dep`, `date` d'émission et `niveau_j1`. Joindre sur le code département harmonisé et le jour prévu, soit le jour d'émission + 1. |
| 6. Lignes utilisables | La [section 2 du diagnostic](01_diagnostic_objectifs.md#2-hypothèse-stratégique-binôme-a) utilise **557/557 feux en saison (100 %)** en Occitanie et **4/4 (100 %)** dans le 31. Rapportés aux feux recensés toute l'année, ces effectifs représentent **557/885 (62,9 %)** et **4/5 (80 %)**. Les feux hors saison sont comptés à part (328 en Occitanie) et les échecs de jointure en saison sont à signaler séparément. |
| 7. Proxy et biais | Le jour local de première alerte approxime le jour de départ réel. Une alerte après minuit peut déplacer le feu vers un autre niveau, dans les deux sens. Le seuil simule le déclenchement. Si le SDIS active parfois le renfort sous le seuil, la part estimée de feux hors renfort est **surestimée**. S'il omet des activations au-dessus du seuil, elle est **sous-estimée**. Si des petits feux sont davantage omis sous le seuil, le taux est **sous-estimé**. |
| 8. Décision éclairée | Une part élevée justifie de tester un seuil plus bas et de chiffrer les jours supplémentaires. Si le coût ou la part de jours sans feu recensé dépasse la limite, soumettre le compromis au SDIS et examiner une surveillance ciblée. Si la part est faible et les volumes suffisants, le SDIS peut garder le seuil testé. |
| 9. Propriétaire | Soukaina Goumih porte l'indicateur. Samy Bouaouni vérifie le calcul et Hocine Ait Yakoub relit la qualité des données et le RACER. Répartition proposée pour validation en groupe. |

**Changement de paramètre.** En Occitanie, passer de `N = 3` à `N = 2` ramène le numérateur de **315 à 59** sur les mêmes **557** départs, soit de **57 % à 11 %**. À `N = 2`, seuls les feux des jours prévus au niveau 1 comptent au numérateur. Les sources, dates, clés de jointure, effectifs de référence et règles du garde-fou restent identiques. Les jours de renfort simulé passent de **254 à 1 054** et leur part sans départ recensé de **116/254 (46 %)** à **739/1 054 (70 %)**. Le seuil 2 couvre plus de feux sur ces saisons, mais échoue au garde-fou et demanderait de financer **800 jours-départements** supplémentaires à l'échelle régionale.

**RACER**

- **Relevant** — La part des départs sous le seuil renseigne directement le choix de seuil D2.
- **Accepted** — Faire valider par le SDIS la définition d'un feu recensé, l'usage du J+1 et la cible locale.
- **Credible** — La prévision et la date de première alerte sont définies et traçables, et le taux s'interprète avec le dénominateur et la part appariée.
- **Easy** — Le calcul utilise deux sources publiques, et un suivi en cours de saison dépend des données d'intervention du SDIS.
- **Robust** — Le taux est sensible au seuil, à la date retenue et aux petits effectifs, d'où les garde-fous et le contrôle de jointure.

**Détournement (K4).** L'équipe qui calibre le seuil pourrait l'abaisser pour couvrir beaucoup plus de feux sur le papier. Le taux de feux sous le seuil baisserait mécaniquement, tandis que la charge de renfort pourrait dépasser le budget.

**Garde-fou.** Afficher à côté du KPI la part des jours de renfort simulé sans feu recensé et le volume de jours à financer. Figer les dates et les règles de comptage avant le calcul. Pour le 31, afficher les effectifs et différer l'arbitrage local si le volume est inférieur au plancher à fixer avec le SDIS.

**Risque résiduel.** Une journée de renfort sans feu recensé peut correspondre à un départ évité ou à un feu absent de la BDIFF. Le croisement mesure la couverture théorique de la règle. Les activations réelles et l'effet des patrouilles nécessitent des données du SDIS.

**Second indicateur — part des jours de renfort simulé sans départ recensé.** Diviser le nombre de jours-départements au niveau J+1 supérieur ou égal à `N` sans départ recensé par le nombre total de jours-départements éligibles au même seuil, sur la même saison et le même périmètre, puis multiplier par 100. Sources : archives de la Météo des forêts et BDIFF. Partir des jours-départements météo en saison et y joindre le nombre de départs par jour-département. Si une rupture de couverture est identifiée, compter ces jours à part et les exclure des deux termes pour chaque scénario comparé. Avec zéro jour éligible, afficher « non calculable ». Repère régional à `N = 3` selon le diagnostic : **116/254 (46 %)**.

**Pre-mortem**

| Rang | Raison d'échec | Probabilité | Gravité | Garde-fou |
|---|---|---|---|---|
| 1 | Dans le 31, un feu reclassé change le taux historique de 25 points sur quatre feux en saison. Un seuil est retenu sur un résultat instable. | Élevée | Élevée | Afficher les volumes, fixer un effectif minimal, lire le repère régional et demander les données d'intervention au SDIS. |
| 2 | L'équipe abaisse le seuil après avoir vu les résultats, puis recommande une règle qui mobilise trop souvent les équipes. | Moyenne | Élevée | Figer les règles avant le test, évaluer le taux sans départ recensé et la charge au regard du budget. |
| 3 | Des alertes proches de minuit sont appariées au mauvais jour à cause de l'heure UTC ou du décalage J+1. | Moyenne | Moyenne | Vérifier un échantillon d'alertes près de minuit et de feux aux limites de saison. |

**Rôle de chaque indicateur**

| Indicateur | Rôle | Raison |
|---|---|---|
| Part des départs de feu sous le seuil | KPI principal D2 | Mesure la couverture de la règle de renfort testée. |
| Nombre de jours de renfort simulé | KPI secondaire | Sert à chiffrer la charge et aide à éliminer les seuils incompatibles avec le budget. |
| Part des jours de renfort simulé sans départ recensé | Garde-fou | Rend visible la mobilisation supplémentaire les jours où aucun feu n'est recensé. |
| Nombre de feux appariés et part des feux hors saison | Contexte | Documente la solidité du taux et la limite calendaire de l'analyse. |
| Température maximale seule | Écarté | Sa valeur seule ne permet pas de choisir un seuil de la Météo des forêts pour le dispositif. |

## Jeu d'indicateurs v0 (groupe)

| Indicateur | Rôle | Objectif suivi | Garde-fou associé | Raison (si écarté) |
|---|---|---|---|---|
| | KPI principal | | | |
| | KPI secondaire | | | |
| | Garde-fou | | | |
| | Contexte | | | |
| | Écarté | | | |

Test pour écarter un indicateur : si sa valeur double, qui fait quoi différemment ? Si personne, il est écarté.

Taille du jeu : [nombre : à fixer] indicateurs.
