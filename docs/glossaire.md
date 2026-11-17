# Glossaire — Occitanie

Dernière mise à jour : 2026-11-17

> Version 0 (fin de S1). Commanditaire : Direction du SDIS 31 (Haute-Garonne), voir [commande.md](commande.md).
> Les définitions marquées « à vérifier » doivent être confirmées par la documentation du producteur avant validation. Toute modification passe par un ticket et une pull request relue par la cheffe de projet. On ne supprime jamais un terme : on le marque « obsolète » avec la raison et la date.

---

## Cause d'un feu

- **Définition :** l'origine présumée d'un incendie, regroupée en grandes familles (par exemple : naturelle, accidentelle, involontaire liée à une activité humaine, malveillance, inconnue).
- **Sources et colonnes :** BDIFF (colonne de nature ou de cause), Prométhée pour les départements méditerranéens.
- **Divergences :** les familles de causes et leur niveau de détail peuvent différer entre BDIFF et Prométhée. Une part importante des feux a une cause « inconnue ». La cause est souvent présumée, rarement établie.
- **Règle retenue :** à décider (lien vers le journal à ajouter).
- **Unité ou granularité :** un feu.
- **Exemple :** à compléter avec une valeur tirée d'une source.
- **Statut :** à vérifier
- **Origine de la définition :** à confirmer dans la documentation BDIFF et Prométhée.
- **Ajouté par :** Soukaina Goumih, 2026-11-16

## Chef de centre

- **Définition :** l'officier ou le sous-officier qui dirige un centre d'incendie et de secours (une caserne) du SDIS. C'est lui ou elle qui constate sur le terrain si l'indice de danger correspond aux feux réellement observés.
- **Sources et colonnes :** commande de la direction (pas de colonne dans les sources de données).
- **Divergences :** dans la commande, les chefs de centre n'ont pas le même ressenti sur l'indice : certains voient trop d'alertes sans feu, d'autres des feux les jours de danger faible. Leur avis est un témoignage, pas une mesure.
- **Règle retenue :** sans objet (terme de contexte).
- **Unité ou granularité :** un centre d'incendie et de secours.
- **Exemple :** sans objet.
- **Statut :** proposé
- **Origine de la définition :** commande de la direction ; organisation des SDIS à confirmer.
- **Ajouté par :** Maha Younsi, 2026-11-16

## Commune

- **Définition :** la plus petite unité administrative française. Elle sert à localiser l'endroit où un feu a démarré.
- **Sources et colonnes :** BDIFF (code INSEE de la commune), référentiels géographiques INSEE / IGN.
- **Divergences :** le code INSEE (identifiant officiel) ne correspond pas au code postal. Avec les fusions de communes, un même code peut changer au fil des années, donc un feu ancien peut porter le code d'une commune qui n'existe plus.
- **Règle retenue :** à décider. Piste : utiliser le code INSEE et un millésime unique du code officiel géographique (lien vers le journal à ajouter).
- **Unité ou granularité :** commune (code INSEE à 5 caractères).
- **Exemple :** à compléter avec une valeur tirée d'une source.
- **Statut :** proposé
- **Origine de la définition :** INSEE, Code officiel géographique.
- **Ajouté par :** hocine Ait Yakoub, 2026-11-16

## Danger élevé (Météo des forêts)

- **Définition :** un des niveaux de l'échelle de danger de feu publiée chaque jour par la Météo des forêts. Il indique la probabilité qu'un feu démarre et se propage, selon la météo et l'état de la végétation.
- **Sources et colonnes :** Météo des forêts (Météo-France), carte de danger par zone et par jour.
- **Divergences :** l'échelle a plusieurs niveaux, et « danger élevé » est parfois utilisé à l'oral pour dire « élevé ou plus ». Dans la commande, les chefs de centre disent que l'indice « annonce souvent un danger élevé » sans feu : il faut savoir de quel niveau exact ils parlent. Le danger publié est une prévision par zone, pas une mesure à la commune. Il ne faut pas le confondre avec l'IFM (valeur numérique) ni avec les arrêtés préfectoraux d'accès aux massifs.
- **Règle retenue :** à décider : retenir le niveau « élevé » seul, ou « élevé et au-dessus » (lien vers le journal à ajouter).
- **Unité ou granularité :** zone de prévision ; jour.
- **Exemple :** à compléter avec une valeur tirée d'une source.
- **Statut :** à vérifier (nombre exact de niveaux et libellés à confirmer)
- **Origine de la définition :** documentation Météo-France / Météo des forêts.
- **Ajouté par :** samy Bouaouni, 2026-11-16

## Départ de feu

- **Définition :** le début d'un incendie, c'est-à-dire le lieu et le moment où il démarre, quelle que soit la surface brûlée ensuite.
- **Sources et colonnes :** terme employé par la direction dans la commande ; BDIFF (date et commune d'alerte), données d'intervention des SDIS.
- **Divergences :** la direction parle de « départs de feu » et de « feux de forêt » dans le même courrier. BDIFF recense des feux de forêt, avec parfois un seuil de surface. Les SDIS comptent des interventions. Un départ de feu éteint très vite peut ne pas apparaître dans BDIFF.
- **Règle retenue :** à décider (lien vers le journal à ajouter).
- **Unité ou granularité :** un événement ; date (et heure si disponible) ; commune.
- **Exemple :** à compléter avec une valeur tirée d'une source.
- **Statut :** proposé
- **Origine de la définition :** décision du groupe (à formaliser).
- **Ajouté par :** hocine Ait Yakoub, 2026-11-16

## Département

- **Définition :** une division administrative identifiée par un code INSEE. L'Occitanie en compte 13 : 09, 11, 12, 30, 31, 32, 34, 46, 48, 65, 66, 81, 82. Le département du commanditaire est la Haute-Garonne (31).
- **Sources et colonnes :** toutes les sources (code département, ou déduit du code commune).
- **Divergences :** le code INSEE du département ne correspond pas toujours au territoire couvert par un service d'incendie (SDIS). Certaines interventions sont faites en renfort hors du département. La Météo des forêts découpe le territoire en zones qui ne suivent pas forcément les limites départementales.
- **Règle retenue :** à décider. Piste : rattacher chaque feu au département de sa commune de départ (lien vers le journal à ajouter).
- **Unité ou granularité :** département (code INSEE).
- **Exemple :** 31 = Haute-Garonne.
- **Statut :** proposé
- **Origine de la définition :** INSEE, Code officiel géographique.
- **Ajouté par :** hocine Ait Yakoub, 2026-11-16

## Dispositif renforcé

- **Définition :** l'ensemble des moyens supplémentaires que le SDIS met en place les jours de danger, en plus de son fonctionnement normal : patrouilles, guet, renforts de personnel, etc.
- **Sources et colonnes :** commande de la direction (pas de colonne dans les sources de données).
- **Divergences :** la commande ne détaille pas son contenu exact (« patrouilles, guet, etc. »), ni le seuil actuel qui le déclenche. Il coûte cher et ne peut pas être activé sur tout le département tout l'été.
- **Règle retenue :** à demander à la direction : contenu du dispositif et seuil actuel de déclenchement (lien vers le journal à ajouter).
- **Unité ou granularité :** jour ; zone ou département.
- **Exemple :** sans objet.
- **Statut :** à vérifier
- **Origine de la définition :** commande de la direction.
- **Ajouté par :** Maha Younsi, 2026-11-16

## Fausse alerte

- **Définition :** un jour où le dispositif renforcé aurait été déclenché (niveau de la Météo des forêts égal ou supérieur au seuil) sans qu'aucun départ de feu ne se produise dans le département.
- **Sources et colonnes :** Météo des forêts (niveau du jour) croisée avec BDIFF (date et commune des feux).
- **Divergences :** dans la commande, les chefs de centre en parlent d'après leur ressenti, sans comptage. Le résultat dépend de la définition retenue pour « départ de feu » et de l'emprise (département ou commune). Un feu absent de BDIFF fait apparaître à tort un jour de feu comme une fausse alerte.
- **Règle retenue :** à décider : seuil testé, emprise et définition du départ de feu (lien vers le journal à ajouter).
- **Unité ou granularité :** un jour ; un département.
- **Exemple :** à compléter après croisement des sources.
- **Statut :** proposé
- **Origine de la définition :** décision du groupe, à partir de la commande.
- **Ajouté par :** Hocine Ait Yakoub, 2026-11-17

## Feu de forêt

- **Définition :** un incendie qui touche des forêts, landes, maquis ou garrigues. La définition couramment citée fixe un seuil d'au moins 1 hectare d'un seul tenant, avec une partie de la végétation arbustive ou arborée détruite.
- **Sources et colonnes :** BDIFF, Prométhée, données d'intervention des SDIS.
- **Divergences :** BDIFF et Prométhée recensent des feux de forêt, avec des règles de saisie propres. Les SDIS comptent des interventions pour feux de végétation, qui incluent aussi les feux agricoles ou de broussailles. Le seuil de 1 ha n'est pas appliqué partout de la même façon.
- **Règle retenue :** à décider (lien vers le journal à ajouter).
- **Unité ou granularité :** un feu ; surface en hectares.
- **Exemple :** à compléter avec une valeur tirée d'une source.
- **Statut :** à vérifier
- **Origine de la définition :** à confirmer dans la documentation BDIFF / Géorisques.
- **Ajouté par :** Soukaina Goumih, 2026-11-16

## Feu manqué

- **Définition :** un départ de feu survenu un jour où le niveau de la Météo des forêts était en dessous du seuil de déclenchement, donc sans dispositif renforcé en place.
- **Sources et colonnes :** BDIFF (date et commune des feux) croisée avec la Météo des forêts (niveau du jour).
- **Divergences :** dans la commande, des chefs de centre disent avoir combattu des feux les jours où l'indice était au plus bas. Les feux hors saison (printemps, hiver) n'ont pas de niveau publié : ils ne peuvent être classés ni manqués ni détectés.
- **Règle retenue :** à décider : traitement des feux survenus hors période de publication de l'indice (lien vers le journal à ajouter).
- **Unité ou granularité :** un départ de feu ; un jour.
- **Exemple :** à compléter après croisement des sources.
- **Statut :** proposé
- **Origine de la définition :** décision du groupe, à partir de la commande.
- **Ajouté par :** Hocine Ait Yakoub, 2026-11-17

## Guet

- **Définition :** une surveillance fixe depuis des points hauts (tours ou postes de guet) pour repérer très tôt les fumées et signaler un départ de feu.
- **Sources et colonnes :** commande de la direction (composante du dispositif renforcé).
- **Divergences :** à préciser avec la direction : guet assuré par le SDIS, par d'autres acteurs (forestiers, communes), ou les deux.
- **Règle retenue :** sans objet pour l'instant.
- **Unité ou granularité :** poste de guet ; jour.
- **Exemple :** sans objet.
- **Statut :** à vérifier
- **Origine de la définition :** à confirmer (doctrine de défense des forêts contre l'incendie).
- **Ajouté par :** Maha Younsi, 2026-11-16

## Indice Forêt Météo (IFM)

- **Définition :** une note calculée chaque jour à partir de la météo (température, humidité, vent, pluie) qui estime le risque qu'un feu démarre et se propage. Plus la valeur est haute, plus le danger est grand.
- **Sources et colonnes :** Météo-France (IFM), sert de base à la Météo des forêts.
- **Divergences :** l'IFM est une valeur numérique continue, alors que la Météo des forêts publie des niveaux. Les seuils de passage d'un niveau à l'autre peuvent dépendre de la zone. Dans la commande, la direction dit « l'indice » pour parler du niveau de la Météo des forêts.
- **Règle retenue :** à décider (lien vers le journal à ajouter).
- **Unité ou granularité :** sans unité ; jour ; point de grille ou zone.
- **Exemple :** à compléter avec une valeur tirée d'une source.
- **Statut :** à vérifier
- **Origine de la définition :** documentation Météo-France.
- **Ajouté par :** Soukaina Goumih, 2026-11-16

## Intervention pour incendie

- **Définition :** une sortie des pompiers déclenchée pour un feu. Une intervention n'est pas un feu : un même feu peut entraîner plusieurs interventions.
- **Sources et colonnes :** statistiques des services d'incendie et de secours (ministère de l'Intérieur), données SDIS.
- **Divergences :** les SDIS comptent des interventions, BDIFF compte des feux, la direction parle de départs de feu. Les catégories « feux de végétation », « feux de forêt » et « feux d'espaces naturels » ne se recoupent pas exactement.
- **Règle retenue :** à décider (lien vers le journal à ajouter).
- **Unité ou granularité :** une intervention ; département ; année.
- **Exemple :** à compléter avec une valeur tirée d'une source.
- **Statut :** à vérifier
- **Origine de la définition :** à confirmer dans la documentation du producteur.
- **Ajouté par :** Soukaina Goumih, 2026-11-16

## Météo des forêts

- **Définition :** la carte publiée chaque jour par Météo-France, avec l'Office national des forêts, qui annonce pour chaque département le niveau de danger de feu du lendemain et du surlendemain, sur quatre niveaux : faible (vert), modéré (jaune), élevé (orange), très élevé (rouge). Elle annonce un danger, pas des feux.
- **Sources et colonnes :** Météo-France ; colonnes à identifier dans la fiche d'identité de la source.
- **Divergences :** publiée seulement depuis juin 2023 et seulement en saison (juin à septembre) : environ quatre saisons d'historique, et aucun niveau pour les feux de printemps ou d'hiver. Deux prévisions existent pour un même jour (publiées la veille et l'avant-veille). Elle couvre l'Hexagone et la Corse. Elle s'appuie sur l'IFM mais ne se confond pas avec lui. L'« indice au plus bas » de la commande correspond au niveau faible (vert). L'entrée « Danger élevé » parle de zone de prévision alors que la carte est publiée par département : à harmoniser.
- **Règle retenue :** à décider : prévision de la veille ou de l'avant-veille (lien vers le journal à ajouter).
- **Unité ou granularité :** un département ; un jour.
- **Exemple :** Haute-Garonne, vendredi 10 juillet 2026 : danger très élevé (rouge), seul département de France à ce niveau ce jour-là (relevé dans la presse, à confirmer dans les données Météo-France).
- **Statut :** à vérifier
- **Origine de la définition :** Météo-France et Service-Public.fr ; à confirmer dans la documentation Météo-France.
- **Ajouté par :** Hocine Ait Yakoub, 2026-11-17

## Moyens humains et financiers

- **Définition :** les personnels (sapeurs-pompiers professionnels et volontaires), les véhicules et le matériel, ainsi que le budget, que le SDIS peut affecter à la prévention et à la lutte contre les feux.
- **Sources et colonnes :** commande de la direction ; aucune source de données identifiée à ce stade.
- **Divergences :** la commande ne précise ni le budget disponible, ni l'unité de répartition des moyens (centre de secours, commune, massif). Sans cette information, on peut montrer où se produisent les feux, mais pas combien de moyens y affecter.
- **Règle retenue :** à demander à la direction (lien vers le journal à ajouter).
- **Unité ou granularité :** centre d'incendie et de secours (à confirmer) ; euros ; jour.
- **Exemple :** sans objet.
- **Statut :** à vérifier
- **Origine de la définition :** commande de la direction.
- **Ajouté par :** Hocine Ait Yakoub, 2026-11-17

## Patrouille

- **Définition :** une surveillance mobile sur le terrain, en véhicule, dans les zones sensibles, pour dissuader, repérer et attaquer très vite un départ de feu.
- **Sources et colonnes :** commande de la direction (composante du dispositif renforcé).
- **Divergences :** à préciser avec la direction : patrouilles du SDIS seules, ou aussi d'autres acteurs (forestiers, gendarmerie, communes).
- **Règle retenue :** sans objet pour l'instant.
- **Unité ou granularité :** patrouille ; jour ; secteur.
- **Exemple :** sans objet.
- **Statut :** à vérifier
- **Origine de la définition :** à confirmer (doctrine de défense des forêts contre l'incendie).
- **Ajouté par :** Maha Younsi, 2026-11-16

## Saison feux

- **Définition :** la période de l'année où le risque de feux de forêt est le plus fort et où le dispositif de lutte est renforcé. La direction parle de « l'été » et prépare « le printemps et l'été ».
- **Sources et colonnes :** commande de la direction ; Météo des forêts (période de publication) ; BDIFF (dates des feux).
- **Divergences :** « l'été » de la direction (calendrier) n'est pas forcément la période de publication de la Météo des forêts, ni la période fixée par arrêté préfectoral. Des feux ont aussi lieu au printemps ou en hiver, notamment en zone de montagne.
- **Règle retenue :** à décider : bornes de dates retenues pour comparer les saisons 2026 et 2027 (lien vers le journal à ajouter).
- **Unité ou granularité :** période (dates de début et de fin) ; année.
- **Exemple :** saison 2026 (référence de la direction).
- **Statut :** à vérifier
- **Origine de la définition :** commande de la direction ; période de publication de la Météo des forêts à confirmer.
- **Ajouté par :** samy Bouaouni, 2026-11-16

## SDIS (Service départemental d'incendie et de secours)

- **Définition :** le service public qui organise les pompiers dans un département et intervient sur les incendies. Notre commanditaire est la direction du SDIS 31.
- **Sources et colonnes :** données d'intervention, statistiques nationales des SDIS.
- **Divergences :** le territoire d'action d'un SDIS correspond en principe au département, mais des renforts entre départements existent. Ses chiffres sont des interventions, pas des feux.
- **Règle retenue :** à décider (lien vers le journal à ajouter).
- **Unité ou granularité :** département.
- **Exemple :** SDIS 31 (Haute-Garonne).
- **Statut :** proposé
- **Origine de la définition :** Code général des collectivités territoriales.
- **Ajouté par :** Maha Younsi, 2026-11-16

## Seuil de déclenchement

- **Définition :** le niveau de la Météo des forêts à partir duquel le SDIS active le dispositif renforcé. C'est la décision que la direction nous demande d'éclairer.
- **Sources et colonnes :** commande de la direction ; Météo des forêts (niveau du jour) ; BDIFF (feux observés).
- **Divergences :** le seuil actuel n'est pas indiqué dans la commande. Un seuil trop bas déclenche des alertes sans feu (coût inutile) ; un seuil trop haut laisse passer des feux les jours de danger faible.
- **Règle retenue :** à décider après analyse ; seuil actuel à demander à la direction (lien vers le journal à ajouter).
- **Unité ou granularité :** niveau de danger ; jour ; zone ou département.
- **Exemple :** sans objet.
- **Statut :** à vérifier
- **Origine de la définition :** commande de la direction.
- **Ajouté par :** samy Bouaouni, 2026-11-16

## Surface brûlée

- **Définition :** l'étendue de terrain parcourue par un feu, exprimée en hectares.
- **Sources et colonnes :** BDIFF (surface parcourue, parfois détaillée par type de végétation), Prométhée.
- **Divergences :** une source peut donner la surface totale ou la détailler (forêt, landes, autres terres). Les surfaces sont souvent estimées et non mesurées. Les petits feux peuvent avoir une surface arrondie ou nulle.
- **Règle retenue :** à décider (lien vers le journal à ajouter).
- **Unité ou granularité :** hectare ; un feu.
- **Exemple :** à compléter avec une valeur tirée d'une source.
- **Statut :** à vérifier
- **Origine de la définition :** à confirmer dans la documentation BDIFF.
- **Ajouté par :** Soukaina Goumih, 2026-11-16

## Territoire national

- **Définition :** l'ensemble de la France auquel la direction veut comparer la Haute-Garonne et l'Occitanie.
- **Sources et colonnes :** commande de la direction ; couverture géographique de BDIFF et de la Météo des forêts.
- **Divergences :** France métropolitaine seule, ou avec l'outre-mer ? Les sources n'ont pas forcément la même couverture : il faut comparer sur un territoire couvert par toutes.
- **Règle retenue :** à décider. Piste : France métropolitaine (lien vers le journal à ajouter).
- **Unité ou granularité :** France ; agrégé par département.
- **Exemple :** sans objet.
- **Statut :** à vérifier
- **Origine de la définition :** commande de la direction ; couverture des sources à confirmer.
- **Ajouté par :** hocine Ait Yakoub, 2026-11-16
