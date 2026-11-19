# Objectif de Soukaina Goumih

Projet feux-de-foret-occitanie · Auteur : Soukaina Goumih · Statut : brouillon, à présenter au groupe

## Question de départ

**G4.** Quelle part des départs de feu survient les jours de danger faible, et ces feux se concentrent-ils dans certains secteurs ou à certaines heures ? Pour la décision D2, je mesure la part des feux recensés les jours où le niveau prévu est inférieur au seuil de renfort testé. Le niveau 1 correspond au danger faible. Sous le seuil 3, on compte les niveaux 1 et 2.

## Décision que la réponse permet de prendre

**D2.** À partir de quel niveau de la Météo des forêts le SDIS 31 doit-il déclencher le dispositif renforcé pour la saison 2027 ?

Si un seuil plus bas permet de couvrir davantage de feux, le SDIS peut estimer combien de jours de renfort cela ajoute. Si ces jours dépassent le budget ou si la part de jours de renfort sans feu recensé augmente trop, il peut examiner une surveillance ciblée sur les créneaux ou les secteurs où les feux de niveau faible se concentrent.

## Trois formulations (exercice 2)

1. **Une action, qui n'est pas un objectif** — Comparer les seuils 2, 3 et 4 en croisant les prévisions J+1 et les départs de feu recensés.
2. **Un objectif, sans être SMART** — Réduire la part des départs de feu survenus les jours où la règle de déclenchement ne prévoit pas de renfort.
3. **Un objectif SMART (un résultat, une échéance, une condition)** — D'ici le **30 septembre 2027**, viser une baisse d'au moins **[x points de pourcentage]** de la part des départs de feu recensés en Haute-Garonne qui auraient été hors renfort sur les jours de la saison couverts par la Météo des forêts. Comparer la règle proposée au seuil 3 sur les mêmes jours et les mêmes feux. La règle proposée doit tenir dans le budget saisonnier et la part de ses jours de renfort sans départ recensé ne doit pas dépasser celle du seuil 3.

### Le même objectif, critère par critère

- **Spécifique** — Suivre les départs de feu en Haute-Garonne pendant la période couverte par les bulletins J+1 de la saison 2027. Un départ compte hors renfort simulé si le niveau prévu ce jour-là est inférieur au seuil testé.
- **Mesurable** — Diviser le nombre de départs recensés sous le seuil par le nombre total de départs recensés avec une prévision J+1 appariée. Joindre la BDIFF (`Departement`, `Date_de_premiere_alerte` en heure locale) et la Météo des forêts (`num_dep`, `date` du bulletin de la veille, `niveau_j1`).
- **Atteignable** — Fixer [x] avec le SDIS après avoir mesuré la référence locale sur un effectif suffisant et comparé les scénarios sur l'historique.
- **Réaliste** — Comparer le coût estimé au budget et suivre la part des jours de renfort sans départ recensé. Si aucun seuil testé ne satisfait les deux conditions, présenter le compromis à la direction.
- **Temporel** — Appliquer les mêmes règles aux scénarios sur les jours couverts jusqu'au 30 septembre 2027. Les données d'intervention du SDIS permettent un suivi pendant la saison. Avec la seule BDIFF, le bilan devra attendre la publication annuelle.

## Situation de référence

- **Occitanie, saisons communes 2024 et 2025.** Avec `N = 3`, **315 feux sur 557 (57 %)** sont partis un jour prévu au niveau 1 ou 2. Parmi les **557 feux en saison**, **59 (11 %)** sont partis au niveau 1. Pour le même seuil, **116 jours-départements sur 254 (46 %)** n'ont enregistré aucun départ. Sources et méthode dans le [diagnostic du binôme A, sections 2 et 4](01_diagnostic_objectifs.md#2-hypothèse-stratégique-binôme-a).
- **Haute-Garonne.** Les données disponibles donnent **2 feux sous le seuil 3 sur 4 en saison** en 2024 et 2025. La référence opérationnelle locale est **à mesurer** avec les données d'intervention. Le seuil effectivement appliqué et l'enveloppe de renfort sont **à demander** au SDIS (D-006).

## Test de cohérence

Comment améliorer l'indicateur sans mieux préparer le renfort ?

1. **Abaisser le seuil au prix d'une forte mobilisation.** En Occitanie, passer de 3 à 2 fait baisser la part des feux sous le seuil de **57 % à 11 %**, mais le renfort simulé passe de **254 à 1 054 jours-départements** et la part de ces jours sans feu recensé monte de **46 % à 70 %**. Parade — suivre ces deux valeurs et chiffrer les jours de renfort avant de proposer un seuil.
2. **Choisir les dates ou la prévision après avoir vu les chiffres.** Une autre fenêtre de saison ou le passage de J+1 à J+2 peut modifier artificiellement le résultat. Parade — fixer d'avance la période, le périmètre, la date locale de première alerte et la règle J+1.
3. **Conclure sur trop peu de feux.** Dans le 31, un seul feu reclassé sur les quatre recensés en saison change le taux historique de 25 points. Parade — afficher les effectifs, fixer un minimum de feux pour interpréter la valeur locale et utiliser le repère régional pour éclairer la discussion.
