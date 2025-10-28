================================================================================
                           EXAMEN - QCM 6
      COMPARAISON TECHNOLOGIES STREAMING - KINESIS VS KAFKA
================================================================================

Durée : 35 minutes
Note sur : 20 points
Documents non autorisés

================================================================================
INSTRUCTIONS
================================================================================

- Cet examen comporte 20 questions à choix multiples
- Chaque question vaut 1 point
- Pour chaque question, une seule réponse est correcte sauf indication contraire
- Aucun point ne sera retiré pour une mauvaise réponse
- Répondez directement sur le sujet d'examen
- Veillez à la clarté de vos réponses

================================================================================
QUESTIONS
================================================================================

SECTION A - KINESIS VS KAFKA FONDAMENTAUX (Questions 1 à 6)

Question 1 (1 point)
--------------------
Amazon Kinesis est un service :

A. Open-source hébergé par Apache
B. Entièrement géré par AWS
C. Qui nécessite une installation manuelle sur des serveurs
D. Uniquement disponible pour les applications Java


Question 2 (1 point)
--------------------
Apache Kafka est :

A. Un service cloud propriétaire d'AWS
B. Un produit commercial fermé
C. Une plateforme de streaming distribuée open-source
D. Un service exclusif à Microsoft Azure


Question 3 (1 point)
--------------------
En termes de gestion opérationnelle, quelle affirmation est correcte ?

A. Kinesis nécessite plus de gestion que Kafka
B. Kafka nécessite la gestion de l'infrastructure (serveurs, monitoring, patches)
C. Les deux nécessitent exactement la même charge de gestion
D. Aucun ne nécessite de gestion


Question 4 (1 point)
--------------------
Dans AWS, quel service Kinesis est le plus comparable à Apache Kafka ?

A. Kinesis Video Streams
B. Kinesis Data Analytics
C. Kinesis Data Streams
D. Kinesis Data Firehose


Question 5 (1 point)
--------------------
Apache Kafka utilise des "topics" pour organiser les données. L'équivalent dans 
Kinesis Data Streams est :

A. Les buckets
B. Les streams
C. Les queues
D. Les tables


Question 6 (1 point)
--------------------
En termes de rétention des données par défaut :

A. Kinesis conserve les données 7 jours, Kafka 7 jours également
B. Kinesis 24 heures, Kafka peut être configuré (par défaut 7 jours)
C. Les deux conservent indéfiniment
D. Aucun ne conserve les données


================================================================================

SECTION B - ARCHITECTURE ET PERFORMANCES (Questions 7 à 11)

Question 7 (1 point)
--------------------
Dans Kinesis, une unité de capacité s'appelle :

A. Un partition
B. Un shard
C. Un broker
D. Un node


Question 8 (1 point)
--------------------
Dans Kafka, les données sont organisées en :

A. Shards
B. Streams
C. Topics divisés en partitions
D. Files d'attente


Question 9 (1 point)
--------------------
Quelle technologie offre généralement un débit plus élevé pour des charges de 
travail très importantes ?

A. Kinesis Data Streams
B. Apache Kafka
C. Les deux offrent exactement les mêmes performances
D. Aucune n'est performante


Question 10 (1 point)
---------------------
La mise à l'échelle horizontale dans Kafka se fait en :

A. Ajoutant des shards
B. Ajoutant des brokers et des partitions
C. Augmentant la mémoire RAM
D. Changeant de région AWS


Question 11 (1 point)
---------------------
Pour une entreprise déjà présente sur AWS avec peu d'expertise en systèmes 
distribués, quelle solution est généralement plus adaptée ?

A. Apache Kafka auto-hébergé
B. Amazon Kinesis
C. Les deux nécessitent la même expertise
D. Aucune n'est adaptée


================================================================================

SECTION C - ECOSYSTEME ET ALTERNATIVES (Questions 12 à 16)

Question 12 (1 point)
---------------------
Parmi les alternatives suivantes à Kafka, laquelle est développée par Apache 
et conçue pour la messagerie multi-tenant ?

A. RabbitMQ
B. Apache Pulsar
C. Google Pub/Sub
D. Amazon SQS


Question 13 (1 point)
---------------------
RabbitMQ est principalement utilisé pour :

A. Le stockage de fichiers
B. La messagerie avec files d'attente et routage complexe
C. L'indexation de documents
D. L'authentification des utilisateurs


Question 14 (1 point)
---------------------
Apache Pulsar se différencie de Kafka par :

A. Il n'y a aucune différence
B. Architecture découplant le stockage et le calcul, support multi-tenant natif
C. Il est plus ancien que Kafka
D. Il ne supporte pas le streaming


Question 15 (1 point)
---------------------
Amazon MSK (Managed Streaming for Apache Kafka) est :

A. Une alternative à Kafka
B. Un service AWS qui gère Kafka pour vous
C. Un remplacement de Kinesis
D. Une base de données relationnelle


Question 16 (1 point)
---------------------
Parmi les outils suivants, lequel N'est PAS une alternative de streaming de 
données ?

A. Apache Flink
B. Apache Storm
C. Apache Cassandra
D. Google Cloud Dataflow


================================================================================

SECTION D - CAS D'USAGE ET CHOIX TECHNOLOGIQUES (Questions 17 à 20)

Question 17 (2 points)
---------------------
Une startup avec une équipe réduite souhaite implémenter un pipeline de 
streaming sur AWS pour analyser des logs en temps réel. Elle privilégie la 
simplicité opérationnelle. Quelle solution recommandez-vous ?

A. Apache Kafka auto-hébergé sur EC2
B. Amazon Kinesis Data Streams
C. Apache Pulsar sur Kubernetes
D. Développer une solution custom


Question 18 (2 points)
---------------------
Une grande entreprise dispose déjà d'une expertise Kafka en interne et veut 
migrer vers AWS tout en conservant cette technologie. Quelle solution est 
appropriée ?

A. Migrer vers Kinesis et former l'équipe
B. Utiliser Amazon MSK (Managed Streaming for Kafka)
C. Héberger Kafka sur des serveurs physiques
D. Abandonner le streaming


Question 19 (1 point)
---------------------
Pour un cas d'usage nécessitant une rétention des données de plusieurs mois 
avec rejoue fréquente, quelle solution est plus naturellement adaptée ?

A. Kinesis Data Streams (nécessite configuration spéciale)
B. Apache Kafka (rétention configurable facilement)
C. Les deux sont identiques
D. Aucune ne peut le faire


Question 20 (1 point)
---------------------
La principale différence entre Kafka et Pulsar en termes d'architecture est :

A. Il n'y a aucune différence architecturale
B. Pulsar sépare le stockage (BookKeeper) et le traitement (brokers)
C. Kafka est plus moderne que Pulsar
D. Pulsar ne supporte pas les partitions


================================================================================
FIN DE L'EXAMEN
================================================================================

