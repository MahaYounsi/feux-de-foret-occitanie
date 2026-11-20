# Objectif de Samy Bouaouni

Projet feux-de-foret-occitanie · Auteur : Samy Bouaouni · Statut : brouillon, à présenter au groupe

## Question de départ

**[G à confirmer]** (matrice du groupe, issue de ma Q2) : à partir de quel niveau de la Météo des forêts les départs de feu deviennent-ils nettement plus fréquents en Haute-Garonne ?

## Décision que la réponse permet de prendre

**D2 [numéro à confirmer] :** à partir de quel niveau de la Météo des forêts le SDIS 31 déclenche le dispositif renforcé (patrouilles, guet) en 2027, avec un budget qui ne permet pas de renforcer tout l'été.

Si les feux sont plus fréquents à partir d'un niveau précis, le SDIS place son seuil à ce niveau. S'ils partent aussi souvent les jours d'indice bas, l'indice ne sert pas de critère de déclenchement : il faut en chercher un autre.

## Trois formulations (exercice 2)

1. **Une action, qui n'est pas un objectif :** croiser les départs de feu du 31 avec le niveau de la Météo des forêts du jour.
2. **Un objectif, sans être SMART :** déclencher le dispositif renforcé les jours où les feux sont les plus probables.
3. **Un objectif SMART (un résultat, une échéance, une condition) :** d'ici le 30 septembre 2027, faire passer de [a %] à [b %] la part des départs de feu du 31 survenus un jour de niveau inférieur à N pendant la saison de l'indice (environ du 3 juin au 30 septembre). N est fixé avant le début de la saison. Condition : le nombre de jours déclenchés (niveau ≥ N) ne dépasse pas [budget] jours.

### Le même objectif, critère par critère

- **Spécifique :**
  - départs de feu du 31 pendant la saison de l'indice 2027 ;
  - seuil N choisi avant la saison, à partir des saisons passées.
- **Mesurable :**
  - la part passe de [a %] à [b %] ;
  - niveau du jour : `niveau_j1` de l'émission de la veille (archive Météo des forêts, champs `date`, `num_dep`) ;
  - feu : `Date_de_premiere_alerte` et `Departement` de la BDIFF, ou interventions du SDIS 31.
- **Atteignable :** [b %] est fixée avec la direction une fois [a %] connue, pas avant.
- **Réaliste :**
  - la condition sur le budget empêche de gagner en déclenchant tous les jours ;
  - N est fixé à l'avance, il ne peut pas être ajusté après coup.
- **Temporel :**
  - le 30 septembre 2027 ;
  - la commande parle du « printemps et de l'été prochains », mais l'indice n'existe que de juin à septembre : les feux de mars à mai ne peuvent pas être rattachés à un niveau.

## Situation de référence

**[a %] pour le 31 : à mesurer.** Le seul croisement possible aujourd'hui porte sur les 5 départs de feu du 31 recensés en 2024-2025 (dates reprises du fichier de Maha, BDIFF, non revérifiées par moi), croisés avec l'archive :

| Date du feu | Commune | Niveau du jour |
|---|---|---|
| 3 février 2024 | Signac | pas de niveau (hors saison de l'indice) |
| 13 juin 2025 | Aspet | 1 |
| 5 août 2025 | Lodes | 3 |
| 13 août 2025 | Melles | 3 |
| 24 août 2025 | Melles | 1 |

Avec N = 3, 2 feux sur les 4 survenus en saison sont partis un jour de niveau inférieur à 3 (50 %). C'est trop peu de feux pour servir de référence.

Pour mesurer [a %], il faut :

- les **données d'intervention du SDIS 31** (feux de végétation), à demander (D-002) ;
- ou la **BDIFF 2026**, quand elle sera publiée.

**Valeur indicative, nombre de jours déclenchés par saison selon N** (archive, jours calendaires de la saison) :

| Niveau N | Haute-Garonne 2024 / 2025 / 2026 | Occitanie (départements-jours) 2024 / 2025 / 2026 |
|---|---|---|
| ≥ 3 | 1 / 10 / 35 jours | 77 / 177 / 518 |

Ces chiffres disent combien de jours le seuil déclencherait, pas si les feux y sont plus fréquents. Les saisons 2024 (120 jours), 2025 (120 jours) et 2026 (131 jours) sont les seules couvertes.

## Test de cohérence

Comment atteindre l'objectif sans faire avancer la stratégie (« lutter au mieux contre les départs de feu ») ?

1. **Abaisser N au minimum.** Déclencher tous les jours capte presque tous les feux. Parade : la condition sur le nombre de jours déclenchés (budget).
2. **Choisir N après coup.** On prend le N qui donne la meilleure part sur la saison écoulée. Parade : N est écrit dans le dépôt avant la saison et n'est plus modifié.
3. **Bien viser, sans mieux lutter.** Les feux partent les jours déclenchés, mais le dispositif renforcé n'y change rien. L'objectif mesure la justesse du seuil, pas l'efficacité de la lutte. Un jour déclenché sans feu n'est pas une fausse alerte : le dispositif peut avoir dissuadé. C'est le risque résiduel de la fiche d'indicateur.
4. **Profiter d'une saison calme.** Avec 3 ou 4 feux, la part peut changer fortement par hasard. Parade : seuil plancher de [10, à valider] feux, sinon lecture à l'échelle de l'Occitanie (D-004).