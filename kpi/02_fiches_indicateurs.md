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

<!-- Fiche de Samy Bouaouni -->

## Soukaina Goumih

<!-- Fiche de Soukaina Goumih -->

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
