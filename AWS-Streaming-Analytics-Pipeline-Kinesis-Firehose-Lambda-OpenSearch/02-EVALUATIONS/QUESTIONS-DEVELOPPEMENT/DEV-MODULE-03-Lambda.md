# QUESTIONS DE DÉVELOPPEMENT - MODULE 3
## TRANSFORMATION AVEC AWS LAMBDA

> **Durée** : 45 minutes  
> **Note** : 20 points  
> **Format** : Architecture + code + analyses de performance

---

## QUESTION 1 - PIPELINE ENRICHISSEMENT LOGS (10 points)

### Contexte

Pipeline de traitement de logs Apache avec enrichissement Lambda :

**Input - Log brut Apache** :
```
203.0.113.42 - - [28/Oct/2025:10:15:30 +0000] "GET /product.php?id=123 HTTP/1.1" 200 1234 "http://example.com/search.php" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) Chrome/120.0"
```

**Enrichissements requis** :
- Géolocalisation (city, country, lat, lon) depuis IP
- Parsing User-Agent (OS, browser, device_type)
- Extraction page visitée et page de référence
- Classification du produit (depuis API interne)
- Ajout timestamp UTC normalisé

**Volume** : 10 000 logs/seconde

### Consigne

Dessinez le pipeline complet et implémentez la fonction Lambda.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Architecture pipeline** | Schéma EC2 → Firehose → Lambda → OpenSearch | 2 pts |
| **2. Diagramme flux Lambda** | Détaillez les étapes de transformation dans Lambda | 2 pts |
| **3. Code Lambda** | Pseudo-code Python complet avec gestion erreurs | 4 pts |
| **4. Optimisations** | 3 optimisations performance avec justifications | 2 pts |

> **Livrables obligatoires** :  
> - Diagramme de flux du pipeline  
> - Schéma interne Lambda (input → traitements → output)  
> - Pseudo-code commenté  
> - Tableau des optimisations

**Structure code attendue** :
```python
def lambda_handler(event, context):
    # 1. Décoder records Firehose
    # 2. Parser log Apache (regex)
    # 3. Enrichir géolocalisation (GeoIP)
    # 4. Parser User-Agent
    # 5. Lookup API produit
    # 6. Encoder et retourner
```

---

## QUESTION 2 - OPTIMISATION LAMBDA COUT/PERFORMANCE (10 points)

### Contexte

Lambda actuel en production avec problèmes de performance :

**Configuration** :
- Mémoire : 512 MB
- Timeout : 60 secondes
- Batch size : 100 records
- Durée moyenne : **48 secondes** par batch
- Invocations : **2 000 000/mois**
- Coût : **320 USD/mois**

**Traitement effectué** :
- Parsing regex complexe (15s)
- 3 appels API externes (20s total, chacun 50-100ms latency)
- Lecture DynamoDB pour chaque record (10s)
- Transformation JSON (3s)

### Consigne

Optimisez cette Lambda pour réduire coût de 40% et durée de 60%.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Diagramme actuel** | Schéma montrant goulots d'étranglement | 2 pts |
| **2. Analyse bottlenecks** | Identifiez les 3 principaux problèmes | 2 pts |
| **3. Solutions optimisées** | 5 optimisations concrètes avec architecture | 4 pts |
| **4. Estimation gains** | Temps gagné + économies USD pour chaque optimisation | 2 pts |

> **Livrables obligatoires** :  
> - Schéma "avant/après" de l'architecture Lambda  
> - Tableau des optimisations avec gains chiffrés  
> - Pseudo-code optimisé des parties critiques

**Objectifs chiffrés** :
- Durée cible : **< 20 secondes** par batch
- Coût cible : **< 200 USD/mois**

---

## EXEMPLE SCHÉMA ATTENDU

### Pipeline Lambda Transformation

```
[Kinesis Firehose]
        ↓
    (Batch 100 records)
        ↓
   [Lambda Function]
        ↓
    ┌───────────────────┐
    │ 1. Decode base64  │ (< 1ms)
    ├───────────────────┤
    │ 2. Parse logs     │ (regex)
    ├───────────────────┤
    │ 3. Enrich GeoIP   │ (lookup)
    ├───────────────────┤
    │ 4. Call API       │ (external)
    ├───────────────────┤
    │ 5. Transform JSON │
    ├───────────────────┤
    │ 6. Encode return  │
    └───────────────────┘
        ↓
   [Retour Firehose]
        ↓
   [OpenSearch]
```

---

## GRILLE NOTATION

| Score | Appréciation | Caractéristiques |
|-------|--------------|------------------|
| **18-20** | Excellent | Schémas parfaits, code optimisé, calculs exacts |
| **15-17** | Très bien | Bons schémas, code fonctionnel, calculs corrects |
| **12-14** | Bien | Schémas basiques, code incomplet, calculs approximatifs |
| **10-11** | Passable | Schémas manquants ou incorrects, code minimal |
| **< 10** | Insuffisant | Absence schémas, code erroné, pas de calculs |

