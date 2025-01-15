
Le but des templates est de normaliser :
- l'arborescence des données ;
- l'écriture des programmes ;
- 

## Arborescence expérience
L'arborescence d'une expérience est la suivante :
```
Experience
├── Climates
│   ├── Climat_xxxx_01.csv
│   ├── Climat_xxxx_02.csv
│   └── ...
├── Config
│   ├── res-used.json
│   └── ...
├── DATA
│   ├── AcqCtrl
│   │   ├── YYYY-mm-dd_HH-MM-SS_Instrum-xxxxx.csv
│   │   └── ...
│   ├── Logs
│   │   ├── YYYY-mm-dd_HH-MM-SS_App-xxxx.log
│   │   ├── YYYY-mm-dd_HH-MM-SS_App-xxxx.log.1
│   │   ├── YYYY-mm-dd_HH-MM-SS_App-xxxx.log.2
│   │   └── ...
│   ├── Processed
│   │   ├── Step-1
│   │   │   ├── ...
│   │   │   └── ...
│   │   ├── Step-2
│   │   │   ├── ...
│   │   │   └── ...
│   │   └── Step-X
│   │       ├── ...
│   │       └── ...
│   └── Supervison
│      ├── ECOLAB-X
│      │   ├── CELL-1
│      │   │   ├── YYYY-mm-dd_HH-MM-SS_EXC1.csv
│      │   │   └── ...
│      │   ├── CELL-2
│      │   │   ├── YYYY-mm-dd_HH-MM-SS_EXC2.csv
│      │   │   └── ...
│      │   └── CELL-3
│      │       ├── YYYY-mm-dd_HH-MM-SS_EXC3.csv
│      │       └── ...
│      └── ...
├── Doc
│   ├── Global
│   │   ├── YYYY-mm-dd_Doc-xxxx.pdf
│   │   └── ...
│   ├── Hardware
│   │   ├── YYYY-mm-dd_Doc-xxxx.pdf
│   │   └── ...
│   └── Software
│       ├── YYYY-mm-dd_Doc-xxxx.pdf
│       └── ...
├── Programs
|   ├── Commons
|   │   ├── Devices
|   │   │   ├── Device_xxxx
|   |   │   │   ├── Config
|   │   │   │   |   ├── module_xxxx.json
|   |   │   │   │   └── ...
|   │   │   │   ├── module_xxxx.py
|   │   │   │   ├── module_xxxx_test.py
|   │   │   │   └── ...
|   │   │   └── ...
|   │   └── ...
|   ├── Config
|   │   ├── acqctrl.json
|   │   ├── data_process.json
|   │   ├── data_sync.json
|   │   └── ...
|   ├── data_process.py
|   ├── data_sync.py
|   ├── LICENSE
|   ├── main_engine.py
|   ├── module_xxxx.py
|   ├── ... .py
|   └── README.md
└── README.md
```
