# INDEX DE LA FORMATION - PARTIE 2
## PIPELINES ETL BATCH AWS

**Version** : 1.0 Professionnelle  
**Format** : Condensé et minimaliste  
**Durée totale** : 3h30 cours + 2h30 évaluations

---

# STRUCTURE COMPLETE

```
FORMATION-PROFESSIONNELLE-PARTIE-2/
│
├── README.md
├── 00-INDEX-FORMATION.md (ce fichier)
├── 00-GUIDE-UTILISATION.md
│
├── 01-COURS/ (4 modules - 3h30)
│   ├── MODULE-01-ETL-Batch-vs-Streaming.md
│   ├── MODULE-02-AWS-Step-Functions.md
│   ├── MODULE-03-AWS-Glue-Athena.md
│   └── MODULE-04-Optimisation-Parquet-Partitionnement.md
│
├── 02-EVALUATIONS/
│   ├── QCM/
│   │   ├── QCM-MODULE-01.md (10 questions)
│   │   ├── QCM-MODULE-02.md (10 questions)
│   │   ├── QCM-MODULE-03.md (10 questions)
│   │   ├── QCM-MODULE-04.md (10 questions)
│   │   └── CORRIGES-QCM.md
│   │
│   └── QUESTIONS-DEVELOPPEMENT/
│       ├── DEV-MODULES-01-02-Workflows.md (2 questions)
│       └── DEV-MODULES-03-04-Optimisation.md (2 questions)
│
└── 03-RESSOURCES/
    └── GLOSSAIRE-ETL.md
```

---

# MODULES DE COURS

## Détail des Modules

| Module | Titre | Durée | Niveau | Diagrammes | Code |
|--------|-------|-------|--------|------------|------|
| **01** | ETL Batch vs Streaming | 45 min | Fondamental | 5 Mermaid | SQL |
| **02** | AWS Step Functions | 60 min | Intermédiaire | 6 Mermaid | JSON |
| **03** | AWS Glue & Athena | 60 min | Intermédiaire | 4 Mermaid | SQL |
| **04** | Optimisation Parquet | 45 min | Avancé | 2 Mermaid | SQL |

**Total** : 3h30 - 17 diagrammes - Nombreux exemples code

---

# EVALUATIONS

## QCM (40 questions - 60 minutes)

| Fichier | Questions | Durée | Points |
|---------|-----------|-------|--------|
| QCM-MODULE-01 | 10 | 15 min | 10 |
| QCM-MODULE-02 | 10 | 15 min | 10 |
| QCM-MODULE-03 | 10 | 15 min | 10 |
| QCM-MODULE-04 | 10 | 15 min | 10 |
| **TOTAL** | **40** | **60 min** | **40** |

## Questions de Développement (4 questions - 120 minutes)

| Fichier | Questions | Points | Durée |
|---------|-----------|--------|-------|
| DEV-MODULES-01-02-Workflows | 2 | 20 | 60 min |
| DEV-MODULES-03-04-Optimisation | 2 | 20 | 60 min |
| **TOTAL** | **4** | **40** | **120 min** |

---

# PARCOURS PEDAGOGIQUE

## Semaine 1 : ETL Batch et Orchestration

**Jour 1** : MODULE 01 (ETL Batch vs Streaming)  
**Jour 2** : MODULE 02 (Step Functions)  
**Jour 3** : QCM Modules 01-02  
**Jour 4-5** : Questions développement workflows

## Semaine 2 : Glue, Athena et Optimisation

**Jour 1** : MODULE 03 (Glue & Athena)  
**Jour 2** : MODULE 04 (Optimisation Parquet)  
**Jour 3** : QCM Modules 03-04  
**Jour 4-5** : Questions développement optimisation

---

# OBJECTIFS D'APPRENTISSAGE

## Par Module

**MODULE 01** :
- Différencier batch et streaming
- Choisir approche selon cas d'usage
- Comprendre architecture Lambda (architecturale)

**MODULE 02** :
- Concevoir workflows Step Functions
- Maîtriser types d'états (Task, Choice, Map, Parallel)
- Implémenter gestion d'erreurs (Retry, Catch)

**MODULE 03** :
- Utiliser Glue Data Catalog
- Requêter S3 avec Athena SQL
- Créer tables et vues
- Utiliser CTAS

**MODULE 04** :
- Optimiser avec format Parquet
- Choisir compression appropriée
- Partitionner efficacement
- Calculer ROI optimisations

---

# COMPARAISON PARTIE 1 vs PARTIE 2

| Aspect | PARTIE 1 - Streaming | PARTIE 2 - ETL Batch |
|--------|---------------------|----------------------|
| **Durée cours** | 5h15 (6 modules) | 3h30 (4 modules) |
| **QCM** | 60 questions | 40 questions |
| **Questions dév** | 12 questions | 4 questions |
| **Technologies** | Kinesis, Lambda, OpenSearch | Step Functions, Glue, Athena |
| **Latence** | < 1 seconde | Minutes à heures |
| **Cas d'usage** | Temps réel, alertes | Rapports, BI, ML |

**Complémentaires** : Ensemble couvre ingénierie données AWS complète

---

# NOTATION

## Répartition

| Composante | Poids | Détails |
|------------|-------|---------|
| QCM | 40% | 40 questions, 40 points |
| Questions Développement | 50% | 4 questions, 40 points |
| Participation | 10% | Engagement |

**Note finale** : Moyenne pondérée /20

**Seuil réussite** : 12/20

---

# RESSOURCES

## Documentation AWS

- AWS Step Functions Developer Guide
- AWS Glue Developer Guide
- Amazon Athena User Guide
- Apache Parquet Format Specification

## Pratique

- AWS Free Tier (Athena, Glue, S3)
- AWS Workshops ETL
- Exemples GitHub AWS

---

**Dernière mise à jour** : Octobre 2025  
**Auteur** : Formation Data Engineering AWS

