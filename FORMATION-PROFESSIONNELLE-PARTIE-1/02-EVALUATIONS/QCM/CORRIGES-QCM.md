================================================================================
                        CORRIGES DES QCM
              INGENIERIE DES DONNEES - STREAMING AWS
================================================================================

IMPORTANT : Consulter uniquement après avoir complété les QCM.

================================================================================
MODULE 1 - ARCHITECTURE DE STREAMING AWS
================================================================================

1. B - Vélocité correspond au streaming temps réel
2. B - AWS Lambda pour transformation serverless
3. C - Firehose collecte, transforme et livre automatiquement
4. B - Latence minimale 60 secondes pour Firehose
5. C - Documents JSON dans OpenSearch
6. B - Amazon Cognito pour authentification utilisateurs métier
7. C - Lambda enrichit les données (géolocalisation, OS, navigateur)
8. B - CloudWatch pour monitoring et observabilité
9. B - Défense en profondeur = multiples couches indépendantes
10. B - Firehose seul suffit pour livraison simple vers S3

================================================================================
MODULES 2 - AMAZON KINESIS
================================================================================

1. B - Shard = unité de capacité de traitement
2. C - 1 MB/s en écriture par shard
3. B - 24 heures de rétention par défaut
4. B - Firehose se met à l'échelle automatiquement
5. B - Data Streams pour multiples consumers parallèles
6. B - 8 shards (8 MB/s écriture, 16 MB/s lecture pour 2 consumers)
7. B - Utiliser les deux pour traitement temps réel ET archivage
8. C - Streams nécessite provisionnement manuel, Firehose managé
9. A - Direct PUT = données depuis applications via API/agent
10. B - Data Streams pour latence < 1s avec replay

================================================================================
MODULE 3 - TRANSFORMATION AVEC AWS LAMBDA
================================================================================

11. B - Lambda est serverless sans gestion infrastructure
12. B - Timeout max 5 minutes pour Lambda avec Firehose
13. B - Facturation sur invocations et durée d'exécution
14. B - Lambda ajoute géolocalisation, OS et navigateur
15. B - Cold start = première invocation avec délai initialisation
16. C - Optimiser coûts : traiter par batch et réutiliser connexions
17. B - Lambda invoqué à nouveau automatiquement si erreur
18. B - Mémoire Lambda : 128 MB - 10 GB
19. C - Lambda idéal pour enrichir et transformer en vol
20. B - Lambda offre scaling automatique sans gestion serveurs

================================================================================
MODULE 4 - OPENSEARCH ET INDEXATION
================================================================================

21. C - OpenSearch = fork Elasticsearch 7.10.2
22. C - Document JSON = unité de base OpenSearch
23. B - Mappings définissent structure et types de champs
24. B - Cluster à nœud unique = état Yellow (replicas manquants)
25. B - Créer index pattern avant visualisations
26. B - keyword pour recherche exacte, agrégations, tri
27. B - Hot-warm-cold optimise coûts de stockage
28. B - Shards < 50 GB recommandé
29. B - Terms aggregation groupe et compte par valeur
30. B - Algolia = SaaS recherche avec latence ultra-faible

================================================================================
MODULE 5 - SECURITE ET ENCRYPTION
================================================================================

31. B - Moindre privilège = permissions strictement nécessaires
32. B - Cognito authentifie utilisateurs métier
33. B - Encryption en transit = pendant transmission réseau
34. B - KMS crée et contrôle clés de chiffrement
35. B - Rôle IAM attaché à instance (pas de credentials codés)
36. B - Kinesis Data Streams utilise KMS au repos
37. B - CloudTrail audite activités API AWS
38. C - Responsabilité partagée : AWS infra, client config/sécurité
39. B - VPC Endpoint = connexion privée sans internet
40. C - Secrets Manager pour credentials avec rotation auto

================================================================================
MODULE 6 - COMPARAISONS TECHNOLOGIQUES
================================================================================

41. B - Stream Kinesis = Topic Kafka
42. C - Kafka offre flexibilité et débit supérieur
43. B - MSK = service AWS hébergeant Kafka managé
44. A - Pulsar découple compute et storage
45. C - Lambda architecture = batch ET streaming parallèles
46. B - Kappa = uniquement streaming
47. B - Kinesis plus approprié pour startup AWS sans expertise Kafka
48. B - RabbitMQ = messaging traditionnel et task queues
49. C - Kafka offre meilleure portabilité multi-cloud
50. A - Elasticsearch offre fonctionnalités propriétaires additionnelles

================================================================================
BAREME ET APPRECIATION
================================================================================

MODULE 1 (10 points) :
9-10 : Excellent
7-8  : Très bien
6    : Bien
5    : Passable
< 5  : Insuffisant

MODULES 2-6 (40 points) :
36-40 : Excellent
30-35 : Très bien
24-29 : Bien
20-23 : Passable
< 20  : Insuffisant

TOTAL (50 points) :
45-50 : Excellent - Maîtrise complète
38-44 : Très bien - Très bonne compréhension
30-37 : Bien - Bonne maîtrise avec lacunes mineures
25-29 : Passable - Connaissances de base acquises
< 25  : Insuffisant - Révision nécessaire

================================================================================
RECOMMANDATIONS POST-EVALUATION
================================================================================

SCORE < 25/50 :
- Réviser en profondeur les modules concernés
- Refaire les QCM après étude
- Consulter ressources complémentaires
- Demander support formateur si disponible

SCORE 25-37/50 :
- Identifier thèmes des questions manquées
- Réviser sections spécifiques
- Approfondir via questions développement
- Refaire QCM pour validation

SCORE 38-44/50 :
- Excellent niveau de base
- Approfondir via questions développement
- Pratiquer avec projets concrets
- Consulter documentation AWS officielle

SCORE 45-50/50 :
- Maîtrise excellente
- Passer aux cas pratiques complexes
- Partager connaissances (mentorat)
- Approfondir architectures avancées

================================================================================

