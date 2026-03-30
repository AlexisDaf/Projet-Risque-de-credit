# 💳 Analyse du risque de défaut de crédit

## 🎯 Objectif du projet

Ce projet vise à analyser et prédire le risque de défaut de crédit à partir de données clients.

L’objectif n’est pas uniquement de construire un modèle prédictif, mais également de comprendre les principaux facteurs de risque dans une perspective métier (scoring crédit).

---

## 📊 Données

Le projet repose sur le dataset **Home Credit Default Risk** (Kaggle), comprenant :

* Informations démographiques et financières des clients
* Historique de crédit et prêts précédents
* Comportement de paiement

La variable cible indique si un client a rencontré des difficultés de remboursement.

---

## 🛠️ Méthodologie

### 🔹 Préparation des données

* Nettoyage et traitement des valeurs manquantes
* Transformation des variables
* Feature engineering (ratio dette / revenu, indicateurs financiers)

### 🔹 Analyse exploratoire

* Analyse du déséquilibre des classes (~8% de défaut)
* Identification des facteurs de risque (âge, revenu, endettement)
* Construction d’indicateurs économiques (DTI)

### 🔹 Modélisation

* Modèle de régression logistique
* Évaluation avec la métrique ROC-AUC
* Intégration progressive de variables comportementales (historique de crédit)

---

## 📈 Résultats

* Modèle initial (variables financières) : **ROC-AUC ≈ 0,59**
* Modèle enrichi (avec historique de crédit) : **ROC-AUC ≈ 0,66**

👉 L’ajout des variables comportementales améliore significativement la performance du modèle.

---

## 💡 Insights clés

* Les clients jeunes et fortement endettés présentent un risque plus élevé
* Le ratio dette / revenu est un indicateur central du risque
* L’historique de crédit joue un rôle déterminant dans la prédiction
* Les variables financières seules sont insuffisantes pour un modèle performant

---

## ⚠️ Limites

* Nombre limité de variables utilisées
* Approche volontairement simplifiée
* Performance prédictive modérée

👉 Le projet met l’accent sur la compréhension plutôt que l’optimisation.

---

## 🚀 Pistes d’amélioration

* Enrichissement des variables via du feature engineering orienté métier
* Utilisation de modèles plus avancés (Random Forest, Gradient Boosting)
* Amélioration de l’interprétabilité du modèle

---

## 🧰 Outils utilisés

* Python (Pandas, NumPy, Scikit-learn, Matplotlib)
* Jupyter Notebook

---

## 📌 Conclusion

Ce projet permet de reproduire les principales étapes d’un cas d’usage classique en finance : l’évaluation du risque de crédit.

Il met en évidence l’importance de combiner modélisation statistique et compréhension métier pour construire des outils d’aide à la décision pertinents.

---
