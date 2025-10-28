# QUESTIONS DE DÉVELOPPEMENT - MODULES 3-4
## GLUE, ATHENA & OPTIMISATION PARQUET

> **Durée** : 60 minutes  
> **Note** : 20 points  
> **Format** : Schémas + configurations + calculs

---

## QUESTION 1 - CATALOGUE GLUE ET PIPELINE COMPLET (10 points)

### Contexte

Entreprise avec données logs applicatifs à traiter quotidiennement :

**Données sources S3** :
- Logs application : **200 GB/jour** (format JSON Lines)
- Logs erreurs : **10 GB/jour** (format JSON Lines)
- Metadata utilisateurs : **5 GB** (CSV, mise à jour quotidienne)

**Structure JSON log** :
```json
{
  "timestamp": "2025-10-28T10:15:30.123Z",
  "level": "ERROR",
  "service": "payment-api",
  "user_id": "usr_123",
  "message": "Timeout",
  "duration_ms": 5000
}
```

**Besoins** :
- Catalogue Glue avec tables optimisées
- Format Parquet + compression Snappy
- Partitionnement par date (year/month/day)
- Vue SQL combinant logs + metadata users
- Requêtes Athena performantes

### Consigne

Concevez architecture complète Glue + Athena.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Architecture Glue Catalog** | Schéma databases + tables avec locations S3 | 3 pts |
| **2. Requête CTAS** | SQL complet conversion JSON → Parquet partitionné | 3 pts |
| **3. Vue SQL** | CREATE VIEW joignant logs + metadata | 2 pts |
| **4. Workflow Athena** | Séquence requêtes SQL (ordre exécution) | 2 pts |

> **Livrables obligatoires** :  
> - Diagramme architecture Glue Catalog  
> - Requête CTAS complète avec tous paramètres  
> - Requête CREATE VIEW avec JOIN  
> - Liste ordonnée des requêtes SQL

---

## QUESTION 2 - OPTIMISATION PERFORMANCES ET COUTS (10 points)

### Contexte

Table Athena actuelle avec problèmes performance :

**Configuration actuelle** :
- Format : CSV non compressé
- Taille : **10 TB** (2 ans données)
- Structure : Pas de partitions
- Fichiers : 50K petits fichiers (100-200 MB chacun)

**Utilisation** :
- 5000 requêtes/mois
- Chaque requête scanne moyenne **500 GB**
- Latence moyenne : **45 secondes**
- Coût Athena/mois : **12,500 USD** (500 GB × 5K × 5 USD/TB)

**Requêtes typiques** :
```sql
SELECT service, COUNT(*) as errors
FROM logs
WHERE date BETWEEN '2025-01-01' AND '2025-01-31'
  AND level = 'ERROR'
GROUP BY service;
```

**Objectifs** :
- Réduire latence à < 5 secondes
- Réduire coût de 80%

### Consigne

Proposez plan complet d'optimisation.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Diagnostic** | Identifiez 4 problèmes performance actuels | 2 pts |
| **2. Architecture optimisée** | Schéma avec format, partitions, compression | 3 pts |
| **3. Migration CTAS** | Requête SQL conversion CSV → Parquet optimisé | 2 pts |
| **4. Calculs économies** | Avant/Après : taille, latence, coûts mensuels | 3 pts |

> **Livrables obligatoires** :  
> - Tableau diagnostic (problème → impact)  
> - Schéma architecture optimisée  
> - Requête CTAS de migration  
> - Tableau avant/après avec calculs détaillés

**Tableau attendu** :

| Métrique | Avant (CSV) | Après (Parquet) | Gain |
|----------|-------------|-----------------|------|
| Taille totale | 10 TB | ? | ? |
| Taille scannée/query | 500 GB | ? | ? |
| Latence query | 45s | ? | ? |
| Coût/mois | 12,500 USD | ? | ? |

---

## GRILLE D'ÉVALUATION

| Critère | Points | Description |
|---------|--------|-------------|
| **Schémas/Architectures** | /6 | Clarté, complétude, annotations |
| **Requêtes SQL** | /7 | Syntaxe, optimisations, fonctionnalité |
| **Calculs** | /5 | Justesse, méthodologie, résultats |
| **Justifications** | /2 | Arguments techniques solides |

---

## BARÈME

| Score | Niveau | Livrables |
|-------|--------|-----------|
| **18-20** | Excellent | Tous schémas + SQL parfait + calculs exacts |
| **15-17** | Très bien | Bons schémas + SQL fonctionnel + calculs corrects |
| **12-14** | Bien | Schémas basiques + SQL avec erreurs mineures |
| **10-11** | Passable | Schémas incomplets + erreurs SQL |
| **< 10** | Insuffisant | Absence schémas ou SQL incorrect |

