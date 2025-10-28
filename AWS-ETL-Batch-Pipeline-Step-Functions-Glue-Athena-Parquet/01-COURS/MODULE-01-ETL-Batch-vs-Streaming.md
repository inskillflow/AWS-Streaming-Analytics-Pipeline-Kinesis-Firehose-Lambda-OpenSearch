# MODULE 1 - ETL BATCH VS STREAMING

**Durée** : 45 minutes  
**Niveau** : Fondamental  
**Objectifs** : Comprendre les différences entre ETL batch et streaming, savoir choisir

---

# 1. CONCEPTS ETL

## 1.1 Définition ETL

**ETL** = Extract, Transform, Load

```mermaid
graph LR
    E[EXTRACT<br/>Extraire données<br/>sources] --> T[TRANSFORM<br/>Transformer<br/>nettoyer, enrichir]
    T --> L[LOAD<br/>Charger<br/>dans destination]
    
    style E fill:#3498db,stroke:#2980b9,stroke-width:2px,color:#fff
    style T fill:#f39c12,stroke:#e67e22,stroke-width:2px,color:#fff
    style L fill:#27ae60,stroke:#229954,stroke-width:2px,color:#fff
```

| Phase | Description | Exemples |
|-------|-------------|----------|
| **Extract** | Récupération données depuis sources | CSV, bases de données, APIs, logs |
| **Transform** | Nettoyage, enrichissement, agrégation | Parsing, jointures, calculs, filtrage |
| **Load** | Chargement dans système cible | Data warehouse, data lake, base analytics |

---

## 1.2 ETL Batch vs ETL Streaming

```mermaid
graph TB
    subgraph BATCH["ETL BATCH - Traitement Par Lots"]
        B1[Données<br/>accumulées] -->|Périodique| B2[Traitement<br/>complet]
        B2 --> B3[Résultats<br/>différés]
    end
    
    subgraph STREAM["ETL STREAMING - Traitement Continu"]
        S1[Données<br/>continues] -->|Temps réel| S2[Traitement<br/>immédiat]
        S2 --> S3[Résultats<br/>instantanés]
    end
    
    style B1 fill:#34495e,stroke:#2c3e50,color:#ecf0f1
    style B2 fill:#f39c12,stroke:#e67e22,stroke-width:2px,color:#fff
    style B3 fill:#e74c3c,stroke:#c0392b,stroke-width:2px,color:#fff
    style S1 fill:#34495e,stroke:#2c3e50,color:#ecf0f1
    style S2 fill:#3498db,stroke:#2980b9,stroke-width:2px,color:#fff
    style S3 fill:#27ae60,stroke:#229954,stroke-width:2px,color:#fff
```

### Tableau Comparatif

| Critère | ETL BATCH | ETL STREAMING |
|---------|-----------|---------------|
| **Fréquence** | Périodique (horaire, quotidien) | Continu (temps réel) |
| **Latence** | Minutes à heures | < 1 seconde |
| **Volume traité** | Gros volumes par lot | Flux continu record par record |
| **Complexité** | Faible à moyenne | Moyenne à élevée |
| **Coût** | Prévisible (batch planifié) | Variable (basé sur flux) |
| **Technologies AWS** | Step Functions, Glue, Athena, EMR | Kinesis, Lambda, OpenSearch |
| **Format données** | Parquet, ORC, CSV (optimisé) | JSON, Avro (streaming) |
| **Cas d'usage** | Rapports quotidiens, BI, ML training | Monitoring, alertes, fraude temps réel |

---

# 2. ARCHITECTURE ETL BATCH

## 2.1 Architecture de Référence

```mermaid
flowchart TB
    subgraph SOURCES["SOURCES DE DONNEES"]
        DB[(Bases de<br/>données)]
        API[APIs<br/>externes]
        Files[Fichiers<br/>CSV/JSON]
    end
    
    subgraph ORCHESTRATION["ORCHESTRATION"]
        SF[Step Functions<br/>Workflow]
    end
    
    subgraph PROCESSING["TRAITEMENT"]
        Glue[AWS Glue<br/>Catalogue + ETL]
        Athena[Amazon Athena<br/>Requêtes SQL]
    end
    
    subgraph STORAGE["STOCKAGE"]
        S3Raw[S3<br/>Données brutes]
        S3Opt[S3<br/>Données optimisées<br/>Parquet]
    end
    
    DB --> S3Raw
    API --> S3Raw
    Files --> S3Raw
    
    S3Raw --> SF
    SF -->|Déclenche| Glue
    SF -->|Déclenche| Athena
    
    Glue --> S3Opt
    Athena --> S3Opt
    
    S3Opt -->|Requêtes| Athena
    
    style SF fill:#e91e63,stroke:#c2185b,stroke-width:2px,color:#fff
    style Glue fill:#9c27b0,stroke:#7b1fa2,stroke-width:2px,color:#fff
    style Athena fill:#ff9800,stroke:#f57c00,stroke-width:2px,color:#fff
    style S3Raw fill:#95a5a6,stroke:#7f8c8d,color:#2c3e50
    style S3Opt fill:#27ae60,stroke:#229954,stroke-width:2px,color:#fff
```

---

## 2.2 Services AWS pour ETL Batch

| Service | Rôle | Caractéristiques |
|---------|------|------------------|
| **AWS Step Functions** | Orchestration workflows | State machines, logique conditionnelle, retry automatique |
| **AWS Glue** | Catalogue de données + ETL | Métadonnées, schémas, crawlers, jobs Spark |
| **Amazon Athena** | Requêtes SQL sur S3 | Serverless, SQL standard, sans infrastructure |
| **Amazon S3** | Stockage data lake | Scalable, peu coûteux, formats multiples |
| **AWS Glue DataBrew** | Préparation données visuelle | No-code data prep |

---

# 3. AWS STEP FUNCTIONS - VUE D'ENSEMBLE

## 3.1 Concept de State Machine

**State Machine** = Workflow défini par états et transitions

```mermaid
stateDiagram-v2
    [*] --> Start
    Start --> CheckDB: Vérifier DB
    CheckDB --> CreateDB: DB n'existe pas
    CheckDB --> CheckTables: DB existe
    CreateDB --> CheckTables
    CheckTables --> CreateTables: Tables manquantes
    CheckTables --> InsertData: Tables existent
    CreateTables --> [*]
    InsertData --> [*]
    
    note right of CheckDB
        Choice State
        Logique conditionnelle
    end note
```

### Types d'États

| Type | Description | Usage |
|------|-------------|-------|
| **Task** | Exécute une action (invoke Lambda, requête Athena) | Traitement principal |
| **Choice** | Logique conditionnelle (if/else) | Routage workflow |
| **Parallel** | Exécution parallèle de branches | Traitement simultané |
| **Map** | Itération sur array | Traiter chaque élément |
| **Wait** | Pause temporelle | Attente délai |
| **Pass** | Passe données sans action | Debug, placeholder |
| **Succeed/Fail** | Termine avec succès/échec | Fin workflow |

---

## 3.2 Intégration Athena

Step Functions peut déclencher Athena de 2 façons :

**Synchrone (.sync)** :
- Step Functions attend la fin de la requête
- Retourne résultats
- Usage : Créer tables, vérifications

**Asynchrone** :
- Lance requête et continue
- Ne bloque pas le workflow
- Usage : Requêtes longues en background

---

# 4. AWS GLUE - CATALOGUE DE DONNEES

## 4.1 Architecture Glue

```mermaid
graph TB
    subgraph GLUE["AWS GLUE DATA CATALOG"]
        DB[Database<br/>nyctaxidb]
        T1[Table<br/>taxi_data_csv]
        T2[Table<br/>taxi_lookup_csv]
        T3[Table<br/>taxi_data_parquet]
        
        DB --> T1
        DB --> T2
        DB --> T3
    end
    
    subgraph S3["AMAZON S3"]
        Raw[Données brutes<br/>CSV]
        Opt[Données optimisées<br/>Parquet]
    end
    
    T1 -.->|Pointe vers| Raw
    T2 -.->|Pointe vers| Raw
    T3 -.->|Pointe vers| Opt
    
    style DB fill:#9c27b0,stroke:#7b1fa2,stroke-width:2px,color:#fff
    style T1 fill:#34495e,stroke:#2c3e50,color:#ecf0f1
    style T2 fill:#34495e,stroke:#2c3e50,color:#ecf0f1
    style T3 fill:#27ae60,stroke:#229954,stroke-width:2px,color:#fff
    style Raw fill:#95a5a6,stroke:#7f8c8d,color:#2c3e50
    style Opt fill:#27ae60,stroke:#229954,stroke-width:2px,color:#fff
```

### Composants Glue

| Composant | Description | Utilité |
|-----------|-------------|---------|
| **Database** | Container logique de tables | Organisation |
| **Table** | Métadonnées (schema, location S3) | Définition structure |
| **Crawler** | Scan automatique S3 pour inférer schema | Discovery |
| **Job** | Script ETL Spark/Python | Transformation |
| **Catalog** | Registre central métadonnées | Partage entre services |

---

# 5. AMAZON ATHENA - REQUETES SQL

## 5.1 Fonctionnement

**Athena** = SQL sur S3 sans serveur

```mermaid
sequenceDiagram
    participant U as Utilisateur
    participant A as Athena
    participant G as Glue Catalog
    participant S3 as Amazon S3
    
    U->>A: Requête SQL
    A->>G: Récupère métadonnées<br/>(schema, location)
    G-->>A: Retourne définition table
    A->>S3: Scan données<br/>(selon partitions)
    S3-->>A: Données
    A->>A: Exécute requête
    A-->>U: Résultats
```

### Caractéristiques

- **Serverless** : Aucune infrastructure à gérer
- **SQL standard** : Syntaxe ANSI SQL
- **Pricing** : Basé sur données scannées (5 USD/TB)
- **Performance** : Parallélisation automatique
- **Formats** : CSV, JSON, Parquet, ORC, Avro

---

# 6. OPTIMISATION : FORMAT PARQUET

## 6.1 CSV vs Parquet

```mermaid
graph LR
    subgraph CSV["FORMAT CSV - Ligne par Ligne"]
        C1[Row 1: id,name,age,city]
        C2[Row 2: 1,John,25,Paris]
        C3[Row 3: 2,Jane,30,Lyon]
    end
    
    subgraph PARQUET["FORMAT PARQUET - Colonnes"]
        P1[Column: id<br/>1,2,3,...]
        P2[Column: name<br/>John,Jane,...]
        P3[Column: age<br/>25,30,...]
    end
    
    style CSV fill:#e74c3c,stroke:#c0392b,color:#fff
    style PARQUET fill:#27ae60,stroke:#229954,stroke-width:2px,color:#fff
```

### Comparaison Technique

| Aspect | CSV | Parquet |
|--------|-----|---------|
| **Structure** | Ligne par ligne (row-based) | Colonnes (columnar) |
| **Compression** | Faible (gzip) | Excellente (Snappy, gzip) |
| **Taille** | 100% | **20-40%** du CSV |
| **Lecture colonne** | Scan fichier complet | Lecture colonnes nécessaires uniquement |
| **Performance SELECT** | Lente (scan tout) | **Très rapide** (colonnes ciblées) |
| **Cas d'usage** | Export simple, compatibilité | **Analytics, Big Data, Athena** |

### Gains Parquet

**Exemple réel** : Données taxis NYC

| Métrique | CSV | Parquet + Snappy | Gain |
|----------|-----|------------------|------|
| Taille stockage | 1 GB | 300 MB | **-70%** |
| Coût S3/mois | 0.023 USD | 0.007 USD | **-70%** |
| Scan Athena | 1 GB | 300 MB | **-70%** coût requête |
| Latence requête | 10 sec | 3 sec | **-70%** temps |

---

## 6.2 Compression Snappy

**Snappy** = Algorithme compression rapide

| Compression | Ratio | Vitesse Compression | Vitesse Décompression | Usage |
|-------------|-------|---------------------|----------------------|-------|
| **Snappy** | Moyen (2-3x) | **Très rapide** | **Très rapide** | **Parquet analytics** |
| **Gzip** | Élevé (3-5x) | Lente | Moyenne | Archivage long terme |
| **Zstd** | Élevé (3-4x) | Rapide | Rapide | Équilibre optimal |

> **Choix Snappy** : Compromis optimal vitesse/compression pour analytics interactives

---

## 6.3 Partitionnement

**Partitionnement** = Division données par valeurs de colonnes

```
s3://bucket/data/
├── pickup_year=2020/
│   ├── pickup_month=01/
│   │   └── data.parquet (Janvier 2020)
│   ├── pickup_month=02/
│   │   └── data.parquet (Février 2020)
│   └── pickup_month=12/
│       └── data.parquet (Décembre 2020)
└── pickup_year=2021/
    └── pickup_month=01/
        └── data.parquet (Janvier 2021)
```

**Avantages** :

| Bénéfice | Description | Gain |
|----------|-------------|------|
| **Partition pruning** | Scan uniquement partitions pertinentes | -90% données scannées |
| **Performance** | Requêtes ciblées ultra rapides | 10x plus rapide |
| **Coût** | Moins de données scannées | -90% coût Athena |
| **Parallélisation** | Traitement partitions en parallèle | Scalabilité |

**Exemple requête** :
```sql
SELECT * FROM taxi_data 
WHERE pickup_year = '2020' AND pickup_month = '01'
```
→ Scan uniquement `s3://bucket/data/pickup_year=2020/pickup_month=01/`

---

# 7. CAS D'USAGE : BATCH VS STREAMING

## 7.1 Quand Choisir ETL Batch

**Scénarios préférables** :

**Rapports quotidiens/mensuels** :
- Résultats ne sont pas urgents
- Traitement de gros volumes
- Historisation et tendances

**Data Warehouse / BI** :
- Alimenter Redshift, Snowflake
- Dashboards business non temps réel
- Analyses complexes (agrégations lourdes)

**ML Training** :
- Préparation datasets historiques
- Feature engineering batch
- Entraînement modèles offline

**Archivage et Conformité** :
- Conversion formats (CSV → Parquet)
- Compression et optimisation stockage
- Rétention long terme

---

## 7.2 Quand Choisir ETL Streaming

**Scénarios préférables** :

**Monitoring temps réel** :
- Dashboards live (< 1s)
- Alertes immédiates
- Métriques opérationnelles

**Détection anomalies** :
- Fraude bancaire
- Cyberattaques
- Défaillances IoT

**Personnalisation temps réel** :
- Recommandations live
- Contenu dynamique
- Tarification dynamique

---

## 7.3 Architecture Hybride

**Meilleure approche** : Combiner batch ET streaming

```mermaid
graph TB
    Source[Source<br/>Données] --> Stream[STREAMING]
    Source --> Batch[BATCH]
    
    Stream --> Lambda[Lambda<br/>Temps réel]
    Lambda --> OpenSearch[OpenSearch<br/>Dashboards live]
    Lambda --> S3[S3<br/>Archivage]
    
    S3 --> Glue[Glue + Athena<br/>Analytics batch]
    Batch --> S3
    
    Glue --> DW[Data Warehouse<br/>Rapports BI]
    
    style Stream fill:#3498db,stroke:#2980b9,stroke-width:2px,color:#fff
    style Batch fill:#f39c12,stroke:#e67e22,stroke-width:2px,color:#fff
    style Lambda fill:#e67e22,stroke:#d35400,color:#fff
    style OpenSearch fill:#3498db,stroke:#2980b9,color:#fff
    style Glue fill:#9c27b0,stroke:#7b1fa2,color:#fff
    style DW fill:#16a085,stroke:#138d75,color:#fff
```

**Exemple e-commerce** :
- **Streaming** : Détection fraude transactions en temps réel
- **Batch** : Rapport ventes quotidien + analytics tendances

---

# 8. WORKFLOW ETL BATCH TYPIQUE

## 8.1 Étapes Standard

```mermaid
flowchart TD
    Start([Déclencheur<br/>Quotidien 2AM]) --> Extract[1. EXTRACT<br/>Copier données sources<br/>vers S3]
    
    Extract --> Validate[2. VALIDATE<br/>Vérifier qualité<br/>données]
    
    Validate -->|OK| Transform[3. TRANSFORM<br/>Nettoyer, enrichir<br/>Parquet + Snappy]
    Validate -->|Erreurs| Alert[Alerte<br/>SNS]
    
    Transform --> Partition[4. PARTITION<br/>Organiser par<br/>date/catégorie]
    
    Partition --> Load[5. LOAD<br/>Créer tables Glue<br/>Vues Athena]
    
    Load --> Test[6. TEST<br/>Requêtes validation]
    
    Test -->|OK| Success([Succès<br/>Notification])
    Test -->|Erreurs| Retry[Retry<br/>ou escalade]
    
    style Extract fill:#3498db,stroke:#2980b9,color:#fff
    style Transform fill:#f39c12,stroke:#e67e22,color:#fff
    style Load fill:#27ae60,stroke:#229954,color:#fff
    style Success fill:#27ae60,stroke:#229954,stroke-width:3px,color:#fff
```

---

# 9. COMPARAISON ARCHITECTURES

## 9.1 Architecture Lambda (Streaming + Batch)

```mermaid
graph TB
    Source[Source<br/>Données continues]
    
    subgraph SPEED["SPEED LAYER - Streaming"]
        K[Kinesis]
        L[Lambda]
        OS[OpenSearch]
    end
    
    subgraph BATCH["BATCH LAYER - Batch"]
        S3[S3]
        G[Glue]
        A[Athena]
    end
    
    subgraph SERVING["SERVING LAYER"]
        D1[Dashboards<br/>Temps réel]
        D2[Rapports<br/>Historiques]
    end
    
    Source --> K
    Source --> S3
    
    K --> L --> OS --> D1
    S3 --> G --> A --> D2
    
    style K fill:#9b59b6,stroke:#8e44ad,color:#fff
    style L fill:#e67e22,stroke:#d35400,color:#fff
    style OS fill:#3498db,stroke:#2980b9,color:#fff
    style G fill:#9c27b0,stroke:#7b1fa2,color:#fff
    style A fill:#ff9800,stroke:#f57c00,color:#fff
```

**Architecture Lambda** = Speed Layer (streaming) + Batch Layer (batch)

**Avantage** : Meilleur des 2 mondes  
**Inconvénient** : 2 pipelines à maintenir

---

# 10. POINTS CLES DU MODULE

- ETL Batch traite données par lots périodiquement (vs streaming continu)
- Step Functions orchestre workflows complexes avec logique conditionnelle
- Glue fournit catalogue métadonnées (tables, schemas)
- Athena permet requêtes SQL serverless sur S3
- Parquet + Snappy optimise stockage et performances (70% économie)
- Partitionnement réduit drastiquement données scannées (-90%)
- Choisir batch ou streaming selon latence requise et cas d'usage
- Architecture hybride combine avantages batch + streaming

---

# 11. EXERCICES DE REFLEXION

1. Votre entreprise génère 500 GB de logs/jour. Besoin de rapports quotidiens uniquement. Batch ou streaming ?

2. Calculez économies si données 10 TB CSV converties en Parquet (70% réduction) :
   - Stockage S3 : 0.023 USD/GB/mois
   - Requêtes Athena : 5 USD/TB scanné, 100 requêtes/mois

3. Concevez workflow Step Functions pour :
   - Vérifier si table existe
   - Si non : créer table
   - Si oui : insérer nouvelles données
   - Créer vue finale

4. Comparez latence bout-en-bout :
   - Pipeline batch : Données → S3 → Step Functions → Athena → Résultat
   - Pipeline streaming : Données → Kinesis → Lambda → OpenSearch → Résultat

5. Quelle stratégie de partitionnement pour logs applicatifs horodatés ?

