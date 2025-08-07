# churn-waze-prediction-
# 🛰️ Prédiction du Churn Utilisateur – Waze

Ce projet a pour objectif de développer un modèle de machine learning capable de prédire quels utilisateurs risquent de **cesser d’utiliser l’application Waze**. Une telle prédiction permettrait à l’entreprise de cibler efficacement ses actions de **fidélisation**.

---

## 🔍 1. Préparation et Traitement des Données

- **Analyse exploratoire** : Étude des comportements utilisateurs.
- **Feature engineering** :
  - % de sessions sur le dernier mois
  - Indication conducteur professionnel
  - Sessions moyennes par jour, etc.
- **Encodage des variables catégorielles** : `label`, `device` → variables numériques.
- **Split des données** :
  - **Entraînement** : 60%
  - **Validation** : 20%
  - **Test** : 20%

---

## 🌲 2. Modèles Évalués

Deux modèles basés sur les **arbres de décision** ont été comparés :

- `Random Forest`
- `XGBoost`

Ces modèles sont performants pour gérer des interactions complexes et des données non linéaires.

---

## ⚙️ 3. Ajustement du Seuil de Classification

Par défaut, les modèles utilisent un seuil de 0.5.  
Un **ajustement du seuil** a été réalisé pour maximiser le **F1-score** sur l’ensemble de validation, et donc améliorer le compromis **précision / rappel**.

---

## 📊 4. Résultats

### ✅ Seuil par Défaut (0.5)

| Modèle         | Précision | Rappel | F1-score | Accuracy | ROC AUC |
|----------------|-----------|--------|----------|----------|---------|
| Random Forest  | 0.314     | 0.650  | 0.424    | 0.686    | 0.735   |
| XGBoost        | 0.303     | 0.713  | 0.425    | 0.658    | 0.733   |

### 🎯 Seuil Optimisé

| Modèle         | Seuil     | Précision | Rappel | F1-score | Accuracy | ROC AUC |
|----------------|-----------|-----------|--------|----------|----------|---------|
| Random Forest  | 0.524     | 0.330     | 0.603  | 0.427    | 0.713    | 0.735   |
| XGBoost        | 0.508     | 0.311     | 0.689  | 0.429    | 0.674    | 0.733   |

### 📌 Analyse Comparative

- **Random Forest** :
  - + Précision, + Accuracy, F1-score stable
  - Légère baisse du rappel
- **XGBoost** :
  - + Précision, + F1-score, + Accuracy
  - Baisse modérée du rappel

---

## 🧠 5. Conclusion & Perspectives

Le **choix du seuil** dépend des objectifs métiers :

- 🎯 **Maximiser le rappel** : mieux identifier tous les churners (même avec des faux positifs).
- 💰 **Maximiser la précision** : éviter d’agir inutilement sur des utilisateurs fidèles.

Ajuster le seuil est un **levier stratégique** : il permet d’adapter le modèle aux besoins sans le modifier.

### 🔄 Améliorations possibles

- Optimisation du seuil selon des **coûts métier**
- Tester d’autres modèles / techniques d’**ensemble learning**
- Créer une **interface de monitoring** pour la mise en production

---

## 💻 6. Code & Ressources

Le code source du projet est disponible dans ce dépôt :
- Préparation des données
- Entraînement des modèles
- Optimisation du seuil
- Visualisations ROC et Precision-Recall

> 👉 *N'hésite pas à explorer le code et à proposer des améliorations via issues ou pull requests !*

---

