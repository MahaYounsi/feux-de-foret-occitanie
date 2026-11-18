# Journal des décisions — Occitanie

Une entrée numérotée par décision. On ne supprime jamais une entrée : une décision remplacée est marquée « remplacée par D-xxx ». Les questions G1 à G9 sont celles de la [matrice](matrice.md).

Statuts : **proposée** (en attente de validation par le groupe) · **validée** · **remplacée**.

---

## D-001 — Questions retenues par le groupe

- **Question :** quelles questions le groupe traite-t-il ?
- **Manque :** 21 questions dans les quatre analyses, avec de nombreux doublons.
- **Décision :** fusion en 9 questions (G1 à G9), avec la trace des questions d'origine dans la matrice. Priorité proposée : G3, G5, G6 (seuil) puis G1, G2 (moyens) puis G4, G7, G8, G9.
- **Raison :** les quatre analyses convergent sur les deux décisions de la direction (où placer les moyens, quel seuil) : G1, G5 et G6 ont été posées par les quatre membres, G3 par trois. La priorité suit la décision la plus précise de la commande (le seuil).
- **Ce qu'elle coûte :** G7, G8 et G9, posées par un seul membre, risquent de n'être traitées qu'en partie.
- **Date :** 2026-11-18
- **Auteurs :** Maha Younsi, à partir des analyses de Maha Younsi, Hocine Ait Yakoub, Samy Bouaouni et Soukaina Goumih
- **Statut :** proposée

## D-002 — G1 : localiser les départs de feu

- **Question :** G1 — où se concentrent les départs de feu dans le 31 ?
- **Manque :** historique des départs à la commune sur dix saisons ; secteurs du SDIS 31. La BDIFF ouverte ne couvre que 2024-2025 et ne compte que 5 incendies dans le 31.
- **Décision :** **collecter** et **approximer** en attendant :
  - collecter la BDIFF sur les années antérieures à 2024 (export du portail ou couches plus anciennes) ;
  - collecter auprès du SDIS 31 les secteurs d'intervention et, si possible, les interventions pour feux de végétation ;
  - en attendant, approximer avec EFFIS 2000-2026 (surfaces brûlées par commune) et la BDIFF 2024-2025.
- **Raison :** la BDIFF a le bon grain (`Code_INSEE`) mais pas assez d'années ; EFFIS est la seule source ouverte avec un historique long et localisé ; les secteurs n'existent que chez le SDIS.
- **Ce qu'elle coûte :** du temps de collecte, et une dépendance au portail BDIFF et à la réponse du SDIS 31. EFFIS ne voit pas les petits feux et compte des surfaces, pas des départs. Si rien n'est obtenu, la question se limite à 2024-2025 (Hocine) ou se reformule à l'échelle du département (Samy).
- **Divergence :** les quatre membres proposent de collecter, mais pas la même chose : l'historique BDIFF (Hocine, Samy), les secteurs et départs auprès du SDIS (Soukaina, Samy, Maha). Maha ajoute l'approximation par EFFIS. La décision regroupe les trois pistes.
- **Date :** 2026-11-18
- **Auteurs :** Maha Younsi, Hocine Ait Yakoub, Samy Bouaouni, Soukaina Goumih
- **Statut :** proposée

## D-003 — G2 : heure des départs de feu

- **Question :** G2 — à quelles heures partent les feux ?
- **Manque :** l'heure réelle du départ.
- **Décision :** **approximer** par l'heure de première alerte de la BDIFF, convertie de UTC en heure locale. EFFIS sert seulement pour les mois.
- **Raison :** c'est la seule heure disponible ; celle d'EFFIS n'est pas exploitable (26 % des dates à 00:00).
- **Ce qu'elle coûte :** l'alerte arrive après le départ, avec un délai inconnu ; très peu de feux dans le 31.
- **Date :** 2026-11-18
- **Auteurs :** Maha Younsi
- **Statut :** proposée

## D-004 — G3 : part des jours avec feu par niveau

- **Question :** G3 — pour chaque niveau, quelle part des jours a connu au moins un départ de feu ?
- **Manque :** assez de feux et de saisons dans le 31 : 5 incendies BDIFF sur 2024-2025 ; 1 seul jour au niveau 3 et aucun au niveau 4 en 2024.
- **Décision :** **renoncer** au grain « Haute-Garonne seule » et **reformuler** : croiser la BDIFF et la Météo des forêts sur les saisons 2024 et 2025, à l'échelle de l'Occitanie (885 incendies, 13 départements), puis regarder si le 31 s'écarte de la région. **Approximer** les saisons avant 2024 avec le FWI de Copernicus, à tester.
- **Raison :** un taux calculé sur 5 feux n'a pas de sens ; la région donne un échantillon exploitable. Le FWI suit de près les niveaux dans le 31 à l'été 2025 (valeur moyenne 4,8 au niveau 1, 15,5 au niveau 2, 31,5 au niveau 3).
- **Ce qu'elle coûte :** le résultat décrit l'Occitanie, pas exactement le 31 ; les feux hors saison sont exclus ; le FWI ne reprend pas la sécheresse de la végétation ni l'occupation des sols, que les prévisionnistes ajoutent, et demande un traitement en Python (NetCDF, jointure spatiale).
- **Divergence :** Hocine propose de renoncer en gardant le 31 sur 2024-2025 ; Samy propose de collecter les feux et de présenter le résultat comme indicatif ; Maha propose l'échelle de l'Occitanie. Le retour au fichier (5 incendies dans le 31) fait pencher vers l'Occitanie. L'approximation par le FWI rejoint la « piste à discuter » de Hocine. **À valider en groupe.**
- **Date :** 2026-11-18
- **Auteurs :** Maha Younsi, Hocine Ait Yakoub, Samy Bouaouni
- **Statut :** proposée

## D-005 — G4 : feux les jours de danger faible et hors saison

- **Question :** G4 — quelle part des feux part les jours de danger faible ?
- **Manque :** l'heure réelle du départ, les secteurs, et un niveau de danger hors de la saison de la Météo des forêts, alors que 85 % des surfaces brûlées d'Occitanie le sont hors juin-septembre (EFFIS).
- **Décision :** **approximer** pendant la saison : communes et heures d'alerte BDIFF 2024-2025, croisées avec le niveau J+1. **Renoncer** hors saison en reformulant : traiter à part les feux hors saison et les présenter à la direction comme un résultat.
- **Raison :** c'est ce que les fichiers permettent d'étudier en premier ; on ne peut pas juger un indice les jours où il n'est pas publié, mais ces feux expliquent peut-être les feux « des jours où l'indice était au plus bas » cités dans la commande.
- **Ce qu'elle coûte :** l'heure d'alerte peut être décalée par rapport au départ ; deux saisons seulement ; la commune ne représente pas toujours un secteur du SDIS ; les feux d'hiver sortent de l'analyse du seuil.
- **Date :** 2026-11-18
- **Auteurs :** Soukaina Goumih, Maha Younsi
- **Statut :** proposée

## D-006 — G5 : coûts, budget et seuil actuel

- **Question :** G5 — quel seuil est compatible avec le budget ?
- **Manque :** seuil actuel, jours d'activation, coût d'une journée de renfort, budget (nombre de jours ou de zones renforçables par été).
- **Décision :** **collecter** auprès de la direction du SDIS 31.
- **Raison :** aucune source publique ne contient ces informations ; les jours au-dessus de chaque seuil sont déjà comptés dans la Météo des forêts.
- **Ce qu'elle coûte :** dépendance à la réponse de la direction. En attendant, on présente pour chaque seuil le nombre de jours, les fausses alertes et les feux manqués, sans les chiffrer.
- **Date :** 2026-11-18
- **Auteurs :** Maha Younsi, Hocine Ait Yakoub, Samy Bouaouni, Soukaina Goumih (décision identique dans les quatre analyses)
- **Statut :** proposée

## D-007 — G6 : comparaison nationale

- **Question :** G6 — le lien niveau-feux est-il le même dans le 31, en Occitanie et en France ?
- **Manque :** les feux des départements hors Occitanie (extrait BDIFF filtré sur la région).
- **Décision :** **collecter** les couches BDIFF complètes 2024 et 2025 (1 367 et 2 539 incendies) et vérifier la couverture de chaque département avant de comparer ; en attendant, comparaison limitée à l'Occitanie et à la métropole.
- **Raison :** la Météo des forêts couvre déjà les 96 départements métropolitains ; il ne manque que les feux, et les couches complètes existent.
- **Ce qu'elle coûte :** un volume plus important à traiter et des contrôles supplémentaires ; pour l'IFM, une jointure spatiale (pas de code département).
- **Date :** 2026-11-18
- **Auteurs :** Maha Younsi, Hocine Ait Yakoub, Samy Bouaouni, Soukaina Goumih (décision identique dans les quatre analyses)
- **Statut :** proposée

## D-008 — G7 : surface boisée

- **Question :** G7 — le 31 est-il plus touché, rapporté à sa surface boisée ?
- **Manque :** la surface boisée par département.
- **Décision :** **collecter** : explorer la BD Forêt V2 (IGN) et en faire une fiche source.
- **Raison :** source présente dans la liste du défi, absente de l'inventaire.
- **Ce qu'elle coûte :** une source de plus à explorer ; membre à désigner.
- **Date :** 2026-11-18
- **Auteurs :** Maha Younsi
- **Statut :** proposée

## D-009 — G8 : causes des feux

- **Question :** G8 — quelles sont les causes principales des départs de feu ?
- **Manque :** vérification faite le 18/11 : la colonne `Nature` de la BDIFF est remplie pour 71 % (2024) et 84 % (2025) des incendies d'Occitanie, mais vide pour les 5 incendies du 31.
- **Décision :** **renoncer** au grain du 31 et **reformuler** à l'échelle de l'Occitanie (répartition des causes sur 2024-2025) ; demander au SDIS 31 s'il dispose des causes de ses feux.
- **Raison :** aucune cause n'est renseignée pour le 31 dans la source.
- **Ce qu'elle coûte :** les causes régionales, dominées par les départements méditerranéens (Aude, Hérault), ne décrivent peut-être pas le 31.
- **Date :** 2026-11-18
- **Auteurs :** Maha Younsi
- **Statut :** proposée

## D-010 — G9 : la saison 2026

- **Question :** G9 — l'été 2026 a-t-il été exceptionnel ?
- **Manque :** les feux 2026 recensés au sol (BDIFF 2026 non diffusée) ; présence de 2026 dans Copernicus non vérifiée.
- **Décision :** **vérifier** d'abord la présence de 2026 dans Copernicus (Hocine, qui a un compte) ; **approximer** ensuite avec EFFIS 2019-2026 et les niveaux de la Météo des forêts 2024-2026.
- **Raison :** EFFIS est la seule source qui couvre déjà 2026.
- **Ce qu'elle coûte :** EFFIS sous-estime les petits feux ; un danger élevé n'est pas forcément synonyme de plus de feux.
- **Date :** 2026-11-18
- **Auteurs :** Maha Younsi
- **Statut :** proposée

## D-011 — Période commune pour les croisements

- **Question :** sur quelle période croiser les feux et les niveaux de danger ?
- **Manque :** la BDIFF ouverte couvre 2024-2025, la Météo des forêts 2024-2026.
- **Décision :** commencer les croisements sur les **saisons 2024 et 2025**, aux dates où les deux sources existent.
- **Raison :** seules saisons communes ; proposée dans l'[inventaire](../sources/inventaire.md) et reprise dans les quatre confrontations.
- **Ce qu'elle coûte :** deux saisons seulement, avec des niveaux élevés rares.
- **Date :** 2026-11-18
- **Auteurs :** Soukaina Goumih (inventaire), Maha Younsi, Hocine Ait Yakoub, Samy Bouaouni
- **Statut :** proposée

## D-012 — Divergence G1 × IFM Copernicus

- **Question :** G1 — l'IFM Copernicus aide-t-il à localiser les départs de feu ?
- **Manque :** degrés divergents pour la même cellule : « absent » (Maha, Soukaina), « partiel » (Hocine, « donnée indirecte »).
- **Décision :** retour au fichier : les variables sont `fwinx`, `latitude`, `longitude` et `valid_time`, sans aucun feu ni surface. Degré retenu : **absent**. L'idée de Hocine devient une question nouvelle dans la matrice : dans quelles parties du 31 le danger météo est-il le plus souvent élevé ?
- **Raison :** la question porte sur les départs de feu ; un danger météo n'est pas un départ.
- **Ce qu'elle coûte :** rien pour G1 ; la question nouvelle demande la jointure spatiale des 13 points de grille du 31.
- **Date :** 2026-11-18
- **Auteurs :** Maha Younsi, Hocine Ait Yakoub, Soukaina Goumih
- **Statut :** proposée

---

## Décisions en attente (à trancher en groupe)

| Sujet | Options | Ce qui permettra de trancher |
|---|---|---|
| Prévision retenue pour un jour donné | J+1 (la plus récente) ou J+2 (connue plus tôt) | Le délai dont le SDIS 31 a besoin pour déclencher le dispositif (à demander) |
| « Danger élevé » | Niveau 3 seul ou niveaux 3 et 4 | Ce que les chefs de centre entendent par « danger élevé » (à demander) |
| Fiche de référence Météo des forêts | Fiche de Hocine ou de Samy | Fusion en une fiche, en gardant les contributions des deux |
| Territoire national | France métropolitaine ou avec l'outre-mer | Couverture de la Météo des forêts : métropole seulement |
| Unité des surfaces BDIFF | Hectares ou mètres carrés | Documentation de l'export BDIFF (valeurs comme 40 000 pour un feu du 31) |
| Écart BDIFF / EFFIS dans le 31 | 5 incendies BDIFF contre 12 surfaces EFFIS sur 2024-2025 | Comparer feu par feu (date, commune) pour comprendre ce que chaque source retient |
| Critère de réussite du dispositif | Moins de feux ou moins de surface brûlée (question de Samy) | À demander à la direction |
