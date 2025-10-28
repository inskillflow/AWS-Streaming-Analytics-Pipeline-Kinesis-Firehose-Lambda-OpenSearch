================================================================================
                           EXAMEN - QCM 8
      INGENIERIE DES DONNEES - CONCEPTS TRANSVERSAUX
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

SECTION A - LES CINQ V DES BIG DATA (Questions 1 à 4)

Question 1 (1 point)
--------------------
Parmi les cinq V des mégadonnées (Big Data), lequel désigne la quantité 
massive de données générées ?

A. Variété
B. Volume
C. Vélocité
D. Valeur


Question 2 (1 point)
--------------------
Le "V" qui correspond à la rapidité de génération et de traitement des données 
en temps réel est :

A. Volume
B. Véracité
C. Vélocité
D. Variété


Question 3 (1 point)
--------------------
La "Variété" dans les cinq V fait référence à :

A. La quantité de données
B. La vitesse de traitement
C. Les différents types et formats de données (structurées, non-structurées)
D. La fiabilité des données


Question 4 (1 point)
--------------------
La "Véracité" concerne :

A. La rapidité du traitement
B. La qualité et la fiabilité des données
C. Le volume de stockage
D. Le nombre d'utilisateurs


================================================================================

SECTION B - ARCHITECTURES DE TRAITEMENT (Questions 5 à 9)

Question 5 (1 point)
--------------------
Une architecture Lambda dans le contexte du Big Data combine :

A. Uniquement du traitement batch
B. Uniquement du traitement streaming
C. Du traitement batch et du traitement streaming en parallèle
D. Uniquement du stockage


Question 6 (1 point)
--------------------
L'architecture Kappa simplifie l'architecture Lambda en :

A. Utilisant uniquement le traitement batch
B. Utilisant uniquement le traitement streaming
C. Combinant trois couches de traitement
D. Éliminant complètement le traitement


Question 7 (1 point)
--------------------
Dans une architecture de streaming temps réel, la latence fait référence à :

A. La quantité de données traitées
B. Le délai entre la génération et le traitement des données
C. Le coût du traitement
D. Le nombre de serveurs nécessaires


Question 8 (1 point)
--------------------
Un pipeline ETL (Extract, Transform, Load) dans le contexte du laboratoire 
correspond à :

A. EC2 (Extract) → Lambda (Transform) → OpenSearch (Load)
B. S3 → EC2 → RDS
C. Cognito → IAM → CloudWatch
D. Lambda → EC2 → S3


Question 9 (1 point)
--------------------
La différence entre un traitement batch et un traitement streaming est :

A. Le traitement batch est en temps réel, le streaming est différé
B. Le traitement streaming est en temps réel, le batch traite par lots périodiques
C. Il n'y a aucune différence
D. Le streaming est toujours plus lent


================================================================================

SECTION C - PATTERNS D'INGENIERIE DES DONNEES (Questions 10 à 14)

Question 10 (1 point)
---------------------
Dans un pipeline de données, l'enrichissement consiste à :

A. Supprimer des données inutiles
B. Ajouter des informations supplémentaires aux données brutes
C. Compresser les données
D. Chiffrer les données


Question 11 (1 point)
---------------------
Un Data Lake est :

A. Un système de stockage centralisé pour données brutes de tous types
B. Uniquement pour les données structurées
C. Une base de données relationnelle
D. Un outil de visualisation


Question 12 (1 point)
---------------------
Un Data Warehouse est optimisé pour :

A. Le stockage de fichiers bruts
B. L'analyse et les requêtes sur des données structurées
C. Le streaming temps réel uniquement
D. L'authentification des utilisateurs


Question 13 (1 point)
---------------------
Dans le laboratoire, la transformation des logs par Lambda avant indexation 
dans OpenSearch est un exemple de :

A. Traitement batch différé
B. Enrichissement en temps réel dans un pipeline streaming
C. Stockage à froid
D. Archivage


Question 14 (1 point)
---------------------
L'idempotence dans le traitement de données signifie que :

A. Traiter plusieurs fois la même donnée produit le même résultat
B. Les données sont toujours perdues
C. Le traitement est toujours en erreur
D. Les données sont dupliquées


================================================================================

SECTION D - MONITORING ET OBSERVABILITE (Questions 15 à 17)

Question 15 (1 point)
---------------------
Amazon CloudWatch dans l'architecture sert principalement à :

A. Stocker les données
B. Authentifier les utilisateurs
C. Surveiller et logger les événements et métriques
D. Transformer les données


Question 16 (1 point)
---------------------
Les métriques importantes à surveiller dans un pipeline de streaming incluent :
(Plusieurs réponses possibles - cochez toutes les bonnes réponses)

A. La latence de traitement
B. Le taux d'erreurs
C. Le débit (throughput)
D. La couleur de l'interface


Question 17 (1 point)
---------------------
L'observabilité d'un système distribué repose sur trois piliers :

A. CPU, Mémoire, Disque
B. Logs, Métriques, Traces
C. AWS, Azure, GCP
D. Batch, Streaming, Storage


================================================================================

SECTION E - CAS D'USAGE METIER (Questions 18 à 20)

Question 18 (2 points)
---------------------
Dans le scénario de la librairie universitaire du laboratoire, l'objectif 
principal est de :

A. Réduire les coûts du serveur web
B. Analyser le comportement des visiteurs en temps réel via les logs serveur
C. Augmenter le nombre de visiteurs
D. Remplacer le site web


Question 19 (2 points)
---------------------
Une entreprise de e-commerce souhaite :
- Personnaliser les recommandations en temps réel
- Détecter les fraudes immédiatement
- Analyser les tendances de vente
- Stocker l'historique complet

Quelle architecture est la plus appropriée ?

A. Batch processing uniquement avec traitement nocturne
B. Architecture streaming temps réel + stockage pour analyse historique
C. Stockage S3 uniquement
D. Base de données relationnelle traditionnelle


Question 20 (1 point)
---------------------
Pour un système critique nécessitant une haute disponibilité et une faible 
latence, quelles pratiques d'ingénierie des données sont essentielles ?
(Plusieurs réponses possibles - cochez toutes les bonnes réponses)

A. Réplication des données sur plusieurs zones
B. Monitoring et alertes en temps réel
C. Sauvegarde des données
D. Ignorer les erreurs de traitement


================================================================================
FIN DE L'EXAMEN
================================================================================

