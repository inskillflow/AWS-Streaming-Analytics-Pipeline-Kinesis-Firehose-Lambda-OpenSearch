================================================================================
                            MODULE 6
              COMPARAISONS TECHNOLOGIQUES
================================================================================

Durée : 60 minutes
Niveau : Avancé

================================================================================
1. KINESIS VS APACHE KAFKA
================================================================================

1.1 Vue d'Ensemble
------------------

AMAZON KINESIS :
- Service managé AWS
- Intégration native écosystème AWS
- Simplicité opérationnelle

APACHE KAFKA :
- Plateforme open-source
- Standard industrie
- Ecosystème riche
- Flexibilité maximale


1.2 Comparaison Architecture
-----------------------------

TERMINOLOGIE :

| CONCEPT          | KINESIS          | KAFKA              |
|------------------|------------------|--------------------|
| Flux de données  | Stream           | Topic              |
| Unité capacité   | Shard            | Partition          |
| Serveur          | N/A (managé)     | Broker             |
| Cluster          | Service AWS      | Ensemble brokers   |


ARCHITECTURE KINESIS :
- Abstraction infrastructure
- Scaling par ajout/suppression shards
- Pas de gestion brokers

ARCHITECTURE KAFKA :
- Brokers visibles, configurables
- ZooKeeper (ou KRaft) pour coordination
- Gestion complète infrastructure


1.3 Comparaison Fonctionnelle
------------------------------

| CRITERE                  | KINESIS              | KAFKA                |
|--------------------------|----------------------|----------------------|
| Gestion infrastructure   | AWS (managé)         | Client (self-hosted) |
| Latence                  | < 1 seconde          | < 100ms              |
| Débit                    | 1 MB/s par shard     | Très élevé           |
| Rétention                | 24h - 365j           | Configurable illimité|
| Replay                   | Oui (dans rétention) | Oui                  |
| Multi-datacenter         | Limité (régions AWS) | Oui (mirror maker)   |
| Ecosystème               | Intégration AWS      | Kafka Connect, KSQL  |
| Coût initial             | Faible               | Elevé (infra)        |
| Expertise requise        | Faible               | Elevée               |
| Elasticité               | Manuelle shards      | Manuelle partitions  |


1.4 Cas d'Usage Préférentiels
------------------------------

CHOISIR KINESIS SI :
- Infrastructure AWS existante
- Equipe réduite, peu d'expertise systèmes distribués
- Intégration Lambda, S3, Redshift, OpenSearch
- Budget infrastructure limité
- Besoin démarrage rapide

CHOISIR KAFKA SI :
- Débits très élevés (> 100 MB/s)
- Latence ultra-faible critique (< 100ms)
- Multi-cloud ou on-premise
- Expertise Kafka en interne
- Ecosystème Kafka requis (Connect, Streams, KSQL)
- Rétention longue avec replay fréquent


1.5 Amazon MSK (Managed Streaming for Kafka)
---------------------------------------------

DEFINITION :
Service AWS hébergeant Apache Kafka managé.

AVANTAGES VS SELF-HOSTED KAFKA :
- Provisionnement automatisé
- Patches et mises à jour gérés
- Monitoring intégré CloudWatch
- Integration IAM

AVANTAGES VS KINESIS :
- API Kafka native
- Ecosystème Kafka (Connect, Streams)
- Débits supérieurs
- Rétention configurable

INCONVENIENTS :
- Plus coûteux que Kinesis
- Moins simple que Kinesis
- Configuration Kafka requise


================================================================================
2. ALTERNATIVES DE STREAMING
================================================================================

2.1 Apache Pulsar
-----------------

CARACTERISTIQUES :
- Développé par Apache (Yahoo origin)
- Architecture découplée : compute (brokers) + storage (BookKeeper)
- Multi-tenancy natif
- Geo-replication intégrée

AVANTAGES VS KAFKA :
- Scaling indépendant compute/storage
- Pas de rebalancing lors d'ajout brokers
- Messages ordering par défaut
- Tiered storage natif

INCONVENIENTS :
- Ecosystème moins mature
- Communauté plus petite
- Expertise rare

CAS D'USAGE :
- Multi-tenancy (SaaS providers)
- Geo-replication critique
- Scaling storage indépendant compute


2.2 RabbitMQ
------------

CARACTERISTIQUES :
- Message broker AMQP
- Routing complexe (exchanges, queues)
- Patterns pub/sub, request/reply

DIFFERENCES VS STREAMING :
- Focus : messaging traditionnel vs streaming
- Ordering : faible vs fort
- Rétention : courte vs longue

CAS D'USAGE :
- Microservices communication
- Task queues
- RPC (request/reply)
- Pas pour analytics streaming


2.3 Google Cloud Pub/Sub
-------------------------

CARACTERISTIQUES :
- Service managé Google Cloud
- Push et pull delivery
- Au moins une livraison garantie

COMPARAISON KINESIS :
- Similaire en simplicité
- Meilleur multi-cloud
- Moins d'intégrations que Kinesis (écosystème GCP)


2.4 Azure Event Hubs
--------------------

CARACTERISTIQUES :
- Service managé Microsoft Azure
- Compatible protocole Kafka
- Intégration Azure ecosystem

COMPARAISON KINESIS :
- Equivalent Azure de Kinesis
- Bon pour organisations Azure-centric


================================================================================
3. ALTERNATIVES OPENSEARCH
================================================================================

3.1 Elasticsearch
-----------------

RELATION :
OpenSearch = fork Elasticsearch 7.10.2

DIFFERENCES POST-FORK :
- Elasticsearch : fonctionnalités propriétaires (ML, security advanced)
- OpenSearch : open-source, AWS backing
- Compatibilité API : partielle

CHOISIR ELASTICSEARCH SI :
- Besoin fonctionnalités propriétaires Elastic
- Support commercial Elastic requis
- Elastic Cloud

CHOISIR OPENSEARCH SI :
- Open-source pure
- Integration AWS
- Coût inférieur


3.2 Apache Solr
---------------

CARACTERISTIQUES :
- Projet Apache mature (2006)
- Basé sur Lucene (comme ES/OpenSearch)
- Faceting avancé

AVANTAGES :
- Maturité, stabilité
- Faceting riche
- SQL support

INCONVENIENTS :
- Configuration complexe
- Moins moderne que ES/OpenSearch
- Communauté plus petite

CAS D'USAGE :
- E-commerce (faceted search)
- Bibliothèques, archives
- Pas pour log analytics streaming


3.3 Algolia
-----------

CARACTERISTIQUES :
- SaaS spécialisé recherche
- Latence ultra-faible (< 50ms)
- Typo-tolerance avancée
- API simple

AVANTAGES :
- Setup immédiat
- Performance exceptionnelle
- UX optimisée

INCONVENIENTS :
- Coût élevé (requêtes facturées)
- Vendor lock-in
- Pas pour logs/analytics (focus search)

CAS D'USAGE :
- Recherche produits e-commerce
- Autocomplete
- Search-as-a-service


3.4 Typesense
-------------

CARACTERISTIQUES :
- Open-source récent
- Typo-tolerance
- Performance (C++)
- Self-hosted ou cloud

AVANTAGES :
- Léger, rapide
- Moins complexe que ES/OpenSearch
- Typo-tolerance native

INCONVENIENTS :
- Moins de fonctionnalités analytics
- Communauté petite
- Pas pour log aggregation streaming


================================================================================
4. ARCHITECTURES LAMBDA VS KAPPA
================================================================================

4.1 Architecture Lambda
-----------------------

PRINCIPE :
Deux couches parallèles : batch + streaming.

BATCH LAYER :
- Traitement exhaustif données historiques
- Latence haute, exactitude garantie
- Regeneration possible

SPEED LAYER :
- Traitement temps réel données récentes
- Latence faible, approximations tolérées

SERVING LAYER :
- Merge résultats batch + speed
- Requêtes utilisateurs

AVANTAGES :
- Exactitude batch + rapidité streaming
- Correction erreurs possible

INCONVENIENTS :
- Complexité : deux pipelines à maintenir
- Duplication code
- Synchronisation batch/speed


4.2 Architecture Kappa
----------------------

PRINCIPE :
Une seule couche streaming.

ARCHITECTURE :
Source → Stream (Kafka/Kinesis) → Processing → Views

REPROCESSING :
- Replay stream depuis début
- Pas de batch séparé

AVANTAGES :
- Simplicité : un seul pipeline
- Code unifié
- Moins de maintenance

INCONVENIENTS :
- Stream doit retenir toutes données
- Reprocessing peut être long
- Besoin latence faible même pour historique


4.3 Choix Architecture
----------------------

LAMBDA SI :
- Données historiques volumineuses
- Retraitement fréquent
- Batch analytics complexes
- Exactitude critique

KAPPA SI :
- Rétention stream possible (coût acceptable)
- Processing uniforme batch/streaming
- Retraitement occasionnel
- Simplicité valorisée


================================================================================
5. CRITERES DE CHOIX TECHNOLOGIQUE
================================================================================

5.1 Matrice de Décision
------------------------

FACTEURS TECHNIQUES :
- Débit requis (MB/s, messages/s)
- Latence acceptable (ms, secondes)
- Rétention nécessaire (heures, jours, mois)
- Ordering requis (strict, partiel)
- Exactly-once vs at-least-once

FACTEURS OPERATIONNELS :
- Expertise équipe
- Temps setup
- Charge maintenance
- Observabilité

FACTEURS ECONOMIQUES :
- Coût infrastructure
- Coût opérationnel (FTE)
- Coût scaling
- Budget

FACTEURS STRATEGIQUES :
- Ecosystème existant (AWS, GCP, Azure, on-prem)
- Vendor lock-in acceptable ?
- Open-source vs propriétaire
- Communauté et support


5.2 Scénarios Typiques
-----------------------

STARTUP EARLY-STAGE SUR AWS :
Kinesis Firehose + Lambda + OpenSearch
- Simplicité maximale
- Coût démarrage faible
- Scaling automatique

ENTERPRISE MULTI-CLOUD :
Kafka + Kafka Streams + Elasticsearch
- Portabilité
- Flexibilité maximale
- Expertise disponible

SAAS B2B ANALYTICS :
Kafka + Apache Flink + TimescaleDB
- Multi-tenancy (Kafka)
- Stream processing avancé (Flink)
- Time-series optimisé (TimescaleDB)

E-COMMERCE RECHERCHE PRODUITS :
Kinesis + Lambda + Algolia
- Backend AWS
- Recherche utilisateur Algolia (performance)


================================================================================
6. TENDANCES ET EVOLUTION
================================================================================

6.1 Stream Processing Frameworks
---------------------------------

APACHE FLINK :
- Framework stream processing avancé
- Stateful computations
- Exactly-once semantics
- Windowing complexe

SPARK STRUCTURED STREAMING :
- Extension Spark pour streaming
- API unifiée batch/stream
- Integration ecosystem Spark

KAFKA STREAMS :
- Bibliothèque traitement Kafka
- Topologies de processing
- Stateful, fault-tolerant


6.2 Nouvelles Approches
------------------------

SERVERLESS STREAMING :
- AWS Lambda, GCP Cloud Functions
- Scaling automatique
- Facturation usage

REAL-TIME DATABASES :
- Apache Druid (OLAP temps réel)
- ClickHouse (analytics rapide)
- TimescaleDB (time-series)

DATA LAKEHOUSE :
- Delta Lake, Apache Iceberg, Hudi
- Merge data lake + warehouse
- ACID sur object storage


================================================================================
7. POINTS CLES DU MODULE
================================================================================

- Kinesis simple et managé, Kafka flexible et puissant
- MSK compromis entre les deux
- Alternatives (Pulsar, Pub/Sub) selon contexte
- Architecture Lambda (batch+stream) vs Kappa (stream only)
- Choix dépend : technique, opérationnel, économique, stratégique
- Pas de solution universelle, évaluer cas par cas


================================================================================
8. EXERCICES DE REFLEXION
================================================================================

1. Votre entreprise migre vers AWS avec équipe Kafka expérimentée.
   Kinesis, MSK ou Kafka self-hosted ? Justifiez.

2. Comparez coût sur 1 an : Kinesis (10 shards) vs Kafka (3 brokers m5.large).

3. Architecture Lambda ou Kappa pour analytics e-commerce temps réel ?

4. Opensearch ou Algolia pour recherche catalogue 100K produits ?

5. Concevez architecture streaming multi-cloud (AWS + GCP).


================================================================================

