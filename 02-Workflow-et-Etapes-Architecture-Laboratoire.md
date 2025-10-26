# 1 - *Explication des étapes du schéma (Numérotées 1 à 9)*

![image](https://github.com/user-attachments/assets/455d28a5-dd72-4a4a-b029-4524eca478ef)

## 📋 Diagramme des 9 Étapes du Laboratoire

```mermaid
graph TB
    Start([🎯 Début du Laboratoire]) --> Step1
    
    Step1[Étape 1: Examiner EC2 & IAM<br/>Configuration serveur web<br/>& rôles IAM] --> Step2
    Step2[Étape 2: Examiner Kinesis<br/>Data Streams<br/>Flux de données] --> Step3
    Step3[Étape 3: Examiner OpenSearch<br/>Configuration cluster<br/>Indexation] --> Step4
    
    Step4[Étape 4: Configurer Index<br/>OpenSearch<br/>Stocker logs enrichis] --> Step5
    Step5[Étape 5: Naviguer sur le site<br/>Générer logs d'accès<br/>Simuler trafic] --> Step6
    Step6[Étape 6: Consulter CloudWatch<br/>Observer traitement<br/>Lambda & Firehose] --> Step7
    
    Step7[Étape 7: Créer Index Pattern<br/>OpenSearch Dashboards<br/>Modèle visualisation] --> Step8
    Step8[Étape 8: Créer Pie Chart<br/>OS & Navigateurs<br/>visiteurs] --> Step9
    Step9[Étape 9: Créer Heat Map<br/>Analyse pages origine<br/>Search vs Reco] --> End
    
    End([✅ Laboratoire Terminé])
    
    style Step1 fill:#ffd700
    style Step2 fill:#ffd700
    style Step3 fill:#ffd700
    style Step4 fill:#87ceeb
    style Step5 fill:#87ceeb
    style Step6 fill:#87ceeb
    style Step7 fill:#90ee90
    style Step8 fill:#90ee90
    style Step9 fill:#90ee90
    style Start fill:#ff6b6b
    style End fill:#51cf66
```



| # | **Étape** | **Description en français** |
|---|-----------|------------------------------|
| 1 | EC2 & IAM | Vous allez examiner la configuration de l’instance EC2 qui héberge le serveur web. Vous allez aussi analyser le rôle IAM `OsDemoWebserverIAMRole` et les politiques associées pour comprendre les autorisations accordées. |
| 2 | Kinesis Data Streams | Vous étudierez le flux de données Kinesis qui capture les journaux d’accès web en temps réel générés par les utilisateurs du site. |
| 3 | OpenSearch Service | Vous examinerez la configuration du cluster OpenSearch utilisé pour indexer et stocker les données. |
| 4 | Index OpenSearch | Vous configurerez un **index OpenSearch** pour stocker les journaux d’accès enrichis. Cet index permettra les recherches et les visualisations. |
| 5 | Navigation sur le site | Une fois la configuration terminée, vous naviguerez sur le site pour **générer des journaux d’accès**. Ces journaux simulent le trafic utilisateur. |
| 6 | Logs dans CloudWatch | Vous consulterez les **logs générés dans Amazon CloudWatch**, afin de comprendre comment Kinesis Firehose transmet les données à Lambda pour les enrichir avant l’indexation. |
| 7 | Pattern d’index | Vous créerez un **modèle d’index (index pattern)** dans OpenSearch Dashboards. Ce pattern est nécessaire pour pouvoir visualiser les données dans des graphiques. |
| 8 | Diagramme circulaire | Vous construirez une **visualisation en diagramme circulaire (pie chart)** pour montrer les systèmes d’exploitation et navigateurs utilisés par les visiteurs. |
| 9 | Carte thermique | Enfin, vous terminerez le laboratoire en créant une **carte thermique (heat map)** pour analyser les pages d’origine des visiteurs (page de recherche ou de recommandations). |




# 2 - **Vulgarisation du workflow de l’image**

Imagine que des gens visitent un **site web** (comme une boutique en ligne). Voici ce qui se passe en coulisses, étape par étape :

<br/>

### 🧍‍♂️ 2.1. **Un utilisateur visite le site web**  
➡️ Chaque fois qu’un visiteur clique sur une page, cela génère un **journal d’activité** (log).  
Ce journal contient des infos comme :
- la page consultée,
- l’heure,
- l’adresse IP,
- le navigateur utilisé,
- etc.

<br/>

### 💻 2.2. **Le serveur (Amazon EC2) enregistre le log**  
➡️ Le serveur web tourne dans **Amazon EC2**, un ordinateur virtuel dans le cloud.  
Chaque action d’un visiteur y génère un **fichier de log**.

<br/>

### 📤 2.3. **Les logs sont envoyés à Kinesis (Data Streams)**  
➡️ Ces fichiers sont envoyés **en continu** dans un tuyau spécial appelé **Kinesis Data Streams**.  
C’est un peu comme un **tapis roulant rapide** qui transporte les données dès qu’elles sont créées.

<br/>

### 📦 2.4. **Firehose prend le relais**  
➡️ Les données du tapis roulant sont transférées à **Kinesis Data Firehose**, qui agit comme un **livreur intelligent** :
- Il peut **enrichir** les données (par exemple : déterminer la ville du visiteur à partir de son IP),
- Et les **livrer automatiquement** à un endroit où on peut les analyser.

<br/>

### ⚙️ 2.5. **Une fonction Lambda transforme les données**  
➡️ Avant de stocker les logs, Firehose déclenche une **fonction AWS Lambda** (un petit programme automatique).  
Cette fonction ajoute des **informations utiles** : géolocalisation, système d’exploitation, type d’appareil, etc.

<br/>

### 📊 2.6. **Les données enrichies vont dans OpenSearch**  
➡️ Une fois prêtes, les données sont envoyées dans **Amazon OpenSearch Service**, un moteur de recherche qui permet :
- de **rechercher** dans les logs,
- de **trier**, **filtrer**, **compter**,
- et surtout : de **visualiser les résultats**.

<br/>

### 👁️ 2.7. **On affiche les données dans OpenSearch Dashboards**  
➡️ Grâce à **OpenSearch Dashboards**, on peut créer :
- des **diagrammes circulaires** pour voir quels navigateurs sont les plus utilisés,
- des **cartes thermiques** pour savoir d’où viennent les visiteurs.

<br/>

### 🔐 2.8. **Amazon Cognito gère l’accès**  
➡️ Pour que seuls les **bons utilisateurs** aient accès aux tableaux de bord, on utilise **Amazon Cognito**, qui gère l’authentification (identifiants, sécurité).

<br/>

### 👮 2.9. **IAM contrôle les permissions**  
➡️ Enfin, **IAM (Identity and Access Management)** définit les **droits d’accès** :
- qui peut lire les données,
- qui peut modifier,
- qui peut accéder au Dashboard, etc.

<br/>

# Résumé ultra simplifié

> 1. 👨‍💻 Un visiteur clique →  
> 2. 📄 EC2 enregistre →  
> 3. 📡 Les logs partent dans Kinesis →  
> 4. 📦 Firehose les prend →  
> 5. ⚙️ Lambda enrichit →  
> 6. 🔍 OpenSearch stocke →  
> 7. 📊 Dashboards affiche →  
> 8. 🔐 Cognito protège →  
> 9. 👮 IAM contrôle les accès.

## 🔄 Workflow Détaillé en Diagramme de Séquence

```mermaid
sequenceDiagram
    autonumber
    actor V as 👥 Visiteur
    participant S as 🌐 Site Web
    participant EC2 as 💻 EC2
    participant KA as 📡 Agent Kinesis
    participant KDS as 🚀 Kinesis Streams
    participant KDF as 📦 Firehose
    participant L as ⚙️ Lambda
    participant OS as 🔍 OpenSearch
    participant OSD as 📊 Dashboards
    participant C as 🔐 Cognito
    participant IAM as 👮 IAM
    
    V->>S: 1. Clique sur page
    S->>EC2: 2. Requête HTTP
    EC2->>EC2: Génère log d'accès
    EC2->>KA: 3. Log envoyé
    KA->>KDS: Stream continu
    KDS->>KDF: 4. Firehose prend relais
    KDF->>L: 5. Déclenche transformation
    L->>L: Enrichit (géoloc, OS, browser)
    L-->>KDF: Retourne données enrichies
    KDF->>OS: 6. Indexe dans OpenSearch
    OS->>OSD: 7. Données disponibles
    Note over OSD: Visualisations créées
    C->>OSD: 8. Authentifie utilisateur
    IAM->>OSD: 9. Vérifie permissions
    OSD-->>V: Affiche dashboards
```

