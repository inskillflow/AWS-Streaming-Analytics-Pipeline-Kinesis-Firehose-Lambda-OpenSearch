# QUESTIONS DE DÉVELOPPEMENT - MODULE 5
## SECURITE ET ENCRYPTION

> **Durée** : 45 minutes  
> **Note** : 20 points  
> **Format** : Architectures sécurisées + politiques IAM + analyses

---

## QUESTION 1 - ARCHITECTURE SECURISEE COMPLETE (10 points)

### Contexte

Système de santé collectant données médicales temps réel (conformité HIPAA obligatoire).

**Architecture actuelle (NON CONFORME)** :
```
Mobile Apps → API Gateway (HTTP) → Lambda → Kinesis → OpenSearch (public)
```

**Problèmes identifiés** :
- Pas d'encryption en transit
- OpenSearch accessible publiquement
- Pas d'authentification forte
- IAM avec AdministratorAccess
- Aucun audit des accès
- Logs non chiffrés au repos

**Requirements HIPAA** :
- Encryption bout-en-bout (transit + repos)
- Authentification multi-facteurs (MFA)
- Audit complet tous accès données
- Séparation réseau (VPC privé)
- Contrôle accès granulaire (rôle-based)

### Consigne

Redesignez l'architecture pour conformité HIPAA complète.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Schéma architecture sécurisée** | Diagramme complet avec VPC, subnets, security groups | 4 pts |
| **2. Configuration IAM** | 3 rôles avec politiques JSON (EC2, Lambda, Users) | 3 pts |
| **3. Stratégie encryption** | En transit (TLS) + au repos (KMS) pour chaque service | 2 pts |
| **4. Mécanismes audit** | CloudTrail + CloudWatch + logs spécifiques | 1 pt |

> **Livrables obligatoires** :  
> - Schéma architecture réseau (VPC) sécurisée  
> - 3 politiques IAM en JSON  
> - Tableau encryption (service × type × clé KMS)  
> - Configuration CloudTrail

---

## QUESTION 2 - POLITIQUE IAM ET COGNITO (10 points)

### Contexte

Architecture multi-tenant SaaS avec séparation par client :

```
Clients → Cognito → Lambda → Kinesis → OpenSearch (multi-index)
```

**Exigences** :
- Chaque client ne voit que ses données
- 3 rôles : Admin, Analyst, Viewer
- Isolation complète entre tenants
- Rotation automatique credentials

**Services à sécuriser** :
- Kinesis Data Streams (lecture/écriture)
- Lambda (execution)
- OpenSearch (index par client)
- S3 (archivage partitionné par client)

### Consigne

Concevez l'architecture d'authentification et autorisation complète.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Architecture Cognito** | Schéma User Pools + Identity Pools + rôles IAM | 3 pts |
| **2. Politiques IAM** | JSON pour 3 rôles (Admin/Analyst/Viewer) par tenant | 4 pts |
| **3. Isolation tenants** | Mécanisme garantissant séparation données | 2 pts |
| **4. Gestion secrets** | Secrets Manager config + rotation policy | 1 pt |

> **Livrables obligatoires** :  
> - Diagramme flux authentification/autorisation  
> - 3 politiques IAM complètes en JSON  
> - Schéma isolation multi-tenant  
> - Configuration Secrets Manager

**Exemple politique IAM attendue** :
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["kinesis:GetRecords", "kinesis:GetShardIterator"],
      "Resource": "arn:aws:kinesis:region:account:stream/${tenant_id}-stream",
      "Condition": {
        "StringEquals": {
          "kinesis:StreamTag/tenant": "${aws:userid}"
        }
      }
    }
  ]
}
```

---

## GRILLE D'ÉVALUATION

### Critères Techniques

| Critère | Points | Détails |
|---------|--------|---------|
| **Schémas sécurité** | /7 | VPC, IAM, Cognito, encryption |
| **Politiques IAM** | /7 | Syntaxe JSON, least privilege, conditions |
| **Conformité** | /4 | HIPAA/RGPD requirements complets |
| **Faisabilité** | /2 | Solutions production-ready |

---

## BARÈME

- **18-20** : Architecture sécurisée parfaite, politiques IAM expertes
- **15-17** : Bonne sécurité, politiques correctes, quelques optimisations possibles
- **12-14** : Sécurité basique fonctionnelle, politiques à améliorer
- **10-11** : Sécurité incomplète, erreurs dans politiques
- **< 10** : Architecture non sécurisée, politiques incorrectes

