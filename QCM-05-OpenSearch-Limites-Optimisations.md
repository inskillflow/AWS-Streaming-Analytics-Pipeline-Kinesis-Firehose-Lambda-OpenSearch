================================================================================
                           EXAMEN - QCM 5
       OPENSEARCH - INDEXATION, LIMITES ET OPTIMISATIONS
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

SECTION A - CONCEPTS D'INDEXATION (Questions 1 à 5)

Question 1 (1 point)
--------------------
Dans OpenSearch, l'indexation est :

A. La méthode pour organiser les données afin de les récupérer rapidement
B. Un type de compression des données
C. Une technique de sauvegarde
D. Un protocole réseau


Question 2 (1 point)
--------------------
Dans OpenSearch, l'unité de base de données est :

A. Un fichier CSV
B. Une table relationnelle
C. Un document JSON
D. Un fichier XML


Question 3 (1 point)
--------------------
Dans le laboratoire, quel est le nom de l'index créé pour stocker les logs 
Apache ?

A. web_logs
B. apache_logs
C. server_logs
D. kinesis_logs


Question 4 (1 point)
--------------------
Lors de la création d'un index dans OpenSearch, les "mappings" définissent :

A. Les performances du cluster
B. Les types de données et la structure des champs
C. Les utilisateurs autorisés
D. La localisation géographique du cluster


Question 5 (1 point)
--------------------
Dans le laboratoire, combien de shards sont configurés pour l'index 
"apache_logs" ?

A. 5
B. 10
C. 1
D. 20


================================================================================

SECTION B - LIMITES ET CAPACITES (Questions 6 à 10)

Question 6 (1 point)
--------------------
Dans un cluster OpenSearch à nœud unique, quel est l'état typique du cluster ?

A. Green (Vert)
B. Yellow (Jaune)
C. Red (Rouge)
D. Blue (Bleu)


Question 7 (1 point)
--------------------
Un état "Yellow" dans un cluster OpenSearch à nœud unique signifie :

A. Le cluster est en panne critique
B. Tous les fragments primaires sont alloués mais au moins une réplique ne l'est pas
C. Le cluster fonctionne de manière optimale
D. Les données sont corrompues


Question 8 (1 point)
--------------------
Pour qu'un cluster OpenSearch passe à l'état "Green", il faut généralement :

A. Redémarrer tous les services
B. Augmenter le nombre de nœuds à 2 ou plus
C. Réduire la quantité de données
D. Désactiver l'indexation


Question 9 (1 point)
--------------------
Les limites de stockage dans OpenSearch dépendent principalement de :

A. La région AWS uniquement
B. La version d'OpenSearch uniquement
C. Le type et le nombre d'instances dans le cluster
D. Le nombre d'utilisateurs


Question 10 (1 point)
---------------------
Une stratégie de données chaudes et froides dans OpenSearch permet de :

A. Supprimer automatiquement les anciennes données
B. Optimiser les coûts en stockant les données anciennes sur du stockage moins cher
C. Augmenter la vitesse d'indexation
D. Chiffrer les données sensibles


================================================================================

SECTION C - CONFIGURATION ET UTILISATION (Questions 11 à 15)

Question 11 (1 point)
---------------------
Dans le laboratoire, quelle commande API est utilisée pour créer un index ?

A. GET
B. POST
C. PUT
D. DELETE


Question 12 (1 point)
---------------------
Pour créer un modèle d'index (index pattern) dans OpenSearch Dashboards, quel 
champ temporel a été utilisé dans le laboratoire ?

A. timestamp
B. datetime
C. created_at
D. log_time


Question 13 (1 point)
---------------------
Un index pattern dans OpenSearch Dashboards est nécessaire pour :

A. Créer des utilisateurs
B. Créer des visualisations et analyser les données
C. Supprimer des index
D. Configurer l'encryption


Question 14 (1 point)
---------------------
Dans le laboratoire, la commande "DELETE /apache_logs" permet de :

A. Supprimer le cluster entier
B. Supprimer l'index apache_logs s'il existe
C. Supprimer tous les utilisateurs
D. Désactiver OpenSearch


Question 15 (1 point)
---------------------
Les types de champs dans les mappings OpenSearch incluent :
(Plusieurs réponses possibles - cochez toutes les bonnes réponses)

A. text
B. keyword
C. date
D. image


================================================================================

SECTION D - ALTERNATIVES ET OPTIMISATIONS (Questions 16 à 20)

Question 16 (1 point)
---------------------
Elasticsearch et OpenSearch sont liés car :

A. Ils n'ont aucun lien
B. OpenSearch est un fork d'Elasticsearch
C. Elasticsearch est un fork d'OpenSearch
D. Ce sont deux produits d'entreprises différentes sans historique commun


Question 17 (1 point)
---------------------
Parmi les alternatives suivantes à OpenSearch pour l'indexation et la 
recherche, laquelle est spécialisée dans la recherche textuelle rapide pour 
les applications web ?

A. Apache Solr
B. Algolia
C. Amazon RDS
D. Amazon DynamoDB


Question 18 (1 point)
---------------------
Apache Solr est :

A. Un système de gestion de bases de données relationnelles
B. Une plateforme de recherche open-source basée sur Lucene
C. Un service de streaming de données
D. Un outil de visualisation


Question 19 (2 points)
---------------------
Pour optimiser les performances d'un cluster OpenSearch en production, quelles 
pratiques sont recommandées ?
(Plusieurs réponses possibles - cochez toutes les bonnes réponses)

A. Utiliser plusieurs nœuds pour la haute disponibilité
B. Configurer des répliques pour les données critiques
C. Implémenter une stratégie de données chaudes/froides
D. Stocker toutes les données indéfiniment sur le même type de stockage


Question 20 (1 point)
---------------------
Si un cluster OpenSearch atteint ses limites de stockage, quelle solution 
N'est PAS appropriée ?

A. Ajouter des nœuds au cluster
B. Migrer les anciennes données vers un stockage froid
C. Supprimer les anciens index non utilisés
D. Désactiver complètement l'indexation


================================================================================
FIN DE L'EXAMEN
================================================================================

