================================================================================
                           EXAMEN - QCM 7
           LABORATOIRE PRATIQUE - IMPLEMENTATION COMPLETE
================================================================================

Durée : 40 minutes
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

SECTION A - TACHES 1-3 : VERIFICATION DES RESSOURCES (Questions 1 à 6)

Question 1 (1 point)
--------------------
Dans la Tâche 1, pour trouver l'adresse IP publique de l'instance EC2, vous 
devez accéder à :

A. La console Lambda
B. La console EC2, section Instances
C. La console S3
D. La console OpenSearch directement


Question 2 (1 point)
--------------------
Le nom de l'instance EC2 dans le laboratoire est :

A. WebServer
B. ApacheServer
C. OpenSearch Demo
D. Kinesis Instance


Question 3 (1 point)
--------------------
Le rôle IAM attaché à l'instance EC2 du serveur web se nomme :

A. EC2Role
B. OsDemoWebserverIAMRole
C. LambdaExecutionRole
D. AdminRole


Question 4 (1 point)
--------------------
Dans la Tâche 2, le nom du flux de livraison Kinesis Data Firehose est :

A. demo-stream
B. os-demo-firehose-stream
C. kinesis-delivery-stream
D. apache-log-stream


Question 5 (1 point)
--------------------
La source configurée pour le flux de livraison Kinesis Data Firehose est :

A. Kinesis Data Streams
B. Amazon S3
C. Direct PUT
D. DynamoDB Streams


Question 6 (1 point)
--------------------
Dans la Tâche 3, le nom du domaine OpenSearch Service est :

A. opensearch-cluster
B. os-demo
C. elasticsearch-domain
D. search-domain


================================================================================

SECTION B - TACHES 4-6 : CONFIGURATION ET GENERATION (Questions 7 à 12)

Question 7 (1 point)
--------------------
Dans la Tâche 4, pour accéder à la console Dev Tools dans OpenSearch 
Dashboards, vous devez d'abord :

A. Installer un plugin
B. Créer un index pattern
C. Vous connecter avec les identifiants Cognito
D. Redémarrer le cluster


Question 8 (1 point)
--------------------
Le mot de passe initial pour se connecter à OpenSearch Dashboards est :

A. Admin123!
B. Passw0rd1!
C. Password123
D. OpenSearch2024!


Question 9 (1 point)
--------------------
Après la première connexion, le nouveau mot de passe configuré est :

A. Passw0rd1!2
B. NewPassw0rd!
C. Passw0rd123
D. Admin123!2


Question 10 (1 point)
---------------------
Dans la commande de création d'index, le paramètre "number_of_shards" est 
défini à :

A. 1
B. 5
C. 10
D. 20


Question 11 (1 point)
---------------------
Dans la Tâche 5, pour générer des logs, vous devez accéder au site web via :

A. https://<PUBLIC-IP>/index.html
B. http://<PUBLIC-IP>/main.php
C. http://<PUBLIC-IP>/
D. https://<PUBLIC-IP>/home.html


Question 12 (1 point)
---------------------
Pour diversifier les résultats dans le laboratoire, il est recommandé d'utiliser :

A. Le même navigateur sur le même appareil
B. Au moins deux navigateurs web différents
C. Uniquement Internet Explorer
D. Une seule page du site


================================================================================

SECTION C - TACHE 6 : CLOUDWATCH ET MONITORING (Questions 13 à 15)

Question 13 (1 point)
---------------------
Dans CloudWatch Logs, le groupe de journaux pour observer les événements 
Lambda est :

A. /aws/lambda/kinesis-function
B. /aws/lambda/aes-demo-lambda-function
C. /aws/ec2/logs
D. /aws/opensearch/logs


Question 14 (1 point)
---------------------
Un événement "Incoming Record from Kinesis Firehose" dans CloudWatch montre :

A. Les données après transformation Lambda
B. Les données brutes avant enrichissement
C. Les métriques de performance uniquement
D. Les erreurs système


Question 15 (1 point)
---------------------
L'événement "REPORT RequestId" dans CloudWatch fournit des informations sur :
(Plusieurs réponses possibles - cochez toutes les bonnes réponses)

A. La durée d'exécution de Lambda
B. La mémoire utilisée
C. Le nombre de visiteurs
D. Les coûts de facturation détaillés


================================================================================

SECTION D - TACHES 7-9 : VISUALISATIONS (Questions 16 à 20)

Question 16 (1 point)
---------------------
Dans la Tâche 7, pour créer un index pattern, vous devez accéder à la section :

A. Management
B. Discover
C. Visualize
D. Dev Tools


Question 17 (1 point)
---------------------
Le champ temporel utilisé pour le filtrage dans l'index pattern est :

A. timestamp
B. datetime
C. created_at
D. log_time


Question 18 (2 points)
---------------------
Dans la Tâche 8, pour créer un graphique circulaire (pie chart) montrant les 
systèmes d'exploitation et navigateurs, vous devez créer des buckets avec 
l'agrégation :

A. Histogram
B. Terms
C. Date Histogram
D. Average


Question 19 (1 point)
---------------------
Dans la Tâche 9, pour la carte thermique (heat map), l'axe X représente :

A. La page web visitée
B. La page de référence (refering_page)
C. Le système d'exploitation
D. L'heure de visite


Question 20 (2 points)
---------------------
Si la carte thermique montre que plus de visiteurs accèdent aux pages produits 
depuis la page de recherche que depuis la page de recommandations, quelle 
conclusion peut-on tirer ?

A. La page de recherche doit être supprimée
B. La page de recherche est plus efficace pour diriger les utilisateurs
C. Le site web est trop lent
D. Il faut augmenter le nombre de serveurs


================================================================================
FIN DE L'EXAMEN
================================================================================

