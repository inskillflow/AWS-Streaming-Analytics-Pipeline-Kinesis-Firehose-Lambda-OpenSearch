================================================================================
                           EXAMEN - QCM 4
         SECURITE ET ENCRYPTION DANS LES PIPELINES AWS
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

SECTION A - AUTHENTIFICATION ET COGNITO (Questions 1 à 5)

Question 1 (1 point)
--------------------
Amazon Cognito dans l'architecture du laboratoire est principalement utilisé 
pour :

A. Stocker les données utilisateur
B. Gérer l'authentification et les identités des utilisateurs
C. Transformer les données en transit
D. Surveiller les accès aux ressources


Question 2 (1 point)
--------------------
Dans le laboratoire, qui peut accéder aux OpenSearch Dashboards ?

A. Tous les utilisateurs internet sans restriction
B. Uniquement les utilisateurs authentifiés via Cognito
C. Uniquement les administrateurs AWS
D. Uniquement les instances EC2


Question 3 (1 point)
--------------------
Le rôle IAM "osdemocognitoauthuserrole" permet :

A. Au domaine OpenSearch d'utiliser Cognito pour authentifier les utilisateurs
B. Aux utilisateurs de modifier la configuration EC2
C. À Lambda de transformer les données
D. À Kinesis de stocker les données


Question 4 (1 point)
--------------------
Dans le scénario du laboratoire, lors de la première connexion, l'utilisateur 
doit :

A. Fournir sa carte de crédit
B. Changer son mot de passe temporaire
C. Configurer un serveur
D. Installer un certificat SSL


Question 5 (1 point)
--------------------
La combinaison de Cognito pour l'authentification et IAM pour l'autorisation 
permet de :

A. Réduire les coûts uniquement
B. Séparer la gestion des identités utilisateurs et des permissions d'accès
C. Augmenter la vitesse de traitement
D. Compresser les données


================================================================================

SECTION B - ENCRYPTION EN TRANSIT ET AU REPOS (Questions 6 à 10)

Question 6 (1 point)
--------------------
L'encryption en transit protège les données :

A. Stockées dans une base de données
B. Pendant leur transfert sur le réseau
C. Archivées dans Glacier
D. Supprimées définitivement


Question 7 (1 point)
--------------------
L'encryption au repos protège les données :

A. Pendant leur transmission
B. Lorsqu'elles sont stockées sur disque
C. Uniquement en mémoire RAM
D. Pendant le traitement par Lambda


Question 8 (1 point)
--------------------
Quel protocole est généralement utilisé pour l'encryption en transit dans AWS ?

A. FTP
B. HTTP
C. TLS/SSL (HTTPS)
D. Telnet


Question 9 (1 point)
--------------------
AWS Key Management Service (KMS) est utilisé pour :

A. Gérer les instances EC2
B. Créer et contrôler les clés de chiffrement
C. Surveiller les performances réseau
D. Authentifier les utilisateurs


Question 10 (1 point)
---------------------
Dans Kinesis Data Firehose, l'encryption des données peut être activée :

A. Uniquement côté serveur
B. Uniquement côté client
C. À la fois en transit et au repos
D. Elle n'est jamais disponible


================================================================================

SECTION C - CONFIGURATION ENCRYPTION KINESIS (Questions 11 à 15)

Question 11 (1 point)
---------------------
Lorsque l'encryption côté serveur est activée dans Kinesis Data Firehose, les 
données sont chiffrées :

A. Avant d'être envoyées depuis la source
B. Après réception par Kinesis et avant stockage
C. Uniquement dans OpenSearch
D. Jamais


Question 12 (1 point)
---------------------
Pour chiffrer les données dans Kinesis Data Firehose, quelle clé peut être 
utilisée ?

A. Uniquement une clé AWS gérée par le client
B. Uniquement une clé générée par Cognito
C. Une clé AWS KMS ou une clé gérée par AWS
D. Une clé publique SSH


Question 13 (1 point)
---------------------
L'avantage d'utiliser AWS KMS pour l'encryption est :

A. C'est gratuit
B. Gestion centralisée des clés avec rotation automatique possible
C. Plus rapide que l'encryption manuelle
D. Ne nécessite aucune configuration


Question 14 (1 point)
---------------------
Dans un flux de livraison Kinesis Data Firehose, si l'encryption n'est pas 
activée, les données :

A. Sont refusées par le service
B. Transitent et sont stockées en clair
C. Sont automatiquement chiffrées par défaut
D. Provoquent une erreur système


Question 15 (1 point)
---------------------
Pour activer l'encryption dans Kinesis Data Firehose, où configure-t-on ce 
paramètre ?

A. Dans la console Lambda
B. Dans la configuration du flux de livraison Firehose
C. Dans OpenSearch Dashboards
D. Dans Amazon Cognito


================================================================================

SECTION D - IAM ET POLITIQUES DE SECURITE (Questions 16 à 20)

Question 16 (1 point)
---------------------
Le rôle IAM "os_demo_firehose_delivery_role" permet à Kinesis Data Firehose de :
(Plusieurs réponses possibles - cochez toutes les bonnes réponses)

A. Accéder à S3 pour lire et écrire des objets
B. Invoquer des fonctions Lambda
C. Créer des logs CloudWatch
D. Gérer les utilisateurs Cognito


Question 17 (1 point)
---------------------
Une politique IAM définit :

A. Les performances du système
B. Les permissions et actions autorisées sur les ressources AWS
C. Le format des données
D. La durée de rétention des logs


Question 18 (1 point)
---------------------
Dans le laboratoire, quelle politique IAM permet à l'instance EC2 d'écrire 
dans le bucket S3 ?

A. OsDemoWebserverIAMPolicy
B. AdminAccessPolicy
C. CognitoAuthPolicy
D. LambdaExecutionPolicy


Question 19 (2 points)
---------------------
Une entreprise souhaite implémenter une architecture sécurisée où :
- Les données sont chiffrées en transit et au repos
- Seuls les utilisateurs authentifiés accèdent aux dashboards
- Les permissions sont finement contrôlées

Quels services sont nécessaires ?

A. Cognito + IAM + KMS
B. Uniquement IAM
C. Cognito + S3
D. Uniquement KMS


Question 20 (1 point)
---------------------
Dans le contexte de la sécurité AWS, le principe du moindre privilège signifie :

A. Donner tous les accès à tous les utilisateurs
B. Accorder uniquement les permissions nécessaires pour accomplir une tâche
C. Bloquer tous les accès par défaut
D. Permettre uniquement l'accès administrateur


================================================================================
FIN DE L'EXAMEN
================================================================================

