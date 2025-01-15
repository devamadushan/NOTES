## Introduction
Un ECOLAB est composé de 3 cellules climatiques et d'une Thermofrigopompe. Les cellules climatiques sont indépendantes : elles peuvent être contrôlées indépendamment.
La Thermofrigopompe permet de produire du chaud ou du froid pour réguler les différentes cellules climatiques.
Il y a 5 ECOLAB sur site.
Chaque ECOLAB dispose d'un PC de Supervision qui permet de piloter les climats dans les cellules.

## Paramètres de climats
Le climat est actuellement chargé à partir de la Supervision de l'ECOLAB. Il prend la forme d'un fichier au format Excel avec plusieurs feuilles de calcul.

Les différents paramètres sont les suivants :


"No_Pas": 1, "mn": 5, "secondes": 0, "no_h": 0, "no_jours": 1,
    "TEMP_CEL": 0.0, "REGUL_ECORIUM": 0, "T_ECOR_FOND": 0.0, "T_ECOR_INF": 0.0, "T_ECOR_SUP": 0.0,
    "REGUL_HYG": 0, "HYG_CEL": 0.0,
    "REGUL_PRESSION": 0, "PRESSION": 0.0,
    "REGUL_C": 0, "C": 0.0, "REGUL_O": 0, "O": 0.0, "REGUL_N": 0, "N": 0.0, "REGUL_X": 0, "X": 0.0,
    "HAUT_ECOLUX": 0.0, "INT_ECOLUX": 0, "CONFIG_ECOLUX": 0,
    "INT_PLUIE": 0,
    "VITESSE_VENT": 0.0, "VENT_LATERAL_UN": 0, "VENT_LATERAL_DEUX": 0, "VENT_LATERAL_TROIS": 0, "VENT_LATERAL_QUATRE": 0, "INT_VENT_LAT": 0.0,
    "RENO_AIR": 0, "EVENT": 0.0, "Chromato": 0, "CONFIG_MES_INCUB": 0,
    "ACTION_1": 0, "ACTION_2": 0, "ACTION_3": 0, "ACTION_4": 0, "ACTION_5": 0, "ACTION_6": 0, "ACTION_7": 0, "ACTION_8": 0,
    "ACTION_9": 0, "ACTION_10": 0, "ACTION_11": 0,  "ACTION_12": 0, "ACTION_13": 0, "ACTION_14": 0, "ACTION_15": 0,
    "TEMP_PLUIE": 10.0, "CHROMATO": 0, "EV_VIDANGE_ECORIUM": 0, "VIDANGE_CANIVEAU": 0, "EV_VIDANGE_CLIM": 0



L'API ECOLAB permet de connaître l'état des cellules climatiques par appel de méthodes classiques.
La réponse aux différentes questions sera au format JSON.
Cette API permettra de développer une interface Web avec le résumé de tous les ECOLAB.

La cellule climatique est régulée par différents paramètres :
- Température
- Humidité / poids d'eau
- Concentration CO2

Les paramètres à gérer sont les suivants :
- Numéro de pas
- Températures
- Humidités
- CO2

