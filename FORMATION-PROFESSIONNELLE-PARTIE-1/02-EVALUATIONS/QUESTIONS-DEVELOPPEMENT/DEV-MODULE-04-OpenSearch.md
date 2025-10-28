# QUESTIONS DE DÉVELOPPEMENT - MODULE 4
## OPENSEARCH ET INDEXATION

> **Durée** : 50 minutes  
> **Note** : 20 points  
> **Format** : Configuration technique + schémas + analyses

---

## QUESTION 1 - CONCEPTION INDEX ET CLUSTER (10 points)

### Contexte

Vous devez indexer des logs applicatifs microservices avec ce format :

```json
{
  "timestamp": "2025-10-28T10:15:30.123Z",
  "level": "ERROR",
  "service": "payment-api",
  "trace_id": "abc123xyz",
  "user_id": "usr_456789",
  "message": "Payment timeout",
  "duration_ms": 5234,
  "metadata": {
    "amount": 149.99,
    "currency": "EUR",
    "country": "FR",
    "payment_method": "card"
  },
  "stack_trace": "..."
}
```

**Contraintes** :
- Volume : **2 TB/mois** (croissance 30%/an)
- Rétention : **90 jours** total
- Recherches fréquentes : **7 derniers jours** uniquement
- Requêtes complexes : agrégations par service, pays, montant
- SLA : Latence recherche < 500ms

### Consigne

Concevez un cluster OpenSearch optimisé avec stratégie ILM.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Mappings complets** | Configuration JSON de tous les champs avec types | 3 pts |
| **2. Architecture cluster** | Schéma avec types/nombres de nœuds + justifications | 3 pts |
| **3. Stratégie ILM** | Diagramme hot-warm-cold avec règles de transition | 2 pts |
| **4. Calculs dimensionnement** | Shards, replicas, stockage par tier | 2 pts |

> **Livrables obligatoires** :  
> - Configuration JSON complète des mappings  
> - Schéma d'architecture du cluster  
> - Diagramme ILM avec timeline  
> - Tableau de dimensionnement

**Exemple mapping attendu** :
```json
{
  "mappings": {
    "properties": {
      "timestamp": {"type": "date"},
      "level": {"type": "keyword"},
      "service": {"type": "keyword"},
      ...
    }
  }
}
```

---

## QUESTION 2 - DASHBOARDS ET VISUALISATIONS (10 points)

### Contexte

Pour les logs indexés ci-dessus, l'équipe ops a besoin de visualisations temps réel.

**Besoins métier** :
- Taux d'erreurs par service (dernière heure)
- Top 10 erreurs les plus fréquentes
- Distribution géographique des erreurs
- Heatmap : service × type d'erreur
- Timeline des erreurs avec pics

### Consigne

Concevez les dashboards OpenSearch complets.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Architecture dashboards** | Schéma index → patterns → visualisations | 2 pts |
| **2. Configuration index pattern** | Champ temps, filtres, format | 1 pt |
| **3. 5 Visualisations** | Pour chaque viz : type, config, requête aggregation | 5 pts |
| **4. Assemblage dashboard** | Schéma final du dashboard avec layout | 2 pts |

> **Livrables obligatoires** :  
> - Diagramme du workflow de création  
> - Configuration JSON de chaque visualisation  
> - Mockup du dashboard final  
> - Requêtes d'agrégation OpenSearch

**Types de visualisations à utiliser** :
- Pie Chart (camembert)
- Bar Chart (histogramme)
- Heat Map (carte thermique)
- Line Chart (courbe temporelle)
- Coordinate Map (carte géographique)

---

## EXEMPLE REQUETE AGGREGATION

```json
{
  "size": 0,
  "aggs": {
    "errors_by_service": {
      "terms": {
        "field": "service",
        "size": 10
      },
      "aggs": {
        "error_count": {
          "value_count": {
            "field": "level"
          }
        }
      }
    }
  }
}
```

---

## GRILLE NOTATION

| Score | Appréciation | Livrables |
|-------|--------------|-----------|
| **18-20** | Excellent | Tous schémas + config complètes + requêtes optimisées |
| **15-17** | Très bien | Schémas clairs + config correctes + requêtes fonctionnelles |
| **12-14** | Bien | Schémas basiques + config partielles |
| **10-11** | Passable | Schémas incomplets, erreurs configuration |
| **< 10** | Insuffisant | Absence schémas ou configurations erronées |

