# GLOSSAIRE TECHNIQUE - ETL BATCH

---

# A

**ATHENA**  
Service SQL serverless AWS pour requêter données dans S3. Pricing basé sur volume scanné.

**AVRO**  
Format de sérialisation row-based avec schema. Utilisé pour streaming et evolution schema.

---

# B

**BATCH PROCESSING**  
Traitement de données par lots à intervalles réguliers (horaire, quotidien).

**BUCKETING**  
Division données en buckets basée sur hash d'une colonne. Optimise JOIN.

---

# C

**COLUMNAR FORMAT**  
Format stockant données par colonnes (Parquet, ORC) vs lignes (CSV, JSON).

**COMPACTION**  
Regroupement de nombreux petits fichiers en fichiers plus gros pour performance.

**COMPRESSION**  
Réduction taille données. Algorithmes : Snappy (rapide), Gzip (ratio élevé), Zstd.

**CRAWLER (Glue)**  
Processus automatique scannant S3 pour découvrir et cataloguer données.

**CTAS**  
Create Table As Select. Crée table et charge données en une requête SQL.

---

# D

**DATA CATALOG**  
Registre centralisé de métadonnées (tables, schemas, locations).

**DATA LAKE**  
Stockage centralisé données brutes tous formats. Typiquement S3.

**DATA WAREHOUSE**  
Base de données optimisée pour analytics. Ex: Redshift, Snowflake.

**DDL**  
Data Definition Language. SQL pour définir structures (CREATE, DROP, ALTER).

**DML**  
Data Manipulation Language. SQL pour manipuler données (SELECT, INSERT, UPDATE).

---

# E

**ETL**  
Extract, Transform, Load. Processus traitement données.

**EXTERNAL TABLE**  
Table Glue où données restent dans S3. Opposite : managed table.

---

# G

**GLUE**  
Service AWS de catalogue données et jobs ETL Spark/Python.

**GLUE JOB**  
Script ETL Spark ou Python exécuté par Glue pour transformer données.

---

# M

**MAP STATE**  
État Step Functions itérant sur array pour traiter chaque élément.

**MSCK REPAIR TABLE**  
Commande SQL découvrant automatiquement partitions dans S3.

---

# O

**ORC**  
Optimized Row Columnar. Format columnar pour Hive/Spark.

**ORCHESTRATION**  
Coordination et séquencement d'étapes multiples. Ex: Step Functions.

---

# P

**PARALLEL STATE**  
État Step Functions exécutant branches simultanément.

**PARQUET**  
Format columnar open-source optimisé pour analytics Big Data.

**PARTITION**  
Subdivision données basée sur valeurs colonnes (ex: year=2020/month=01/).

**PARTITION PRUNING**  
Optimisation scannant uniquement partitions pertinentes pour requête.

---

# R

**RETRY**  
Mécanisme Step Functions retentant automatiquement tâche échouée.

**ROW-BASED FORMAT**  
Format stockant données ligne par ligne (CSV, JSON, Avro).

---

# S

**SERVERLESS**  
Modèle où infrastructure gérée automatiquement par provider.

**SNAPPY**  
Algorithme compression rapide, compromis optimal pour analytics.

**STATE MACHINE**  
Workflow Step Functions défini par états et transitions.

**STEP FUNCTIONS**  
Service AWS orchestration workflows serverless.

---

# T

**TASK STATE**  
État Step Functions exécutant une action (Lambda, Athena, Glue).

**TBLPROPERTIES**  
Propriétés table Glue (ex: skip.header.line.count pour CSV).

---

# V

**VIEW (Vue SQL)**  
Requête SQL sauvegardée réexécutée à chaque accès. Pas de stockage.

---

# W

**WORKFLOW**  
Séquence ordonnée d'étapes de traitement.

**WORKGROUP (Athena)**  
Groupe logique isolation ressources et contrôle coûts requêtes.

---

# Z

**ZSTD**  
Algorithme compression Zstandard. Équilibre entre ratio et vitesse.

