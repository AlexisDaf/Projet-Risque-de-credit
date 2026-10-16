# Scoring du risque de défaut de crédit — Home Credit Default Risk

Projet de **classification supervisée**, privilégiant un modèle de **régression logistique interprétable**, l’agrégation d’historiques et la comparaison progressive des variables explicatives. Le but est pédagogique : découvrir les mécanismes du risque de crédit, sans prétendre disposer d'un système opérationnel de scoring bancaire.

## Données

Le projet utilise quatre CSV du jeu de données public **Home Credit Default Risk (Kaggle)** : `application_train.csv`, `bureau.csv`, `previous_application.csv`, `installments_payments.csv`.

Ces fichiers ne sont pas inclus dans ce dépôt. Pour reproduire les résultats, **placer les quatre CSV dans le même dossier d'exécution que le notebook**, puis exécuter toutes ses cellules.

## Méthodologie

- **Exploration** : taux de défaut, âge, revenu, charge d’annuité par rapport au revenu, relations descriptives.
- **Feature engineering** : statistiques agrégées par client issues des historiques de crédits, anciennes demandes et paiements avec date observée.
- **Prétraitement** : imputation médiane et standardisation dans un `Pipeline` Scikit-learn (apprentissage seulement sur les données d'entraînement).
- **Évaluation** : mêmes clients dans les ensembles **entraînement (60 %) / validation (20 %) / test (20 %)**, avec stratification ; choix sur validation, évaluation finale sur test indépendant.
- **Classification** : régression logistique, avec test de `class_weight='balanced'`.

## Résultats obtenus sur les fichiers Kaggle fournis

| Variables utilisées | ROC-AUC validation |
|---|---:|
| Âge, revenu, charge d'annuité | 0,5888 |
| + Historique `bureau` | 0,6179 |
| + Demandes précédentes | 0,6379 |
| + Paiements observés | 0,6506 |
| + Pondération des classes (`balanced`) | 0,6518 |

**Test final (61 503 clients) : ROC-AUC = 0,6508 et Average Precision = 0,1450** (prévalence du défaut ≈ 8,07 %). Au seuil illustratif de 0,50, précision sur la classe positive de 0,12 et rappel de 0,59. Les résultats affichés sont ceux d'une exécution complète sur les CSV fournis, avec le code corrigé.

## Points d'attention

- Le ratio annuité/revenu n'est qu'un **proxy** et non un véritable ratio global dette/revenu (DTI).
- Le dataset est **déséquilibré** : la ROC-AUC doit être complétée par des métriques telles que l'Average Precision, la précision et le rappel.
- Le choix de la pondération apporte une amélioration minime sur la validation ; son avantage n'est pas démontré au-delà de cette expérience.
- Les historiques doivent être audités pour s’assurer que les informations utilisées étaient **disponibles à la date de la demande de crédit** ; le notebook ne prouve pas à lui seul l'absence de fuite temporelle.
- Une utilisation opérationnelle nécessiterait notamment calibration, validation temporelle, choix de seuil selon les coûts métiers, analyse de stabilité, d'équité et conformité réglementaire.

## Technologies

Python • Pandas • NumPy • Scikit-learn • Matplotlib • Jupyter

## Reproduction

Dépendances usuelles : `pip install pandas numpy scikit-learn matplotlib jupyter`

Télécharger les données Home Credit depuis Kaggle, placer les CSV dans le dossier de travail, ouvrir **`Scoring_credit_Home_Credit_final.ipynb`** et exécuter toutes les cellules.
