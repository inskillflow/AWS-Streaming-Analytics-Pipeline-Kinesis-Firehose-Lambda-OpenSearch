# QUESTIONS DE DÉVELOPPEMENT - MODULE 6
## COMPARAISONS TECHNOLOGIQUES

> **Durée** : 50 minutes  
> **Note** : 20 points  
> **Format** : Analyses comparatives + architectures + matrices de décision

---

## QUESTION 1 - KINESIS VS KAFKA - CHOIX STRATEGIQUE (10 points)

### Contexte

Entreprise fintech (800 personnes) doit choisir plateforme streaming pour :

**Use cases** :
- Transactions bancaires temps réel (100K transactions/seconde)
- Détection fraude (latence < 100ms critique)
- Analytics client (dashboards)
- Data lake feeding (archivage)
- Event-driven microservices (50 services)

**Contexte technique** :
- Infrastructure : 80% AWS, 20% on-premise
- Équipe : 8 data engineers (2 avec expertise Kafka, 6 AWS)
- Budget : 15 000 USD/mois
- Croissance prévue : × 3 en 2 ans

**OPTIONS** :
- **A** : Amazon Kinesis (Data Streams + Firehose)
- **B** : Apache Kafka self-hosted sur EC2
- **C** : Amazon MSK (Managed Kafka)
- **D** : Architecture hybride Kinesis + Kafka

### Consigne

Réalisez une analyse comparative complète et recommandez la solution.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Schéma chaque option** | 4 architectures avec flux de données | 3 pts |
| **2. Matrice comparative** | Tableau 4 options × 8 critères avec scoring /5 | 3 pts |
| **3. Analyse détaillée** | Avantages/inconvénients de chaque option | 2 pts |
| **4. Recommandation** | Choix final argumenté + plan déploiement | 2 pts |

> **Livrables obligatoires** :  
> - 4 schémas d'architecture (un par option)  
> - Matrice de décision avec scores  
> - Tableau TCO (Total Cost of Ownership) 3 ans  
> - Roadmap d'implémentation (6 mois)

**Critères d'évaluation à utiliser** :

| Critère | Poids | Description |
|---------|-------|-------------|
| Performance (débit/latence) | 20% | Capacité à gérer 100K txn/s |
| Coût (3 ans TCO) | 20% | Investissement + opérationnel |
| Expertise équipe | 15% | Courbe apprentissage |
| Scalabilité | 15% | Croissance × 3 en 2 ans |
| Portabilité | 10% | Dépendance vendor |
| Ecosystem | 10% | Intégrations disponibles |
| Opérationnel | 5% | Charge maintenance |
| Résilience | 5% | HA, DR capabilities |

---

## QUESTION 2 - ARCHITECTURE HYBRIDE ON-PREM + CLOUD (10 points)

### Contexte

Banque traditionnelle avec infrastructure mixte obligatoire :

**Infrastructure existante** :
- Datacenter principal : Applications core banking (mainframe + Java)
- Datacenter secondaire : DR site
- AWS Cloud : Applications digitales (mobile, web)

**Contraintes réglementaires** :
- Données bancaires core **ne peuvent PAS** quitter datacenter
- Données analytics **peuvent** aller dans cloud
- Latence streaming on-prem ↔ cloud < **3 secondes**
- Audit complet des flux de données

**Besoins** :
- Stream transactions (10K/s) : datacenter → cloud (analytics)
- Stream events utilisateurs (5K/s) : cloud → datacenter (détection fraude)
- Replay possible des 48 dernières heures

### Consigne

Concevez une architecture streaming hybride complète.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Architecture globale** | Schéma on-prem ↔ cloud avec tous composants | 4 pts |
| **2. Solution streaming** | Kafka/Kinesis/autre + justification choix | 2 pts |
| **3. Connectivité réseau** | VPN/Direct Connect + encryption + latence | 2 pts |
| **4. Flux bidirectionnels** | Diagrammes détaillés des 2 flux de données | 2 pts |

> **Livrables obligatoires** :  
> - Schéma architecture hybride complet  
> - Diagramme réseau (VPN/Direct Connect)  
> - 2 diagrammes de flux de données  
> - Tableau comparatif solutions (Kafka vs Kinesis vs MSK)  
> - Estimation latence bout-en-bout

**Exemple schéma attendu** :

```
┌─────────────────────────┐         ┌─────────────────────────┐
│   ON-PREMISE DATACENTER │         │      AWS CLOUD          │
│                         │         │                         │
│  [Core Banking]         │         │  [Mobile Apps]          │
│        ↓                │         │        ↓                │
│  [Kafka Cluster]        │<------->│  [Kinesis / MSK]        │
│        ↓                │  Direct │        ↓                │
│  [Analytics Local]      │  Connect│  [Lambda]               │
│                         │  VPN    │        ↓                │
│                         │  10Gbps │  [OpenSearch]           │
└─────────────────────────┘         └─────────────────────────┘
```

---

## GRILLE D'ÉVALUATION

### Critères

| Critère | Points | Description |
|---------|--------|-------------|
| **Architectures** | /9 | Complétude, clarté, annotations |
| **Analyses techniques** | /5 | Pertinence, profondeur, chiffrage |
| **Décisions** | /4 | Justifications, matrices, scoring |
| **Faisabilité** | /2 | Production-ready, réaliste |

---

## BARÈME

| Score | Niveau | Livrables |
|-------|--------|-----------|
| **18-20** | Excellent | Architectures parfaites, analyses exhaustives, décisions argumentées |
| **15-17** | Très bien | Bonnes architectures, analyses solides, choix justifiés |
| **12-14** | Bien | Architectures fonctionnelles, analyses correctes |
| **10-11** | Passable | Architectures basiques, analyses superficielles |
| **< 10** | Insuffisant | Architectures incohérentes, analyses insuffisantes |

