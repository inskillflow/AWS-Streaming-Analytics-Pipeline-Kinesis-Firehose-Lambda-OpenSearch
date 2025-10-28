================================================================================
                           QCM - MODULE 2
                      AMAZON KINESIS
================================================================================

Durée : 20 minutes
Note sur : 10 points
Documents non autorisés

================================================================================

1. Dans Kinesis Data Streams, un "shard" représente :

   A. Un document JSON
   B. Une unité de capacité de traitement
   C. Un serveur physique
   D. Un type de donnée


2. Quelle est la capacité d'écriture d'un shard Kinesis Data Streams ?

   A. 100 KB/s
   B. 500 KB/s
   C. 1 MB/s
   D. 10 MB/s


3. Par défaut, combien de temps Kinesis Data Streams conserve-t-il les données ?

   A. 1 heure
   B. 24 heures
   C. 7 jours
   D. 30 jours


4. Quelle affirmation concernant Kinesis Data Firehose est correcte ?

   A. Nécessite le provisionnement manuel de shards
   B. Se met à l'échelle automatiquement
   C. Conserve les données pendant 7 jours
   D. Nécessite l'écriture de code consumer


5. Pour un système nécessitant que 3 applications différentes consomment les 
   mêmes données en parallèle avec des logiques distinctes, quel service 
   est préférable ?

   A. Kinesis Data Firehose uniquement
   B. Kinesis Data Streams
   C. Amazon S3 avec polling
   D. Amazon SQS


6. Si votre application génère 8 MB/s de données et nécessite que 2 consumers 
   les lisent, combien de shards minimum provisionneriez-vous ?

   A. 4 shards
   B. 8 shards
   C. 16 shards
   D. 2 shards


7. Dans quel scénario utiliser Kinesis Data Streams ET Data Firehose ensemble ?

   A. Pour réduire les coûts uniquement
   B. Pour avoir traitement temps réel ET archivage automatique
   C. C'est toujours obligatoire
   D. Ce n'est jamais recommandé


8. Quelle est la différence principale de gestion entre Data Streams et 
   Data Firehose ?

   A. Data Streams est plus simple à gérer
   B. Data Firehose nécessite plus de configuration
   C. Data Streams nécessite provisionnement manuel, Firehose est entièrement managé
   D. Il n'y a aucune différence


9. La configuration "Direct PUT" dans Kinesis Data Firehose signifie :

   A. Les données proviennent directement d'applications via API/agent
   B. Les données proviennent de Data Streams
   C. Les données sont stockées dans DynamoDB
   D. Les données sont chiffrées automatiquement


10. Pour un cas d'usage nécessitant une latence < 1 seconde avec replay des 
    données, quel service choisir ?

    A. Kinesis Data Firehose
    B. Kinesis Data Streams
    C. Amazon S3
    D. Amazon SQS


================================================================================
FIN DU QCM
================================================================================

