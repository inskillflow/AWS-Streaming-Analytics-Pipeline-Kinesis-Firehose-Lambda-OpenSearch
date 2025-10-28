================================================================================
                        GLOSSAIRE TECHNIQUE
              INGENIERIE DES DONNEES - STREAMING AWS
================================================================================

================================================================================
A
================================================================================

AGGREGATION
Opération de regroupement et calcul sur des données (somme, moyenne, comptage).
Exemple : nombre de visites par navigateur dans OpenSearch.

API (Application Programming Interface)
Interface permettant la communication entre applications.
Exemple : API Kinesis PutRecord pour envoyer des données.

AT-LEAST-ONCE DELIVERY
Garantie de livraison où un message peut être délivré plusieurs fois.
Nécessite idempotence du traitement.

================================================================================
B
================================================================================

BATCH PROCESSING
Traitement de données par lots à intervalles réguliers.
Opposé au streaming (traitement continu).

BATCHING
Regroupement de plusieurs records pour optimiser les performances et coûts.
Exemple : Lambda traite 100 records Kinesis à la fois.

BROKER
Serveur dans un système de messaging (terme Kafka).
Équivalent : pas de broker visible dans Kinesis (abstrait).

BUFFER
Zone mémoire temporaire pour accumulation de données.
Exemple : Firehose bufferise 60s ou 1MB avant livraison.

================================================================================
C
================================================================================

COLD START
Délai initialisation lors de première invocation Lambda.
Solutions : provisioned concurrency, optimisation package.

CONSUMER
Application qui lit/consomme des données depuis un stream.
Exemple : Lambda consumant Kinesis Data Streams.

================================================================================
D
================================================================================

DATA LAKE
Stockage centralisé de données brutes tous formats.
Exemple : S3 comme data lake avec données Firehose.

DATA WAREHOUSE
Base de données optimisée pour analytics sur données structurées.
Exemple : Amazon Redshift.

DEAD LETTER QUEUE (DLQ)
File d'attente pour messages échoués après retries.
Permet retraitement hors ligne sans perte.

================================================================================
E
================================================================================

ENCRYPTION AT REST
Chiffrement des données stockées sur disque.
Exemple : OpenSearch avec KMS.

ENCRYPTION IN TRANSIT
Chiffrement des données pendant transmission réseau.
Protocole : TLS/SSL (HTTPS).

ENRICHMENT
Ajout d'informations complémentaires aux données brutes.
Exemple : Lambda ajoutant géolocalisation depuis IP.

EVENT-DRIVEN ARCHITECTURE
Architecture où les composants réagissent à des événements.
Lambda déclenché par Kinesis = event-driven.

EXACTLY-ONCE DELIVERY
Garantie de livraison où chaque message est traité une seule fois.
Difficile à atteindre dans systèmes distribués.

================================================================================
F
================================================================================

FAN-OUT
Pattern où une source alimente plusieurs destinations en parallèle.
Exemple : Kinesis Streams vers 3 consumers différents.

FIREHOSE
Service AWS de livraison automatique de données streaming.
Alternative : Kinesis Data Streams (plus de contrôle).

================================================================================
H
================================================================================

HOT DATA
Données récentes fréquemment accédées.
Stockage : haute performance (SSD).

================================================================================
I
================================================================================

IAM (Identity and Access Management)
Service AWS de gestion des identités et permissions.
Principe : moindre privilège.

IDEMPOTENCE
Propriété où répéter une opération produit même résultat.
Essentiel pour at-least-once delivery.

INDEX
Structure de données optimisée pour recherche rapide.
Exemple : index OpenSearch pour logs.

INGESTION
Processus de collecte et import de données dans un système.
Exemple : Kinesis ingère logs depuis EC2.

================================================================================
K
================================================================================

KMS (Key Management Service)
Service AWS de gestion de clés de chiffrement.
Features : rotation automatique, audit CloudTrail.

================================================================================
L
================================================================================

LAMBDA ARCHITECTURE
Pattern combinant batch layer + speed layer + serving layer.
Pas Lambda AWS (service).

LATENCY
Délai entre génération et traitement/disponibilité d'une donnée.
Kinesis Streams : < 1s, Firehose : 60s+.

================================================================================
M
================================================================================

MANAGED SERVICE
Service où le provider gère l'infrastructure.
Exemple : Kinesis Data Firehose vs Kafka self-hosted.

MAPPING
Définition de la structure et types de champs dans OpenSearch.
Explicite (recommandé) vs dynamique (inféré).

================================================================================
N
================================================================================

NEAR REAL-TIME
Traitement avec latence de quelques secondes à minutes.
Exemple : Kinesis Firehose (60s min).

================================================================================
P
================================================================================

PARTITION
Division de données pour parallélisation (terme Kafka).
Équivalent Kinesis : shard.

PIPELINE
Série d'étapes de traitement de données enchaînées.
Exemple : EC2 → Kinesis → Lambda → OpenSearch.

PRODUCER
Application qui écrit/produit des données vers un stream.
Exemple : EC2 avec agent Kinesis.

================================================================================
R
================================================================================

REAL-TIME
Traitement immédiat avec latence minimale (< 1 seconde).
Exemple : Kinesis Data Streams.

RECORD
Unité de données individuelle dans un stream.
Structure : clé partition, données, métadonnées.

REPLICA
Copie d'un shard (terme OpenSearch) pour haute disponibilité.
Améliore également performance lecture.

RETENTION
Durée de conservation des données dans un stream.
Kinesis : 24h - 365j, Kafka : configurable.

================================================================================
S
================================================================================

SCALABILITY (HORIZONTAL)
Capacité à augmenter performance en ajoutant des ressources (serveurs, shards).

SCALABILITY (VERTICAL)
Capacité à augmenter performance en augmentant puissance d'une ressource.

SERVERLESS
Modèle où le provider gère l'infrastructure automatiquement.
Exemple : AWS Lambda, Kinesis Data Firehose.

SHARD
Unité de capacité dans Kinesis Data Streams.
Capacité : 1 MB/s écriture, 2 MB/s lecture.

STREAM
Flux continu de données ordonnées.
Services : Kinesis Data Streams, Kafka.

STREAMING
Traitement continu de données au fur et à mesure de leur arrivée.

================================================================================
T
================================================================================

THROUGHPUT
Débit de données traitées par unité de temps.
Mesure : MB/s, records/s.

TOPIC
Catégorie de messages dans Kafka.
Équivalent Kinesis : stream.

TRANSFORMATION
Modification de données (parsing, enrichissement, filtrage).
Exemple : Lambda dans pipeline Kinesis.

================================================================================
V
================================================================================

VELOCITY
Un des 5 V des Big Data : rapidité de génération des données.
Streaming répond au défi de vélocité.

VPC (Virtual Private Cloud)
Réseau virtuel isolé dans AWS.
Sécurité : isolation ressources.

================================================================================
W
================================================================================

WARM DATA
Données moyennement anciennes, accès occasionnel.
Stockage : performance moyenne.

WINDOWING
Découpage du stream en fenêtres temporelles pour agrégations.
Exemples : tumbling window, sliding window.

================================================================================

