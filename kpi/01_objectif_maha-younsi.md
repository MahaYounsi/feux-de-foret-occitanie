# Objectif de Maha Younsi

Projet feux-de-foret-occitanie · Auteur : Maha Younsi · Statut : brouillon, à présenter au groupe

## Question de départ

**G1** (matrice du groupe, issue de ma Q1) : dans quelles communes ou quels secteurs de la Haute-Garonne les départs de feu se concentrent-ils, et se répètent-ils d'une saison à l'autre ?

## Décision que la réponse permet de prendre

**D1 :** sur quels secteurs du 31 placer en priorité les patrouilles, le guet et les moyens financiers au printemps et à l'été 2027, au lieu de les répartir sur tout le département.

Si les départs de feu se répètent dans les mêmes communes, le SDIS peut désigner à l'avance des secteurs prioritaires. S'ils changent de place chaque saison, une liste fixe de secteurs ne sert à rien : il faut des moyens mobiles.

## Trois formulations (exercice 2)

1. **Une action, qui n'est pas un objectif :** cartographier les départs de feu du 31 par commune.
2. **Un objectif, sans être SMART :** concentrer les moyens de surveillance sur les secteurs où les feux se répètent.
3. **Un objectif SMART (un résultat, une échéance, une condition) :** d'ici le 30 septembre 2027, faire passer de [a %] à [b %] la part des départs de feu du 31 survenus entre le 1er mars et le 30 septembre 2027 dans des secteurs prioritaires. Ces secteurs sont désignés avant le 1er mars 2027 et ne dépassent pas [x %] des communes du département. Condition : la surface médiane parcourue par les feux partis hors de ces secteurs n'augmente pas.

### Le même objectif, critère par critère

- **Spécifique :**
  - départs de feu du 31 entre le 1er mars et le 30 septembre 2027 ;
  - secteurs prioritaires désignés avant la saison, à partir des saisons passées.
- **Mesurable :**
  - la part passe de [a %] à [b %] ;
  - commune du feu : `Code_INSEE` de la BDIFF, ou données d'intervention du SDIS 31 ;
  - surface parcourue : `Surface_parcourue` de la BDIFF, renseignée pour les 885 feux d'Occitanie en 2024-2025 ;
  - le champ `SurfaceFeuArriveeSecour` (surface à l'arrivée des secours) aurait mieux mesuré la rapidité d'intervention, mais il est vide pour les 885 feux.
- **Atteignable :** [b %] est fixée avec la direction une fois [a %] connue, pas avant.
- **Réaliste :**
  - le plafond de [x %] des communes empêche de gagner en déclarant tout le département prioritaire ;
  - la condition sur les feux hors secteurs empêche d'abandonner le reste du territoire.
- **Temporel :**
  - le 30 septembre 2027 ;
  - la période du 1er mars au 30 septembre reprend « le printemps et l'été prochains » de la commande.

## Situation de référence

**[a %] pour le 31 : à mesurer.** La BDIFF ne compte que 5 départs de feu dans le 31 en 2024-2025 :

| Année | Commune | Date d'alerte |
|---|---|---|
| 2024 | Signac | 3 février 2024 |
| 2025 | Aspet | 13 juin 2025 |
| 2025 | Lodes | 5 août 2025 |
| 2025 | Melles | 13 août 2025 |
| 2025 | Melles | 24 août 2025 |

Aucun feu de 2025 n'est parti dans la commune touchée en 2024, soit 0 sur 4. C'est trop peu de feux pour servir de référence.

Pour mesurer [a %], il faut :

- les **données d'intervention du SDIS 31** (feux de végétation par commune), à demander (D-002) ;
- ou la **BDIFF 2026**, quand elle sera publiée.

Les **secteurs utilisés par le SDIS 31** sont aussi à demander : un secteur prioritaire peut regrouper plusieurs communes. [x %] et [b %] sont à fixer avec la direction.

**Valeur indicative, à l'échelle de l'Occitanie :**

- règle simple : un secteur prioritaire est une commune touchée la saison précédente ;
- **43 % des départs de feu de 2025** (202 sur 472) sont partis dans l'une des 284 communes touchées en 2024 ;
- calcul sur toute l'année 2025, BDIFF, couches Géorisques.

Ce chiffre montre qu'une partie des feux se répète au même endroit. Ce n'est pas la référence du 31.

## Test de cohérence

Comment atteindre l'objectif sans faire avancer la stratégie (« lutter au mieux contre les départs de feu ») ?

1. **Déclarer presque tout le département prioritaire.** La part atteint 100 % sans que les moyens soient concentrés. Parade : le plafond de [x %] des communes, inscrit dans l'objectif.
2. **Délaisser le reste du territoire.** Les feux partis hors des secteurs prioritaires sont atteints plus tard et brûlent davantage, mais la part ne le voit pas. Parade : la condition sur la surface médiane parcourue hors secteurs.
3. **Bien viser, sans mieux lutter.** Les feux partent bien dans les secteurs prioritaires, mais la présence des moyens n'y change rien. L'objectif mesure la justesse du ciblage, pas l'efficacité de la lutte. C'est le risque résiduel de la fiche d'indicateur (S2).
4. **Profiter d'une saison calme.** Avec 3 ou 4 feux dans la saison, la part peut passer de 0 % à 100 % par hasard. Il faudra fixer un nombre minimal de feux sous lequel l'objectif n'est pas évalué, ou juger à l'échelle de l'Occitanie (D-004).
