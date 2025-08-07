# churn-waze-prediction
Ce projet vise à créer un modèle de machine learning capable de prédire les utilisateurs qui risquent de cesser d'utiliser l'application Waze (churn). L'objectif est de permettre à l'entreprise de mettre en place des stratégies de rétention ciblées pour fidéliser ses utilisateurs.

---

### 🔍 1. Préparation et Traitement des Données

* **Analyse Exploratoire des Données (AED)** : Une analyse des données a été réalisée pour comprendre les caractéristiques des utilisateurs.
* **Création de Caractéristiques (Feature Engineering)** : De nouvelles variables ont été créées pour enrichir le modèle, telles que le pourcentage de sessions sur le dernier mois, l'indication d'un conducteur professionnel, la moyenne de sessions par jour, etc.
* **Encodage des Variables Catégorielles** : Les variables non numériques (`label` et `device`) ont été transformées en formats compréhensibles pour le modèle.
* **Division du Dataset** : Le jeu de données a été scindé en trois parties pour l'entraînement (60%), la validation (20%) et le test (20%).

---

### 🌲 2. Modèles Évalués

Deux modèles basés sur les arbres de décision ont été choisis pour leur capacité à gérer des données complexes et des interactions non linéaires :
* **Random Forest**
* **XGBoost**

---

### ⚙️ 3. Ajustement du Seuil de Classification

Un ajustement du seuil de classification a été réalisé pour améliorer les performances du modèle. Initialement, les modèles utilisent un seuil par défaut de **0.5**. Pour maximiser le compromis entre la **précision** et le **rappel**, un seuil optimal a été recherché sur l'ensemble de validation en maximisant le **F1-score**.

---

### 📊 4. Résultats et Analyse

Les modèles ont été évalués sur l'ensemble de test, en utilisant d'abord le seuil par défaut (0.5), puis le seuil optimisé.

#### ✅ Seuil par défaut (0.5)

| Modèle | Précision | Rappel | F1-score | Accuracy | ROC AUC |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Random Forest** | 0.314 | 0.650 | 0.424 | 0.686 | 0.735 |
| **XGBoost** | 0.303 | 0.713 | 0.425 | 0.658 | 0.733 |

#### 🎯 Après optimisation du Seuil

| Modèle | Seuil Optimal | Précision | Rappel | F1-score | Accuracy | ROC AUC |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Random Forest** | 0.524 | 0.330 | 0.603 | 0.427 | 0.713 | 0.735 |
| **XGBoost** | 0.508 | 0.311 | 0.689 | 0.429 | 0.674 | 0.733 |

#### Analyse Comparative

L'ajustement du seuil a permis d'améliorer la précision et l'accuracy des deux modèles. En se concentrant sur le F1-score, qui est une mesure d'équilibre entre la précision et le rappel, on observe une légère amélioration pour les deux modèles.

* **Random Forest** : L'optimisation du seuil a légèrement amélioré la précision et l'accuracy, avec une légère baisse du rappel. Le F1-score reste stable.
* **XGBoost** : L'optimisation a permis d'améliorer la précision, le F1-score et l'accuracy, avec une légère baisse du rappel.

---

### 5. Conclusion et Perspectives

L'objectif principal était de trouver le meilleur compromis entre la précision (limiter les faux positifs) et le rappel (détecter un maximum de churners potentiels).

Le choix du modèle dépendra de l'objectif métier :
* Si l'entreprise souhaite **maximiser le rappel** pour ne manquer aucun utilisateur à risque (même si cela génère plus de faux positifs), un seuil plus bas pourrait être utilisé.
* Si elle préfère **limiter les faux positifs** pour ne pas dépenser de ressources inutilement, un seuil légèrement plus élevé (proche de l'optimal) est plus approprié.

En ajustant le seuil, nous avons un levier puissant pour adapter le modèle aux priorités de l'entreprise, sans avoir à modifier le modèle en profondeur.

Pour améliorer ce projet, il serait intéressant de :
* Tester des techniques d'optimisation du seuil plus avancées, en tenant compte des coûts métier.
* Évaluer d'autres modèles ou des techniques d'**ensemble learning**.
* Développer une interface pour le suivi en continu des performances en production.

---

### 6. Code et Ressources

Le code source complet de ce projet, y compris l'implémentation de l'ajustement du seuil et les visualisations associées (courbes ROC et Precision-Recall), est disponible sur ce dépôt GitHub.

J'espère que cette version te plaît ! Elle est prête à être déposée sur ton portfolio. 😊

