================================================================================
                           EXAMEN - QCM 2
            KINESIS - DATA STREAMS VS DATA FIREHOSE
================================================================================

Durée : 30 minutes
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

SECTION A - COMPARAISON FONCTIONNELLE (Questions 1 à 6)

Question 1 (1 point)
--------------------
Quelle est la principale différence entre Kinesis Data Streams et Kinesis Data 
Firehose en termes de gestion ?

A. Data Streams est entièrement géré, Firehose nécessite une configuration serveur
B. Data Streams nécessite un provisionnement de capacité, Firehose est entièrement géré
C. Les deux nécessitent une configuration serveur complète
D. Les deux sont identiques en termes de gestion


Question 2 (1 point)
--------------------
Quelle affirmation concernant la rétention des données est correcte ?

A. Data Streams conserve les données 24h par défaut, Firehose ne les conserve pas
B. Firehose conserve les données 7 jours, Data Streams 24h
C. Les deux conservent les données indéfiniment
D. Aucun des deux ne conserve les données


Question 3 (1 point)
--------------------
En termes de latence, quelle solution offre le traitement le plus rapide ?

A. Kinesis Data Streams (latence de l'ordre de la seconde)
B. Kinesis Data Firehose (latence de 60 secondes minimum)
C. Les deux ont la même latence
D. Cela dépend uniquement de la taille des données


Question 4 (1 point)
--------------------
Quelle solution nécessite que vous écriviez du code pour consommer les données ?

A. Kinesis Data Firehose uniquement
B. Kinesis Data Streams uniquement
C. Les deux nécessitent du code personnalisé
D. Aucune ne nécessite de code


Question 5 (1 point)
--------------------
Kinesis Data Firehose peut charger directement les données vers :
(Plusieurs réponses possibles - cochez toutes les bonnes réponses)

A. Amazon S3
B. Amazon Redshift
C. Amazon OpenSearch Service
D. Une base de données MySQL sur EC2


Question 6 (1 point)
--------------------
Dans une analogie de restaurant, Kinesis Data Streams peut être comparé à :

A. Un buffet où chaque client se sert à son rythme
B. Un service de livraison qui apporte les plats directement
C. Une cuisine qui prépare les plats
D. Une réservation de table


================================================================================

SECTION B - CAS D'USAGE ET CHOIX D'ARCHITECTURE (Questions 7 à 12)

Question 7 (1 point)
--------------------
Quel service choisir pour un cas d'usage nécessitant que plusieurs applications 
consomment les mêmes données en parallèle ?

A. Kinesis Data Firehose
B. Kinesis Data Streams
C. Les deux sont équivalents
D. Aucun des deux ne le permet


Question 8 (1 point)
--------------------
Pour un simple pipeline d'ingestion de logs vers S3 sans traitement complexe, 
quelle est la meilleure option ?

A. Kinesis Data Streams seul
B. Kinesis Data Firehose seul
C. Les deux combinés
D. Ni l'un ni l'autre


Question 9 (1 point)
--------------------
Vous devez traiter des données avec une latence inférieure à 1 seconde. 
Quelle solution privilégier ?

A. Kinesis Data Firehose
B. Kinesis Data Streams
C. Les deux offrent la même performance
D. Aucune ne peut atteindre cette latence


Question 10 (1 point)
---------------------
Dans quelle situation utiliser Kinesis Data Streams ET Data Firehose ensemble ?

A. Pour réduire les coûts
B. Pour avoir à la fois un traitement temps réel et un stockage automatique
C. C'est obligatoire dans toute architecture streaming
D. Ce n'est jamais recommandé


Question 11 (1 point)
---------------------
Pour un système d'analyse en temps réel nécessitant des transformations 
complexes avec Lambda, quelle architecture est appropriée ?

A. EC2 → Firehose → S3
B. EC2 → Data Streams → Lambda → Destination
C. EC2 → S3 → Lambda
D. EC2 → Lambda → Data Streams


Question 12 (1 point)
---------------------
Quel service permet de rejouer (replay) les données des dernières 24 heures ?

A. Kinesis Data Firehose
B. Kinesis Data Streams
C. Les deux le permettent
D. Aucun ne le permet


================================================================================

SECTION C - ARCHITECTURE ET CONFIGURATION (Questions 13 à 17)

Question 13 (1 point)
---------------------
Dans Kinesis Data Streams, qu'est-ce qu'un "shard" ?

A. Une unité de capacité de traitement
B. Un type de donnée
C. Un format de compression
D. Une région AWS


Question 14 (1 point)
---------------------
Quelle est la source de données configurée dans le laboratoire pour Kinesis 
Data Firehose ?

A. Amazon S3
B. Direct PUT
C. Kinesis Data Streams
D. Amazon DynamoDB


Question 15 (1 point)
---------------------
Dans le laboratoire, quelle fonction Lambda est associée au flux de livraison 
Firehose pour transformer les enregistrements ?

A. kinesis-transform-function
B. os-demo-lambda-function
C. firehose-processor
D. data-enrichment-function


Question 16 (1 point)
---------------------
Kinesis Data Firehose peut-il transformer les données avant de les livrer à 
leur destination ?

A. Non, il ne fait que transporter les données
B. Oui, via une fonction AWS Lambda
C. Oui, mais uniquement avec des scripts Python
D. Oui, mais uniquement pour la compression


Question 17 (1 point)
---------------------
Quelle affirmation concernant la mise à l'échelle est correcte ?

A. Data Streams se met à l'échelle automatiquement, Firehose nécessite un ajustement manuel
B. Data Streams nécessite un ajustement des shards, Firehose se met à l'échelle automatiquement
C. Les deux nécessitent une intervention manuelle
D. Les deux se mettent à l'échelle automatiquement de la même manière


================================================================================

SECTION D - SCÉNARIOS PRATIQUES (Questions 18 à 20)

Question 18 (2 points)
---------------------
Une entreprise de télécommunications doit :
- Ingérer des logs de millions d'appareils IoT
- Stocker les données brutes dans S3
- Analyser en temps réel pour détecter des anomalies
- Archiver dans Redshift pour des rapports mensuels

Quelle architecture recommanderiez-vous ?

A. Data Streams → Lambda (analyse) + Firehose → S3 + Redshift
B. Firehose → S3 uniquement
C. Data Streams → S3 → Lambda
D. EC2 → S3 → Redshift


Question 19 (1 point)
---------------------
Dans le laboratoire, l'agent Kinesis installé sur Linux collecte les logs 
Apache. Pourquoi Direct PUT a-t-il été choisi comme source pour Firehose ?

A. C'est l'option la moins chère
B. C'est la seule option disponible
C. Car l'instance EC2 utilise Linux et Apache, permettant l'usage de Kinesis Agent
D. Pour des raisons de sécurité uniquement


Question 20 (1 point)
---------------------
Si vous devez implémenter un système où plusieurs équipes ont besoin d'accéder 
aux mêmes données streaming avec des logiques de traitement différentes, 
quelle solution est préférable ?

A. Créer plusieurs flux Firehose indépendants
B. Utiliser Data Streams avec plusieurs consommateurs
C. Stocker d'abord dans S3 puis distribuer
D. Utiliser un seul consommateur qui redistribue les données


================================================================================
FIN DE L'EXAMEN
================================================================================

