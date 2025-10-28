# QUESTIONS DE DÉVELOPPEMENT - MODULES 2 à 6

> **Durée recommandée** : 90 minutes  
> **Format** : Réponses rédigées (300-500 mots par question)  
> **Évaluation** : Analyse, synthèse, résolution de problèmes

---

# MODULE 2 - AMAZON KINESIS

## QUESTION 6 - DIMENSIONNEMENT (8 points)

### Contexte

Une application IoT collecte des données de 10 000 capteurs. Chaque capteur envoie un message de 500 bytes toutes les 10 secondes.

**Exigences** :
- 2 applications doivent consommer ces données en parallèle
- Une pour alertes temps réel (latence < 1s)
- Une pour archivage S3

### Consigne

a) Calculez le volume de données (records/s et MB/s)  
b) Dimensionnez le nombre de shards Kinesis Data Streams nécessaires  
c) Architecturez la solution complète (schéma + explications)  
d) Estimez le coût mensuel (utilisez tarification publique AWS)  
e) Proposez une stratégie de scaling si le nombre de capteurs double

---

## QUESTION 7 - CHOIX TECHNOLOGIQUE (7 points)

### Contexte

Comparez Kinesis Data Streams et Kinesis Data Firehose pour les scénarios suivants :

**SCENARIO A** : Logs applicatifs vers S3 pour archivage long terme

**SCENARIO B** : Transactions financières nécessitant traitement par 3 systèmes distincts avec replay possible

**SCENARIO C** : Events e-commerce vers dashboard analytics quasi temps réel

### Consigne

Pour chaque scénario :
- Recommandez la solution (Streams, Firehose, ou les deux)
- Justifiez votre choix (latence, coût, complexité, fonctionnalités)
- Décrivez l'architecture technique

---

# MODULE 3 - TRANSFORMATION AVEC AWS LAMBDA

## QUESTION 8 - OPTIMISATION PERFORMANCE (8 points)

### Contexte

Votre fonction Lambda traite des logs Kinesis avec ces caractéristiques :

**Configuration actuelle** :
- Mémoire : 512 MB
- Batch size : 100 records
- Durée moyenne : 45 secondes par batch
- Invocations : 1 000 000/mois
- Coût mensuel : 150 USD

**Le traitement inclut** :
- Parsing regex des logs
- Lookup géolocalisation (API externe, 100ms latency)
- Enrichissement depuis DynamoDB

### Consigne

a) Identifiez les goulots d'étranglement potentiels  
b) Proposez 4 optimisations concrètes avec justification technique  
c) Estimez le gain de performance et d'économie pour chaque optimisation  
d) Réécrivez les parties critiques du code avec pseudo-code optimisé

---

## QUESTION 9 - GESTION D'ERREURS (7 points)

### Contexte

Dans un pipeline Kinesis Streams → Lambda → OpenSearch, vous observez :
- 2% des records échouent au traitement Lambda
- Causes : timeouts API externes, données malformées, erreurs transitoires

### Consigne

a) Concevez une stratégie complète de gestion d'erreurs  
b) Différenciez le traitement selon le type d'erreur  
c) Implémentez un système de Dead Letter Queue avec reprocessing  
d) Proposez un monitoring et alerting appropriés

---

# MODULE 4 - OPENSEARCH ET INDEXATION

## QUESTION 10 - CONCEPTION INDEX (8 points)

### Contexte

Vous devez indexer des logs d'application avec cette structure :

```json
{
  "timestamp": "2025-10-28T10:15:30Z",
  "level": "ERROR",
  "service": "payment-api",
  "user_id": "usr_123456",
  "message": "Payment processing failed",
  "stack_trace": "...",
  "metadata": {
    "amount": 99.99,
    "currency": "USD",
    "country": "FR"
  }
}
```

**Volume** : 1 TB/mois  
**Rétention** : 90 jours  
**Recherches** : Fréquentes sur 7 derniers jours

### Consigne

a) Définissez les mappings OpenSearch appropriés (types de champs)  
b) Dimensionnez le cluster (nombre shards, replicas, types instances)  
c) Implémentez une stratégie ILM hot-warm-cold avec transitions  
d) Proposez 3 visualisations pertinentes pour les équipes ops

---

## QUESTION 11 - MIGRATION ET PERFORMANCE (7 points)

### Contexte

Un cluster OpenSearch existant montre ces symptômes :
- Latence indexation : 5 secondes (auparavant 500ms)
- Recherches lentes : 10+ secondes
- JVM heap usage : 95% constant
- Cluster state : Yellow
- Taille moyenne shards : 120 GB

### Consigne

a) Diagnostiquez les problèmes (causes racines)  
b) Proposez un plan de remédiation étape par étape  
c) Priorisez les actions (quick wins vs long terme)  
d) Établissez des KPIs pour valider l'amélioration

---

# MODULE 5 - SECURITE ET ENCRYPTION

## QUESTION 12 - AUDIT SECURITE (8 points)

### Contexte

Auditez cette architecture du point de vue sécurité :

```
EC2 (public subnet) → Kinesis → Lambda → OpenSearch (public access)
Dashboard : accessible sans authentification
IAM : rôle EC2 avec AdministratorAccess
Encryption : aucune
CloudTrail : désactivé
```

### Consigne

a) Identifiez toutes les vulnérabilités et risques  
b) Classez par criticité (critique, élevé, moyen, faible)  
c) Proposez des corrections techniques précises pour chaque vulnérabilité  
d) Concevez l'architecture sécurisée cible avec justifications

---

## QUESTION 13 - CONFORMITE RGPD (7 points)

### Contexte

Votre pipeline streaming collecte des données utilisateurs européens.

**Requirements RGPD** :
- Droit à l'effacement (right to be forgotten)
- Pseudonymisation
- Audit des accès données
- Limitation de rétention

### Consigne

a) Identifiez les défis techniques pour respecter le RGPD avec streaming  
b) Proposez une architecture permettant l'effacement des données  
c) Implémentez la pseudonymisation dans le pipeline  
d) Définissez une politique de rétention complète

---

# MODULE 6 - COMPARAISONS TECHNOLOGIQUES

## QUESTION 14 - DECISION STRATEGIQUE (9 points)

### Contexte

Votre entreprise (500 personnes, multi-cloud AWS+GCP) évalue les options pour une nouvelle plateforme de streaming data.

**Context** :
- Volume : 50 GB/jour actuellement, 500 GB/jour prévu dans 2 ans
- Use cases : analytics temps réel, ML training, data lake feeding
- Equipe : 3 data engineers (1 avec expertise Kafka)
- Budget : 5000 USD/mois
- Contrainte : portabilité multi-cloud souhaitée

**OPTIONS** :
- A) Amazon Kinesis
- B) Apache Kafka self-hosted (EC2)
- C) Amazon MSK (Managed Kafka)
- D) Confluent Cloud (Kafka SaaS)

### Consigne

a) Analysez chaque option selon 6 critères (coût, expertise, scalabilité, portabilité, fonctionnalités, opérationnel)  
b) Créez une matrice de décision avec scoring  
c) Recommandez la solution optimale avec justification détaillée  
d) Proposez un plan de migration si changement d'une solution existante

---

## QUESTION 15 - ARCHITECTURE HYBRID (8 points)

### Contexte

Concevez une architecture pour une entreprise avec :
- Datacenter on-premise (applications legacy)
- Cloud AWS (nouvelles applications)
- Exigence : streaming unifié entre on-prem et cloud

**Contraintes** :
- Latence < 5 secondes entre on-prem et cloud
- Données sensibles ne peuvent quitter le datacenter
- Budget limité pour refonte applications legacy

### Consigne

a) Proposez une architecture hybride détaillée  
b) Expliquez la synchronisation données on-prem ↔ cloud  
c) Addressez la sécurité du lien réseau  
d) Évaluez les alternatives (Kafka, Kinesis, autre)  
e) Estimez la complexité d'implémentation et maintenance

---

## CRITERES D'EVALUATION GLOBAUX

### Grille d'Évaluation

| Critère | Poids | Description |
|---------|-------|-------------|
| **Compréhension technique** | 40% | Maîtrise concepts, cohérence architecturale |
| **Analyse et réflexion** | 30% | Identification problèmes, évaluation trade-offs |
| **Communication** | 20% | Clarté, structure, justifications |
| **Créativité et pragmatisme** | 10% | Solutions innovantes, faisabilité |

### Barème de Notation

| Score | Appréciation |
|-------|--------------|
| **18-20/20** | Excellent - Analyse exhaustive, solutions innovantes |
| **15-17/20** | Très bien - Bonne compréhension, solutions pertinentes |
| **12-14/20** | Bien - Compréhension correcte, manque de profondeur |
| **10-11/20** | Passable - Connaissances de base, solutions partielles |
| **< 10/20** | Insuffisant - Lacunes importantes |

---

## CONSEILS REDACTION

### Structure Recommandée

1. **Introduction** (10%) : Reformuler le problème, contexte
2. **Analyse** (30%) : Identifier enjeux, contraintes, options
3. **Solution** (40%) : Propositions détaillées, justifications
4. **Conclusion** (20%) : Synthèse, recommandation finale

### Best Practices

✅ Structurez vos réponses clairement  
✅ Utilisez des schémas si pertinent  
✅ Quantifiez quand possible (coûts, latence, débit)  
✅ Justifiez tous vos choix techniques  
✅ Citez des exemples concrets  
✅ Anticipez les objections et limitations  
✅ Évaluez les trade-offs (avantages vs inconvénients)

### Erreurs à Éviter

❌ Réponses trop courtes ou superficielles  
❌ Absence de justification des choix  
❌ Ignorer les contraintes du contexte  
❌ Solutions irréalistes ou trop théoriques  
❌ Manque de chiffrage (coûts, performances)
