# GUIDE D'UTILISATION
## FORMATION PROFESSIONNELLE - STREAMING AWS

> Guide complet pour utiliser efficacement cette formation

---

# PRESENTATION GENERALE

Cette formation professionnelle condense **31 chapitres** en **6 modules essentiels** focalisés sur l'ingénierie des données en streaming avec AWS.

**Durée totale** : 5h15 de cours + 3h50 d'évaluations  
**Format** : Minimaliste, professionnel, sans emojis  
**Style** : GitHub-ready avec diagrammes Mermaid

---

# STRUCTURE DETAILLEE

## 01-COURS (6 Modules - 5h15)

| Module | Titre | Durée | Niveau | Contenu Clé |
|--------|-------|-------|--------|-------------|
| **01** | Architecture Streaming AWS | 45 min | Fondamental | 5V, services AWS, workflow |
| **02** | Amazon Kinesis | 60 min | Intermédiaire | Streams vs Firehose, choix |
| **03** | Transformation Lambda | 45 min | Intermédiaire | Serverless, enrichissement |
| **04** | OpenSearch Indexation | 60 min | Intermédiaire+ | Index, mappings, visualisations |
| **05** | Sécurité Encryption | 45 min | Intermédiaire | IAM, Cognito, KMS |
| **06** | Comparaisons Technologiques | 60 min | Avancé | Kinesis vs Kafka, alternatives |

### Caractéristiques des Modules

**Format uniforme** :
- Titres markdown structurés (# 1., ## 1.1)
- Diagrammes Mermaid colorés (fond sombre)
- Tableaux markdown pour comparaisons
- Blocs de code avec syntaxe (json, http, python)
- Sections séparées par `---`
- Pas de lignes `================`

**Éléments visuels** :
- Diagrammes de flux (flowchart)
- Diagrammes de séquence (sequenceDiagram)
- Diagrammes de décision (graph TD)
- Schémas d'architecture colorés

## 02-EVALUATIONS

### QCM (60 questions - 80 min)

| Fichier | Questions | Durée | Format |
|---------|-----------|-------|--------|
| QCM-MODULE-01 | 10 | 20 min | Checkbox GitHub |
| QCM-MODULE-02 | 10 | 20 min | Checkbox GitHub |
| QCM-MODULES-03-06 | 40 | 40 min | Checkbox GitHub |

**Format des questions** :
```markdown
### Question X

Texte de la question ?

- [ ] A. Réponse A
- [ ] B. Réponse B
- [ ] C. Réponse C
- [ ] D. Réponse D
```

**Corrigés** : Fichier CORRIGES-QCM.md avec tableaux de réponses

### Questions de Développement (15 questions - 150 min)

| Fichier | Questions | Modules | Durée |
|---------|-----------|---------|-------|
| QUESTIONS-MODULE-01 | 5 | Module 1 | 60 min |
| QUESTIONS-MODULES-02-06 | 10 | Modules 2-6 | 90 min |

**Format structuré** :
- Contexte clair avec données chiffrées
- Tableau décomposant la consigne (a, b, c, d)
- Points attribués par partie
- Attendu précis (type réponse + nb mots)

**Exemple** :
```markdown
### Consigne

**Votre réponse doit inclure :**

| Partie | Description | Points |
|--------|-------------|--------|
| **a)** | Calculez le volume | 2 pts |
| **b)** | Architecturez | 3 pts |

> **Attendu** : Calculs + schéma (300 mots)
```

## 03-RESSOURCES

- **GLOSSAIRE-TECHNIQUE.md** : Définitions alphabétiques de tous les concepts

---

# PARCOURS D'APPRENTISSAGE

## Parcours Débutant (3 semaines)

**Semaine 1** : Fondamentaux
- Jour 1-2 : MODULE 1 + MODULE 2
- Jour 3 : QCM-MODULE-01 + QCM-MODULE-02
- Jour 4-5 : Questions développement 1-7

**Semaine 2** : Transformation & Indexation
- Jour 1 : MODULE 3
- Jour 2 : MODULE 4
- Jour 3-4 : Questions développement 8-11
- Jour 5 : Révision + mini-projet

**Semaine 3** : Sécurité & Comparaisons
- Jour 1 : MODULE 5
- Jour 2 : MODULE 6
- Jour 3 : QCM-MODULES-03-06
- Jour 4-5 : Questions développement 12-15

## Parcours Intensif (1 semaine)

**Jour 1** : MODULE 1 + MODULE 2 + QCM
**Jour 2** : MODULE 3 + MODULE 4 + Questions 1-7
**Jour 3** : MODULE 5 + MODULE 6
**Jour 4** : QCM-MODULES-03-06 + Questions 8-11
**Jour 5** : Questions 12-15 + Révision générale

## Parcours Révision (Avant Certification)

**Focus sur** :
- Tableaux comparatifs (Streams vs Firehose, Kinesis vs Kafka)
- Calculs de dimensionnement (shards, coûts)
- Patterns d'architecture (Fan-Out, Transformation Pipeline)
- Sécurité (IAM, Cognito, KMS)

---

# CONSEILS D'UTILISATION

## Pour les Étudiants

### Étudier les Modules

1. **Lecture active** : Prenez des notes, dessinez les schémas
2. **Comprendre les diagrammes** : Analysez chaque diagramme Mermaid
3. **Retenir les tableaux** : Comparatifs très importants pour QCM
4. **Faire les exercices** : En fin de chaque module

### Réussir les QCM

- **Avant** : Réviser les modules concernés
- **Pendant** : Lire attentivement, éliminer réponses fausses
- **Après** : Analyser erreurs avec corrigés
- **Si < 60%** : Réviser puis refaire le QCM

### Réussir les Questions de Développement

- **Structure** : Toujours intro → analyse → solution → conclusion
- **Tableaux** : Utilisez tableaux pour comparer options
- **Chiffres** : Donnez des estimations (coûts, latences, débits)
- **Schémas** : Dessinez architectures pour clarifier
- **Justification** : Chaque choix doit être argumenté

## Pour les Formateurs

### Utilisation en Cours

**Projection** : Les diagrammes Mermaid s'affichent parfaitement sur GitHub  
**Exercices** : Utiliser les questions de développement comme études de cas  
**Évaluations** : QCM pour contrôle continu, questions développement pour examens

### Adaptation du Contenu

**Durée réduite** : Sélectionner modules 1, 2, 4 (minimum viable)  
**Durée étendue** : Ajouter laboratoires pratiques AWS  
**Spécialisation** : Focus sur modules spécifiques selon public

---

# EVALUATION ET NOTATION

## Système de Notation

| Composante | Poids | Note | Durée |
|------------|-------|------|-------|
| QCM (60 questions) | 30% | /60 | 80 min |
| Questions Développement (15) | 50% | /20 (par question) | 150 min |
| Participation / Projet | 20% | /20 | Variable |

**Note finale** : Moyenne pondérée sur 20

**Seuil réussite** : 12/20

## Barème Questions Développement

Pour chaque question, notation selon grille :

| Score | Niveau | Caractéristiques |
|-------|--------|------------------|
| **18-20** | Excellent | Analyse exhaustive, solutions innovantes, chiffrage précis |
| **15-17** | Très bien | Bonne compréhension, solutions pertinentes, arguments solides |
| **12-14** | Bien | Compréhension correcte, solutions fonctionnelles, manque profondeur |
| **10-11** | Passable | Connaissances base, solutions partielles |
| **< 10** | Insuffisant | Lacunes importantes, solutions inadaptées |

---

# TROUBLESHOOTING

## Problèmes Courants

### Les diagrammes Mermaid ne s'affichent pas

**Cause** : Éditeur ne supporte pas Mermaid  
**Solution** : Ouvrir sur GitHub ou utiliser extension VS Code "Markdown Preview Mermaid"

### Les blocs de code ne sont pas colorés

**Cause** : Manque syntaxe après triple backticks  
**Solution** : Vérifier que blocs ont `json`, `http`, `python` etc.

### Je ne comprends pas un concept

**Solution** :
1. Consulter GLOSSAIRE-TECHNIQUE.md
2. Relire section module concerné
3. Consulter documentation AWS officielle
4. Poser question en cours/forum

---

# RESSOURCES EXTERNES

## Documentation AWS

- [AWS Kinesis](https://docs.aws.amazon.com/kinesis/)
- [AWS Lambda](https://docs.aws.amazon.com/lambda/)
- [Amazon OpenSearch](https://docs.aws.amazon.com/opensearch-service/)
- [AWS Well-Architected](https://aws.amazon.com/architecture/well-architected/)

## Tutoriels Pratiques

- AWS Free Tier : 12 mois gratuits
- AWS Workshops : workshops.aws
- AWS Architecture Center : Patterns et exemples

## Communauté

- AWS re:Post (forums officiels)
- Stack Overflow (tags: aws-kinesis, aws-lambda, opensearch)
- Reddit r/aws

---

# CERTIFICATION AWS

## Préparation

Cette formation couvre partiellement :

**AWS Certified Data Analytics - Specialty** :
- Domaine 1 : Collection (Kinesis) - Couvert
- Domaine 2 : Stockage (S3, OpenSearch) - Couvert
- Domaine 3 : Processing (Lambda) - Couvert
- Domaine 4 : Analysis (Dashboards) - Couvert
- Domaine 5 : Security (IAM, KMS) - Couvert

**Compléments nécessaires** :
- Amazon EMR, Glue, Athena
- QuickSight
- Data Lake Formation
- Redshift

## Timeline Suggérée

**Après cette formation** → 2 semaines compléments → Certification

---

# CONTACT ET SUPPORT

Pour questions sur la formation :
1. Consulter ce guide
2. README.md principal
3. Modules concernés
4. Glossaire technique

---

**Version** : 1.0 Professionnelle  
**Dernière mise à jour** : Octobre 2025

