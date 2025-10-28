================================================================================
                           EXAMEN - QCM 1
         FONDAMENTAUX AWS ET ARCHITECTURE DE STREAMING
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

SECTION A - SERVICES AWS FONDAMENTAUX (Questions 1 à 5)

Question 1 (1 point)
--------------------
Dans le contexte d'une architecture de streaming temps réel, quel est le rôle 
principal d'Amazon EC2 dans le laboratoire étudié ?

A. Héberger le cluster OpenSearch
B. Exécuter les fonctions Lambda
C. Héberger le serveur web Apache et générer les logs d'accès
D. Gérer l'authentification des utilisateurs


Question 2 (1 point)
--------------------
Amazon Kinesis Data Firehose est utilisé dans l'architecture pour :

A. Stocker les données de manière permanente
B. Collecter, transformer et charger des données en streaming vers d'autres services
C. Remplacer AWS Lambda dans le traitement des données
D. Authentifier les utilisateurs accédant aux dashboards


Question 3 (1 point)
--------------------
AWS Lambda dans cette architecture est déclenché par :

A. Amazon EC2 directement
B. Amazon Cognito
C. Amazon Kinesis Data Firehose
D. OpenSearch Dashboards


Question 4 (1 point)
--------------------
Quel service AWS est utilisé pour l'indexation, le stockage et la recherche 
rapide dans les logs ?

A. Amazon S3
B. Amazon DynamoDB
C. Amazon OpenSearch Service
D. Amazon RDS


Question 5 (1 point)
--------------------
Amazon Cognito dans cette architecture a pour fonction principale de :

A. Transformer les données en temps réel
B. Gérer l'authentification et les identités des utilisateurs
C. Stocker les logs du serveur web
D. Surveiller les performances du système


================================================================================

SECTION B - WORKFLOW ET FLUX DE DONNÉES (Questions 6 à 10)

Question 6 (1 point)
--------------------
Dans le workflow complet, quelle est la première étape après qu'un visiteur 
consulte une page web ?

A. Lambda enrichit les données
B. Kinesis Firehose collecte les logs
C. EC2 génère un log d'accès
D. OpenSearch indexe les données


Question 7 (1 point)
--------------------
L'agent Kinesis installé sur l'instance EC2 a pour rôle de :

A. Transformer les logs avant envoi
B. Collecter et envoyer les logs vers Kinesis Data Firehose
C. Authentifier les requêtes HTTP
D. Visualiser les données en temps réel


Question 8 (1 point)
--------------------
Dans le flux de données, à quel moment les données sont-elles enrichies avec 
des informations de géolocalisation ?

A. Lors de la génération du log sur EC2
B. Lors du passage dans Kinesis Data Firehose
C. Lors du traitement par AWS Lambda
D. Lors de l'indexation dans OpenSearch


Question 9 (1 point)
--------------------
Quel service permet de surveiller en temps réel les événements et les logs 
applicatifs ?

A. Amazon CloudWatch Logs
B. Amazon S3
C. Amazon Cognito
D. AWS IAM


Question 10 (1 point)
---------------------
Dans l'ordre correct, le flux de données suit le chemin :

A. EC2 → Lambda → Kinesis → OpenSearch
B. EC2 → Kinesis → Lambda → OpenSearch
C. EC2 → OpenSearch → Lambda → Kinesis
D. EC2 → Lambda → OpenSearch → Kinesis


================================================================================

SECTION C - ARCHITECTURE ET CONCEPTS (Questions 11 à 15)

Question 11 (1 point)
---------------------
Les problèmes liés aux mégadonnées nécessitent des solutions en temps réel. 
Parmi les cinq V des mégadonnées, lequel correspond aux données de streaming ?

A. Volume
B. Variété
C. Vélocité
D. Véracité


Question 12 (1 point)
---------------------
Dans l'architecture du laboratoire, quel composant garantit que seuls les 
utilisateurs autorisés peuvent accéder aux ressources ?

A. Amazon S3
B. AWS IAM (Identity and Access Management)
C. Amazon Kinesis
D. Amazon CloudWatch


Question 13 (1 point)
---------------------
OpenSearch Dashboards est utilisé pour :

A. Collecter les logs du serveur web
B. Transformer les données en temps réel
C. Créer des visualisations interactives des données indexées
D. Gérer les permissions des utilisateurs


Question 14 (1 point)
---------------------
Dans le contexte du laboratoire, que signifie l'acronyme POC ?

A. Point of Contact
B. Proof of Concept (Preuve de Concept)
C. Protocol of Communication
D. Power of Cloud


Question 15 (1 point)
---------------------
Quelle est la durée approximative du processus d'ingestion, transformation et 
indexation des logs dans l'architecture présentée ?

A. Plusieurs secondes
B. Quelques millisecondes
C. Plusieurs minutes
D. Une heure


================================================================================

SECTION D - MISE EN SITUATION (Questions 16 à 20)

Question 16 (1 point)
---------------------
Une entreprise souhaite analyser les comportements des visiteurs de son site 
e-commerce en temps réel. Parmi les services suivants, lequel N'est PAS 
nécessaire dans l'architecture de base ?

A. Amazon EC2 pour héberger le site web
B. Amazon Kinesis pour collecter les données
C. Amazon Redshift pour l'entreposage de données
D. AWS Lambda pour enrichir les données


Question 17 (1 point)
---------------------
Dans le laboratoire, les journaux d'accès Apache contiennent initialement des 
informations telles que l'adresse IP, la page visitée et l'heure. Quel type 
d'enrichissement Lambda effectue-t-il sur ces données ?

A. Compression des données pour réduire leur taille
B. Ajout de la géolocalisation, du système d'exploitation et du navigateur
C. Suppression des données sensibles
D. Conversion des données en format binaire


Question 18 (1 point)
---------------------
Si le cluster OpenSearch Service présente un état "Yellow" dans un 
environnement à nœud unique, cela signifie :

A. Le cluster est en panne et nécessite une intervention immédiate
B. Tous les fragments primaires sont alloués mais au moins une réplique ne l'est pas
C. Le cluster fonctionne de manière optimale
D. Il y a une erreur de configuration critique


Question 19 (1 point)
---------------------
Pour visualiser les données dans OpenSearch Dashboards, quelle étape est 
nécessaire avant de créer des graphiques ?

A. Créer un bucket S3
B. Configurer un index pattern
C. Redémarrer le service Lambda
D. Modifier la politique IAM


Question 20 (1 point)
---------------------
Dans le scénario du laboratoire, l'administratrice du site web de la librairie 
universitaire cherche une solution pour obtenir des données plus précises car :

A. Le système actuel est trop coûteux
B. Les visiteurs utilisent des navigateurs qui bloquent les scripts tiers
C. Le serveur web est surchargé
D. Les données sont stockées trop longtemps


================================================================================
FIN DE L'EXAMEN
================================================================================

