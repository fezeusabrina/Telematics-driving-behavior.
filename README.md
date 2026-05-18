# Predictive Fleet Telematics & Driving Behavior

Ce projet est un Proof of Concept (PoC) visant à analyser des données de capteurs OBD (télématique) pour classifier le comportement de conduite.

## Stack Technique
- **Langage :** Python
- **Librairies :** Pandas (Data manipulation), Scikit-Learn (Machine Learning)

## Objectifs du projet
1. Traiter des données brutes issues de capteurs de véhicules.
2. Éviter le *Data Leakage* en retirant les variables de définition (vitesse, RPM) lors de l'entraînement.
3. Gérer un dataset fortement déséquilibré (Imbalanced classes) pour forcer la détection des conduites à risque (anomalies).

## Modèle utilisé
- Algorithme : Random Forest Classifier.
- Optimisation : Utilisation de `class_weight='balanced'` pour pallier le manque de données sur la classe "Conduite Agressive", permettant de faire passer le rappel (recall) de 0% à 50% sur cette classe minoritaire critique.

- ##  Évolution Jour 2 : Deep Learning (LSTM)
Pour capturer la nature temporelle des données de conduite, un réseau de neurones récurrents (LSTM) a été implémenté via **TensorFlow/Keras**.

- **Approche :** Création de séquences temporelles (fenêtres glissantes de 5 pas de temps) pour donner une "mémoire" au modèle.
- **Résultat :** Le LSTM a surperformé le Random Forest sur la détection des anomalies critiques. Sur la classe ultra-minoritaire "Conduite Agressive" (4 cas sur 20 000), le modèle a atteint un **rappel (recall) de 75 %**, prouvant l'importance de l'analyse séquentielle (historique des capteurs) par rapport à une analyse instantanée.
