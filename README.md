Projet Fabric data RH

Pipeline de transformation de données RH avec Microsoft Fabric (Lakehouse)
Ce projet met en œuvre la méthode médaillon (Bronze → Silver → Gold) pour construire un pipeline de traitement de données RH à l’aide de notebooks Spark orchestrés dynamiquement via YAML, avec un système de monitoring intégré.


Architecture du pipeline

                ┌─────────────┐
                │  Données    │
                │  brutes     │
                └────┬────────┘
                     ↓
                ┌─────────────┐
                │   Bronze    │ ← Ingestion des fichiers source (.csv)
                └────┬────────┘
                     ↓
                ┌─────────────┐
                │   Silver    │ ← Nettoyage et normalisation
                └────┬────────┘
                     ↓
                ┌─────────────┐
                │    Gold     │ ← Agrégation pour analyse métier
                └─────────────┘
                

Notebook	Rôle
notebook_init_folder_lakehouse:	Initialisation des dossiers dans le Lakehouse
notebook_init_table:	Création des tables Bronze, Silver, Gold
notebook_function:	Fonctions réutilisables (via %run)
notebook_load_data:	Ingestion des fichiers source vers Bronze
notebook_orchestration:	Orchestration dynamique des étapes du pipeline (inputs YAML)
notebook_init_monitoring_table:	Initialisation des tables de monitoring

Orchestration dynamique
Le pipeline est orchestré via un notebook principal qui lit des fichiers YAML pour :

Connaitre les sources à traiter

Déterminer le schéma cible et les transformations

Définir les tables Gold à générer à partir de multiples sources


Suivi et Monitoring
Un système de logs et monitoring est intégré au pipeline via des tables de monitoring :

Suivi de l’état des étapes d’exécution

Journalisation des erreurs

Temps d’exécution

Monitoring centralisé dans le notebook monitoring.orchestration


Comment exécuter le pipeline
Initialiser le lac et les tables :

notebook_init_folder_lakehouse

notebook_init_table

notebook_init_monitoring_table

Lancer l’orchestration principale :

notebook_orchestration

Surveiller les exécutions :

monitoring.orchestration ou via les tables de monitoring
