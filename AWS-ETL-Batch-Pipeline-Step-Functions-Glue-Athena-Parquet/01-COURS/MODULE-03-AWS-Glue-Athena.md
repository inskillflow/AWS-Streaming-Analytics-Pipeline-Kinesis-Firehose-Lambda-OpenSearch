# MODULE 3 - AWS GLUE & AMAZON ATHENA

**Durée** : 60 minutes  
**Niveau** : Intermédiaire  
**Objectifs** : Maîtriser Glue Data Catalog et requêtes Athena sur S3

---

# 1. AWS GLUE DATA CATALOG

## 1.1 Architecture Glue

```mermaid
graph TB
    subgraph CATALOG["AWS GLUE DATA CATALOG"]
        DB[(Database<br/>nyctaxidb)]
        
        DB --> T1[Table taxi_csv<br/>Schema CSV]
        DB --> T2[Table lookup_csv<br/>Schema CSV]
        DB --> T3[Table taxi_parquet<br/>Schema Parquet]
        
        T1 -.->|Métadonnées| M1[Colonnes, types<br/>Location S3]
        T3 -.->|Métadonnées| M2[Colonnes, types<br/>Partitions<br/>Compression]
    end
    
    subgraph S3["AMAZON S3"]
        Raw[s3://bucket/raw/<br/>taxi_2020-01.csv]
        Opt[s3://bucket/optimized/<br/>year=2020/month=01/<br/>data.parquet]
    end
    
    T1 -.->|Pointe vers| Raw
    T3 -.->|Pointe vers| Opt
    
    style DB fill:#9c27b0,stroke:#7b1fa2,stroke-width:2px,color:#fff
    style T1 fill:#34495e,stroke:#2c3e50,color:#ecf0f1
    style T3 fill:#27ae60,stroke:#229954,stroke-width:2px,color:#fff
    style Raw fill:#95a5a6,stroke:#7f8c8d,color:#2c3e50
    style Opt fill:#27ae60,stroke:#229954,color:#fff
```

> **Point clé** : Glue Catalog stocke MÉTADONNÉES, pas données. Données restent dans S3.

---

## 1.2 Création Table Glue via Athena

**CREATE EXTERNAL TABLE** :

```sql
CREATE EXTERNAL TABLE nyctaxidb.taxi_data_csv (
  vendorid BIGINT,
  pickup_datetime STRING,
  dropoff_datetime STRING,
  passenger_count BIGINT,
  trip_distance DOUBLE,
  fare_amount DOUBLE
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
LOCATION 's3://bucket/data/'
TBLPROPERTIES ('skip.header.line.count'='1');
```

**Éléments clés** :

| Élément | Description |
|---------|-------------|
| **EXTERNAL** | Données restent dans S3 (pas copiées) |
| **ROW FORMAT** | Format parsing (CSV, JSON, etc.) |
| **LOCATION** | Chemin S3 des données |
| **TBLPROPERTIES** | Skip header pour CSV |

---

## 1.3 Glue Crawlers

**Crawler** = Scan automatique S3 pour inférer schema

```mermaid
sequenceDiagram
    participant U as Utilisateur
    participant C as Glue Crawler
    participant S3 as Amazon S3
    participant Cat as Glue Catalog
    
    U->>C: Start Crawler
    C->>S3: Scan fichiers
    S3-->>C: Structure données
    C->>C: Inférer schema<br/>(types, colonnes)
    C->>Cat: Créer/Update tables
    Cat-->>U: Tables disponibles
```

**Avantages** :
- Découverte automatique schema
- Mise à jour auto si nouvelles données
- Support multi-formats

**Inconvénients** :
- Parfois imprécis (inférence)
- Coût crawls fréquents

---

# 2. AMAZON ATHENA

## 2.1 Fonctionnement

**Athena** = Moteur SQL serverless sur S3

```mermaid
graph LR
    subgraph USER["UTILISATEUR"]
        SQL[Requête SQL<br/>SELECT * FROM table]
    end
    
    subgraph ATHENA["AMAZON ATHENA"]
        Parse[Parser SQL]
        Plan[Query Planner]
        Exec[Exécution<br/>distribuée]
    end
    
    subgraph BACKEND["BACKEND"]
        Glue[(Glue Catalog<br/>Métadonnées)]
        S3[(S3<br/>Données)]
    end
    
    SQL --> Parse
    Parse --> Glue
    Glue -->|Schema, location| Plan
    Plan --> S3
    S3 -->|Scan données| Exec
    Exec -->|Résultats| SQL
    
    style Parse fill:#ff9800,stroke:#f57c00,color:#fff
    style Plan fill:#ff9800,stroke:#f57c00,color:#fff
    style Exec fill:#ff9800,stroke:#f57c00,color:#fff
    style Glue fill:#9c27b0,stroke:#7b1fa2,color:#fff
    style S3 fill:#27ae60,stroke:#229954,color:#fff
```

---

## 2.2 Types de Requêtes

### DDL (Data Definition Language)

```sql
-- Créer database
CREATE DATABASE IF NOT EXISTS mydb;

-- Créer table
CREATE EXTERNAL TABLE mydb.mytable (
  id INT,
  name STRING
) LOCATION 's3://bucket/data/';

-- Supprimer table
DROP TABLE mydb.mytable;

-- Afficher tables
SHOW TABLES IN mydb;
```

### DML (Data Manipulation Language)

```sql
-- SELECT
SELECT * FROM taxi_data WHERE fare > 50;

-- INSERT (CTAS - Create Table As Select)
CREATE TABLE taxi_parquet
WITH (format='PARQUET')
AS SELECT * FROM taxi_csv;

-- INSERT INTO (ajout données)
INSERT INTO taxi_parquet
SELECT * FROM taxi_csv WHERE month = '02';
```

---

## 2.3 CTAS (Create Table As Select)

**Pattern puissant** : Créer table ET charger données en une requête

```sql
CREATE TABLE nyctaxidb.taxi_optimized
WITH (
  format = 'PARQUET',
  parquet_compression = 'SNAPPY',
  partitioned_by = ARRAY['year', 'month'],
  external_location = 's3://bucket/optimized/'
)
AS
SELECT 
  vendorid,
  fare_amount,
  SUBSTR(pickup_datetime, 1, 4) AS year,
  SUBSTR(pickup_datetime, 6, 2) AS month
FROM nyctaxidb.taxi_csv
WHERE year = '2020';
```

**Avantages** :
- Conversion format (CSV → Parquet)
- Compression automatique
- Partitionnement
- Une seule commande

---

## 2.4 Vues Athena

```sql
CREATE OR REPLACE VIEW nyctaxidb.taxi_analytics AS
SELECT 
  t.pickup_location,
  t.pickup_month,
  l.borough,
  l.zone,
  SUM(t.fare_amount) AS total_fare,
  SUM(t.trip_distance) AS total_distance,
  COUNT(*) AS num_trips
FROM nyctaxidb.taxi_data t
JOIN nyctaxidb.locations l ON t.pickup_location = l.locationid
GROUP BY t.pickup_location, t.pickup_month, l.borough, l.zone;
```

**Avantages vues** :
- Simplification requêtes complexes
- Réutilisation logique métier
- Pas de stockage additionnel
- Mise à jour auto (query-time)

---

# 3. INTEGRATION STEP FUNCTIONS + ATHENA

## 3.1 Workflow ETL Complet

```mermaid
flowchart TD
    Start([Start]) --> CreateDB[CreateDatabase<br/>Athena Query]
    
    CreateDB --> ShowTables[Show Tables<br/>Athena Query]
    
    ShowTables --> GetResults[GetQueryResults<br/>Récupérer résultats]
    
    GetResults --> Choice{Choice<br/>Tables existent?}
    
    Choice -->|Non| CreateT[CreateTables<br/>Athena DDL]
    Choice -->|Oui| MapT[Map Tables<br/>Itération]
    
    CreateT --> ConvertP[Convert Parquet<br/>Athena CTAS]
    ConvertP --> CreateV[Create View<br/>Athena DDL]
    CreateV --> End([End])
    
    MapT --> InsertData[Insert New Data<br/>Athena INSERT]
    InsertData --> End
    
    style Start fill:#34495e,stroke:#2c3e50,color:#ecf0f1
    style CreateDB fill:#ff9800,stroke:#f57c00,color:#fff
    style ShowTables fill:#ff9800,stroke:#f57c00,color:#fff
    style Choice fill:#f39c12,stroke:#e67e22,stroke-width:3px,color:#fff
    style CreateT fill:#e91e63,stroke:#c2185b,color:#fff
    style ConvertP fill:#27ae60,stroke:#229954,color:#fff
    style End fill:#27ae60,stroke:#229954,stroke-width:3px,color:#fff
```

---

## 3.2 Passage de Données Entre États

**Utilisation JSONPath** :

```json
{
  "QueryExecutionId.$": "$.QueryExecution.QueryExecutionId"
}
```

**Symboles** :
- `$` : Racine objet
- `$.field` : Accès champ
- `$.array[0]` : Premier élément array
- `.$` : Valeur dynamique (runtime)

---

# 4. BONNES PRATIQUES

## 4.1 Organisation Tables

**Structure recommandée** :

```
Database par domaine métier
├── finance_db
│   ├── transactions_raw (CSV)
│   ├── transactions_clean (Parquet)
│   └── transactions_aggregated (Parquet, partitionné)
│
└── customer_db
    ├── customers_raw (JSON)
    └── customers_clean (Parquet)
```

---

## 4.2 Naming Conventions

| Type | Pattern | Exemple |
|------|---------|---------|
| **Database** | `{domain}_db` | `sales_db`, `finance_db` |
| **Table raw** | `{entity}_raw` ou `_csv` | `orders_raw`, `users_csv` |
| **Table optimized** | `{entity}_parquet` | `orders_parquet` |
| **View** | `{entity}_vw` ou `_view` | `sales_analytics_vw` |

---

## 4.3 Gestion Partitions

```sql
-- Ajouter partition manuellement
ALTER TABLE taxi_data ADD PARTITION (year='2021', month='03')
LOCATION 's3://bucket/data/year=2021/month=03/';

-- Réparer partitions (auto-discover)
MSCK REPAIR TABLE taxi_data;

-- Lister partitions
SHOW PARTITIONS taxi_data;
```

---

# 5. MONITORING

## 5.1 Métriques Athena

| Métrique | Description | Action |
|----------|-------------|--------|
| **Data Scanned** | Volume données lues | Optimiser avec partitions |
| **Query Runtime** | Temps exécution | Optimiser requêtes SQL |
| **Failed Queries** | Requêtes échouées | Debug, retry |

---

## 5.2 Optimisation Requêtes

**Avant optimisation** :
```sql
SELECT * FROM taxi_data WHERE fare > 100;
```
Scan : **10 TB** (toutes années)

**Après optimisation** :
```sql
SELECT * FROM taxi_data 
WHERE year = '2020' AND month = '01' AND fare > 100;
```
Scan : **100 GB** (partition spécifique)

**Gain** : -99% données scannées

---

# 6. POINTS CLES DU MODULE

- Glue Catalog = registre métadonnées (tables, schemas)
- Athena = requêtes SQL serverless sur S3
- CTAS (Create Table As Select) convertit formats en une commande
- Vues simplifient requêtes complexes (jointures, agrégations)
- Step Functions orchestre séquence requêtes Athena
- Partitionnement réduit drastiquement données scannées
- Pricing Athena basé sur volume scanné (5 USD/TB)
- Glue Crawlers automatisent découverte schema

---

# 7. EXERCICES

1. Écrivez requête CTAS pour convertir table CSV 100GB en Parquet partitionné par année/mois.

2. Calculez coût Athena mensuel :
   - 1000 requêtes/mois
   - Moyenne 500 GB scannés par requête
   - Avec vs sans partitionnement (10x réduction)

3. Créez vue Athena joignant tables taxi_data et locations pour analytics géographique.

4. Workflow Step Functions : 
   - Crawler Glue scan S3
   - Vérifier tables créées
   - Si non : créer via Athena
   - Si oui : requête validation

5. Pourquoi utiliser EXTERNAL TABLE plutôt que table managée ?

