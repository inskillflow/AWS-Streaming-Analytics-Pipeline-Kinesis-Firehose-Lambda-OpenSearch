# QUESTIONS DE DÉVELOPPEMENT - MODULE 1
## ARCHITECTURE DE STREAMING AWS

> **Durée** : 45 minutes  
> **Note** : 20 points  
> **Format** : Schémas + analyses rédigées (300-400 mots par question)

---

## QUESTION 1 - CONCEPTION ARCHITECTURE E-COMMERCE (10 points)

### Contexte

Une entreprise e-commerce génère **50 000 événements/seconde** :
- Clics produits
- Ajouts au panier
- Achats
- Navigation sur le site

**Besoins métier** :
- Personnalisation en temps réel (< 2 secondes)
- Analytics historique (data lake)
- Dashboards business pour direction
- Détection fraude immédiate

### Consigne

Concevez une architecture streaming AWS complète.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Schéma architecture** | Diagramme complet avec tous les services AWS et flux de données | 4 pts |
| **2. Justification services** | Pour chaque service : pourquoi ce choix ? | 2 pts |
| **3. Dimensionnement** | Calculez capacités (shards, instances, etc.) | 2 pts |
| **4. Estimation coûts** | Coût mensuel estimé avec détails | 2 pts |

> **Livrables obligatoires** :  
> - Schéma architectural annoté  
> - Calculs de dimensionnement  
> - Tableau comparatif streaming vs batch

---

## QUESTION 2 - PIPELINE DE LOGS WEB (10 points)

### Contexte

Un site web Apache génère **500 GB de logs/jour** :
- Logs d'accès (IP, page, timestamp, user-agent)
- Logs d'erreurs
- Logs de performance

**Objectifs** :
- Monitoring temps réel (alertes < 30s)
- Analytics comportemental
- Archivage 1 an pour conformité

### Consigne

Dessinez et expliquez le pipeline complet de traitement.

**Vous devez fournir** :

| Élément | Description | Points |
|---------|-------------|--------|
| **1. Pipeline détaillé** | Schéma du flux EC2 → ... → Dashboards | 4 pts |
| **2. Transformation Lambda** | Quels enrichissements ? Code pseudo-code | 3 pts |
| **3. Configuration OpenSearch** | Mappings index + stratégie ILM | 2 pts |
| **4. Monitoring** | Métriques CloudWatch critiques à surveiller | 1 pt |

> **Livrables obligatoires** :  
> - Diagramme de séquence du flux de données  
> - Pseudo-code Lambda d'enrichissement  
> - Configuration JSON des mappings OpenSearch

---

## GRILLE D'ÉVALUATION

### Critères Techniques (60%)

| Critère | Description | Points |
|---------|-------------|--------|
| **Schémas** | Clarté, complétude, annotations | /8 |
| **Architecture** | Cohérence, choix pertinents | /6 |
| **Dimensionnement** | Calculs corrects, réalistes | /4 |
| **Implémentation** | Détails techniques, faisabilité | /4 |

### Critères Communication (40%)

| Critère | Description | Points |
|---------|-------------|--------|
| **Clarté** | Organisation, lisibilité | /4 |
| **Justifications** | Arguments solides, convaincants | /3 |
| **Anticipation** | Trade-offs, risques, limites | /3 |

---

## CONSEILS

**Pour les schémas** :
- Utilisez notation standard (rectangles = services, flèches = flux)
- Annotez les flux (type données, fréquence)
- Indiquez les points de transformation
- Montrez les mécanismes de sécurité

**Pour les calculs** :
- Montrez vos formules
- Justifiez les hypothèses
- Donnez résultats intermédiaires
- Concluez avec estimation finale

**Pour le code** :
- Pseudo-code clair et commenté
- Logique métier explicite
- Gestion d'erreurs incluse

