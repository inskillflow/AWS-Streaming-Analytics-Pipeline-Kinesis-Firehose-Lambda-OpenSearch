================================================================================
                       QCM - MODULES 3 à 6
================================================================================

Durée : 40 minutes
Note sur : 40 points
Documents non autorisés

================================================================================
MODULE 3 - TRANSFORMATION AVEC AWS LAMBDA (10 points)
================================================================================

1. AWS Lambda est un service de calcul :

   A. Nécessitant la gestion de serveurs
   B. Serverless sans gestion d'infrastructure
   C. Uniquement pour le stockage
   D. Remplaçant EC2 dans tous les cas


2. Dans un pipeline Kinesis Firehose → Lambda, quel est le timeout maximum 
   pour la fonction de transformation ?

   A. 1 minute
   B. 5 minutes
   C. 15 minutes
   D. Pas de limite


3. La facturation AWS Lambda est basée sur :

   A. Un tarif mensuel fixe
   B. Le nombre d'invocations et la durée d'exécution
   C. Le nombre de serveurs provisionnés
   D. La taille du code déployé uniquement


4. Dans l'enrichissement de logs web, Lambda ajoute typiquement :

   A. Le code HTML des pages
   B. La géolocalisation, l'OS et le navigateur
   C. Les mots de passe utilisateurs
   D. Les images du site


5. Un "cold start" Lambda signifie :

   A. Lambda ne fonctionne pas
   B. Première invocation avec délai initialisation
   C. Environnement déjà initialisé et réutilisé
   D. Lambda est en maintenance


6. Pour optimiser les coûts Lambda dans un pipeline streaming :

   A. Augmenter la taille mémoire au maximum
   B. Réduire le batch size à 1 record
   C. Traiter par batch et réutiliser connexions
   D. Invoquer Lambda manuellement


7. En cas d'erreur de traitement Lambda avec Kinesis Streams :

   A. Le record est perdu définitivement
   B. Lambda est invoqué à nouveau automatiquement
   C. Le stream est supprimé
   D. Aucune action n'est prise


8. Quelle est la plage de mémoire configurable pour Lambda ?

   A. 64 MB - 1 GB
   B. 128 MB - 10 GB
   C. 512 MB - 5 GB
   D. 1 GB - 100 GB


9. Lambda dans un pipeline streaming est idéal pour :

   A. Stocker des données à long terme
   B. Remplacer les bases de données
   C. Enrichir et transformer les données en vol
   D. Héberger des sites web


10. Par rapport à une application EC2, Lambda offre :

    A. Plus de contrôle sur l'infrastructure
    B. Mise à l'échelle automatique sans gestion serveurs
    C. Coût fixe prévisible
    D. Durée d'exécution illimitée


================================================================================
MODULE 4 - OPENSEARCH ET INDEXATION (10 points)
================================================================================

11. OpenSearch est un fork de :

    A. Apache Solr
    B. MongoDB
    C. Elasticsearch 7.10.2
    D. PostgreSQL


12. Dans OpenSearch, l'unité de base de données est :

    A. Une table SQL
    B. Un fichier CSV
    C. Un document JSON
    D. Un record binaire


13. Les "mappings" dans OpenSearch définissent :

    A. Les utilisateurs autorisés
    B. La structure et les types de champs des documents
    C. Les performances du cluster
    D. Les coûts de stockage


14. Un cluster OpenSearch à nœud unique affiche généralement l'état :

    A. Green (tout opérationnel avec replicas)
    B. Yellow (primaires alloués, replicas manquants)
    C. Red (dysfonctionnel)
    D. Blue (en maintenance)


15. Pour créer des visualisations dans OpenSearch Dashboards, il faut d'abord :

    A. Redémarrer le cluster
    B. Créer un index pattern
    C. Configurer Cognito
    D. Installer un plugin


16. Le type de champ "keyword" dans OpenSearch est utilisé pour :

    A. Recherche full-text avec analyse
    B. Recherche exacte, agrégations et tri
    C. Stocker des images
    D. Calculer des moyennes


17. Une stratégie "hot-warm-cold" dans OpenSearch permet de :

    A. Augmenter la vitesse d'indexation
    B. Optimiser les coûts en déplaçant données anciennes vers stockage économique
    C. Améliorer la sécurité
    D. Remplacer les snapshots


18. Pour dimensionner un cluster OpenSearch, la règle générale recommande :

    A. Shards < 1 GB chacun
    B. Shards < 50 GB chacun
    C. Shards < 500 GB chacun
    D. Pas de limite de taille


19. Une agrégation "Terms" dans OpenSearch permet de :

    A. Supprimer des documents
    B. Grouper et compter par valeur de champ
    C. Chiffrer les données
    D. Créer des snapshots


20. Algolia comparé à OpenSearch se distingue par :

    A. Être open-source et self-hosted
    B. Être un SaaS spécialisé recherche avec latence ultra-faible
    C. Être moins cher
    D. Être adapté aux logs analytics


================================================================================
MODULE 5 - SECURITE ET ENCRYPTION (10 points)
================================================================================

21. Le principe du "moindre privilège" en IAM signifie :

    A. Donner tous les accès admin
    B. Accorder uniquement les permissions strictement nécessaires
    C. Bloquer tous les accès
    D. Partager un seul compte entre utilisateurs


22. Dans une architecture streaming AWS, Amazon Cognito est utilisé pour :

    A. Chiffrer les données
    B. Authentifier les utilisateurs métier
    C. Stocker les logs
    D. Transformer les données


23. L'encryption "en transit" protège les données :

    A. Stockées sur disque
    B. Pendant leur transmission sur le réseau
    C. Archivées dans Glacier
    D. Uniquement en développement


24. AWS KMS (Key Management Service) permet de :

    A. Gérer les instances EC2
    B. Créer et contrôler les clés de chiffrement
    C. Monitorer les applications
    D. Créer des utilisateurs IAM


25. Pour qu'une instance EC2 puisse envoyer des données à Kinesis sans 
    credentials codés en dur, on utilise :

    A. Un mot de passe dans le code
    B. Un rôle IAM attaché à l'instance
    C. Une clé API stockée en clair
    D. L'adresse IP


26. L'encryption au repos dans Kinesis Data Streams utilise :

    A. TLS/SSL
    B. AWS KMS
    C. HTTPS
    D. SSH


27. CloudTrail est utilisé pour :

    A. Acheminer le trafic réseau
    B. Auditer les activités API AWS
    C. Stocker les fichiers
    D. Visualiser les données


28. Dans le modèle de responsabilité partagée AWS :

    A. AWS gère tout y compris la configuration client
    B. Le client gère tout y compris l'infrastructure physique
    C. AWS gère l'infrastructure, client gère configuration et sécurité app
    D. Aucune responsabilité n'incombe au client


29. Un VPC Endpoint permet de :

    A. Exposer des services sur internet
    B. Connexion privée entre VPC et services AWS sans internet
    C. Créer des instances EC2
    D. Chiffrer les données


30. Pour stocker de manière sécurisée des credentials et secrets avec rotation 
    automatique, on utilise :

    A. Un fichier texte sur S3
    B. Variables d'environnement EC2
    C. AWS Secrets Manager
    D. CloudWatch Logs


================================================================================
MODULE 6 - COMPARAISONS TECHNOLOGIQUES (10 points)
================================================================================

31. Dans Kinesis, l'équivalent d'un "Topic" Kafka est :

    A. Un shard
    B. Un stream
    C. Un bucket
    D. Un document


32. Apache Kafka comparé à Kinesis offre généralement :

    A. Moins de débit
    B. Plus de simplicité opérationnelle
    C. Plus de flexibilité et débit supérieur
    D. Pas de rétention des données


33. Amazon MSK (Managed Streaming for Kafka) est :

    A. Un remplacement de Kinesis
    B. Un service AWS hébergeant Kafka managé
    C. Un fork open-source de Kafka
    D. Une alternative à Lambda


34. Apache Pulsar se différencie de Kafka par :

    A. Architecture découplant compute et storage
    B. Pas de support du streaming
    C. Absence de partitionnement
    D. Coût plus élevé systématiquement


35. Dans une architecture Lambda (au sens architectural), on combine :

    A. Uniquement du traitement batch
    B. Uniquement du streaming
    C. Traitement batch ET streaming en parallèle
    D. Uniquement du stockage


36. L'architecture Kappa simplifie en utilisant :

    A. Trois couches de traitement
    B. Uniquement du traitement streaming
    C. Uniquement du batch
    D. Aucun traitement


37. Pour une startup avec équipe réduite sur AWS sans expertise Kafka :

    A. Kafka self-hosted est idéal
    B. Kinesis est plus approprié
    C. Apache Pulsar est recommandé
    D. Aucune solution streaming n'est adaptée


38. RabbitMQ comparé à Kinesis/Kafka se positionne plutôt sur :

    A. Le streaming de données massives
    B. Le messaging traditionnel et task queues
    C. Le stockage de données
    D. La visualisation


39. Pour un système multi-cloud nécessitant portabilité maximale :

    A. Kinesis est le meilleur choix
    B. Azure Event Hubs exclusivement
    C. Kafka offre plus de portabilité
    D. Google Pub/Sub uniquement


40. Elasticsearch post-fork offre comparé à OpenSearch :

    A. Fonctionnalités propriétaires additionnelles
    B. Est complètement identique
    C. Est moins performant
    D. Ne supporte plus l'indexation


================================================================================
FIN DU QCM
================================================================================

