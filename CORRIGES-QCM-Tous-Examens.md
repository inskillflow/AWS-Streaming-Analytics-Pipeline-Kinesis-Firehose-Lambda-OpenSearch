================================================================================
                    CORRIGES DES EXAMENS QCM
          INGENIERIE DES DONNEES - AWS STREAMING
================================================================================

IMPORTANT : Ce document contient les réponses correctes de tous les examens.
Ne pas consulter avant d'avoir complété les examens.

================================================================================

QCM 1 : FONDAMENTAUX AWS ET ARCHITECTURE DE STREAMING
================================================================================

SECTION A - Services AWS Fondamentaux

Question 1 : C
Explication : EC2 héberge le serveur web Apache et génère les logs d'accès.

Question 2 : B
Explication : Kinesis Data Firehose collecte, transforme et charge des données 
en streaming vers d'autres services.

Question 3 : C
Explication : Lambda est déclenché par Kinesis Data Firehose pour transformer 
les données.

Question 4 : C
Explication : Amazon OpenSearch Service est utilisé pour l'indexation, le 
stockage et la recherche rapide.

Question 5 : B
Explication : Amazon Cognito gère l'authentification et les identités des 
utilisateurs.

SECTION B - Workflow et Flux de Données

Question 6 : C
Explication : Après qu'un visiteur consulte une page, EC2 génère un log d'accès.

Question 7 : B
Explication : L'agent Kinesis collecte et envoie les logs vers Kinesis Data 
Firehose.

Question 8 : C
Explication : Lambda enrichit les données avec géolocalisation, OS et navigateur.

Question 9 : A
Explication : Amazon CloudWatch Logs permet de surveiller en temps réel les 
événements et logs.

Question 10 : B
Explication : Le flux correct est EC2 → Kinesis → Lambda → OpenSearch.

SECTION C - Architecture et Concepts

Question 11 : C
Explication : La Vélocité correspond aux données de streaming temps réel.

Question 12 : B
Explication : AWS IAM garantit que seuls les utilisateurs autorisés accèdent 
aux ressources.

Question 13 : C
Explication : OpenSearch Dashboards crée des visualisations interactives.

Question 14 : B
Explication : POC signifie Proof of Concept (Preuve de Concept).

Question 15 : B
Explication : Le processus complet prend quelques millisecondes.

SECTION D - Mise en Situation

Question 16 : C
Explication : Amazon Redshift n'est pas nécessaire dans l'architecture de base.

Question 17 : B
Explication : Lambda ajoute géolocalisation, OS et navigateur.

Question 18 : B
Explication : État "Yellow" signifie que tous les fragments primaires sont 
alloués mais au moins une réplique ne l'est pas.

Question 19 : B
Explication : Il faut configurer un index pattern avant de créer des graphiques.

Question 20 : B
Explication : Les visiteurs utilisent des navigateurs qui bloquent les scripts 
tiers.

================================================================================

QCM 2 : KINESIS - DATA STREAMS VS DATA FIREHOSE
================================================================================

SECTION A - Comparaison Fonctionnelle

Question 1 : B
Explication : Data Streams nécessite provisionnement de capacité, Firehose est 
entièrement géré.

Question 2 : A
Explication : Data Streams conserve 24h par défaut, Firehose ne conserve pas.

Question 3 : A
Explication : Data Streams offre une latence de l'ordre de la seconde.

Question 4 : B
Explication : Kinesis Data Streams nécessite du code pour consommer les données.

Question 5 : A, B, C
Explication : Firehose peut charger vers S3, Redshift et OpenSearch Service.

Question 6 : A
Explication : Data Streams est comme un buffet où chaque client se sert.

SECTION B - Cas d'Usage et Choix d'Architecture

Question 7 : B
Explication : Data Streams permet plusieurs consommateurs en parallèle.

Question 8 : B
Explication : Firehose seul suffit pour un simple pipeline vers S3.

Question 9 : B
Explication : Data Streams offre une latence inférieure à 1 seconde.

Question 10 : B
Explication : Utiliser les deux permet traitement temps réel + stockage 
automatique.

Question 11 : B
Explication : Data Streams → Lambda permet des transformations complexes.

Question 12 : B
Explication : Data Streams permet de rejouer les données des dernières 24h.

SECTION C - Architecture et Configuration

Question 13 : A
Explication : Un shard est une unité de capacité de traitement.

Question 14 : B
Explication : La source configurée est Direct PUT.

Question 15 : B
Explication : La fonction Lambda est os-demo-lambda-function.

Question 16 : B
Explication : Firehose peut transformer via AWS Lambda.

Question 17 : B
Explication : Data Streams nécessite ajustement des shards, Firehose s'adapte 
automatiquement.

SECTION D - Scénarios Pratiques

Question 18 : A
Explication : Data Streams → Lambda (analyse) + Firehose → S3 + Redshift.

Question 19 : C
Explication : Direct PUT car l'instance utilise Linux et Apache avec Kinesis 
Agent.

Question 20 : B
Explication : Data Streams permet plusieurs consommateurs avec logiques 
différentes.

================================================================================

QCM 3 : TRANSFORMATION ET ENRICHISSEMENT AVEC AWS LAMBDA
================================================================================

SECTION A - Rôle de EC2 et Génération de Logs

Question 1 : B
Explication : Le serveur web installé est Apache.

Question 2 : A
Explication : Les logs contiennent IP, page visitée, heure, navigateur.

Question 3 : B
Explication : Le fichier agent.json permet la connexion à Kinesis Firehose.

Question 4 : B
Explication : L'instance EC2 se trouve dans un sous-réseau public.

SECTION B - AWS Lambda et Transformation

Question 5 : B
Explication : Lambda est un service serverless (sans serveur).

Question 6 : B
Explication : Lambda est déclenché automatiquement par Kinesis Firehose.

Question 7 : A, B, C
Explication : Lambda enrichit avec géolocalisation, OS et navigateur.

Question 8 : B
Explication : "Incoming Record" montre les données avant enrichissement.

Question 9 : B
Explication : "Transformed Record" montre les données enrichies.

Question 10 : B
Explication : "REPORT RequestId" fournit durée d'exécution et mémoire utilisée.

Question 11 : C
Explication : Lambda est facturé sur durée d'exécution et ressources utilisées.

SECTION C - Pipeline Complet

Question 12 : B
Explication : Firehose est le système de transport et logistique.

Question 13 : A
Explication : Lambda est le coordinateur qui organise et améliore.

Question 14 : B
Explication : Le pipeline permet collecte, transformation et indexation 
automatique.

Question 15 : C
Explication : Les données apparaissent en quelques millisecondes à secondes.

Question 16 : B
Explication : CloudWatch Logs est utilisé pour observer le traitement.

SECTION D - Choix d'Architecture et Scénarios

Question 17 : B
Explication : Lambda avec Firehose permet enrichissement en temps réel avant 
indexation.

Question 18 : B
Explication : Lambda dans Firehose permet enrichissement en temps réel.

Question 19 : B
Explication : EC2 → Kinesis Firehose → Lambda → OpenSearch minimise la latence.

Question 20 : B
Explication : Le rôle permet lire/écrire S3 et envoyer données à Kinesis.

================================================================================

QCM 4 : SECURITE ET ENCRYPTION DANS LES PIPELINES AWS
================================================================================

SECTION A - Authentification et Cognito

Question 1 : B
Explication : Cognito gère l'authentification et les identités.

Question 2 : B
Explication : Seuls les utilisateurs authentifiés via Cognito peuvent accéder.

Question 3 : A
Explication : Le rôle permet à OpenSearch d'utiliser Cognito pour 
authentification.

Question 4 : B
Explication : L'utilisateur doit changer son mot de passe temporaire.

Question 5 : B
Explication : Cognito gère les identités, IAM gère les permissions.

SECTION B - Encryption en Transit et au Repos

Question 6 : B
Explication : L'encryption en transit protège pendant le transfert réseau.

Question 7 : B
Explication : L'encryption au repos protège les données stockées sur disque.

Question 8 : C
Explication : TLS/SSL (HTTPS) est utilisé pour l'encryption en transit.

Question 9 : B
Explication : KMS crée et contrôle les clés de chiffrement.

Question 10 : C
Explication : L'encryption peut être activée en transit et au repos.

SECTION C - Configuration Encryption Kinesis

Question 11 : B
Explication : Les données sont chiffrées après réception par Kinesis.

Question 12 : C
Explication : Une clé AWS KMS ou gérée par AWS peut être utilisée.

Question 13 : B
Explication : KMS offre gestion centralisée avec rotation automatique possible.

Question 14 : B
Explication : Sans encryption, les données transitent et sont stockées en clair.

Question 15 : B
Explication : Configuration dans le flux de livraison Firehose.

SECTION D - IAM et Politiques de Sécurité

Question 16 : A, B, C
Explication : Le rôle permet accès S3, invocation Lambda et création logs 
CloudWatch.

Question 17 : B
Explication : Une politique IAM définit permissions et actions autorisées.

Question 18 : A
Explication : OsDemoWebserverIAMPolicy permet à EC2 d'écrire dans S3.

Question 19 : A
Explication : Cognito + IAM + KMS sont nécessaires pour cette architecture 
sécurisée.

Question 20 : B
Explication : Principe du moindre privilège = accorder uniquement les 
permissions nécessaires.

================================================================================

QCM 5 : OPENSEARCH - INDEXATION, LIMITES ET OPTIMISATIONS
================================================================================

SECTION A - Concepts d'Indexation

Question 1 : A
Explication : L'indexation organise les données pour récupération rapide.

Question 2 : C
Explication : L'unité de base est un document JSON.

Question 3 : B
Explication : L'index créé est apache_logs.

Question 4 : B
Explication : Les mappings définissent types de données et structure des champs.

Question 5 : B
Explication : 10 shards sont configurés pour apache_logs.

SECTION B - Limites et Capacités

Question 6 : B
Explication : Un cluster à nœud unique est typiquement en état Yellow.

Question 7 : B
Explication : Yellow signifie fragments primaires alloués mais répliques non 
allouées.

Question 8 : B
Explication : Augmenter le nombre de nœuds à 2+ passe le cluster en Green.

Question 9 : C
Explication : Les limites dépendent du type et nombre d'instances.

Question 10 : B
Explication : Stratégie chaude/froide optimise les coûts de stockage.

SECTION C - Configuration et Utilisation

Question 11 : C
Explication : La méthode PUT crée un index.

Question 12 : B
Explication : Le champ datetime est utilisé pour le modèle d'index.

Question 13 : B
Explication : Index pattern est nécessaire pour créer visualisations.

Question 14 : B
Explication : DELETE supprime l'index apache_logs s'il existe.

Question 15 : A, B, C
Explication : Les types incluent text, keyword et date.

SECTION D - Alternatives et Optimisations

Question 16 : B
Explication : OpenSearch est un fork d'Elasticsearch.

Question 17 : B
Explication : Algolia est spécialisé dans la recherche textuelle rapide.

Question 18 : B
Explication : Solr est une plateforme de recherche basée sur Lucene.

Question 19 : A, B, C
Explication : Plusieurs nœuds, répliques et stratégie chaude/froide sont 
recommandés.

Question 20 : D
Explication : Désactiver l'indexation n'est PAS une solution appropriée.

================================================================================

QCM 6 : COMPARAISON TECHNOLOGIES STREAMING - KINESIS VS KAFKA
================================================================================

SECTION A - Kinesis vs Kafka Fondamentaux

Question 1 : B
Explication : Kinesis est entièrement géré par AWS.

Question 2 : C
Explication : Kafka est une plateforme de streaming distribuée open-source.

Question 3 : B
Explication : Kafka nécessite gestion de l'infrastructure.

Question 4 : C
Explication : Kinesis Data Streams est comparable à Kafka.

Question 5 : B
Explication : L'équivalent des topics Kafka est les streams Kinesis.

Question 6 : B
Explication : Kinesis 24h, Kafka configurable (défaut 7 jours).

SECTION B - Architecture et Performances

Question 7 : B
Explication : Une unité de capacité Kinesis est un shard.

Question 8 : C
Explication : Kafka utilise topics divisés en partitions.

Question 9 : B
Explication : Kafka offre généralement un débit plus élevé.

Question 10 : B
Explication : Kafka se met à l'échelle en ajoutant brokers et partitions.

Question 11 : B
Explication : Amazon Kinesis est plus adapté pour les entreprises AWS avec peu 
d'expertise.

SECTION C - Ecosystème et Alternatives

Question 12 : B
Explication : Apache Pulsar est développé par Apache pour multi-tenant.

Question 13 : B
Explication : RabbitMQ est utilisé pour messagerie avec files d'attente.

Question 14 : B
Explication : Pulsar découple stockage et calcul, support multi-tenant natif.

Question 15 : B
Explication : Amazon MSK est un service AWS qui gère Kafka.

Question 16 : C
Explication : Apache Cassandra est une base de données, pas du streaming.

SECTION D - Cas d'Usage et Choix Technologiques

Question 17 : B
Explication : Amazon Kinesis Data Streams pour simplicité opérationnelle.

Question 18 : B
Explication : Amazon MSK permet de conserver Kafka sur AWS.

Question 19 : B
Explication : Kafka permet rétention configurable facilement.

Question 20 : B
Explication : Pulsar sépare stockage (BookKeeper) et traitement (brokers).

================================================================================

QCM 7 : LABORATOIRE PRATIQUE - IMPLEMENTATION COMPLETE
================================================================================

SECTION A - Tâches 1-3 : Vérification des Ressources

Question 1 : B
Explication : Console EC2, section Instances pour trouver l'IP publique.

Question 2 : C
Explication : Le nom de l'instance est OpenSearch Demo.

Question 3 : B
Explication : Le rôle IAM est OsDemoWebserverIAMRole.

Question 4 : B
Explication : Le flux est os-demo-firehose-stream.

Question 5 : C
Explication : La source configurée est Direct PUT.

Question 6 : B
Explication : Le domaine OpenSearch est os-demo.

SECTION B - Tâches 4-6 : Configuration et Génération

Question 7 : C
Explication : Se connecter avec Cognito avant d'accéder à Dev Tools.

Question 8 : B
Explication : Le mot de passe initial est Passw0rd1!

Question 9 : A
Explication : Le nouveau mot de passe est Passw0rd1!2

Question 10 : C
Explication : number_of_shards est défini à 10.

Question 11 : B
Explication : Accéder via http://<PUBLIC-IP>/main.php

Question 12 : B
Explication : Utiliser au moins deux navigateurs différents.

SECTION C - Tâche 6 : CloudWatch et Monitoring

Question 13 : B
Explication : Le groupe de journaux est /aws/lambda/aes-demo-lambda-function.

Question 14 : B
Explication : "Incoming Record" montre données brutes avant enrichissement.

Question 15 : A, B
Explication : REPORT fournit durée d'exécution et mémoire utilisée.

SECTION D - Tâches 7-9 : Visualisations

Question 16 : B
Explication : Accéder à la section Discover pour créer index pattern.

Question 17 : B
Explication : Le champ temporel est datetime.

Question 18 : B
Explication : Utiliser l'agrégation Terms pour les buckets.

Question 19 : B
Explication : L'axe X représente la page de référence (refering_page).

Question 20 : B
Explication : La page de recherche est plus efficace pour diriger les 
utilisateurs.

================================================================================

QCM 8 : INGENIERIE DES DONNEES - CONCEPTS TRANSVERSAUX
================================================================================

SECTION A - Les Cinq V des Big Data

Question 1 : B
Explication : Volume désigne la quantité massive de données.

Question 2 : C
Explication : Vélocité correspond à la rapidité de génération et traitement.

Question 3 : C
Explication : Variété fait référence aux différents types et formats de données.

Question 4 : B
Explication : Véracité concerne la qualité et fiabilité des données.

SECTION B - Architectures de Traitement

Question 5 : C
Explication : Architecture Lambda combine traitement batch et streaming.

Question 6 : B
Explication : Architecture Kappa utilise uniquement le traitement streaming.

Question 7 : B
Explication : Latence = délai entre génération et traitement des données.

Question 8 : A
Explication : EC2 (Extract) → Lambda (Transform) → OpenSearch (Load).

Question 9 : B
Explication : Streaming est temps réel, batch traite par lots périodiques.

SECTION C - Patterns d'Ingénierie des Données

Question 10 : B
Explication : Enrichissement = ajouter informations supplémentaires.

Question 11 : A
Explication : Data Lake = stockage centralisé pour données brutes tous types.

Question 12 : B
Explication : Data Warehouse est optimisé pour analyse et requêtes structurées.

Question 13 : B
Explication : Lambda fait de l'enrichissement temps réel dans pipeline streaming.

Question 14 : A
Explication : Idempotence = traiter plusieurs fois produit même résultat.

SECTION D - Monitoring et Observabilité

Question 15 : C
Explication : CloudWatch surveille et loggue événements et métriques.

Question 16 : A, B, C
Explication : Métriques importantes : latence, taux d'erreurs, débit.

Question 17 : B
Explication : Trois piliers de l'observabilité : Logs, Métriques, Traces.

SECTION E - Cas d'Usage Métier

Question 18 : B
Explication : Objectif = analyser comportement visiteurs temps réel via logs.

Question 19 : B
Explication : Architecture streaming temps réel + stockage pour historique.

Question 20 : A, B, C
Explication : Réplication multi-zones, monitoring temps réel et sauvegarde sont 
essentiels.

================================================================================

STATISTIQUES PAR EXAMEN
================================================================================

QCM 1 : 20 questions
QCM 2 : 20 questions (dont 1 question à réponses multiples)
QCM 3 : 20 questions (dont 1 question à réponses multiples)
QCM 4 : 20 questions (dont 2 questions à réponses multiples)
QCM 5 : 20 questions (dont 2 questions à réponses multiples)
QCM 6 : 20 questions
QCM 7 : 20 questions (dont 1 question à réponses multiples)
QCM 8 : 20 questions (dont 3 questions à réponses multiples)

TOTAL : 160 questions

================================================================================

RECOMMANDATIONS APRES CONSULTATION DES CORRIGES
================================================================================

SCORE 18-20/20
--------------
Excellente maîtrise. Continuer sur cette lancée.
Recommandation : Passer au QCM suivant ou approfondir avec des projets pratiques.

SCORE 15-17/20
--------------
Très bonne compréhension. Quelques révisions ponctuelles nécessaires.
Recommandation : Revoir les concepts des questions manquées puis avancer.

SCORE 12-14/20
--------------
Bonne base mais des lacunes existent.
Recommandation : Réviser les chapitres concernés avant de passer au QCM suivant.

SCORE 10-11/20
--------------
Connaissances minimales atteintes mais fragiles.
Recommandation : Révision approfondie des chapitres puis refaire le QCM.

SCORE < 10/20
-------------
Connaissances insuffisantes.
Recommandation : Étude complète des chapitres concernés, puis refaire le QCM 
avant de continuer.

================================================================================

VERSION
================================================================================

Document : CORRIGES DES EXAMENS QCM
Version : 1.0
Date : Octobre 2025
Auteur : Documentation AWS Services - Ingénierie des Données

================================================================================
FIN DU DOCUMENT DES CORRIGES
================================================================================

