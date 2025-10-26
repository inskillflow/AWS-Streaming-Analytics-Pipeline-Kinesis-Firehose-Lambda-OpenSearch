# Table des Matières - Documentation AWS et OpenSearch

Ce document présente l'organisation complète de la documentation AWS et OpenSearch, renommée de manière professionnelle et organisée logiquement.

---

## 📚 Structure de la Documentation

### **Section 0 : Documentation Générale**
- **00-README-Documentation-AWS-OpenSearch.md** - README principal du projet

---

### **Section 1 : Introduction et Concepts de Base (01-07)**

#### **Architecture et Services Fondamentaux**
- **01-Introduction-Services-AWS-Utilises.md** - Introduction aux services AWS (EC2, Kinesis, Lambda, OpenSearch, Cognito, CloudWatch)
- **02-Workflow-et-Etapes-Architecture-Laboratoire.md** - Explication du workflow complet et des 9 étapes de l'architecture

#### **Comparaison Kinesis Firehose vs Kinesis Streams**
- **03-Comparaison-Kinesis-Firehose-vs-Kinesis-Streams.md** - Comparaison détaillée des deux services avec tableaux et cas d'usage
- **04-Architecture-Pipeline-Donnees-Streaming-AWS.md** - Guide de fonctionnement d'un pipeline de données en streaming
- **05-Differences-Fonctionnelles-Streams-vs-Firehose-Partie-1.md** - Différences fonctionnelles (métaphore restaurant)
- **06-Differences-Fonctionnelles-Streams-vs-Firehose-Partie-2.md** - Pourquoi utiliser les deux ensemble
- **07-Utilisation-Exclusive-Streams-ou-Firehose.md** - Quand utiliser uniquement l'un ou l'autre

---

### **Section 2 : Architecture et Pipelines (08-12)**

#### **Rôle des Composants**
- **08-Role-Serveur-EC2-Generation-Logs-Web.md** - Rôle du serveur EC2 dans la génération des logs
- **09-Workflow-Complet-Analyse-Logs-Web-AWS.md** - Workflow complet d'analyse des logs web
- **10-Pipeline-Kinesis-Firehose-Lambda-OpenSearch.md** - Pipeline complet avec transformation Lambda

#### **Exemples et Analogies**
- **11-Analogie-Fonctionnement-Kinesis-Lambda-OpenSearch.md** - Analogie de l'organisation d'un événement
- **12-Exemple-Pratique-Architecture-AWS-SAQ.md** - Exemple pratique avec la SAQ (Société d'Assurance du Québec)

---

### **Section 3 : Sécurité et Authentification (13-16)**

#### **Authentification et Encryption**
- **13-Authentification-Cognito-Acces-Securise-OpenSearch.md** - Gestion de l'authentification avec Cognito
- **14-Securite-Encryption-Transit-et-Repos.md** - Sécurisation des données en transit et au repos
- **15-Configuration-Encryption-Kinesis-Firehose.md** - Configuration de l'encryption dans Firehose
- **16-Gestion-Encryption-Kinesis-Data-Firehose.md** - Gestion complète de l'encryption (avec/sans encryption)

---

### **Section 4 : OpenSearch - Limites et Optimisations (17-20)**

#### **Capacités et Limites**
- **17-Limites-Stockage-Cluster-OpenSearch.md** - Limites de stockage par instance et cluster
- **18-Limites-Noeuds-Donnees-Chaudes-Froides.md** - Limites des nœuds et stratégies données chaudes/froides
- **19-Apercu-Limites-Optimisations-OpenSearch.md** - Aperçu complet des limites et optimisations
- **20-Alternatives-OpenSearch-Indexation-Recherche.md** - Alternatives à OpenSearch (Elasticsearch, Algolia, Solr, etc.)

---

### **Section 5 : Comparaisons avec Kafka et Alternatives (21-24)**

#### **Kinesis vs Kafka**
- **21-Comparaison-Kinesis-vs-Kafka.md** - Comparaison détaillée Kinesis vs Kafka
- **22-Kinesis-Data-Streams-Equivalent-Kafka.md** - Kinesis Data Streams comme équivalent de Kafka

#### **Alternatives de Streaming**
- **23-Alternatives-Apache-Kafka-Streaming.md** - 10 alternatives à Kafka (Pulsar, RabbitMQ, etc.)
- **24-Comparaison-Kafka-vs-Pulsar.md** - Comparaison détaillée entre Kafka et Pulsar

---

### **Section 6 : Choix des Services (25)**

- **25-Choix-Lambda-Firehose-ou-DataStreams.md** - Guide de décision : quand utiliser Lambda, Firehose ou Data Streams

---

### **Section 7 : Laboratoires Pratiques (26-31)**

#### **Laboratoire Complet AWS Kinesis et OpenSearch**
- **26-Laboratoire-Complet-Vue-Ensemble.md** - Vue d'ensemble complète du laboratoire (90 min)
- **27-Laboratoire-Description-Taches.md** - Description détaillée des tâches
- **28-Laboratoire-Taches-1-3-Verification-Ressources.md** - Tâches 1-3 : EC2, Kinesis, OpenSearch
- **29-Laboratoire-Taches-4-6-Configuration-OpenSearch.md** - Tâches 4-6 : Index, génération de logs, CloudWatch
- **30-Laboratoire-Taches-7-9-Visualisation-Dashboards.md** - Tâches 7-9 : Index pattern, visualisations (pie chart, heat map)
- **31-Laboratoire-Conclusion-Soumission-Ressources.md** - Conclusion, soumission et ressources supplémentaires

---

## 🎯 Parcours de Lecture Recommandés

### **Parcours 1 : Débutant - Comprendre les Bases**
1. 📖 01 - Introduction aux Services
2. 📖 02 - Workflow et Architecture
3. 📖 03 - Comparaison Firehose vs Streams
4. 📖 08 - Rôle du Serveur EC2
5. 📖 09 - Workflow Complet
6. 📖 26-31 - Laboratoires pratiques

### **Parcours 2 : Technique - Architecture Avancée**
1. 📖 04 - Architecture Pipeline Streaming
2. 📖 10 - Pipeline avec Lambda
3. 📖 05-07 - Différences fonctionnelles Streams/Firehose
4. 📖 11-12 - Analogies et exemples pratiques
5. 📖 25 - Choix des services

### **Parcours 3 : Sécurité et Conformité**
1. 📖 13 - Authentification Cognito
2. 📖 14-16 - Encryption et sécurité
3. 📖 17-20 - Limites et optimisations OpenSearch

### **Parcours 4 : Comparaisons et Alternatives**
1. 📖 21 - Kinesis vs Kafka
2. 📖 22 - Data Streams équivalent Kafka
3. 📖 23 - Alternatives à Kafka
4. 📖 24 - Kafka vs Pulsar
5. 📖 20 - Alternatives à OpenSearch

---

## 📊 Statistiques de la Documentation

- **Total de documents** : 32 fichiers
- **Documents conceptuels** : 25
- **Laboratoires pratiques** : 6 + 1 vue d'ensemble
- **Comparaisons détaillées** : 5
- **Guides de sécurité** : 4
- **Exemples et analogies** : 2

---

## 🔍 Index Thématique

### **Thèmes Principaux**

#### **Amazon Kinesis**
- 03, 04, 05, 06, 07, 10, 11, 12, 21, 22

#### **AWS Lambda**
- 10, 11, 25

#### **Amazon OpenSearch**
- 08, 09, 10, 11, 12, 13, 17, 18, 19, 20, 26-31

#### **Sécurité et Encryption**
- 13, 14, 15, 16

#### **Apache Kafka et Alternatives**
- 21, 22, 23, 24

#### **Laboratoires Pratiques**
- 26, 27, 28, 29, 30, 31

---

## ✅ Changements Effectués

### **Améliorations de Nommage**
- ✅ Tous les fichiers ont une numérotation séquentielle professionnelle (00-31)
- ✅ Noms descriptifs et cohérents sans caractères spéciaux problématiques
- ✅ Organisation logique par thème et complexité croissante
- ✅ Suppression du doublon (ancien fichier 18)
- ✅ README placé en position 00 pour visibilité

### **Structure Logique**
- 📌 Section 0 : Documentation générale
- 📌 Sections 1-2 : Concepts de base et architecture
- 📌 Section 3 : Sécurité
- 📌 Section 4 : OpenSearch
- 📌 Section 5 : Comparaisons Kafka
- 📌 Section 6 : Guide de décision
- 📌 Section 7 : Laboratoires pratiques

---

## 📝 Notes

- Les noms utilisent des tirets (`-`) plutôt que des espaces pour une meilleure compatibilité
- Les caractères accentués ont été préservés là où c'était essentiel
- La numérotation permet une navigation séquentielle logique
- Les laboratoires (26-31) forment un ensemble cohérent de 6 parties

---

**Dernière mise à jour** : Octobre 2025  
**Auteur** : Documentation AWS Services

