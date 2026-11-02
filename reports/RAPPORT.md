# Rapport — Atelier Git + DVC + MLflow

**Projet :** classification du dataset Iris avec RandomForest et KNN  
**Dépôt GitHub :** https://github.com/tahalrh/atelier-mlops

---

## 1. Objectif

Ce TP montre comment construire un projet Machine Learning versionné et reproductible avec :

- **Git** pour versionner le code ;
- **DVC** pour versionner les données et le pipeline ;
- **MLflow** pour suivre les expériences et comparer les modèles.

---

## 2. Versionnement Git

![Historique Git](git_log.png)

**Description :** l’historique Git montre les différentes étapes du projet, les branches `main` et `develop`, ainsi que les tags `v1.0` et `v2.0`.

---

## 3. Données et pipeline DVC

![Pipeline DVC](dvc_dag.png)

**Description :** les datasets Iris et Wine sont versionnés avec DVC. Le pipeline contient une étape `train` qui produit le modèle et les métriques.

---

## 4. Dépôt GitHub

![Dépôt GitHub](github_repo.png)

**Description :** le projet est publié sur GitHub avec deux branches et deux tags. Le dépôt contient le code, les fichiers DVC, les paramètres et les résultats.

---

## 5. Comparaison RandomForest et KNN

![Comparaison RandomForest et KNN](mlflow_comparaison.png)

**Description :** comparaison de deux runs MLflow. KNN obtient une accuracy de **1,0**, contre **0,9333** pour le RandomForest baseline.

---

## 6. Comparaison des trois expériences

![Comparaison de trois runs](mlflow_3_runs.png)

**Description :** comparaison de trois runs :

- RandomForest 100 arbres / profondeur 5 : **0,9333**
- RandomForest 200 arbres / profondeur 8 : **0,9**
- KNN avec 5 voisins : **1,0**

Ce résultat montre qu’augmenter le nombre d’arbres et la profondeur ne garantit pas une meilleure accuracy.

---

## 7. Restauration de la version v1.0

![Restauration de la version v1.0](restauration_v1.png)

**Description :** retour au tag `v1.0` avec `git checkout v1.0` puis `dvc checkout`. Les métriques restaurées sont celles de la version baseline :

```text
accuracy = 0.93333
```

Le modèle rechargé prédit correctement la classe `setosa`.

---

## 8. Reproduction dans un clone

![Reproduction dans le clone](reproduction_clone.png)

**Description :** le projet a été cloné dans un autre dossier. Les données ont été récupérées avec `dvc pull`, puis le pipeline a été relancé avec `dvc repro --force`.

Les métriques retrouvées sont :

```text
accuracy = 0.9
f1_score = 0.89975
```

Cela montre que le projet est reproductible.

---

## 9. Résultats

| Modèle | Paramètres | Accuracy | F1-score |
|---|---|---:|---:|
| RandomForest | 100 arbres, profondeur 5 | 0,9333 | 0,9333 |
| RandomForest | 200 arbres, profondeur 8 | 0,9 | 0,89975 |
| KNN | 5 voisins | 1,0 | 1,0 |

---

## 10. Conclusion

Git permet de versionner le code, DVC permet de versionner les données et le pipeline, et MLflow permet de suivre et comparer les expériences.

La restauration d’une ancienne version et la reproduction du projet dans un clone fonctionnent correctement. Le pipeline est donc traçable, versionné et reproductible.
