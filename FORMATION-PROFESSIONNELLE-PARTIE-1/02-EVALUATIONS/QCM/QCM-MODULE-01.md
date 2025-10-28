================================================================================
                           QCM - MODULE 1
              ARCHITECTURE DE STREAMING AWS
================================================================================

Durée : 20 minutes
Note sur : 10 points
Documents non autorisés

================================================================================

1. Parmi les cinq V des mégadonnées, lequel correspond spécifiquement aux 
   données de streaming temps réel ?

   A. Volume
   B. Vélocité
   C. Variété
   D. Valeur


2. Quel service AWS est utilisé pour la transformation serverless des données 
   en vol dans un pipeline de streaming ?

   A. Amazon EC2
   B. AWS Lambda
   C. Amazon S3
   D. Amazon CloudWatch


3. Dans l'architecture de streaming, quel est le rôle principal d'Amazon 
   Kinesis Data Firehose ?

   A. Stocker les données de manière permanente
   B. Authentifier les utilisateurs
   C. Collecter, transformer et livrer automatiquement les données
   D. Visualiser les données dans des dashboards


4. Quelle est la latence minimale de Kinesis Data Firehose ?

   A. < 1 seconde
   B. 60 secondes
   C. 5 minutes
   D. 1 heure


5. Amazon OpenSearch Service stocke les données sous forme de :

   A. Tables relationnelles
   B. Fichiers CSV
   C. Documents JSON
   D. Graphes


6. Quel service AWS permet d'authentifier les utilisateurs métier pour accéder 
   aux OpenSearch Dashboards ?

   A. AWS IAM uniquement
   B. Amazon Cognito
   C. AWS KMS
   D. Amazon S3


7. Dans le workflow streaming EC2 → Kinesis → Lambda → OpenSearch, à quelle 
   étape les données sont-elles enrichies avec la géolocalisation ?

   A. Lors de la génération sur EC2
   B. Lors du passage dans Kinesis Firehose
   C. Lors du traitement par Lambda
   D. Lors de l'indexation dans OpenSearch


8. Quel service AWS est essentiel pour le monitoring et l'observabilité du 
   pipeline de streaming ?

   A. Amazon Cognito
   B. Amazon CloudWatch
   C. Amazon S3
   D. Amazon DynamoDB


9. Le principe de "défense en profondeur" en sécurité signifie :

   A. Utiliser une seule couche de sécurité très forte
   B. Utiliser multiples couches de sécurité indépendantes
   C. Désactiver la sécurité en développement
   D. Utiliser uniquement l'encryption


10. Pour un cas d'usage nécessitant uniquement la livraison simple de logs 
    vers S3 sans traitement complexe, quelle solution est la plus appropriée ?

    A. Kinesis Data Streams avec application consumer personnalisée
    B. Kinesis Data Firehose seul
    C. Lambda seul
    D. EC2 avec script personnalisé


================================================================================
FIN DU QCM
================================================================================

