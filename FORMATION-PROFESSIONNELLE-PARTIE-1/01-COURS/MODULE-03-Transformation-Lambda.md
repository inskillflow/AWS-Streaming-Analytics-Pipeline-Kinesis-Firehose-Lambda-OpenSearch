================================================================================
                            MODULE 3
              TRANSFORMATION AVEC AWS LAMBDA
================================================================================

Durée : 45 minutes
Niveau : Intermédiaire

================================================================================
1. AWS LAMBDA - CONCEPTS FONDAMENTAUX
================================================================================

1.1 Définition
--------------

AWS Lambda est un service de calcul serverless qui exécute du code en réponse
à des événements sans nécessiter le provisionnement ou la gestion de serveurs.

CARACTERISTIQUES CLES :
- Serverless : aucune gestion d'infrastructure
- Event-driven : déclenchement par événements
- Mise à l'échelle automatique
- Facturation à la milliseconde d'exécution


1.2 Modèle d'Exécution
-----------------------

CYCLE DE VIE :
1. Evénement déclenche Lambda
2. AWS provisionne environnement d'exécution
3. Code s'exécute
4. Résultat retourné
5. Environnement conservé (warm) ou détruit

COLD START vs WARM START :
- Cold : première invocation, délai initialisation (100-1000ms)
- Warm : environnement réutilisé, démarrage instantané


================================================================================
2. LAMBDA DANS LES PIPELINES DE STREAMING
================================================================================

2.1 Intégration avec Kinesis
-----------------------------

KINESIS DATA STREAMS :
- Lambda lit en continu depuis le stream
- Traitement par batch de records
- Gestion automatique du checkpoint
- Retry en cas d'erreur

Configuration :
- Batch size : 1-10000 records
- Batch window : 0-300 secondes
- Parallélisation par shard

KINESIS DATA FIREHOSE :
- Firehose invoque Lambda pour transformation
- Traitement synchrone
- Lambda retourne données transformées
- Firehose livre vers destination

Timeout : 5 minutes maximum


2.2 Cas d'Usage Transformation
-------------------------------

ENRICHISSEMENT :
- Ajout géolocalisation depuis IP
- Résolution DNS inverse
- Lookup dans DynamoDB (données référence)
- Calcul de métriques dérivées

PARSING :
- Logs bruts → JSON structuré
- Extraction de champs spécifiques
- Normalisation de formats

FILTRAGE :
- Suppression données sensibles (PII)
- Exclusion logs debug en production
- Sélection événements pertinents

VALIDATION :
- Vérification schema
- Détection anomalies
- Enrichissement statut qualité


================================================================================
3. ENRICHISSEMENT DE LOGS WEB - EXEMPLE PRATIQUE
================================================================================

3.1 Données Brutes Apache
--------------------------

FORMAT LOG APACHE (Combined) :
IP - - [Timestamp] "Request" Status Size "Referer" "User-Agent"

EXEMPLE :
203.0.113.42 - - [28/Oct/2025:10:15:30 +0000] "GET /product.php HTTP/1.1" 200
1234 "http://example.com/search.php" "Mozilla/5.0 (Windows NT 10.0; Win64; 
x64) AppleWebKit/537.36"

CHAMPS INITIAUX :
- host (IP)
- datetime
- request (méthode, page, protocole)
- response (code HTTP)
- bytes
- referer
- agent (user-agent string)


3.2 Enrichissements Lambda
---------------------------

GEOLOCALISATION :
- Input : IP (203.0.113.42)
- Lookup : Base GeoIP (MaxMind)
- Output : city, country, latitude, longitude

APPAREIL ET NAVIGATEUR :
- Input : User-Agent string
- Parsing : Bibliothèque user-agent parser
- Output : os (Windows 10), browser (Chrome), device_type (desktop)

PAGE ET REFERRER :
- Extraction : Nom page depuis URL
- Parsing : Page de référence
- Output : webpage (product), refering_page (search)

RESULTAT ENRICHI :
{
  "host": "203.0.113.42",
  "datetime": "28/Oct/2025:10:15:30 +0000",
  "request": "GET /product.php HTTP/1.1",
  "response": "200",
  "bytes": "1234",
  "referer": "http://example.com/search.php",
  "agent": "Mozilla/5.0...",
  "city": "Paris",
  "country": "France",
  "location": {"lat": 48.8566, "lon": 2.3522},
  "os": "Windows",
  "browser": "Chrome",
  "webpage": "product",
  "refering_page": "search"
}


3.3 Code Lambda - Structure
----------------------------

FONCTION HANDLER :

import json
import base64

def lambda_handler(event, context):
    output_records = []
    
    for record in event['records']:
        # Décoder données Kinesis (base64)
        payload = base64.b64decode(record['data']).decode('utf-8')
        
        # Parser log Apache
        parsed_log = parse_apache_log(payload)
        
        # Enrichir
        enriched = enrich_log(parsed_log)
        
        # Encoder résultat
        output_data = base64.b64encode(
            json.dumps(enriched).encode('utf-8')
        ).decode('utf-8')
        
        output_records.append({
            'recordId': record['recordId'],
            'result': 'Ok',  # ou 'Dropped' ou 'ProcessingFailed'
            'data': output_data
        })
    
    return {'records': output_records}

FONCTIONS AUXILIAIRES :
- parse_apache_log() : regex pour extraire champs
- enrich_log() : appels services enrichissement
- Gestion erreurs et logs CloudWatch


================================================================================
4. OPTIMISATION LAMBDA POUR STREAMING
================================================================================

4.1 Performance
---------------

COLD START :
- Réduire taille package de déploiement
- Layers pour dépendances communes
- Provisioned Concurrency si latence critique

MEMOIRE :
- Configuration : 128 MB - 10 GB
- Plus de mémoire = plus de CPU
- Trade-off coût/performance
- Benchmark pour optimal

TIMEOUT :
- Kinesis Streams : adapter à batch size
- Firehose : max 5 minutes
- Buffer suffisant pour traitement + retry


4.2 Gestion d'Erreurs
----------------------

STRATEGIES :

RETRY AUTOMATIQUE :
- Lambda invoqué à nouveau en cas d'exception
- Kinesis : record reste dans stream
- Firehose : 3 tentatives par défaut

DEAD LETTER QUEUE :
- Records échoués → SQS ou SNS
- Investigation hors ligne
- Évite perte de données

LOGGING :
- CloudWatch Logs automatique
- Logs structurés (JSON)
- Métriques custom

EXEMPLE GESTION ERREUR :

try:
    enriched = enrich_log(parsed_log)
    result = 'Ok'
except ValidationError:
    # Donnée invalide, on drop
    enriched = None
    result = 'Dropped'
except TransientError:
    # Erreur temporaire, on retry
    result = 'ProcessingFailed'


4.3 Coûts
---------

FACTURATION :
- Nombre de requêtes (1M gratuites/mois)
- Durée d'exécution (GB-seconde)
- Transfert données sortantes

OPTIMISATION :
- Batch records pour réduire invocations
- Réutiliser connexions (variables globales)
- Caching de données référence
- Right-sizing mémoire allouée

EXEMPLE CALCUL :
- 1M invocations/jour
- 512 MB mémoire
- 200ms durée moyenne
→ Coût: ~30 USD/mois


================================================================================
5. ALTERNATIVES ET COMPARAISONS
================================================================================

5.1 Lambda vs Traitement Applicatif
------------------------------------

LAMBDA :
[+] Pas de gestion infrastructure
[+] Mise à l'échelle automatique
[+] Intégration native AWS
[-] Cold start possible
[-] Timeout limité
[-] Coût variable selon volume

APPLICATION (EC2, ECS) :
[+] Contrôle total
[+] Pas de timeout
[+] Coût prévisible (instances réservées)
[-] Gestion infrastructure
[-] Scaling manuel/complexe
[-] Maintenance serveurs


5.2 Lambda vs Kinesis Data Analytics
-------------------------------------

LAMBDA :
- Transformation record par record
- Logique impérative (Python, Java, etc.)
- Flexibilité totale

KINESIS DATA ANALYTICS :
- Requêtes SQL sur fenêtres de temps
- Agrégations continues
- Déploiement Apache Flink

CHOIX :
- Lambda : transformations simples, enrichissement
- Analytics : agrégations complexes, windowing


================================================================================
6. PATTERNS D'ARCHITECTURE
================================================================================

6.1 Pattern : Transformation Inline (Firehose)
-----------------------------------------------

Source → Firehose → Lambda → Firehose → Destination

AVANTAGES :
- Simplicité
- Données enrichies indexées directement

CONTRAINTES :
- Timeout 5 minutes
- Transformation synchrone


6.2 Pattern : Processing Fan-Out (Streams)
-------------------------------------------

Streams → Lambda 1 (alertes temps réel)
       → Lambda 2 (enrichissement + S3)
       → Lambda 3 (métriques aggregées)

AVANTAGES :
- Logiques indépendantes
- Traitement parallèle

CONTRAINTES :
- Gestion multiples Lambda
- Coûts multiples invocations


6.3 Pattern : Enrichment Pipeline
----------------------------------

Streams → Lambda 1 (enrichissement basique)
       → Streams 2 → Lambda 2 (enrichissement avancé)
       → Destination

AVANTAGES :
- Séparation responsabilités
- Réutilisation enrichissements

CONTRAINTES :
- Latence augmentée
- Complexité architecture


================================================================================
7. MONITORING ET OBSERVABILITE
================================================================================

7.1 Métriques CloudWatch
-------------------------

METRIQUES LAMBDA :
- Invocations : nombre d'exécutions
- Duration : temps d'exécution
- Errors : nombre d'erreurs
- Throttles : limitations dépassées
- ConcurrentExecutions : instances parallèles

METRIQUES KINESIS + LAMBDA :
- IteratorAge : retard lecture stream
- Success/Failure : taux succès traitement


7.2 Logs CloudWatch
--------------------

FORMAT RECOMMANDE :
{
  "timestamp": "2025-10-28T10:15:30Z",
  "level": "INFO",
  "request_id": "abc-123",
  "event_type": "enrichment",
  "duration_ms": 150,
  "records_processed": 100,
  "records_failed": 2
}

REQUETES INSIGHTS :
- Analyse durées moyennes
- Détection anomalies
- Debugging erreurs


7.3 Alarmes
-----------

CONFIGURER ALARMES SUR :
- Error rate > seuil (ex: 1%)
- Duration > timeout -buffer
- IteratorAge > 1 minute (retard traitement)
- Throttles > 0


================================================================================
8. POINTS CLES DU MODULE
================================================================================

- Lambda serverless idéal pour transformations streaming
- Intégration native avec Kinesis (Streams et Firehose)
- Enrichissement de données en vol sans infrastructure
- Optimisation via mémoire, batch size et gestion erreurs
- Monitoring CloudWatch essentiel pour production
- Trade-offs simplicité vs contrôle vs coût


================================================================================
9. EXERCICES DE REFLEXION
================================================================================

1. Votre Lambda traite 1000 records Kinesis en 30 secondes. Comment optimiser
   pour réduire les coûts ?

2. Quand préféreriez-vous une application EC2 à Lambda pour transformation ?

3. Comment gérer un enrichissement nécessitant un appel API externe avec
   latence variable ?

4. Dimensionnez Lambda (mémoire) pour traiter 500 records/seconde avec 
   enrichissement géolocalisation.

5. Architecturez un système de retry intelligent pour records échoués.


================================================================================

