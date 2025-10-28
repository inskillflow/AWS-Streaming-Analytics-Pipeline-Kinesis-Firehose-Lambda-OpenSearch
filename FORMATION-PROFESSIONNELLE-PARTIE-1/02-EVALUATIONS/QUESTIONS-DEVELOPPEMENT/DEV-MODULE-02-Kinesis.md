# QUESTIONS DE DÉVELOPPEMENT - MODULE 2
## AMAZON KINESIS

> **Durée** : 45 minutes  
> **Note** : 20 points  
> **Format** : Schémas d'architecture + calculs + analyses

---

## QUESTION 1 - DIMENSIONNEMENT SYSTEME IOT (10 points)

### Contexte

Système IoT industriel avec ces caractéristiques :

**Capteurs** :
- **15 000 capteurs** répartis sur 50 sites
- Chaque capteur : **1 message de 750 bytes toutes les 5 secondes**
- Criticité : alertes temps réel si valeurs anormales (< 1s)

**Consommateurs** :
- Lambda 1 : Détection anomalies (traitement < 500ms)
- Lambda 2 : Agrégations métriques
- Firehose : Archivage S3 (partitionné par site et date)

### Consigne

Concevez l'architecture Kinesis Data Streams complète.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Schéma architecture** | Diagramme complet producers → stream → consumers | 3 pts |
| **2. Calculs dimensionnement** | Records/s, MB/s, nombre de shards requis | 3 pts |
| **3. Stratégie partitionnement** | Clé de partition choisie + justification | 2 pts |
| **4. Estimation coûts** | Coût mensuel détaillé (Kinesis + Lambda + S3) | 2 pts |

> **Livrables obligatoires** :  
> - Schéma d'architecture annoté  
> - Tous les calculs étape par étape  
> - Tableau récapitulatif des coûts

**Formules à utiliser** :
```
Records/s = Nombre capteurs / Intervalle secondes
MB/s = (Records/s × Taille record) / 1 048 576
Shards écriture = MB/s / 1 MB/s
Shards lecture = (MB/s × Nb consumers) / 2 MB/s
Shards nécessaires = MAX(Shards écriture, Shards lecture)
```

---

## QUESTION 2 - CHOIX DATA STREAMS VS FIREHOSE (10 points)

### Contexte

Trois scénarios réels de l'entreprise nécessitent des solutions streaming :

**SCENARIO A - Logs applicatifs** :
- 200 GB de logs/jour
- Destination : S3 pour archivage
- Aucun traitement temps réel nécessaire
- Budget limité

**SCENARIO B - Transactions bancaires** :
- 50 000 transactions/seconde
- 3 systèmes doivent consommer en parallèle :
  - Système fraud detection (temps réel)
  - Système comptabilité (batch quotidien)
  - Système analytics (temps réel)
- Replay des dernières 24h requis

**SCENARIO C - Events utilisateurs mobile** :
- 10 000 events/seconde
- Dashboard analytics quasi temps réel (latence < 2 min acceptable)
- Enrichissement géolocalisation nécessaire
- Destination finale : OpenSearch

### Consigne

Pour chaque scénario, choisissez et justifiez la solution Kinesis.

**Vous devez fournir (pour chaque scénario)** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Solution choisie** | Streams, Firehose, ou combinaison + pourquoi | 2 pts |
| **2. Schéma pipeline** | Diagramme du flux de données complet | 2 pts |
| **3. Justification technique** | Latence, coût, complexité, fonctionnalités | 2 pts |
| **4. Configuration** | Paramètres clés (shards, buffer, retention) | 1 pt |

> **Livrables obligatoires** :  
> - 3 schémas de pipeline (un par scénario)  
> - Tableau comparatif des 3 solutions  
> - Estimations de coûts pour chaque scénario

---

## GRILLE D'ÉVALUATION

| Critère | Points | Détails |
|---------|--------|---------|
| **Schémas architectures** | /8 | Clarté, complétude, annotations |
| **Calculs techniques** | /6 | Justesse, méthodologie, résultats |
| **Justifications** | /4 | Pertinence choix, arguments solides |
| **Faisabilité** | /2 | Solutions réalistes, production-ready |

---

## BARÈME

- **18-20** : Excellent - Schémas parfaits, calculs exacts, justifications complètes
- **15-17** : Très bien - Bonne architecture, calculs corrects, bonnes justifications
- **12-14** : Bien - Architecture fonctionnelle, quelques imprécisions
- **10-11** : Passable - Architecture basique, erreurs de calcul
- **< 10** : Insuffisant - Architecture incohérente ou incomplète

