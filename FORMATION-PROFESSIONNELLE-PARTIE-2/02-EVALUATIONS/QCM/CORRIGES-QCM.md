# CORRIGES DES QCM
## PIPELINES ETL BATCH AWS

> **IMPORTANT** : Consulter uniquement après avoir complété les QCM

---

# MODULE 1 - ETL BATCH VS STREAMING

| Question | Réponse | Explication |
|----------|---------|-------------|
| 1 | **B** | Batch : latence minutes-heures, Streaming : < 1 seconde |
| 2 | **B** | Rapport quotidien = batch quotidien (pas besoin temps réel) |
| 3 | **C** | Parquet réduit typiquement 70% la taille vs CSV |
| 4 | **B** | Partitionnement réduit 90%+ données scannées |
| 5 | **C** | Architecture Lambda = Speed (streaming) + Batch layer |
| 6 | **B** | Fraude bancaire nécessite streaming temps réel |
| 7 | **B** | Step Functions, Glue, Athena, S3 pour ETL batch |
| 8 | **B** | Snappy = meilleur compromis vitesse/compression analytics |
| 9 | **C** | Data Lake stocke tous formats (structurés, semi, non) |
| 10 | **B** | Data Warehouse alimenté par pipeline ETL batch |

---

# MODULE 2 - AWS STEP FUNCTIONS

| Question | Réponse | Explication |
|----------|---------|-------------|
| 1 | **B** | Step Functions orchestre workflows serverless |
| 2 | **B** | 7 types d'états disponibles |
| 3 | **C** | Choice State pour logique conditionnelle |
| 4 | **B** | Map State itère sur array |
| 5 | **B** | `.sync` = Step Functions attend fin tâche |
| 6 | **B** | Retry et Catch dans définition JSON états |
| 7 | **A** | Pricing basé sur nombre transitions d'états |
| 8 | **B** | Map State traite array en parallèle |
| 9 | **B** | Workflow Studio = design visuel drag-and-drop |
| 10 | **B** | Parallel State exécute branches simultanément |

---

# MODULE 3 - AWS GLUE & ATHENA

| Question | Réponse | Explication |
|----------|---------|-------------|
| 1 | **B** | Glue Catalog stocke métadonnées, pas données |
| 2 | **B** | Athena = requêtes SQL serverless sur S3 |
| 3 | **B** | EXTERNAL = données dans S3, métadonnées dans Glue |
| 4 | **B** | Athena facturé sur volume scanné (5 USD/TB) |
| 5 | **B** | CTAS crée table + charge données en une commande |
| 6 | **A** | Crawler scan S3 et infère schema automatiquement |
| 7 | **B** | Vue = requête SQL réexécutée, pas de stockage |
| 8 | **A** | SHOW TABLES liste tables du catalogue Glue |
| 9 | **B** | MSCK REPAIR auto-découvre partitions manquantes |
| 10 | **A** | Athena supporte SQL standard avec JOIN |

---

# MODULE 4 - OPTIMISATION PARQUET

| Question | Réponse | Explication |
|----------|---------|-------------|
| 1 | **B** | Parquet = format columnar (colonnes) |
| 2 | **B** | Snappy = meilleur compromis pour analytics interactives |
| 3 | **C** | Taille optimale fichier Parquet : 128 MB - 1 GB |
| 4 | **A** | Partition pruning scan uniquement partitions nécessaires |
| 5 | **B** | 5 GB/jour = partition quotidienne recommandée |
| 6 | **B** | Gzip : meilleur ratio mais plus lente que Snappy |
| 7 | **A** | CTAS regroupe petits fichiers (compaction) |
| 8 | **B** | ORC aussi columnar, optimisé Hive/Spark |
| 9 | **C** | Parquet+Snappy économise typiquement 70% vs CSV |
| 10 | **C** | Parquet + Snappy + Partitions = optimal analytics |

---

## STATISTIQUES

| Module | Questions | Note Minimale | Note Moyenne Attendue |
|--------|-----------|---------------|----------------------|
| Module 1 | 10 | 6/10 | 7-8/10 |
| Module 2 | 10 | 6/10 | 7-8/10 |
| Module 3 | 10 | 6/10 | 8-9/10 |
| Module 4 | 10 | 6/10 | 7-8/10 |
| **TOTAL** | **40** | **24/40** | **30-32/40** |

---

## BAREME GLOBAL

| Score | Appréciation | Action |
|-------|--------------|--------|
| **36-40** | Excellent | Passer aux questions développement |
| **30-35** | Très bien | Approfondir points faibles |
| **24-29** | Bien | Réviser modules < 7/10 |
| **20-23** | Passable | Révision approfondie |
| **< 20** | Insuffisant | Réétudier tous modules |

---

## CONSEILS POST-EVALUATION

**Si score < 24/40** :
1. Réviser modules concernés
2. Refaire QCM après étude
3. Consulter ressources AWS

**Si score 24-29/40** :
1. Identifier questions manquées
2. Réviser sections spécifiques
3. Pratiquer avec AWS Free Tier

**Si score 30-35/40** :
1. Bon niveau validé
2. Faire questions développement
3. Projets pratiques

**Si score 36-40/40** :
1. Excellente maîtrise
2. Questions développement complexes
3. Préparation certification AWS

