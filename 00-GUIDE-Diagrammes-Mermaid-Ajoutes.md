# Guide des Diagrammes Mermaid Ajoutés

Ce document récapitule tous les diagrammes Mermaid qui ont été ajoutés à la documentation AWS et OpenSearch pour améliorer la compréhension visuelle des concepts.

---

## Fichiers avec Diagrammes Mermaid Ajoutés

### **Section 1 : Introduction et Workflow (01-02)**

#### **01-Introduction-Services-AWS-Utilises.md**
- **Architecture Globale du Laboratoire** (graph TB)
  - Génération des données (EC2, Visiteurs)
  - Ingestion et Transformation (Kinesis, Lambda)
  - Stockage et Analyse (OpenSearch, Dashboards)
  - Sécurité et Monitoring (Cognito, IAM, CloudWatch)
  
- **Flux de Données Simplifié** (sequenceDiagram)
  - 11 étapes numérotées du visiteur jusqu'à la visualisation
  - Interactions entre tous les services

#### **02-Workflow-et-Etapes-Architecture-Laboratoire.md**
- **Diagramme des 9 Étapes du Laboratoire** (graph TB)
  - Étapes 1-3 : Examen (EC2, Kinesis, OpenSearch)
  - Étapes 4-6 : Configuration (Index, Génération logs, CloudWatch)
  - Étapes 7-9 : Visualisation (Index pattern, Pie chart, Heat map)
  
- **Workflow Détaillé en Diagramme de Séquence** (sequenceDiagram)
  - 11 acteurs et participants
  - Flux complet du visiteur aux dashboards

---

### **Section 2 : Comparaison Kinesis (03-07)**

#### **03-Comparaison-Kinesis-Firehose-vs-Kinesis-Streams.md**
- **Diagramme de Décision : Firehose vs Streams** (graph TD)
  - Arbre de décision basé sur les besoins
  - Critères : transformations, consommateurs, latence
  
- **Comparaison Visuelle des Caractéristiques** (graph LR)
  - Comparaison côte à côte des 5 critères principaux

#### **04-Architecture-Pipeline-Donnees-Streaming-AWS.md**
- **Architecture Complète du Pipeline** (graph TB)
  - 4 subgraphs : Ingestion, Transformation, Stockage, Visualisation
  - Toutes les options de destination (S3, OpenSearch, Redshift)

#### **05-Differences-Fonctionnelles-Streams-vs-Firehose-Partie-1.md**
- **Analogie du Restaurant en Diagramme** (graph LR)
  - Comparaison Restaurant vs Architecture AWS
  - Métaphores visuelles
  
- **Architecture avec les Deux Services** (graph TB)
  - 2 options d'architecture (Streams + Firehose / Direct PUT)
  - Multiples consommateurs et destinations

#### **06-Differences-Fonctionnelles-Streams-vs-Firehose-Partie-2.md**
- **Métaphore du Concert en Diagramme** (graph LR)
  - Analogie concert vs AWS
  - Comparaison visuelle
  
- **Tableau Comparatif Visuel** (graph TB)
  - 5 caractéristiques de chaque service

#### **07-Utilisation-Exclusive-Streams-ou-Firehose.md**
- **Diagramme de Décision : Streams Only vs Firehose Only** (graph TD)
  - 3 chemins : Streams only, Firehose only, Les deux
  - Avantages et inconvénients de chaque option
  
- **Cas d'Usage par Scénario** (graph LR)
  - 9 cas d'usage répartis en 3 catégories

---

### **Section 3 : Architecture et Pipelines (08-12)**

#### **08-Role-Serveur-EC2-Generation-Logs-Web.md**
- **Architecture EC2 dans le Pipeline de Logs** (graph TB)
  - 4 subgraphs : Génération, Agent & Transmission, Traitement, Visualisation
  - Flux complet des visiteurs aux dashboards

---

### **Section 4 : Sécurité et Authentification (13-16)**

#### **13-Authentification-Cognito-Acces-Securise-OpenSearch.md**
- **Architecture de Sécurité avec Cognito** (sequenceDiagram)
  - 11 étapes d'authentification
  - Interactions Cognito, IAM, OpenSearch
  
- **Flux d'Authentification et Autorisation** (graph TB)
  - Arbre de décision complet
  - 3 types d'accès (Lecture, Lecture+Écriture, Admin)

---

### **Section 5 : Comparaison Kafka (21-24)**

#### **21-Comparaison-Kinesis-vs-Kafka.md**
- **Diagramme de Comparaison Visuelle** (graph TB)
  - 6 caractéristiques de chaque plateforme
  - Comparaison côte à côte
  
- **Diagramme de Décision : Kinesis vs Kafka** (graph TD)
  - Arbre de décision basé sur : Cloud, Infrastructure, Latence, Budget

---

### **Section 6 : Guide de Décision (25)**

#### **25-Choix-Lambda-Firehose-ou-DataStreams.md**
- **Arbre de Décision : Lambda vs Firehose vs Data Streams** (graph TD)
  - Décisions basées sur : besoin principal, volume, nombre de consommateurs
  - Suggestions de combinaisons
  
- **Matrice de Comparaison Visuelle** (graph LR)
  - 4 caractéristiques par service (12 au total)

---

## Statistiques des Diagrammes Ajoutés

| Type de Diagramme | Nombre | Utilisation |
|-------------------|--------|-------------|
| **graph TB** (Top to Bottom) | 8 | Architectures, workflows verticaux |
| **graph TD** (Top Down) | 5 | Arbres de décision |
| **graph LR** (Left to Right) | 4 | Comparaisons, flux horizontaux |
| **sequenceDiagram** | 3 | Interactions temporelles |
| **TOTAL** | **20** | **Dans 12 fichiers** |

---

## Palette de Couleurs Utilisée

Les diagrammes utilisent une palette cohérente pour faciliter la reconnaissance visuelle :

| Service / Concept | Couleur | Code Hex |
|-------------------|---------|----------|
| **EC2** | Orange | #ff9900 |
| **Kinesis Data Streams** | Bleu royal | #4169e1 |
| **Kinesis Firehose** | Violet | #9370db |
| **Lambda** | Rouge-orange | #ff6b6b |
| **OpenSearch** | Bleu acier | #4b8bbe |
| **Cognito / Sécurité** | Rouge foncé | #dd344c |
| **IAM** | Orange foncé | #ff9900 |
| **CloudWatch** | Rose | #cc2264 |
| **S3** | Vert | #569a31 |
| **Succès / Validation** | Vert clair | #32cd32 |
| **Erreur / Attention** | Rouge | #dc143c |

---

## Types de Diagrammes par Catégorie

### **Diagrammes d'Architecture** (8 diagrammes)
- Montrent la structure complète des systèmes
- Utilisent `graph TB` pour une vue hiérarchique
- Incluent des subgraphs pour grouper les composants

### **Diagrammes de Décision** (5 diagrammes)
- Aident à choisir entre différentes options
- Utilisent `graph TD` avec des nœuds de décision (losanges)
- Incluent des avantages/inconvénients

### **Diagrammes de Comparaison** (4 diagrammes)
- Comparent deux ou plusieurs services
- Utilisent `graph LR` pour une comparaison côte à côte
- Souvent avec des subgraphs séparés

### **Diagrammes de Séquence** (3 diagrammes)
- Montrent les interactions temporelles
- Utilisent `sequenceDiagram` avec numérotation
- Idéaux pour les workflows d'authentification

---

## Bonnes Pratiques Utilisées

1. **Émojis** : Ajoutés pour rendre les diagrammes plus visuels et mémorables
2. **Subgraphs** : Utilisés pour grouper logiquement les composants
3. **Styles** : Couleurs cohérentes pour chaque service AWS
4. **Annotations** : Notes et labels pour clarifier les flux
5. **Numérotation** : Dans les séquences pour suivre l'ordre des étapes

---

## Fichiers Restants Sans Diagrammes

Les fichiers suivants pourraient bénéficier de diagrammes supplémentaires si nécessaire :

### **Section OpenSearch (17-20)**
- 17-Limites-Stockage-Cluster-OpenSearch.md
- 18-Limites-Noeuds-Donnees-Chaudes-Froides.md
- 19-Apercu-Limites-Optimisations-OpenSearch.md
- 20-Alternatives-OpenSearch-Indexation-Recherche.md

### **Section Kafka Alternatives (22-24)**
- 22-Kinesis-Data-Streams-Equivalent-Kafka.md
- 23-Alternatives-Apache-Kafka-Streaming.md
- 24-Comparaison-Kafka-vs-Pulsar.md

### **Section Laboratoires (26-31)**
- 26-Laboratoire-Complet-Vue-Ensemble.md
- 27-Laboratoire-Description-Taches.md
- 28-31 (Tâches spécifiques du laboratoire)

### **Section Sécurité (14-16)**
- 14-Securite-Encryption-Transit-et-Repos.md
- 15-Configuration-Encryption-Kinesis-Firehose.md
- 16-Gestion-Encryption-Kinesis-Data-Firehose.md

### **Section Pipelines (09-12)**
- 09-Workflow-Complet-Analyse-Logs-Web-AWS.md
- 10-Pipeline-Kinesis-Firehose-Lambda-OpenSearch.md
- 11-Analogie-Fonctionnement-Kinesis-Lambda-OpenSearch.md
- 12-Exemple-Pratique-Architecture-AWS-SAQ.md

---

## Comment Visualiser les Diagrammes

Les diagrammes Mermaid peuvent être visualisés dans :

1. **GitHub** : Affichage natif dans les fichiers `.md`
2. **VS Code** : Extension "Markdown Preview Mermaid Support"
3. **Mermaid Live Editor** : https://mermaid.live/
4. **Documentation Sites** : GitBook, Read the Docs, etc.

---

## Ressources Mermaid

- **Documentation officielle** : https://mermaid.js.org/
- **Syntaxe flowchart** : https://mermaid.js.org/syntax/flowchart.html
- **Syntaxe sequence** : https://mermaid.js.org/syntax/sequenceDiagram.html
- **Éditeur en ligne** : https://mermaid.live/

---

**Date de création** : Octobre 2025  
**Nombre total de diagrammes** : 20  
**Fichiers modifiés** : 12 / 32  
**Couverture** : ~38% des fichiers documentés

**Prochaine étape suggérée** : Ajouter des diagrammes aux fichiers restants pour atteindre 100% de couverture visuelle.

