================================================================================
                            MODULE 4
              OPENSEARCH ET INDEXATION
================================================================================

Durée : 60 minutes
Niveau : Intermédiaire à Avancé

================================================================================
1. INTRODUCTION A OPENSEARCH
================================================================================

1.1 Historique et Positionnement
---------------------------------

ORIGINE :
- Fork d'Elasticsearch 7.10.2 (2021)
- Suite au changement de licence Elastic
- Maintenu par AWS et communauté open-source

OBJECTIF :
Moteur de recherche et d'analyse distribué pour données structurées et non
structurées.

ALTERNATIVES :
- Elasticsearch (Elastic)
- Apache Solr
- Algolia (SaaS)
- Typesense


1.2 Architecture Générale
--------------------------

CLUSTER :
- Ensemble de nœuds travaillant ensemble
- Distribution et réplication automatiques

NOEUD :
- Instance OpenSearch individuelle
- Rôles : master, data, ingest, coordinating

INDEX :
- Collection de documents similaires
- Analogie : base de données relationnelle

DOCUMENT :
- Unité de base (JSON)
- Analogie : ligne dans table SQL

SHARD :
- Subdivision d'un index
- Permet distribution et parallélisation


================================================================================
2. CONCEPTS D'INDEXATION
================================================================================

2.1 Structure des Données
--------------------------

DOCUMENT JSON :

```json
{
  "host": "203.0.113.42",
  "datetime": "28/Oct/2025:10:15:30 +0000",
  "request": "GET /product.php HTTP/1.1",
  "response": "200",
  "city": "Paris",
  "location": {
    "lat": 48.8566,
    "lon": 2.3522
  }
}
```

CHAMPS :
- Types simples : text, keyword, integer, date
- Types complexes : object, nested, geo_point


2.2 Mappings
------------

DEFINITION :
Schema définissant la structure et les types de champs d'un index.

TYPES DE CHAMPS COURANTS :

text :
- Texte analysé pour recherche full-text
- Tokenization, stemming
- Exemple : descriptions, contenu articles

keyword :
- Texte non analysé
- Recherche exacte, agrégations, tri
- Exemple : IDs, statuts, catégories

date :
- Dates et timestamps
- Formats configurables
- Exemple : "dd/MM/yyyy:HH:mm:ss Z"

integer, long, float, double :
- Valeurs numériques
- Calculs, agrégations

geo_point :
- Coordonnées géographiques
- Recherches spatiales, distance

MAPPING EXPLICITE vs DYNAMIQUE :
- Explicite : défini à la création (recommandé)
- Dynamique : inféré automatiquement (risque type incorrect)


2.3 Sharding et Replication
----------------------------

SHARDS PRIMAIRES :
- Subdivision de l'index pour scalabilité horizontale
- Nombre défini à la création (non modifiable ensuite)
- Calcul : fonction hash(routing_key) % nombre_shards

REPLICAS :
- Copies des shards primaires
- Haute disponibilité et performance lecture
- Modifiable après création

EXEMPLE :
- 10 shards primaires
- 1 replica par shard
- Total : 20 shards (10 primary + 10 replica)

ETATS CLUSTER :
- Green : tous shards (primary + replica) alloués
- Yellow : tous primary alloués, certains replica manquants
- Red : certains primary manquants


================================================================================
3. OPERATIONS D'INDEXATION
================================================================================

3.1 Création d'Index
--------------------

API REST :
PUT /apache_logs
{
  "settings": {
    "number_of_shards": 10,
    "number_of_replicas": 1,
    "refresh_interval": "30s"
  },
  "mappings": {
    "properties": {
      "host": {"type": "text"},
      "datetime": {"type": "date", "format": "dd/MMM/yyyy:HH:mm:ss Z"},
      "webpage": {"type": "keyword"},
      "city": {"type": "keyword"},
      "location": {"type": "geo_point"},
      "response": {"type": "keyword"},
      "browser": {"type": "keyword"},
      "os": {"type": "keyword"}
    }
  }
}


3.2 Insertion de Documents
---------------------------

SINGLE DOCUMENT :

```http
POST /apache_logs/_doc
{
  "host": "203.0.113.42",
  "datetime": "28/Oct/2025:10:15:30 +0000",
  ...
}
```

BULK INDEXING :

```http
POST /_bulk
{"index": {"_index": "apache_logs"}}
{"host": "203.0.113.42", ...}
{"index": {"_index": "apache_logs"}}
{"host": "198.51.100.10", ...}
```

Bulk recommandé pour performance (batches de 1000-5000 documents).


3.3 Recherche et Requêtes
--------------------------

MATCH QUERY (full-text) :
GET /apache_logs/_search
{
  "query": {
    "match": {"browser": "Chrome"}
  }
}

TERM QUERY (exact) :
GET /apache_logs/_search
{
  "query": {
    "term": {"response": "404"}
  }
}

RANGE QUERY :
GET /apache_logs/_search
{
  "query": {
    "range": {
      "datetime": {
        "gte": "2025-10-28T00:00:00",
        "lte": "2025-10-28T23:59:59"
      }
    }
  }
}


3.4 Agrégations
---------------

TERMS AGGREGATION (groupement) :
GET /apache_logs/_search
{
  "size": 0,
  "aggs": {
    "browsers": {
      "terms": {"field": "browser", "size": 10}
    }
  }
}

Résultat : top 10 navigateurs avec comptage.

DATE HISTOGRAM :
"aggs": {
  "requests_over_time": {
    "date_histogram": {
      "field": "datetime",
      "interval": "1h"
    }
  }
}


================================================================================
4. OPENSEARCH DASHBOARDS
================================================================================

4.1 Index Pattern
-----------------

ROLE :
Modèle pour identifier les index à visualiser.

CREATION :
1. Management → Index Patterns
2. Définir pattern : "apache_logs" ou "apache_logs*"
3. Sélectionner champ temporel : "datetime"
4. Créer

USAGE :
Requis pour Discover, Visualize, Dashboard.


4.2 Visualisations
------------------

PIE CHART (Camembert) :
- Répartition catégorielle
- Exemple : OS utilisés, navigateurs

Configuration :
- Buckets : Split Slices → Terms → webpage
- Sous-buckets : Terms → os → browser

HEAT MAP (Carte Thermique) :
- Corrélations deux dimensions
- Exemple : page visitée vs source

Configuration :
- X-axis : Terms → refering_page
- Y-axis : Terms → webpage

BAR CHART (Histogramme) :
- Evolution temporelle
- Comparaisons

LINE CHART (Courbe) :
- Tendances dans le temps

COORDINATE MAP (Carte Géo) :
- Visualisation géographique
- Champ geo_point requis


4.3 Dashboards
--------------

COMPOSITION :
Assemblage de visualisations dans vue unifiée.

INTERACTIVITE :
- Filtres dynamiques
- Drill-down
- Rafraîchissement auto

CAS D'USAGE :
- Monitoring temps réel (ops)
- Analyse comportementale (métier)
- Reporting (management)


================================================================================
5. PERFORMANCE ET OPTIMISATION
================================================================================

5.1 Dimensionnement Cluster
----------------------------

CALCUL SHARDS :
Règle générale : shards < 50 GB chacun

Exemple :
- 500 GB de données
- Réplicas : 1
- 500 GB / 50 GB = 10 shards minimum
- Avec replica : 20 shards total

TYPES DE NOEUDS :
- Data nodes : stockage et recherche
- Master nodes : gestion cluster
- Ingest nodes : preprocessing


5.2 Stratégie Hot-Warm-Cold
----------------------------

HOT (données récentes) :
- Noeuds haute performance (SSD)
- Indexation et recherche fréquente

WARM (données moyennement anciennes) :
- Noeuds performance moyenne
- Recherche occasionnelle

COLD (archives) :
- Stockage économique (HDD)
- Recherche rare

TRANSITION AUTOMATIQUE :
Index Lifecycle Management (ILM) déplace index selon age.


5.3 Optimisation Requêtes
--------------------------

FILTRES vs QUERIES :
- Filtres : cachés, plus rapides, binaires
- Queries : scoring, plus lent

LIMIT SIZE :
- Pagination plutôt que tout récupérer
- Search After pour grands résultats

FIELDS SELECTION :
- _source filtering : retourner uniquement champs nécessaires


5.4 Monitoring
--------------

METRIQUES CLES :
- Cluster health (green/yellow/red)
- Indexing rate (docs/s)
- Search latency (ms)
- JVM heap usage (%)
- Disk space

OUTILS :
- API _cluster/health
- API _cat/indices
- CloudWatch (service managé AWS)


================================================================================
6. LIMITES ET CONTRAINTES
================================================================================

6.1 Limites Amazon OpenSearch Service
--------------------------------------

STOCKAGE PAR INSTANCE :
- Dépend du type d'instance
- Exemple : r6g.large → 512 GB EBS max

NOMBRE DE NOEUDS :
- Limite compte AWS
- Augmentation via quota request

RETENTION :
- Pas de limite technique
- Contrainte coût de stockage
- ILM recommandé


6.2 Best Practices
------------------

EVITER :
- Index avec millions de shards
- Shards > 50 GB
- Cluster à noeud unique en production

FAIRE :
- Monitoring proactif
- Sauvegardes automatiques (snapshots)
- Mise à jour régulière
- Index template pour standardisation


================================================================================
7. ALTERNATIVES A OPENSEARCH
================================================================================

ELASTICSEARCH :
[+] Fonctionnalités avancées (ML, APM)
[-] Licence propriétaire depuis 7.11
[-] Coût plus élevé

APACHE SOLR :
[+] Maturité, faceting avancé
[-] Configuration complexe

ALGOLIA :
[+] SaaS, setup instantané, typo-tolerance
[-] Coût élevé, vendor lock-in

TYPESENSE :
[+] Léger, open-source, typo-tolerance
[-] Moins de fonctionnalités analytics


================================================================================
8. POINTS CLES DU MODULE
================================================================================

- OpenSearch = fork Elasticsearch pour indexation et recherche
- Documents JSON organisés en index
- Mappings définissent structure et types
- Sharding pour scalabilité, replica pour disponibilité
- Dashboards pour visualisation interactive
- Stratégie hot-warm-cold optimise coûts
- Monitoring essentiel pour production


================================================================================
9. EXERCICES DE REFLEXION
================================================================================

1. Dimensionnez un cluster pour 1 TB de logs avec recherches fréquentes pendant
   7 jours puis archivage.

2. Quand utiliser "text" vs "keyword" pour un champ ?

3. Votre cluster est Yellow. Que signifie cet état et comment corriger ?

4. Concevez une stratégie ILM pour logs d'application avec rétention 90 jours.

5. Comparez OpenSearch et Algolia pour recherche produits e-commerce.


================================================================================

