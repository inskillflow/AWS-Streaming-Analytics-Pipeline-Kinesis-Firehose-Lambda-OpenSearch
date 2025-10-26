➡️ **Amazon Kinesis Data Streams**  
➡️ **Amazon Kinesis Data Firehose**

<br/>
<br/>

# 01 - Différence entre Kinesis Data Streams et Kinesis Data Firehose

| Caractéristique | **Kinesis Data Streams** | **Kinesis Data Firehose** |
|--------------------|--------------------------|----------------------------|
| **Type** | Service de **streaming en temps réel** | Service de **livraison de données** |
| **Contrôle** | Entièrement **géré par le développeur** | **Complètement managé** (AWS s’occupe de tout) |
| **Utilisation principale** | Traitement **avancé** de flux en temps réel avec une faible latence | **Ingestion automatique** et transformation **simple** avant stockage |
| **Nécessite du code client ?** | Oui, vous devez écrire du code pour consommer les données (ex : via KCL) | Non, vous **n’avez pas besoin de code**, tout est géré |
| **Transformation de données** | Vous devez connecter votre code ou Lambda manuellement | Intègre **AWS Lambda** directement pour enrichir les données |
| **Destination** | Vos applications personnalisées, Lambda, ou autre | **S3, Redshift, OpenSearch, Splunk...** |
| **Latence** | Très faible (en millisecondes) | Légèrement plus élevée (car livraison par batchs) |
| **Cas d’usage typique** | Traitement complexe de flux : fraudes, jeux, finance | Ingestion simple de logs, monitoring, analytique |

<br/>
<br/>

# 02 - Dans ton **schéma**, voici ce qui se passe exactement :

1. **EC2** (Serveur Web) génère des **logs d’accès**.
2. Ces logs sont envoyés à **Kinesis Data Streams** : ce service gère les événements en flux continu.
3. Ensuite, un **Firehose** prend ces données depuis Data Streams et :
   - (4) Les **stocke** dans **OpenSearch**,
   - (6) Envoie les logs à **CloudWatch**,
   - Et utilise **Lambda** pour les **enrichir** (géolocalisation, OS, navigateur, etc.).

> ⚠️ Dans ce labo, **Data Streams agit comme une source tampon**, et **Firehose comme un canal d’enrichissement + livraison**.

<br/>
<br/>

# 03 - Métaphore simple :

Imagine que tu filmes un concert :

- 🎥 **Kinesis Data Streams** = la **caméra** qui enregistre **chaque seconde** du concert en direct.
- 📦 **Kinesis Data Firehose** = le **technicien** qui **regroupe les séquences**, les **transforme si besoin**, puis les **transfère automatiquement** vers un écran géant (OpenSearch, S3…).

## 🎬 Métaphore du Concert en Diagramme

```mermaid
graph LR
    subgraph "🎵 Concert (Analogie)"
        C1[🎸 Musiciens<br/>Performance] -->|Live| C2[🎥 Caméra<br/>Enregistrement continu]
        C2 -->|Vidéo brute| C3[🎬 Technicien<br/>Montage & édition]
        C3 -->|Vidéo finale| C4[📺 Écran géant<br/>Diffusion]
    end
    
    subgraph "☁️ Architecture AWS"
        A1[🌐 Serveur Web<br/>EC2] -->|Logs temps réel| A2[🌊 Kinesis Streams<br/>Capture continue]
        A2 -->|Données brutes| A3[📦 Kinesis Firehose<br/>Bufferisation & transformation]
        A3 -->|Données traitées| A4[🔍 OpenSearch<br/>Stockage & analyse]
    end
    
    style C2 fill:#ff6347
    style C3 fill:#4169e1
    style A2 fill:#ff9900
    style A3 fill:#9370db
```

## 🔄 Tableau Comparatif Visuel

```mermaid
graph TB
    subgraph "🌊 Kinesis Data Streams"
        S1[📊 Type: Streaming temps réel]
        S2[⚙️ Contrôle: Manuel / Développeur]
        S3[💻 Code: Obligatoire KCL]
        S4[⚡ Latence: < 1 seconde]
        S5[🎯 Usage: Traitement complexe]
    end
    
    subgraph "📦 Kinesis Data Firehose"
        F1[📦 Type: Livraison de données]
        F2[🤖 Contrôle: Entièrement managé AWS]
        F3[🚫 Code: Aucun code requis]
        F4[⏱️ Latence: 60+ secondes buffering]
        F5[📊 Usage: Ingestion simple logs]
    end
    
    style S1 fill:#4169e1
    style S2 fill:#4169e1
    style S3 fill:#4169e1
    style S4 fill:#4169e1
    style S5 fill:#4169e1
    style F1 fill:#9370db
    style F2 fill:#9370db
    style F3 fill:#9370db
    style F4 fill:#9370db
    style F5 fill:#9370db
```

