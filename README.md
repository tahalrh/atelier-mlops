# Atelier Git + DVC + MLflow

Atelier indépendant consacré au versionnement du code, des données et du pipeline ML.

Ce dossier est **séparé du TP2 `mlops-tp2`** :

- dépôt Git dédié ;
- projet DVC dédié ;
- base MLflow dédiée (`mlflow.db`) ;
- expérience MLflow dédiée à cet atelier.

Le document de référence est :

`Atelier_Git_DVC_MLflow_MLOps.docx`

## Objectif

Construire un projet de classification Iris reproducible avec :

- Git pour le code ;
- DVC pour les données, les artefacts et le pipeline ;
- MLflow pour le suivi des expériences.

## Structure

```text
atelier-mlops/
├── data/
│   └── raw/
├── src/
├── models/
├── reports/
├── .gitignore
├── requirements.txt
├── params.yaml
├── README.md
└── Atelier_Git_DVC_MLflow_MLOps.docx
```

## Environnement

```powershell
cd C:\Users\HP\Desktop\atelier-mlops
.\.venv\Scripts\Activate.ps1
```

Installation si nécessaire :

```powershell
pip install -r requirements.txt
```

## Commandes de base

```powershell
python src/prepare_data.py
python src/train.py
mlflow ui --backend-store-uri sqlite:///mlflow.db
```

L'interface MLflow sera disponible sur `http://127.0.0.1:5000`.

## Initialisation déjà effectuée

- dossier du projet créé ;
- sous-dossiers `data/raw`, `src`, `models`, `reports` créés ;
- document Word copié ;
- environnement virtuel `.venv` créé ;
- dépendances installées ;
- dépôt Git initialisé ;
- DVC initialisé.

## Remarque MLflow

L'atelier utilise sa propre base `mlflow.db` dans ce dossier.  
Il ne faut pas lancer ces scripts depuis `mlops-tp2`, sinon les runs MLflow peuvent se mélanger avec ceux du TP2 et de `partie2`.
