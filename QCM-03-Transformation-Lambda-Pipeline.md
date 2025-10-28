================================================================================
                           EXAMEN - QCM 3
        TRANSFORMATION ET ENRICHISSEMENT AVEC AWS LAMBDA
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

SECTION A - ROLE DE EC2 ET GENERATION DE LOGS (Questions 1 à 4)

Question 1 (1 point)
--------------------
Dans l'architecture du laboratoire, quel serveur web est installé sur 
l'instance EC2 ?

A. Nginx
B. Apache
C. IIS
D. Tomcat


Question 2 (1 point)
--------------------
Les logs d'accès générés par le serveur web contiennent initialement des 
informations telles que :

A. L'adresse IP, la page visitée, l'heure, le navigateur
B. Le mot de passe de l'utilisateur
C. Le contenu complet de la page
D. Les données de la base de données


Question 3 (1 point)
--------------------
Quel fichier de configuration permet de connecter le serveur web à Kinesis 
Data Firehose ?

A. httpd.conf
B. agent.json
C. kinesis.config
D. aws-config.json


Question 4 (1 point)
--------------------
L'instance EC2 dans le laboratoire se trouve dans :

A. Un sous-réseau privé
B. Un sous-réseau public
C. Un VPC dédié isolé
D. Une zone de disponibilité privée


================================================================================

SECTION B - AWS LAMBDA ET TRANSFORMATION (Questions 5 à 11)

Question 5 (1 point)
--------------------
AWS Lambda est défini comme un service de calcul :

A. Nécessitant la gestion de serveurs
B. Serverless (sans serveur)
C. Basé sur des conteneurs Docker obligatoires
D. Uniquement pour le stockage de données


Question 6 (1 point)
--------------------
Dans le pipeline Kinesis Firehose → Lambda → OpenSearch, Lambda est déclenché :

A. Manuellement par un administrateur
B. Automatiquement par Kinesis Firehose
C. Par un cron job planifié
D. Par OpenSearch lorsqu'il a besoin de données


Question 7 (1 point)
--------------------
Parmi les enrichissements suivants, lesquels sont effectués par Lambda dans le 
laboratoire ?
(Plusieurs réponses possibles - cochez toutes les bonnes réponses)

A. Géolocalisation à partir de l'adresse IP
B. Identification du système d'exploitation
C. Identification du type de navigateur
D. Traduction du contenu de la page


Question 8 (1 point)
--------------------
Dans les logs CloudWatch, un enregistrement "Incoming Record from Kinesis 
Firehose" contient les données :

A. Après enrichissement par Lambda
B. Avant enrichissement par Lambda
C. Directement depuis OpenSearch
D. Depuis Amazon S3


Question 9 (1 point)
--------------------
Un enregistrement "Transformed Record going back to Kinesis Firehose" dans 
CloudWatch montre :

A. Les données brutes sans modification
B. Les données enrichies avec géolocalisation, OS, navigateur
C. Uniquement les erreurs de traitement
D. Les métriques de performance


Question 10 (1 point)
---------------------
Dans les logs CloudWatch, l'événement "REPORT RequestId" fournit des 
informations sur :

A. Les erreurs de traitement uniquement
B. La durée d'exécution et la mémoire utilisée par Lambda
C. Le nombre de visiteurs du site
D. La configuration du réseau


Question 11 (1 point)
---------------------
La facturation d'AWS Lambda est basée sur :

A. Un tarif mensuel fixe
B. Le nombre de serveurs provisionnés
C. La durée d'exécution et les ressources utilisées
D. Le nombre d'instances EC2


================================================================================

SECTION C - PIPELINE COMPLET (Questions 12 à 16)

Question 12 (1 point)
---------------------
Dans l'analogie de l'organisation d'un événement, Kinesis Data Firehose peut 
être comparé à :

A. Le lieu de l'événement
B. Le système de transport et de logistique
C. Les invités
D. Le traiteur qui prépare les plats


Question 13 (1 point)
---------------------
Dans la même analogie, AWS Lambda correspond à :

A. Le coordinateur qui organise et améliore l'expérience
B. Les invités de l'événement
C. Le lieu de réception
D. Le service de nettoyage


Question 14 (1 point)
---------------------
Le pipeline complet Kinesis Firehose → Lambda → OpenSearch permet :

A. Uniquement le stockage des données
B. La collecte, transformation et indexation automatique des données
C. Uniquement la visualisation des données
D. La suppression automatique des anciennes données


Question 15 (1 point)
---------------------
Dans le laboratoire, après qu'un visiteur navigue sur le site, combien de 
temps approximativement faut-il pour que les données enrichies apparaissent 
dans OpenSearch ?

A. Plusieurs heures
B. Quelques minutes
C. Quelques millisecondes à secondes
D. Un jour


Question 16 (1 point)
---------------------
Pour observer le traitement et la transformation des données dans le pipeline, 
quel service AWS est principalement utilisé ?

A. Amazon S3
B. Amazon CloudWatch Logs
C. Amazon SNS
D. AWS Config


================================================================================

SECTION D - CHOIX D'ARCHITECTURE ET SCENARIOS (Questions 17 à 20)

Question 17 (1 point)
---------------------
Dans quel cas est-il préférable d'utiliser Lambda avec Firehose plutôt qu'un 
traitement après stockage dans S3 ?

A. Lorsque le coût est le seul facteur
B. Lorsque l'enrichissement en temps réel est nécessaire avant indexation
C. Lorsque les données sont statiques
D. Lorsque les données ne nécessitent aucune transformation


Question 18 (1 point)
---------------------
Si vous devez ajouter des informations de géolocalisation à des logs de 
serveur web contenant uniquement des adresses IP, quelle approche est la 
plus appropriée ?

A. Stocker les données dans S3 puis traiter manuellement
B. Utiliser Lambda dans le pipeline Firehose pour enrichir en temps réel
C. Modifier la configuration du serveur web
D. Utiliser uniquement OpenSearch pour l'enrichissement


Question 19 (2 points)
---------------------
Une entreprise souhaite :
- Capturer les logs applicatifs en temps réel
- Ajouter des métadonnées (localisation, type d'appareil)
- Stocker dans OpenSearch pour analyse
- Minimiser la latence de bout en bout

Quelle architecture recommandez-vous ?

A. EC2 → S3 → Lambda → OpenSearch
B. EC2 → Kinesis Firehose → Lambda → OpenSearch
C. EC2 → Lambda → S3 → OpenSearch
D. EC2 → OpenSearch (sans enrichissement)


Question 20 (1 point)
---------------------
Dans le laboratoire, le rôle IAM "OsDemoWebserverIAMRole" attaché à l'instance 
EC2 permet principalement :

A. D'accéder aux dashboards OpenSearch
B. De lire et écrire dans le bucket S3 et d'envoyer des données à Kinesis
C. De modifier la configuration du cluster OpenSearch
D. De gérer les utilisateurs Cognito


================================================================================
FIN DE L'EXAMEN
================================================================================

