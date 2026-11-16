# Analyse de la commande - Samy Bouaouni

## 1. Les questions

Quatre questions dont la réponse aiderait la direction à trancher.

> [!test] Test
> Le test : si la réponse est X, la direction fait A ; si elle est Y, elle fait B. Si A et B sont identiques, ce n'est pas une question analytique pertinente.

1. Où se concentrent les départs de feu en Haute-Garonne ? S'ils sont concentrés sur quelques zones, la direction y met ses moyens ; s'ils sont répartis, elle garde un dispositif mobile sur tout le département.
2. À partir de quel niveau de l'indice les départs de feu deviennent-ils nettement plus fréquents ? Si c'est à un niveau précis, la direction y place son seuil ; si la fréquence ne change pas, elle cherche un autre critère.
3. Le lien entre l'indice et les départs de feu est-il le même en Haute-Garonne, dans les autres départements d'Occitanie et en France ? Si oui, la direction peut reprendre un seuil commun ; sinon, elle fixe un seuil propre à la Haute-Garonne.
4. Combien de jours par été dépassent le seuil, par rapport au nombre de jours que le budget permet de renforcer ? Si le nombre de jours dépasse ce que le budget permet, la direction relève le seuil ou cible certaines zones ; sinon, elle garde un seuil bas.

## 2. Les termes inconnus

Les mots de la commande que vous ne savez pas définir précisément, ou qui peuvent se comprendre de plusieurs façons.

| Terme | Ce que je crois qu'il veut dire | Ce qu'il faudrait vérifier |
|---|---|---|
| Météo des forêts | Un indice quotidien du danger de feu lié à la météo | Qui le calcule et à quelle échelle (commune, zone) |
| Niveau d'indice / « indice élevé » | Les classes de l'indice, de faible à très élevé | Les bornes de chaque classe |
| Seuil actuel | Le niveau qui déclenche le dispositif renforcé | Sa valeur exacte et qui l'a fixé |
| Dispositif renforcé | Patrouilles, guet, moyens en plus | Ce qu'il contient et ce qu'il coûte par jour |
| Départ de feu | Début d'incendie signalé, même éteint vite | À partir de quelle surface on le compte |
| Région | L'Occitanie | Quels départements exactement |

## 3. Les besoins

La décision à éclairer, en une phrase : où concentrer les moyens du SDIS et à partir de quel niveau de l'indice déclencher le dispositif renforcé en 2027, avec un budget limité.

Ce qui manque dans la commande pour y répondre (une information, une précision, une hypothèse à confirmer) :
- La valeur du seuil actuel.
- La définition d'un « feu » (surface minimale).
- Le budget : combien de jours ou de zones peut-on renforcer ?
- Le critère de réussite : moins de feux ou moins de surface brûlée ?
- La période de référence : sur combien d'années et sur quelle saison juger l'indice ?

## 4. Les données

Pour chaque question, la donnée qu'il vous faudrait idéalement pour répondre.

| Question | Donnée idéale | Grain (une ligne = ?) | Période | Fraîcheur | Emprise géographique |
|---|---|---|---|---|---|
| 1 | Les départs de feu avec leur lieu | Un départ de feu | 10 dernières années | Annuelle, été 2026 inclus | Haute-Garonne |
| 2 | L'indice de chaque jour et les départs de feu du même jour | Un jour × une zone | 10 dernières années | Quotidienne | Haute-Garonne |
| 3 | L'indice de chaque jour et les départs de feu du même jour, pour chaque département | Un jour × un département | 10 dernières années | Annuelle | Haute-Garonne, Occitanie, France |
| 4 | L'indice de chaque jour et le budget du dispositif | Un jour × une zone (le budget est une donnée annuelle à part) | 10 dernières années | Quotidienne pour l'indice, annuelle pour le budget | Haute-Garonne |