# QUESTIONS DE DÉVELOPPEMENT - MODULES 1-2
## WORKFLOWS ETL ET STEP FUNCTIONS

> **Durée** : 60 minutes  
> **Note** : 20 points  
> **Format** : Schémas obligatoires + analyses techniques

---

## QUESTION 1 - PIPELINE ETL COMPLET (10 points)

### Contexte

Entreprise e-commerce avec données de ventes à traiter quotidiennement :

**Données sources** :
- Transactions : 100 GB/jour (CSV) dans S3
- Produits : 5 GB catalogue (JSON) dans S3
- Clients : 2 GB profils (CSV) dans S3

**Besoins** :
- Conversion en Parquet avec compression Snappy
- Partitionnement par date (année/mois/jour)
- Vue SQL combinant transactions + produits + clients
- Rapports BI quotidiens via Athena
- Archivage 2 ans

**Déclenchement** : Chaque jour à 3AM

### Consigne

Concevez le pipeline ETL batch complet avec Step Functions.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Schéma workflow Step Functions** | Diagramme états complet avec logique conditionnelle | 4 pts |
| **2. Définition JSON** | Code JSON Step Functions (au moins 5 états) | 3 pts |
| **3. Requêtes SQL Athena** | CREATE TABLE et CTAS pour optimisation | 2 pts |
| **4. Déclenchement** | EventBridge rule + IAM permissions | 1 pt |

> **Livrables obligatoires** :  
> - Diagramme d'états Step Functions annoté  
> - Code JSON de la state machine  
> - Requêtes SQL (CREATE, CTAS, CREATE VIEW)  
> - Configuration EventBridge

**Workflow attendu doit inclure** :
- Vérification tables existent
- Création si absentes
- Conversion Parquet
- Partitionnement
- Création vue
- Gestion erreurs

---

## QUESTION 2 - ORCHESTRATION COMPLEXE (10 points)

### Contexte

Pipeline ETL multi-sources avec traitement parallèle :

**Sources** :
- API externe : Données météo (100 MB/jour)
- Base RDS : Logs applicatifs (50 GB/jour)
- S3 : Fichiers CSV utilisateurs (20 GB/jour)

**Traitement requis** :
1. Extraire de chaque source **en parallèle**
2. Transformer chacune en Parquet
3. Valider qualité données (chaque source indépendamment)
4. Si validation OK : Merger les 3 sources
5. Si validation KO : Alerte SNS + retry

**Contraintes** :
- Latence totale < 30 minutes
- Retry 3 fois avec backoff exponentiel
- Logs CloudWatch complets

### Consigne

Dessinez le workflow Step Functions avec gestion d'erreurs robuste.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Schéma workflow global** | Diagramme avec Parallel, Map, Choice, Retry/Catch | 4 pts |
| **2. Définition Parallel State** | JSON branches parallèles | 2 pts |
| **3. Gestion erreurs** | Configuration Retry + Catch pour chaque Task | 2 pts |
| **4. Monitoring** | CloudWatch alarmes sur métriques workflow | 2 pts |

> **Livrables obligatoires** :  
> - Diagramme complet du workflow  
> - Code JSON Parallel State  
> - Configuration Retry/Catch  
> - Liste alarmes CloudWatch à créer

**Le workflow doit montrer** :
- 3 branches parallèles (une par source)
- États de validation par branche
- État de merge si toutes validations OK
- Routes d'erreur avec SNS
- Retry policy pour erreurs transitoires

---

## GRILLE D'ÉVALUATION

### Critères

| Critère | Points | Description |
|---------|--------|-------------|
| **Schémas workflows** | /8 | Clarté, complétude, annotations, logique correcte |
| **Code JSON** | /5 | Syntaxe correcte, fonctionnel, best practices |
| **Gestion erreurs** | /4 | Retry, Catch, robustesse |
| **Faisabilité** | /3 | Production-ready, réaliste |

---

## BARÈME

| Score | Niveau | Livrables |
|-------|--------|-----------|
| **18-20** | Excellent | Workflows parfaits, JSON fonctionnel, gestion erreurs complète |
| **15-17** | Très bien | Bons workflows, JSON correct, gestion erreurs solide |
| **12-14** | Bien | Workflows fonctionnels, JSON avec erreurs mineures |
| **10-11** | Passable | Workflows incomplets, erreurs JSON |
| **< 10** | Insuffisant | Workflows incorrects ou absents |

