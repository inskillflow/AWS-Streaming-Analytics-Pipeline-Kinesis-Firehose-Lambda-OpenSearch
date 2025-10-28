# MODULE 5 - SECURITE ET ENCRYPTION

**Durée** : 45 minutes  
**Niveau** : Intermédiaire  
**Objectifs** : Sécuriser une architecture streaming avec IAM, Cognito, encryption et audit

---

# 1. PRINCIPES DE SECURITE AWS

## 1.1 Modèle de Responsabilité Partagée

AWS RESPONSABLE DE :
- Sécurité physique data centers
- Infrastructure réseau
- Hyperviseur et isolation
- Services managés (disponibilité, patches)

CLIENT RESPONSABLE DE :
- Configuration sécurité services
- Gestion identités et accès (IAM)
- Encryption données
- Sécurité applications
- Conformité réglementaire

ZONE GRISE (managé) :
Services comme OpenSearch : AWS gère infra, client configure accès.


1.2 Défense en Profondeur
--------------------------

PRINCIPE :
Multiples couches de sécurité indépendantes.

COUCHES ARCHITECTURE STREAMING :
1. Réseau : VPC, security groups
2. Identité : IAM, Cognito
3. Données : Encryption transit + repos
4. Application : Validation, sanitization
5. Monitoring : CloudWatch, CloudTrail
6. Conformité : Audit, logging


2. GESTION DES IDENTITES ET ACCES (IAM)

2.1 Composants IAM
------------------

UTILISATEURS :
- Identités permanentes (humains)
- Credentials long terme
- MFA recommandé

GROUPES :
- Collection d'utilisateurs
- Permissions partagées
- Simplification gestion

ROLES :
- Identités assumables temporairement
- Pour services AWS, applications
- Credentials temporaires automatiques

POLITIQUES :
- Documents JSON définissant permissions
- Attachées à utilisateurs/groupes/rôles


2.2 Structure Politique IAM
----------------------------

**Format** :

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "kinesis:PutRecord",
        "kinesis:PutRecords"
      ],
      "Resource": "arn:aws:kinesis:us-east-1:123456789012:stream/my-stream"
    }
  ]
}
```

ELEMENTS :
- Effect : Allow ou Deny
- Action : Opérations autorisées
- Resource : Cibles (ARN)
- Condition : Contraintes additionnelles (optionnel)


2.3 Rôles pour Services
------------------------

EC2 INSTANCE ROLE :
Permet à EC2 d'accéder autres services sans credentials codés en dur.

Exemple : OsDemoWebserverIAMRole
Permissions :
- kinesis:PutRecord (envoyer logs)
- s3:PutObject (buffer temporaire)

LAMBDA EXECUTION ROLE :
Permissions pour Lambda d'accéder ressources.

Exemple : Lambda transformation
Permissions :
- kinesis:GetRecords (lire stream)
- logs:CreateLogStream (CloudWatch)
- kms:Decrypt (si encryption)

FIREHOSE DELIVERY ROLE :
Permet Firehose de livrer données.

Permissions :
- s3:PutObject
- lambda:InvokeFunction
- es:ESHttpPost (OpenSearch)


2.4 Principe du Moindre Privilège
----------------------------------

DEFINITION :
Accorder uniquement permissions strictement nécessaires.

APPLICATION :
- Rôle EC2 : PutRecord uniquement (pas DeleteStream)
- Lambda : Lecture d'un stream spécifique (pas tous)
- Firehose : Ecriture dans index spécifique OpenSearch

AUDIT REGULIER :
- IAM Access Analyzer
- Suppression permissions inutilisées


3. AUTHENTIFICATION AVEC AMAZON COGNITO

3.1 Architecture Cognito
-------------------------

USER POOLS :
- Annuaire utilisateurs
- Authentification (login/password)
- MFA, password policies
- Gestion inscription/connexion

IDENTITY POOLS :
- Attribution credentials AWS temporaires
- Fédération identités (Google, Facebook, SAML)
- Roles IAM associés

INTEGRATION OPENSEARCH :
User Pool → Authentification → Identity Pool → Role IAM → Accès OpenSearch


3.2 Configuration Cognito + OpenSearch
---------------------------------------

ETAPES :
1. Créer User Pool Cognito
2. Créer utilisateurs/groupes
3. Configurer domaine OpenSearch avec Cognito
4. Attribuer rôle IAM avec permissions OpenSearch
5. Utilisateurs se connectent via Cognito pour accéder Dashboards

AVANTAGES :
- Séparation utilisateurs métier et comptes IAM
- Interface login standard
- Gestion centralisée accès
- MFA possible


3.3 Gestion des Sessions
-------------------------

TOKENS :
- ID Token : informations utilisateur
- Access Token : autorisation APIs
- Refresh Token : renouvellement

DUREES :
- Access/ID : 1 heure par défaut
- Refresh : jusqu'à 10 ans
- Sessions dashboard : configurables


4. ENCRYPTION DES DONNEES

4.1 Encryption en Transit
--------------------------

DEFINITION :
Protection données pendant transmission réseau.

PROTOCOLE : TLS/SSL (HTTPS)

APPLICATION :
- EC2 → Kinesis : HTTPS API
- Lambda → OpenSearch : HTTPS
- Client → OpenSearch Dashboards : HTTPS

CONFIGURATION :
Automatique pour services AWS managés.

CERTIFICATS :
- AWS Certificate Manager (ACM)
- Renouvellement automatique
- Integration Load Balancers


4.2 Encryption au Repos
------------------------

DEFINITION :
Protection données stockées sur disque.

KINESIS DATA STREAMS :
- Server-side encryption avec AWS KMS
- Encryption/decryption automatique
- Configuration à la création du stream

KINESIS DATA FIREHOSE :
- Encryption à la destination
- S3 : SSE-S3, SSE-KMS
- OpenSearch : encryption node-to-node

OPENSEARCH SERVICE :
- Encryption at rest avec KMS
- Index et snapshots chiffrés
- Configuration domain-level


4.3 AWS Key Management Service (KMS)
-------------------------------------

DEFINITION :
Service de gestion de clés de chiffrement.

CLES KMS :
- Customer Managed Keys (CMK) : contrôle total
- AWS Managed Keys : gérées par AWS pour service
- CloudHSM : hardware security module dédié

AVANTAGES :
- Rotation automatique clés
- Audit CloudTrail
- Contrôle accès granulaire via IAM
- Conformité (FIPS 140-2)

CONFIGURATION KINESIS :
aws kinesis start-stream-encryption \
  --stream-name my-stream \
  --encryption-type KMS \
  --key-id arn:aws:kms:region:account:key/key-id


4.4 Encryption Pipeline Complet
--------------------------------

SOURCE (EC2) :
- Données en clair localement
- TLS vers Kinesis

KINESIS :
- Encryption au repos (KMS)
- TLS entre services

LAMBDA :
- Données déchiffrées en mémoire traitement
- TLS vers destinations

OPENSEARCH :
- Encryption au repos (KMS)
- Encryption node-to-node
- TLS pour accès externe


5. SECURITE RESEAU

5.1 Amazon VPC
--------------

ISOLATION :
- Services dans VPC privé
- Contrôle trafic entrant/sortant

SUBNETS :
- Public : accès internet (Load Balancers)
- Private : services internes (OpenSearch, Lambda)

SECURITY GROUPS :
- Firewall instances
- Règles entrée/sortie par port/protocole
- Stateful

NACLs (Network ACLs) :
- Firewall subnet-level
- Stateless
- Règles allow/deny


5.2 VPC Endpoints
-----------------

DEFINITION :
Connexion privée entre VPC et services AWS sans internet.

TYPES :
- Interface Endpoint : ENI dans VPC
- Gateway Endpoint : route table entry (S3, DynamoDB)

AVANTAGES :
- Pas de traversée internet public
- Meilleure sécurité
- Réduction coûts transfert données

USAGE STREAMING :
Lambda dans VPC → Interface Endpoint → Kinesis (privé)


6. AUDIT ET CONFORMITE

6.1 AWS CloudTrail
------------------

ROLE :
Enregistrement activités API AWS.

LOGS :
- Qui : utilisateur/role
- Quoi : action (ex: PutRecord)
- Quand : timestamp
- Où : région, IP source
- Résultat : succès/échec

STOCKAGE :
S3 avec encryption et versioning.

ALERTES :
CloudWatch Logs Insights pour détection anomalies.


6.2 Conformité
--------------

CERTIFICATIONS AWS :
- SOC 1/2/3
- PCI-DSS
- HIPAA
- ISO 27001
- RGPD

RESPONSABILITES CLIENT :
- Configuration sécurité correcte
- Encryption activée
- Accès restreints
- Documentation architecture


6.3 Bonnes Pratiques
--------------------

CHECKLIST :
- [ ] MFA activé comptes admin
- [ ] Rôles IAM avec moindre privilège
- [ ] Encryption transit et repos
- [ ] CloudTrail activé
- [ ] Monitoring CloudWatch configuré
- [ ] Sauvegardes automatiques
- [ ] Patches et mises à jour régulières
- [ ] Audit accès périodique


7. GESTION DES SECRETS

7.1 AWS Secrets Manager
------------------------

ROLE :
Stockage sécurisé credentials, clés API, passwords.

AVANTAGES :
- Rotation automatique secrets
- Encryption au repos
- Audit accès
- Integration IAM

USAGE :
Lambda récupère password DB depuis Secrets Manager au runtime.


7.2 Systems Manager Parameter Store
------------------------------------

ALTERNATIVE ECONOMIQUE :
- Paramètres configuration
- Secrets simples (sans rotation auto)
- Gratuit (limites)

TYPES :
- String
- StringList
- SecureString (encryption KMS)


8. POINTS CLES DU MODULE

- Sécurité multicouche essentielle (défense en profondeur)
- IAM contrôle permissions (principe moindre privilège)
- Cognito sépare authentification métier et IAM
- Encryption en transit (TLS) et au repos (KMS)
- VPC isole ressources réseau
- CloudTrail audite activités
- Conformité = responsabilité partagée AWS/Client


9. EXERCICES DE REFLEXION

1. Concevez une politique IAM minimale pour EC2 envoyant logs à Kinesis.

2. Expliquez différence entre IAM (autorisation) et Cognito (authentification).

3. Pourquoi encryption au repos ET en transit ?

4. Comment auditeriez-vous accès non autorisé à OpenSearch ?

5. Architecturez un système HIPAA-compliant avec Kinesis et OpenSearch.



