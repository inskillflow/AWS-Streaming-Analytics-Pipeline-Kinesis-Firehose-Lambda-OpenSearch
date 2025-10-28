# QUESTIONS DÉFINITIONS - BASES FONDAMENTALES
## PARTIE 2 - ETL BATCH

> **Durée** : 45 minutes  
> **Note** : 40 points  
> **Format** : Réponses courtes (50-100 mots par question)

---

# INSTRUCTIONS

Pour chaque question, donnez une définition claire et concise incluant :
- **Ce que c'est** (définition)
- **À quoi ça sert** (utilité)
- **Exemple d'usage** (cas concret)

**Format attendu** : 3-5 phrases maximum par réponse

---

# SERVICES AWS ETL

## Question 1 (2 points)

**C'est quoi AWS Step Functions ?**

_(Votre réponse)_

---

## Question 2 (2 points)

**C'est quoi une state machine (machine à états) ?**

_(Votre réponse)_

---

## Question 3 (2 points)

**C'est quoi AWS Glue ?**

_(Votre réponse)_

---

## Question 4 (2 points)

**C'est quoi le AWS Glue Data Catalog ?**

_(Votre réponse)_

---

## Question 5 (2 points)

**C'est quoi un Glue Crawler ?**

_(Votre réponse)_

---

## Question 6 (2 points)

**C'est quoi Amazon Athena ?**

_(Votre réponse)_

---

## Question 7 (2 points)

**C'est quoi une table EXTERNAL dans Glue ?**

_(Votre réponse)_

---

## Question 8 (2 points)

**C'est quoi CTAS (Create Table As Select) ?**

_(Votre réponse)_

---

# FORMATS ET OPTIMISATION

## Question 9 (2 points)

**C'est quoi le format Parquet ?**

_(Votre réponse)_

---

## Question 10 (2 points)

**C'est quoi le format ORC ?**

_(Votre réponse)_

---

## Question 11 (2 points)

**C'est quoi un format columnar (colonnes) ?**

_(Votre réponse)_

---

## Question 12 (2 points)

**C'est quoi un format row-based (lignes) ?**

_(Votre réponse)_

---

## Question 13 (2 points)

**C'est quoi la compression Snappy ?**

_(Votre réponse)_

---

## Question 14 (2 points)

**C'est quoi le partitionnement de données ?**

_(Votre réponse)_

---

## Question 15 (2 points)

**C'est quoi le partition pruning ?**

_(Votre réponse)_

---

# CONCEPTS ETL

## Question 16 (2 points)

**C'est quoi ETL (Extract, Transform, Load) ?**

_(Votre réponse)_

---

## Question 17 (2 points)

**C'est quoi un Data Lake ?**

_(Votre réponse)_

---

## Question 18 (2 points)

**C'est quoi un Data Warehouse ?**

_(Votre réponse)_

---

## Question 19 (2 points)

**C'est quoi une vue SQL dans Athena ?**

_(Votre réponse)_

---

## Question 20 (2 points)

**C'est quoi MSCK REPAIR TABLE ?**

_(Votre réponse)_

---

---

# BARÈME ET CRITÈRES

## Notation par Réponse

| Points | Qualité | Critères |
|--------|---------|----------|
| **2/2** | Parfait | Définition exacte + utilité + exemple pertinent |
| **1.5/2** | Très bien | Définition correcte + utilité OU exemple |
| **1/2** | Correct | Définition approximative mais compréhensible |
| **0.5/2** | Partiel | Définition incomplète ou imprécise |
| **0/2** | Insuffisant | Définition erronée ou absente |

## Note Finale

| Score Total | Appréciation |
|-------------|--------------|
| **36-40** | Excellent - Maîtrise parfaite des concepts |
| **30-35** | Très bien - Bonne compréhension générale |
| **24-29** | Bien - Connaissances correctes avec lacunes |
| **20-23** | Passable - Connaissances de base fragiles |
| **< 20** | Insuffisant - Révision nécessaire |

---

## Conseils de Réponse

**Structure recommandée** :
1. **Définition** : "X est un service/concept qui..."
2. **Utilité** : "Il sert à..."
3. **Exemple** : "Par exemple, ..."

**Exemple de bonne réponse** :

> **C'est quoi le format Parquet ?**
>
> Parquet est un format de stockage columnar (par colonnes) open-source optimisé pour les analytics Big Data. Il sert à stocker les données de manière compressée et permet de lire uniquement les colonnes nécessaires à une requête. Par exemple, pour une requête SELECT AVG(price), Parquet lit uniquement la colonne price au lieu de scanner toutes les colonnes, ce qui réduit drastiquement le temps de traitement et les coûts.

---

**Fin du questionnaire - Vérifiez vos réponses**

