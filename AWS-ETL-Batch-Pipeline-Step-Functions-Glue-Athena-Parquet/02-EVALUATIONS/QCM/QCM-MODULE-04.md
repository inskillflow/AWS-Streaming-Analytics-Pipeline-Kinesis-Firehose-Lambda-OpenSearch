# QCM - MODULE 4
## OPTIMISATION PARQUET & PARTITIONNEMENT

> **Durée** : 15 minutes  
> **Note** : 10 points  
> **Documents** : Non autorisés

---

### Question 1

Le format Parquet est de type :

- [ ] A. Row-based (ligne par ligne)
- [ ] B. Columnar (colonnes)
- [ ] C. Binaire non structuré
- [ ] D. XML

---

### Question 2

Compression Snappy avec Parquet est préférée car :

- [ ] A. Meilleur ratio compression
- [ ] B. Meilleur compromis vitesse/compression pour analytics
- [ ] C. Gratuite
- [ ] D. Obligatoire avec Athena

---

### Question 3

La taille optimale d'un fichier Parquet est :

- [ ] A. < 1 MB
- [ ] B. 10-50 MB
- [ ] C. 128 MB - 1 GB
- [ ] D. > 10 GB

---

### Question 4

Le partitionnement `year=2020/month=01/` permet de :

- [ ] A. Scanner uniquement cette partition si requête filtre dessus
- [ ] B. Augmenter taille données
- [ ] C. Ralentir requêtes
- [ ] D. Rien

---

### Question 5

Pour données de 5 GB/jour, granularité partition recommandée :

- [ ] A. Par heure
- [ ] B. Par jour
- [ ] C. Par minute
- [ ] D. Pas de partition

---

### Question 6

Compression Gzip comparée à Snappy :

- [ ] A. Plus rapide
- [ ] B. Ratio compression meilleur mais plus lente
- [ ] C. Identique
- [ ] D. Incompatible Parquet

---

### Question 7

Pour regrouper nombreux petits fichiers Parquet (compaction) :

- [ ] A. CTAS pour compaction
- [ ] B. Suppression manuelle
- [ ] C. Lambda
- [ ] D. Impossible

---

### Question 8

ORC comparé à Parquet :

- [ ] A. Identique
- [ ] B. Aussi columnar, optimisé pour Hive/Spark
- [ ] C. Row-based
- [ ] D. N'existe pas

---

### Question 9

L'économie stockage S3 typique Parquet+Snappy vs CSV :

- [ ] A. 10%
- [ ] B. 30%
- [ ] C. 70%
- [ ] D. 0%

---

### Question 10

Pour analytics interactives fréquentes sur S3, meilleur choix :

- [ ] A. CSV non compressé
- [ ] B. JSON
- [ ] C. Parquet + Snappy + Partitions
- [ ] D. XML

---

## Fin du QCM

> **Conseil** : Vérifiez vos réponses avant de consulter le corrigé

