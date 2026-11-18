# Glossaire — Occitanie

Dernière mise à jour : 2026-11-18

> Version 0.2 : ajouts issus des quatre confrontations questions × sources ([matrice](matrice/matrice.md), [journal des décisions](matrice/journal-des-decisions.md)). Version 0.1 : version 0 complétée avec les fiches sources (BDIFF, Météo des forêts, EFFIS, IFM Copernicus). Commanditaire : Direction du SDIS 31 (Haute-Garonne), voir [commande.md](commande.md).
> Les définitions marquées « à vérifier » doivent être confirmées par la documentation du producteur avant validation. Toute modification passe par un ticket et une pull request relue par la cheffe de projet. On ne supprime jamais un terme : on le marque « obsolète » avec la raison et la date.

---

## Cause d'un feu

- **Définition :** l'origine présumée d'un incendie, regroupée en grandes familles (par exemple : naturelle, accidentelle, involontaire liée à une activité humaine, malveillance, inconnue).
- **Sources et colonnes :** BDIFF, colonne `Nature` (« Nature du feu »), avec 5 catégories constatées : Malveillance, Involontaire (travaux), Involontaire (particulier), Accidentelle, Naturelle ; la colonne `Connaissance` (niveau de connaissance de la cause) est toujours vide dans l'extrait. Prométhée pour les départements méditerranéens. EFFIS ne donne pas de cause.
- **Divergences :** la cause n'est pas toujours renseignée : `Nature` est vide pour 29 % des incendies d'Occitanie en 2024 et 16 % en 2025, et pour les 5 incendies de la Haute-Garonne. Les familles de causes et leur niveau de détail peuvent différer entre BDIFF et Prométhée. La cause est souvent présumée, rarement établie.
- **Règle retenue :** étudier les causes à l'échelle de l'Occitanie, pas du 31 seul ([D-009](matrice/journal-des-decisions.md#d-009--g8--causes-des-feux)) ; une cause vide est comptée comme « non renseignée », jamais comme une catégorie à part entière.
- **Unité ou granularité :** un feu.
- **Exemple :** en Occitanie en 2025, 157 incendies BDIFF classés « Malveillance » sur 472.
- **Statut :** validé (catégories constatées dans la BDIFF) ; correspondance avec Prométhée à vérifier.
- **Origine de la définition :** BDIFF (couches Géorisques 2024 et 2025, colonne `Nature`) ; description de la couche (causes naturelles ou humaines : intentionnelles, involontaires, liées aux infrastructures).
- **Ajouté par :** Maha Younsi (à partir de la consigne et des sources), 2026-11-16

## Chef de centre

- **Définition :** l'officier ou le sous-officier qui dirige un centre d'incendie et de secours (une caserne) du SDIS. C'est lui ou elle qui constate sur le terrain si l'indice de danger correspond aux feux réellement observés.
- **Sources et colonnes :** commande de la direction (pas de colonne dans les sources de données).
- **Divergences :** dans la commande, les chefs de centre n'ont pas le même ressenti sur l'indice : certains voient trop d'alertes sans feu, d'autres des feux les jours de danger faible. Leur avis est un témoignage, pas une mesure.
- **Règle retenue :** sans objet (terme de contexte).
- **Unité ou granularité :** un centre d'incendie et de secours.
- **Exemple :** sans objet.
- **Statut :** proposé
- **Origine de la définition :** commande de la direction ; organisation des SDIS à confirmer.
- **Ajouté par :** Maha Younsi (analyse individuelle), 2026-11-16

## Commune

- **Définition :** la plus petite unité administrative française. Elle sert à localiser l'endroit où un feu a démarré.
- **Sources et colonnes :** BDIFF (code INSEE de la commune, voir la [fiche BDIFF](sources/fiche-bdiff.md)) ; EFFIS (nom de la commune en texte, sans code INSEE) ; référentiels géographiques INSEE / IGN.
- **Divergences :** le code INSEE (identifiant officiel) ne correspond pas au code postal. Avec les fusions de communes, un même code peut changer au fil des années, donc un feu ancien peut porter le code d'une commune qui n'existe plus. EFFIS ne donne que le nom : une jointure par le nom est fragile (homonymes, accents), il faut passer par les coordonnées.
- **Règle retenue :** à décider. Piste : utiliser le code INSEE et un millésime unique du code officiel géographique ; pour EFFIS, rattacher chaque surface à une commune par sa position (lien vers le journal à ajouter).
- **Unité ou granularité :** commune (code INSEE à 5 caractères).
- **Exemple :** « Fauga », commune de Haute-Garonne, telle qu'elle apparaît dans EFFIS pour un feu du 24 juin 2026 (sans code INSEE).
- **Statut :** proposé
- **Origine de la définition :** INSEE, Code officiel géographique.
- **Ajouté par :** Maha Younsi (à partir de la consigne et des sources), 2026-11-16

## Danger élevé (Météo des forêts)

- **Définition :** le niveau 3 sur 4 de l'échelle de la Météo des forêts (couleur orange), entre « modéré » et « très élevé ». Il signifie que les conditions météorologiques et l'état de la végétation sont favorables au départ et à la propagation des feux.
- **Sources et colonnes :** archives de la Météo des forêts (Météo-France) : niveau prévu pour le lendemain et le surlendemain, valeur 3.
- **Divergences :** à l'oral, « danger élevé » est parfois utilisé pour dire « élevé ou plus », c'est-à-dire niveaux 3 et 4. Dans la commande, les chefs de centre disent que l'indice « annonce souvent un danger élevé » sans feu : il faut savoir s'ils parlent du niveau 3 seul. Le niveau est donné pour un département entier, pas pour une commune ou un massif. Il ne faut pas le confondre avec l'IFM (valeur numérique) ni avec les arrêtés préfectoraux d'accès aux massifs.
- **Règle retenue :** à décider : retenir le niveau 3 seul, ou « 3 et au-dessus » (lien vers le journal à ajouter).
- **Unité ou granularité :** département ; jour.
- **Exemple :** en 2026, la Haute-Garonne a eu 31 jours prévus au niveau élevé (3) et 4 jours au niveau très élevé (4), contre 1 seul jour au niveau 3 en 2024.
- **Statut :** validé (échelle confirmée par Météo-France) ; règle de regroupement à décider.
- **Origine de la définition :** documentation Météo-France (PDF de présentation et documentation des données expertisées) ; fiche Météo des forêts.
- **Ajouté par :** Maha Younsi, Hocine Ait Yakoub, Samy Bouaouni (analyses individuelles), 2026-11-16

## Date de première alerte

- **Définition :** le jour et l'heure où les secours ont été prévenus d'un feu. C'est la meilleure approximation disponible du moment où le feu a démarré, mais ce n'est pas l'heure exacte du départ.
- **Sources et colonnes :** BDIFF (date et heure de première alerte, voir la [fiche BDIFF](sources/fiche-bdiff.md)). EFFIS donne une « date du feu » estimée par satellite, qui n'est pas une date d'alerte.
- **Divergences :** l'horodatage est fourni en heure UTC dans la diffusion explorée ; il faut le convertir en heure locale avant d'en extraire le jour. Pour le croiser avec la Météo des forêts, il faut retrouver le niveau prévu pour ce jour-là, et non le niveau publié ce jour-là (voir « Prévision J+1 / J+2 »).
- **Règle retenue :** l'heure de première alerte, convertie en heure locale, sert d'approximation de l'heure de départ ([D-003](matrice/journal-des-decisions.md#d-003--g2--heure-des-départs-de-feu)) ; choix entre prévision J+1 et J+2 encore en attente.
- **Unité ou granularité :** date et heure ; un feu.
- **Exemple :** à compléter avec une valeur tirée de la BDIFF.
- **Statut :** à vérifier
- **Origine de la définition :** documentation BDIFF ; constat de la fiche source.
- **Ajouté par :** Soukaina Goumih (fiche BDIFF), 2026-11-17

## Départ de feu

- **Définition :** le début d'un incendie, c'est-à-dire le lieu et le moment où il démarre, quelle que soit la surface brûlée ensuite.
- **Sources et colonnes :** terme employé par la direction dans la commande ; BDIFF (date et commune d'alerte), données d'intervention des SDIS.
- **Divergences :** la direction parle de « départs de feu » et de « feux de forêt » dans le même courrier. BDIFF recense des feux de forêt, avec parfois un seuil de surface. Les SDIS comptent des interventions. EFFIS ne recense pas des départs mais des surfaces brûlées vues par satellite, sans les petits feux. Un départ de feu éteint très vite peut n'apparaître dans aucune de ces sources. En Haute-Garonne, sur 2024-2025, la BDIFF ne compte que 5 incendies alors qu'EFFIS cartographie 12 surfaces brûlées : les deux sources ne retiennent pas les mêmes événements (écart à expliquer, voir le journal).
- **Règle retenue :** à décider (lien vers le journal à ajouter).
- **Unité ou granularité :** un événement ; date (et heure si disponible) ; commune.
- **Exemple :** à compléter avec une valeur tirée de la BDIFF.
- **Statut :** proposé
- **Origine de la définition :** décision du groupe (à formaliser).
- **Ajouté par :** Maha Younsi, Hocine Ait Yakoub, Samy Bouaouni, Soukaina Goumih (analyses individuelles), 2026-11-16

## Département

- **Définition :** une division administrative identifiée par un code INSEE. L'Occitanie en compte 13 : 09, 11, 12, 30, 31, 32, 34, 46, 48, 65, 66, 81, 82. Le département du commanditaire est la Haute-Garonne (31).
- **Sources et colonnes :** toutes les sources : code département dans la Météo des forêts, déduit du code commune dans la BDIFF, nom en texte dans EFFIS.
- **Divergences :** le code INSEE du département ne correspond pas toujours au territoire couvert par un service d'incendie (SDIS). Certaines interventions sont faites en renfort hors du département. Le format du code change selon la source et l'année : dans la Météo des forêts, « 9 » pour l'Ariège en 2024 et 2025, mais « 09 » en 2026 ; la Corse est codée « 2A » et « 2B ». EFFIS ne donne que le nom du département. L'IFM Copernicus n'en donne aucun : il faut rattacher chaque point de grille à un département par sa position.
- **Règle retenue :** à décider. Piste : rattacher chaque feu au département de sa commune de départ, avec un code toujours sur deux caractères (lien vers le journal à ajouter).
- **Unité ou granularité :** département (code INSEE).
- **Exemple :** 31 = Haute-Garonne.
- **Statut :** proposé
- **Origine de la définition :** INSEE, Code officiel géographique.
- **Ajouté par :** Maha Younsi, Hocine Ait Yakoub (analyses individuelles), 2026-11-16

## Dispositif renforcé

- **Définition :** l'ensemble des moyens supplémentaires que le SDIS met en place les jours de danger, en plus de son fonctionnement normal : patrouilles, guet, renforts de personnel, etc.
- **Sources et colonnes :** commande de la direction (pas de colonne dans les sources de données).
- **Divergences :** la commande ne détaille pas son contenu exact (« patrouilles, guet, etc. »), ni le seuil actuel qui le déclenche. Il coûte cher et ne peut pas être activé sur tout le département tout l'été.
- **Règle retenue :** à demander à la direction : contenu du dispositif et seuil actuel de déclenchement (lien vers le journal à ajouter).
- **Unité ou granularité :** jour ; zone ou département.
- **Exemple :** sans objet.
- **Statut :** à vérifier
- **Origine de la définition :** commande de la direction.
- **Ajouté par :** Maha Younsi, Hocine Ait Yakoub, Samy Bouaouni, Soukaina Goumih (analyses individuelles), 2026-11-16

## Feu de forêt

- **Définition :** un incendie qui touche des forêts, landes, maquis ou garrigues. La définition couramment citée fixe un seuil d'au moins 1 hectare d'un seul tenant, avec une partie de la végétation arbustive ou arborée détruite.
- **Sources et colonnes :** BDIFF, Prométhée, EFFIS (part de chaque type de végétation brûlée), données d'intervention des SDIS.
- **Divergences :** BDIFF et Prométhée recensent des feux de forêt, avec des règles de saisie propres. Les SDIS comptent des interventions pour feux de végétation, qui incluent aussi les feux agricoles ou de broussailles. EFFIS cartographie toute surface brûlée vue par satellite : une surface peut être à 100 % en végétation naturelle autre que la forêt (landes, prairies), et les petits feux sont absents (seuil d'environ 30 ha avant 2018 d'après la documentation EFFIS). Le seuil de 1 ha n'est pas appliqué partout de la même façon.
- **Règle retenue :** à décider (lien vers le journal à ajouter).
- **Unité ou granularité :** un feu ; surface en hectares.
- **Exemple :** à compléter avec une valeur tirée de la BDIFF.
- **Statut :** à vérifier
- **Origine de la définition :** à confirmer dans la documentation BDIFF / Géorisques.
- **Ajouté par :** Maha Younsi, Hocine Ait Yakoub (analyses individuelles), 2026-11-16

## Guet

- **Définition :** une surveillance fixe depuis des points hauts (tours ou postes de guet) pour repérer très tôt les fumées et signaler un départ de feu.
- **Sources et colonnes :** commande de la direction (composante du dispositif renforcé).
- **Divergences :** à préciser avec la direction : guet assuré par le SDIS, par d'autres acteurs (forestiers, communes), ou les deux.
- **Règle retenue :** sans objet pour l'instant.
- **Unité ou granularité :** poste de guet ; jour.
- **Exemple :** sans objet.
- **Statut :** à vérifier
- **Origine de la définition :** à confirmer (doctrine de défense des forêts contre l'incendie).
- **Ajouté par :** Maha Younsi, Soukaina Goumih (analyses individuelles), 2026-11-16

## Indice de danger intégré

- **Définition :** l'indice calculé chaque jour par Météo-France pour estimer le danger de feu dans chaque département. Il part de l'IFM et y ajoute l'état de sécheresse de la végétation. C'est sur cette base que les prévisionnistes fixent le niveau de la Météo des forêts.
- **Sources et colonnes :** documentation de la Météo des forêts (PDF de présentation). L'indice lui-même n'est pas diffusé dans les archives : seul le niveau final (1 à 4) l'est.
- **Divergences :** le niveau publié ne dépend pas que de la météo : il tient compte aussi de la surface forestière, des interfaces forêt-habitat et des zones où des feux sont observés tous les ans. Deux départements avec la même météo peuvent donc avoir des niveaux différents.
- **Règle retenue :** sans objet (terme de contexte, utile pour expliquer l'indice à la direction).
- **Unité ou granularité :** département ; jour.
- **Exemple :** sans objet (valeur non diffusée).
- **Statut :** validé
- **Origine de la définition :** documentation Météo-France (PDF de présentation de la Météo des forêts).
- **Ajouté par :** Hocine Ait Yakoub (fiche Météo des forêts), 2026-11-17

## Indice Forêt Météo (IFM)

- **Définition :** une note calculée chaque jour à partir de la météo (température, humidité, vent, pluie) qui estime le danger qu'un feu démarre, se propage et soit intense. Plus la valeur est haute, plus le danger est grand.
- **Sources et colonnes :** Météo-France l'utilise pour calculer l'Indice de danger intégré (non diffusé dans les archives explorées). Copernicus diffuse un indice équivalent, `fire_weather_index`, calculé sur une grille mondiale depuis 1940 (voir la [fiche IFM Copernicus](sources/fiche-ifm-copernicus.md)).
- **Divergences :** l'IFM est une valeur numérique continue, alors que la Météo des forêts publie des niveaux de 1 à 4. Dans la commande, la direction dit « l'indice » pour parler du niveau de la Météo des forêts, pas de l'IFM. L'indice de Copernicus est calculé avec d'autres données météorologiques (réanalyse ERA5) que celui de Météo-France : la correspondance entre les deux reste à vérifier. Le fichier Copernicus n'a pas de code département : il faut une jointure spatiale des points de grille (13 points en Haute-Garonne ; aucun à Paris, dans les Hauts-de-Seine et en Seine-Saint-Denis).
- **Règle retenue :** utilisation comme approximation du niveau de la Météo des forêts avant 2024, à tester ([journal, D-004](matrice/journal-des-decisions.md#d-004--g3--part-des-jours-avec-feu-par-niveau)).
- **Unité ou granularité :** sans unité ; jour ; maille de grille (0,25°).
- **Exemple :** Haute-Garonne, été 2025 : valeur moyenne de 4,8 les jours au niveau 1 de la Météo des forêts, 15,5 au niveau 2 et 31,5 au niveau 3.
- **Statut :** à vérifier
- **Origine de la définition :** documentation Météo-France (PDF de présentation) ; catalogue Copernicus.
- **Ajouté par :** Maha Younsi (analyse individuelle), 2026-11-16 ; complété par Hocine Ait Yakoub (confrontation), 2026-11-18

## Intervention pour incendie

- **Définition :** une sortie des pompiers déclenchée pour un feu. Une intervention n'est pas un feu : un même feu peut entraîner plusieurs interventions.
- **Sources et colonnes :** statistiques des services d'incendie et de secours (ministère de l'Intérieur), données SDIS.
- **Divergences :** les SDIS comptent des interventions, BDIFF compte des feux, la direction parle de départs de feu. Les catégories « feux de végétation », « feux de forêt » et « feux d'espaces naturels » ne se recoupent pas exactement.
- **Règle retenue :** à décider (lien vers le journal à ajouter).
- **Unité ou granularité :** une intervention ; département ; année.
- **Exemple :** à compléter avec une valeur tirée d'une source.
- **Statut :** à vérifier
- **Origine de la définition :** à confirmer dans la documentation du producteur.
- **Ajouté par :** Maha Younsi (à partir de la consigne et des sources), 2026-11-16

## Jour sans feu

- **Définition :** un jour où aucun départ de feu n'a été recensé dans le territoire étudié. Il sert à calculer la part des jours avec feu pour chaque niveau de danger.
- **Sources et colonnes :** déduit de la BDIFF (aucun incendie avec ce `Departement` et ce jour local de `Date_de_premiere_alerte`) ou d'EFFIS (aucune surface avec cette `province` et cette `firedate`).
- **Divergences :** un jour sans feu recensé n'est pas forcément un jour sans feu réel : la couche BDIFF explorée signale des lignes non intégrées, et EFFIS ne voit pas les petits feux. Un « zéro » peut donc être un vrai zéro ou une absence de donnée.
- **Règle retenue :** à décider : ne compter comme « jour sans feu » que les jours couverts par une source dont la complétude a été vérifiée sur la période (point soulevé dans la fiche BDIFF et l'inventaire).
- **Unité ou granularité :** un jour × un département.
- **Exemple :** sans objet (à établir après le croisement BDIFF × Météo des forêts).
- **Statut :** proposé
- **Origine de la définition :** décision du groupe (à formaliser) ; fiche BDIFF, « Point de vigilance ».
- **Ajouté par :** Soukaina Goumih (fiche BDIFF et inventaire), Maha Younsi (matrice), 2026-11-18

## Météo des forêts

- **Définition :** le service de Météo-France qui annonce chaque jour, pour chaque département, le niveau de danger de feu prévu pour le lendemain et le surlendemain, sur une échelle à 4 niveaux : faible (1, vert), modéré (2, jaune), élevé (3, orange), très élevé (4, rouge). C'est « l'indice » dont parle la direction dans la commande.
- **Sources et colonnes :** archives de la Météo des forêts (Météo-France, data.gouv.fr) : date de publication, code département, niveau prévu pour le lendemain, niveau prévu pour le surlendemain.
- **Divergences :** la direction dit « l'indice » ; Météo-France publie un niveau (une classe) et non une valeur numérique, à ne pas confondre avec l'IFM. « L'indice au plus bas » dont parle la commande correspond au niveau 1 (faible). Le service existe depuis 2023, mais les archives ne commencent qu'en 2024. Il n'est publié qu'en saison : du 3 juin au 30 septembre en 2024 et 2025, du 28 mai au 5 octobre en 2026. Un feu survenu hors de ces périodes n'a pas de niveau associé. La date d'une ligne est la date de publication, pas le jour concerné (voir « Prévision J+1 / J+2 »).
- **Règle retenue :** à décider (lien vers le journal à ajouter).
- **Unité ou granularité :** niveau de danger ; jour ; département (96 départements : Hexagone et Corse).
- **Exemple :** bulletin publié le 9 juillet 2026 : niveau 4 (très élevé) prévu pour la Haute-Garonne le 10 juillet.
- **Statut :** validé
- **Origine de la définition :** documentation Météo-France (PDF de présentation et documentation des données expertisées) ; fiche Météo des forêts.
- **Ajouté par :** Maha Younsi, Hocine Ait Yakoub, Samy Bouaouni, Soukaina Goumih (analyses individuelles), 2026-11-17 ; complété par Hocine Ait Yakoub (fiche Météo des forêts), 2026-11-17

## Moyens humains et financiers

- **Définition :** les personnels, véhicules, matériels et le budget que le SDIS peut consacrer à la lutte contre les feux de forêt, et qu'il cherche à répartir au mieux.
- **Sources et colonnes :** commande de la direction ; données internes du SDIS 31 (à demander).
- **Divergences :** la commande ne dit pas quels moyens sont déplaçables, ni à quelle unité ils sont répartis (centre de secours, commune, secteur, massif). Le budget disponible et le coût d'une journée de renfort ne sont pas donnés.
- **Règle retenue :** à demander à la direction : unité de répartition, budget et coût journalier (lien vers le journal à ajouter).
- **Unité ou granularité :** centre de secours, secteur ou commune ; saison.
- **Exemple :** sans objet.
- **Statut :** à vérifier
- **Origine de la définition :** commande de la direction.
- **Ajouté par :** Maha Younsi, Hocine Ait Yakoub (analyses individuelles), 2026-11-17

## Patrouille

- **Définition :** une surveillance mobile sur le terrain, en véhicule, dans les zones sensibles, pour dissuader, repérer et attaquer très vite un départ de feu.
- **Sources et colonnes :** commande de la direction (composante du dispositif renforcé).
- **Divergences :** à préciser avec la direction : patrouilles du SDIS seules, ou aussi d'autres acteurs (forestiers, gendarmerie, communes).
- **Règle retenue :** sans objet pour l'instant.
- **Unité ou granularité :** patrouille ; jour ; secteur.
- **Exemple :** sans objet.
- **Statut :** à vérifier
- **Origine de la définition :** à confirmer (doctrine de défense des forêts contre l'incendie).
- **Ajouté par :** Maha Younsi (analyse individuelle), 2026-11-16

## Prévision J+1 / J+2

- **Définition :** chaque bulletin de la Météo des forêts donne deux prévisions : le niveau prévu pour le lendemain (J+1) et celui prévu pour le surlendemain (J+2). Un même jour reçoit donc deux prévisions, publiées à un jour d'écart.
- **Sources et colonnes :** archives de la Météo des forêts (niveau prévu pour le lendemain, niveau prévu pour le surlendemain).
- **Divergences :** les deux prévisions pour un même jour peuvent différer. La date d'une ligne est celle de la publication : sans décalage d'un jour (J+1) ou de deux jours (J+2), le croisement avec les feux est faux.
- **Règle retenue :** à décider : retenir la prévision J+1 (la plus récente) ou la prévision J+2 (celle disponible plus tôt pour organiser le dispositif). Le choix dépend du délai dont le SDIS a besoin pour déclencher le dispositif renforcé (à demander à la direction) (lien vers le journal à ajouter).
- **Unité ou granularité :** département ; jour concerné ; date de publication.
- **Exemple :** pour le 10 juillet 2026 en Haute-Garonne : niveau 3 dans le bulletin du 8 juillet (J+2), niveau 4 dans celui du 9 juillet (J+1).
- **Statut :** validé (fonctionnement confirmé par Météo-France) ; choix de la prévision à décider.
- **Origine de la définition :** documentation Météo-France ; constat de la fiche Météo des forêts.
- **Ajouté par :** Hocine Ait Yakoub (fiche Météo des forêts), 2026-11-17

## Région

- **Définition :** la région administrative Occitanie, qui regroupe 13 départements : Ariège (09), Aude (11), Aveyron (12), Gard (30), Haute-Garonne (31), Gers (32), Hérault (34), Lot (46), Lozère (48), Hautes-Pyrénées (65), Pyrénées-Orientales (66), Tarn (81), Tarn-et-Garonne (82).
- **Sources et colonnes :** toutes les sources (code région ou déduit du code département).
- **Divergences :** l'Occitanie existe depuis 2016 (fusion de Languedoc-Roussillon et Midi-Pyrénées) ; des données anciennes peuvent être rangées sous les anciennes régions. Seuls les départements méditerranéens seraient suivis par Prométhée (liste à vérifier). Dans EFFIS, le Gers n'a aucune surface brûlée enregistrée : la région n'y est représentée que par 12 départements.
- **Règle retenue :** à décider. Piste : définir la région par la liste des 13 codes département, quelle que soit l'année (lien vers le journal à ajouter).
- **Unité ou granularité :** région ; agrégée par département.
- **Exemple :** 31 = Haute-Garonne, département du commanditaire.
- **Statut :** proposé
- **Origine de la définition :** INSEE, Code officiel géographique.
- **Ajouté par :** Samy Bouaouni (analyse individuelle), 2026-11-17

## Saison feux

- **Définition :** la période de l'année où le risque de feux de forêt est le plus fort et où le dispositif de lutte est renforcé. La direction parle de « l'été » et prépare « le printemps et l'été ».
- **Sources et colonnes :** commande de la direction ; Météo des forêts (période de publication) ; BDIFF et EFFIS (dates des feux).
- **Divergences :** « l'été » de la direction (calendrier) ne correspond pas exactement à la période de publication de la Météo des forêts (3 juin au 30 septembre en 2024 et 2025, 28 mai au 5 octobre en 2026), ni à la période fixée par arrêté préfectoral. Surtout, d'après EFFIS, 85 % des surfaces brûlées en Occitanie (1 718 sur 2 016 depuis 2000) l'ont été hors de juin à septembre, principalement de janvier à avril et en montagne.
- **Règle retenue :** l'analyse du seuil se limite à la saison de publication de la Météo des forêts ; les feux hors saison sont traités à part ([D-005](matrice/journal-des-decisions.md#d-005--g4--feux-les-jours-de-danger-faible-et-hors-saison)) ; croisements commencés sur les saisons 2024 et 2025 ([D-011](matrice/journal-des-decisions.md#d-011--période-commune-pour-les-croisements)).
- **Unité ou granularité :** période (dates de début et de fin) ; année.
- **Exemple :** saison 2026 de la Météo des forêts : du 28 mai au 5 octobre.
- **Statut :** à vérifier
- **Origine de la définition :** commande de la direction ; documentation et archives de la Météo des forêts ; fiche EFFIS.
- **Ajouté par :** Maha Younsi, Hocine Ait Yakoub (analyses individuelles), 2026-11-16

## SDIS (Service départemental d'incendie et de secours)

- **Définition :** le service public qui organise les pompiers dans un département et intervient sur les incendies. Notre commanditaire est la direction du SDIS 31.
- **Sources et colonnes :** données d'intervention, statistiques nationales des SDIS.
- **Divergences :** le territoire d'action d'un SDIS correspond en principe au département, mais des renforts entre départements existent. Ses chiffres sont des interventions, pas des feux.
- **Règle retenue :** à décider (lien vers le journal à ajouter).
- **Unité ou granularité :** département.
- **Exemple :** SDIS 31 (Haute-Garonne).
- **Statut :** proposé
- **Origine de la définition :** Code général des collectivités territoriales.
- **Ajouté par :** Maha Younsi (analyse individuelle), 2026-11-16

## Seuil de déclenchement

- **Définition :** le niveau de la Météo des forêts à partir duquel le SDIS active le dispositif renforcé. C'est la décision que la direction nous demande d'éclairer.
- **Sources et colonnes :** commande de la direction ; Météo des forêts (niveau prévu) ; BDIFF et EFFIS (feux observés).
- **Divergences :** le seuil actuel n'est pas indiqué dans la commande. Un seuil trop bas déclenche des alertes sans feu (coût inutile) ; un seuil trop haut laisse passer des feux les jours de danger faible. Les jours aux niveaux 3 et 4 sont rares et varient beaucoup d'une année à l'autre, ce qui rend l'estimation fragile sur trois saisons.
- **Règle retenue :** à décider après analyse ; seuil actuel à demander à la direction (lien vers le journal à ajouter).
- **Unité ou granularité :** niveau de danger ; jour ; département.
- **Exemple :** un seuil fixé au niveau 3 aurait déclenché le dispositif 1 jour en 2024 et 35 jours en 2026 en Haute-Garonne.
- **Statut :** à vérifier
- **Origine de la définition :** commande de la direction.
- **Ajouté par :** Maha Younsi, Hocine Ait Yakoub, Samy Bouaouni, Soukaina Goumih (analyses individuelles), 2026-11-16

## Surface brûlée

- **Définition :** l'étendue de terrain parcourue par un feu, exprimée en hectares.
- **Sources et colonnes :** BDIFF (`Surface_parcourue`, détaillée en `Surface_foret`, `Surface_maquis_garrigues`, `Surfaces_agricoles`, etc., avec `Precision_des_surfaces` : « Mesurées » ou « Estimées » ; unité à confirmer, des valeurs comme 40 000 pour un feu du 31 suggèrent des mètres carrés), Prométhée, EFFIS (surface cartographiée par satellite et part de chaque type d'occupation du sol, voir la [fiche EFFIS](sources/fiche-effis.md)).
- **Divergences :** une source peut donner la surface totale ou la détailler (forêt, landes, autres terres). Dans la BDIFF, les surfaces sont « Estimées » pour environ 16 % des incendies d'Occitanie (67 sur 413 en 2024, 77 sur 472 en 2025), « Mesurées » pour les autres ; l'unité des colonnes n'est pas documentée dans la couche explorée. EFFIS mesure le contour vu par satellite, mais ne voit pas les petits feux ; un même feu peut y apparaître en plusieurs surfaces, et certaines surfaces sont à 0 ha.
- **Règle retenue :** à décider (lien vers le journal à ajouter).
- **Unité ou granularité :** hectare ; un feu.
- **Exemple :** EFFIS, feu du 24 juin 2026 à Fauga (Haute-Garonne) : 16 ha.
- **Statut :** à vérifier
- **Origine de la définition :** à confirmer dans la documentation BDIFF ; documentation EFFIS.
- **Ajouté par :** Maha Younsi (à partir de la consigne et des sources), 2026-11-16

## Territoire national

- **Définition :** l'ensemble de la France auquel la direction veut comparer la Haute-Garonne et l'Occitanie.
- **Sources et colonnes :** commande de la direction ; couverture géographique de chaque source.
- **Divergences :** la Météo des forêts ne couvre que l'Hexagone et la Corse (96 départements, pas d'outre-mer). La documentation de la BDIFF annonce la métropole et les départements d'outre-mer. EFFIS couvre toute l'Europe, filtrable par pays. Pour comparer, il faut se limiter au territoire couvert par toutes les sources utilisées.
- **Règle retenue :** à décider. Piste : France métropolitaine (96 départements), seul territoire couvert par la Météo des forêts (lien vers le journal à ajouter).
- **Unité ou granularité :** France ; agrégé par département.
- **Exemple :** sans objet.
- **Statut :** à vérifier
- **Origine de la définition :** commande de la direction ; fiches BDIFF, Météo des forêts et EFFIS.
- **Ajouté par :** Maha Younsi, Soukaina Goumih (analyses individuelles), 2026-11-16

---

## Termes des analyses regroupés ou écartés

| Terme proposé | Proposé par | Décision | Raison |
|---|---|---|---|
| Zone de prévision | Maha Younsi | Écarté | La Météo des forêts est publiée par département, pas par zone : le terme ne correspond à aucune donnée. |
| Indice au plus bas | Hocine Ait Yakoub | Regroupé dans « Météo des forêts » | Correspond au niveau 1 (faible) de l'échelle. |
| Niveau d'indice / indice élevé | Samy Bouaouni | Regroupé dans « Météo des forêts » et « Danger élevé » | Même notion que les niveaux de l'échelle. |
| Seuil actuel | Hocine Ait Yakoub, Samy Bouaouni, Soukaina Goumih | Regroupé dans « Seuil de déclenchement » | Valeur actuelle du seuil, à demander à la direction. |
| Été | Hocine Ait Yakoub | Regroupé dans « Saison feux » | Même période, vue par la direction. |
