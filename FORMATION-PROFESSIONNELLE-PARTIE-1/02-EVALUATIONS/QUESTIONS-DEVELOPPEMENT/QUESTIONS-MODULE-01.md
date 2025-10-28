================================================================================
                 QUESTIONS DE DEVELOPPEMENT - MODULE 1
              ARCHITECTURE DE STREAMING AWS
================================================================================

Durée recommandée : 60 minutes
Format : Réponses rédigées (200-400 mots par question)
Évaluation : Compréhension, analyse, synthèse

================================================================================

QUESTION 1 - ANALYSE ARCHITECTURALE (10 points)
--------------------------------------------------------------------------------

Une entreprise de e-commerce génère actuellement 50 000 événements par seconde
(clics, ajouts panier, achats). Ces données doivent être :
- Analysées en temps réel pour personnalisation
- Archivées dans un data lake pour analytics long terme
- Indexées pour recherche et dashboards métier

CONSIGNE :
Proposez une architecture AWS complète pour répondre à ces besoins. Votre 
réponse doit inclure :

a) Les services AWS utilisés avec justification de chaque choix
b) Le flux de données détaillé entre les composants
c) Les avantages de cette architecture par rapport à une solution batch 
   traditionnelle
d) Les points d'attention pour assurer la scalabilité


================================================================================

QUESTION 2 - COMPARAISON APPROCHES (8 points)
--------------------------------------------------------------------------------

Comparez deux approches pour l'analyse de logs d'un site web générant 1 GB de
logs par jour :

APPROCHE A : Logs → S3 → Traitement batch quotidien (EMR) → Rapports

APPROCHE B : Logs → Kinesis → Lambda → OpenSearch → Dashboards temps réel

CONSIGNE :
Analysez les deux approches selon les critères suivants :

a) Latence des insights (du log à l'information exploitable)
b) Complexité opérationnelle et expertise requise
c) Coûts estimés (infrastructure + opérationnel)
d) Cas d'usage où chaque approche serait préférable


================================================================================

QUESTION 3 - RESOLUTION DE PROBLEME (7 points)
--------------------------------------------------------------------------------

Une application mobile envoie des événements utilisateur vers un pipeline :
Mobile App → API Gateway → Lambda → Kinesis Firehose → OpenSearch

PROBLEME OBSERVE :
Les dashboards montrent un retard de 5 minutes entre l'action utilisateur et
l'apparition dans OpenSearch. L'exigence métier est < 30 secondes.

CONSIGNE :
a) Identifiez les causes potentielles de cette latence élevée
b) Proposez 3 solutions techniques pour réduire la latence
c) Pour chaque solution, évaluez les trade-offs (coût, complexité, risques)
d) Recommandez la solution optimale avec justification


================================================================================

QUESTION 4 - CONCEPTION SECURISEE (8 points)
--------------------------------------------------------------------------------

Vous devez concevoir une architecture streaming pour une application de santé
traitant des données médicales sensibles (HIPAA compliance requis).

Requirements :
- Données patients collectées depuis applications mobiles
- Analyses temps réel pour alertes médicales
- Accès dashboards restreint au personnel médical autorisé
- Audit complet de tous les accès

CONSIGNE :
Concevez une architecture sécurisée incluant :

a) Services AWS et flux de données
b) Mesures de sécurité à chaque niveau (réseau, identité, données)
c) Stratégie d'encryption (transit et repos)
d) Mécanismes d'audit et de conformité


================================================================================

QUESTION 5 - OPTIMISATION (7 points)
--------------------------------------------------------------------------------

Une startup utilise l'architecture suivante :
EC2 (logs) → Kinesis Firehose → Lambda (enrichissement) → OpenSearch

Coût mensuel actuel : 2000 USD
Volume : 100 GB de logs/jour

Le CEO demande de réduire les coûts de 30% sans sacrifier les fonctionnalités
essentielles.

CONSIGNE :
a) Identifiez les principaux postes de coûts dans cette architecture
b) Proposez 4 optimisations concrètes avec estimation d'économies
c) Évaluez l'impact de chaque optimisation sur les performances et fonctionnalités
d) Chiffrez l'économie totale potentielle et validez l'objectif de 30%


================================================================================

INSTRUCTIONS GENERALES
================================================================================

CRITERES D'EVALUATION :

Compréhension technique (40%) :
- Maîtrise des concepts des services AWS
- Cohérence architecturale
- Pertinence des choix techniques

Analyse et réflexion (30%) :
- Identification des problèmes
- Évaluation des trade-offs
- Pensée critique

Communication (20%) :
- Clarté de l'expression
- Structure de la réponse
- Justifications argumentées

Créativité et pragmatisme (10%) :
- Solutions innovantes
- Faisabilité pratique
- Considération du contexte métier


CONSEILS :

- Structurez vos réponses (introduction, développement, conclusion)
- Utilisez des schémas si pertinent
- Quantifiez quand possible (coûts, latence, débit)
- Justifiez tous vos choix
- Citez des exemples concrets
- Anticipez les objections


BAREME :

18-20 : Excellent - Maîtrise complète, analyse approfondie
15-17 : Très bien - Bonne compréhension, solutions pertinentes
12-14 : Bien - Compréhension correcte, quelques lacunes
10-11 : Passable - Connaissances de base, manque de profondeur
< 10  : Insuffisant - Lacunes importantes

================================================================================

