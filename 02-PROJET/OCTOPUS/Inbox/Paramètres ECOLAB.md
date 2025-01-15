## Fichier de consignes
Le fichier de consignes est au format **Excel** (.xls), il comportent **plusieurs** feuilles de calcul :
- Automate (nécessaire) : valeurs prises en compte par l'automate de la cellule.
- Programmation (nécessaire) : valeurs de consignes de climat à dérouler.
- Graph1 (optionnel) :
- INFOS (optionnel) :
- Config (optionnel) :

### Feuille "Programmation"
Les paramètres de la feuille de réglage du climat sont les suivants :

| Paramètre                  | Type   | Range          | Description                                                               |
| -------------------------- | ------ | -------------- | ------------------------------------------------------------------------- |
| No_Pas                     | Entier | 1 ..           | Numéro de pas, un pas correspond à 5 min.                                 |
| mn                         | Entier | 5 .. 60        | Numéro de minutes.                                                        |
| secondes                   | Entier | 300 ..         | Compteur de secondes.                                                     |
| no h                       | Entier | 0 ..           | Compteur d'heures.                                                        |
| no jours                   | Entier | 1 ..           | Compteur de jours.                                                        |
| TEMP_CEL                   | Float  | N/A            | Température en °C de la cellule.                                          |
| REGUL_ECORIUM              | Entier | 0 ou 1         | Active (1) ou désactive (0) la régulation de l'ECORIUM.                   |
| T_ECOR_FOND                | Float  | N/A            | Température en °C du fond de l'ECORIUM.                                   |
| T_ECOR_INF                 | Float  | N/A            | Température en °C du milieu de l'ECORIUM.                                 |
| T_ECOR_SUP                 | Float  | N/A            | Température en °C du haut de l'ECORIUM.                                   |
| REGUL_HYG                  | Entier | 0 ou 1         | Active (1) ou désactive (0) la régulation de l'humidité de la cellule.    |
| HYG_CEL                    | Float  | 0,0 .. 100,0   | Valeur en % de l'humidité relative de la cellule.                         |
| REGUL_PRESSION             | Entier | 0 ou 1         | Active (1) ou désactive (0) la régulation de la pression dans la cellule. |
| PRESSION                   | Float  | ?              | Valeur de la pression souhaitée dans la cellule.                          |
| REGUL_C                    | Entier | 0 ou 1         | Active (1) ou désactive (0) la régulation du CO2 dans la cellule.         |
| C                          | Float  | 0,0 .. 20000,0 | Concentration en ppm du CO2 dans la cellule.                              |
| REGUL_O                    | Entier | 0 ou 1         | Active (1) ou désactive (0) la régulation du O2 dans la cellule.          |
| O                          | Float  | ?              | Concentration en % (?) du O2 dans la cellule.                             |
| REGUL_N                    | Entier | 0 ou 1         |                                                                           |
| N                          |        |                |                                                                           |
| REGUL_X                    | Entier | 0 ou 1         |                                                                           |
| X                          |        |                |                                                                           |
| HAUT_ECOLUX                |        |                |                                                                           |
| INT_ECOLUX                 |        |                |                                                                           |
| CONFIG_ECOLUX              |        |                |                                                                           |
| INT_PLUIE                  |        |                |                                                                           |
| VITESSE_VENT               |        |                |                                                                           |
| VENT_LATERAL_UN            |        |                |                                                                           |
| VENT_LATERAL_DEUX          |        |                |                                                                           |
| VENT_LATERAL_TROIS         |        |                |                                                                           |
| VENT_LATERAL_QUATRE        |        |                |                                                                           |
| INT_VENT_LAT               |        |                |                                                                           |
| RENO_AIR                   | Entier | 0 ou 1         |                                                                           |
| EVENT                      |        |                |                                                                           |
| Chromato                   | Entier | 0 ou 1         |                                                                           |
| CONFIG_MES_INCUB           |        |                |                                                                           |
| ACTION_1 .. ACTION_15      |        |                |                                                                           |
| TEMP_PLUIE                 |        |                |                                                                           |
| CHROMATO                   |        |                |                                                                           |
| EV_VIDANGE_ECORIUM         |        |                |                                                                           |
| VIDANGE_CANIVEAU           |        |                |                                                                           |
| EV_VIDANGE_CLIM            |        |                |                                                                           |
| MAX T MIN T :              |        |                |                                                                           |
| MAX HR MIN HR :            |        |                |                                                                           |
| tests valeurs Temp         |        |                |                                                                           |
| tests valeurs Hum          |        |                |                                                                           |
| MARCHE                     | Entier | 0 ou 1         |                                                                           |
| HYG_Corrigée pour Temp < 0 |        |                |                                                                           |
| Min Temp                   |        |                |                                                                           |
| Max Temp                   |        |                |                                                                           |
| Temp Mode Mesure           |        |                |                                                                           |
