# projet_fabric_data_rh
pipeline avec fabric


🏗️ Architecture

Bronze Layer : Ingestion brute des fichiers source

Silver Layer : Transformation et nettoyage des données

Gold Layer : Agrégation et préparation pour l'analyse

Monitoring : Suivi des exécutions et logs dans monitoring.orchestration

📘 Notebooks du projet

Notebook

Rôle

notebook_init_folder_lakehouse

Initialisation des dossiers dans le Lakehouse

notebook_init_table

Création des tables Bronze, Silver, Gold

notebook_function

Contient les fonctions réutilisables

notebook_load_data

Ingestion des fichiers source vers Bronze

notebook_orchestration

Orchestration globale du pipeline

notebook_init_monitoring_table

Initialisation des tables de monitoring

📂 Exemple de configuration YAML

tables_gold:
  - name: gold_employee
    target: lakehouse_gold.gold_employee
    sources:
      - name: employee
        source_path: "Files/employee/inbound/"
      - name: education_level
        source_path: "Files/education_level/inbound/"

🛠️ Technologies Utilisées

Microsoft Fabric (Lakehouse, Notebooks, Spark Pools)

PySpark & Delta Lake

mssparkutils (exécution de notebooks, gestion des fichiers)

YAML (Configuration des pipelines)

Logging et monitoring via monitoring.orchestration

📌 Comment exécuter le pipeline

Exécuter l'initialisation : notebook_init_folder_lakehouse, notebook_init_table

Lancer l'orchestration principale : notebook_orchestration

Surveiller les logs : monitoring.orchestration
