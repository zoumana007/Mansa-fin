# 80 — Architecture technique finale Mansa : microservices, API Gateway, ledger, événements, bases de données, sécurité, observabilité, CI/CD, haute disponibilité, PRA, multi-pays et administration centralisée

## 1. Objet du document

Ce document définit l’**architecture technique finale de Mansa**.

Il décrit la manière dont les applications, services, bases de données, partenaires, terminaux, outils d’administration et infrastructures doivent fonctionner ensemble.

Il couvre notamment :

- les applications mobiles ;
- les portails web ;
- l’API Gateway ;
- les microservices ;
- le ledger ;
- les wallets ;
- les paiements ;
- les transferts ;
- les cartes ;
- les Agents ;
- les commerçants ;
- les TPE ;
- les GAB/DAB ;
- Mobile Money ;
- les banques ;
- les événements ;
- les files de messages ;
- PostgreSQL ;
- Redis ;
- le stockage objet ;
- la recherche ;
- la Data Platform ;
- la sécurité ;
- les secrets ;
- le HSM ;
- l’observabilité ;
- la CI/CD ;
- les environnements ;
- la haute disponibilité ;
- le multi-région ;
- le PRA ;
- le multi-pays ;
- l’administration centralisée.

L’objectif est de garantir une plateforme :

- robuste ;
- modulaire ;
- sécurisée ;
- évolutive ;
- auditable ;
- hautement disponible ;
- multi-pays ;
- multi-devises ;
- compatible avec une forte montée en charge ;
- exploitable par une équipe professionnelle.

---

# 2. Principes fondamentaux

## 2.1 Le ledger constitue la source de vérité financière

Aucun solde ne doit être considéré comme fiable s’il ne peut pas être expliqué par les écritures du ledger.

---

## 2.2 Les applications ne doivent pas accéder directement aux bases

Toutes les applications doivent passer par :

```text
Application
→ API Gateway
→ Service métier
→ Base de données
```

---

## 2.3 Les services doivent être séparés par responsabilité

Exemples :

- Auth Service ;
- User Service ;
- KYC Service ;
- Wallet Service ;
- Ledger Service ;
- Payment Service ;
- Transfer Service ;
- Card Service ;
- Merchant Service ;
- Agent Service ;
- TPE Service ;
- ATM Service ;
- Notification Service ;
- Fraud Service ;
- Support Service ;
- Configuration Service.

---

## 2.4 Les intégrations partenaires doivent être abstraites

Le code métier ne doit pas dépendre directement d’un fournisseur unique.

Exemple :

```text
Payment Service
→ MobileMoneyConnector
→ Orange Money / autre opérateur
```

---

## 2.5 Toute opération critique doit être idempotente

Une même requête répétée ne doit pas provoquer plusieurs débits ou plusieurs crédits.

---

# 3. Vue globale

```text
Applications mobiles et web
→ CDN / WAF
→ API Gateway
→ Services métier
→ Ledger
→ Bases de données
→ Event Bus
→ Partenaires externes
→ Data Platform
→ Observabilité
→ Administration
```

---

# 4. Applications concernées

L’architecture doit supporter :

- Application Client ;
- Application Commerce ;
- Application Agent ;
- Application TPE ;
- Application Admin Lite ;
- Portail Admin Web ;
- Portail Commerçant ;
- Site Public ;
- Portail Développeurs ;
- Portail Entreprises ;
- Portail Éducation ;
- Portail Institutions ;
- Back-office Finance ;
- Back-office Fraude ;
- Back-office Data ;
- Logiciel GAB/DAB ;
- outils internes.

---

# 5. Architecture front-end

Les interfaces peuvent utiliser :

- React Native pour les applications mobiles ;
- Next.js pour les portails web ;
- Kotlin ou Android natif pour certains terminaux ;
- composants partagés ;
- Design System commun ;
- SDK API typé ;
- gestion centralisée de la configuration.

---

# 6. Monorepo

Organisation possible :

```text
mansa-platform/
├── apps/
├── services/
├── packages/
├── infrastructure/
├── docs/
├── tools/
├── tests/
└── scripts/
```

---

# 7. Packages partagés

Exemples :

- types ;
- contrats API ;
- validations ;
- erreurs ;
- logs ;
- authentification ;
- autorisation ;
- traduction ;
- design system ;
- analytics ;
- configuration ;
- SDK ;
- tests ;
- observabilité.

---

# 8. API Gateway

L’API Gateway doit gérer :

- routage ;
- authentification ;
- autorisation ;
- rate limiting ;
- quotas ;
- versionnement ;
- journaux ;
- transformations ;
- sécurité ;
- corrélation ;
- limitation des abus ;
- gestion des partenaires.

---

# 9. Responsabilités de l’API Gateway

Elle ne doit pas contenir toute la logique métier.

Elle doit principalement :

- vérifier ;
- router ;
- limiter ;
- journaliser ;
- enrichir ;
- protéger ;
- surveiller.

---

# 10. Versionnement des API

Exemples :

```text
/api/v1/payments
/api/v1/transfers
/api/v2/payments
```

---

# 11. API internes

Les services internes peuvent communiquer via :

- REST ;
- gRPC ;
- événements ;
- files ;
- commandes ;
- réponses asynchrones.

---

# 12. REST

REST peut être utilisé pour :

- requêtes synchrones ;
- consultation ;
- commandes simples ;
- API publiques ;
- intégrations partenaires.

---

# 13. gRPC

gRPC peut être utilisé pour :

- communications internes rapides ;
- contrats fortement typés ;
- services à faible latence ;
- appels internes contrôlés.

---

# 14. Event Bus

L’Event Bus doit transporter les événements métier.

Exemples :

```text
user.created
kyc.approved
wallet.created
payment.completed
transfer.failed
card.blocked
agent.float.low
atm.cash.low
terminal.offline
```

---

# 15. Technologie Event Bus

Technologies possibles :

- Kafka ;
- RabbitMQ ;
- NATS ;
- service managé équivalent.

Le choix final dépend :

- du volume ;
- de la complexité ;
- des compétences ;
- de la résilience ;
- du coût ;
- des besoins de replay.

---

# 16. Kafka

Kafka est adapté à :

- flux volumineux ;
- événements persistants ;
- replay ;
- Data Platform ;
- intégration analytique ;
- journal d’événements.

---

# 17. RabbitMQ

RabbitMQ est adapté à :

- files de travail ;
- commandes asynchrones ;
- retries ;
- routage ;
- priorités ;
- intégrations.

---

# 18. Stratégie hybride

Mansa peut utiliser :

- Kafka pour les événements métier et Data ;
- RabbitMQ pour les tâches et commandes asynchrones.

---

# 19. Événements métier

Chaque événement doit contenir :

- eventId ;
- eventType ;
- version ;
- source ;
- aggregateId ;
- occurredAt ;
- correlationId ;
- causationId ;
- payload ;
- metadata ;
- environment ;
- country.

---

# 20. Versionnement des événements

Un événement doit posséder une version.

Exemple :

```text
payment.completed.v1
payment.completed.v2
```

---

# 21. Schémas d’événements

Les schémas doivent être :

- définis ;
- versionnés ;
- validés ;
- documentés ;
- compatibles ;
- publiés dans un registre.

---

# 22. Schema Registry

Le registre peut gérer :

- JSON Schema ;
- Avro ;
- Protobuf ;
- compatibilité ;
- versions ;
- propriétaires ;
- historique.

---

# 23. Dead Letter Queue

Toute file critique doit posséder une Dead Letter Queue pour :

- messages impossibles à traiter ;
- erreurs répétées ;
- payload invalide ;
- partenaire indisponible ;
- incident ;
- reprise manuelle.

---

# 24. Retries

Les retries doivent utiliser :

- nombre limité ;
- backoff ;
- jitter ;
- distinction erreur temporaire/permanente ;
- journalisation ;
- alerte ;
- DLQ.

---

# 25. Idempotence

Chaque commande sensible doit utiliser :

- clé d’idempotence ;
- référence unique ;
- résultat mémorisé ;
- durée ;
- contrôle de répétition ;
- audit.

---

# 26. Correlation ID

Chaque parcours doit posséder un identifiant de corrélation partagé entre :

- application ;
- gateway ;
- service ;
- ledger ;
- partenaire ;
- notification ;
- support ;
- logs.

---

# 27. Service d’identité

Il doit gérer :

- utilisateurs ;
- organisations ;
- rôles ;
- permissions ;
- sessions ;
- appareils ;
- MFA ;
- passkeys ;
- certificats ;
- récupération ;
- révocation.

---

# 28. Authentification

Méthodes possibles :

- JWT ;
- OAuth 2.0 ;
- OpenID Connect ;
- mTLS ;
- API Keys ;
- certificats appareil ;
- passkeys.

---

# 29. JWT

Le JWT doit contenir uniquement les informations nécessaires :

- subject ;
- issuer ;
- audience ;
- expiration ;
- scope ;
- sessionId ;
- organizationId ;
- country ;
- role.

---

# 30. Refresh Token

Les refresh tokens doivent être :

- rotatifs ;
- révocables ;
- chiffrés ;
- liés à une session ;
- liés à un appareil ;
- limités dans le temps ;
- surveillés.

---

# 31. RBAC

Le RBAC gère les droits selon le rôle.

Exemples :

- CLIENT ;
- MERCHANT_OWNER ;
- AGENT ;
- SUPPORT ;
- FINANCE ;
- FRAUD ;
- ADMIN.

---

# 32. ABAC

L’ABAC complète le RBAC selon :

- pays ;
- organisation ;
- montant ;
- niveau KYC ;
- risque ;
- appareil ;
- localisation ;
- heure ;
- environnement ;
- ressource.

---

# 33. Service Utilisateur

Il gère :

- profil ;
- téléphone ;
- e-mail ;
- préférences ;
- langue ;
- adresse ;
- statut ;
- documents ;
- historique.

---

# 34. Service KYC

Il gère :

- parcours ;
- documents ;
- selfie ;
- vérification ;
- niveau ;
- expiration ;
- revue manuelle ;
- fournisseur ;
- audit.

---

# 35. Service KYB

Il gère :

- entreprise ;
- représentant ;
- bénéficiaires effectifs ;
- activité ;
- documents ;
- validation ;
- risque ;
- statut.

---

# 36. Service Wallet

Il gère :

- wallets ;
- devises ;
- statuts ;
- limites ;
- blocage ;
- gel ;
- réservations ;
- relation avec le ledger.

---

# 37. Ledger Service

Il doit gérer :

- comptes ;
- sous-comptes ;
- écritures ;
- débit ;
- crédit ;
- devise ;
- réservations ;
- compensations ;
- annulations ;
- rapprochement ;
- clôture ;
- audit.

---

# 38. Double entrée

Chaque transaction financière doit produire :

```text
Débit d’un compte
=
Crédit d’un autre compte
```

La somme globale des écritures doit rester équilibrée.

---

# 39. Comptes ledger

Exemples :

- wallet client ;
- wallet commerçant ;
- float Agent ;
- compte Mansa ;
- compte de frais ;
- compte de commission ;
- compte de cantonnement ;
- compte de règlement ;
- compte suspense ;
- compte partenaire ;
- compte de réserve.

---

# 40. Écritures immuables

Une écriture validée ne doit pas être modifiée.

Toute correction doit utiliser :

- reversal ;
- écriture compensatoire ;
- nouvelle référence ;
- justification ;
- approbation ;
- audit.

---

# 41. Réservations

Le ledger doit gérer :

- autorisation carte ;
- préautorisation ;
- transfert en attente ;
- paiement en traitement ;
- retrait GAB ;
- paiement hors ligne ;
- litige.

---

# 42. Solde disponible

Le solde disponible doit être calculé à partir de :

```text
Solde comptable
- montants réservés
- montants bloqués
= solde disponible
```

---

# 43. Service Paiement

Il gère :

- paiements ;
- moyens ;
- autorisations ;
- captures ;
- annulations ;
- remboursements ;
- statuts ;
- frais ;
- commissions ;
- rapprochement.

---

# 44. Orchestrateur de paiement

Le Payment Orchestrator doit choisir :

- connecteur ;
- route ;
- partenaire ;
- réseau ;
- priorité ;
- fallback ;
- coût ;
- disponibilité ;
- risque.

---

# 45. Routage intelligent

Le routage peut tenir compte :

- pays ;
- devise ;
- moyen ;
- montant ;
- partenaire ;
- taux de succès ;
- coût ;
- latence ;
- disponibilité ;
- contrat.

---

# 46. Service Transfert

Il gère :

- Mansa à Mansa ;
- banque ;
- Mobile Money ;
- international ;
- bénéficiaires ;
- limites ;
- frais ;
- conformité ;
- statuts ;
- retries.

---

# 47. Service Cartes

Il gère :

- cartes physiques ;
- cartes virtuelles ;
- tokenisation ;
- activation ;
- PIN ;
- blocage ;
- limites ;
- autorisation ;
- opposition ;
- remplacement ;
- réseau.

---

# 48. Service Agent

Il gère :

- Agents ;
- points de vente ;
- float ;
- caisses ;
- dépôts ;
- retraits ;
- commissions ;
- liquidité ;
- supervision ;
- incidents.

---

# 49. Service Commerce

Il gère :

- commerçants ;
- points de vente ;
- employés ;
- caisses ;
- paiements ;
- remboursements ;
- règlements ;
- catalogue ;
- rapports.

---

# 50. Service TPE

Il gère :

- terminaux ;
- enrôlement ;
- certificats ;
- transactions ;
- versions ;
- périphériques ;
- mode hors ligne ;
- synchronisation ;
- maintenance ;
- supervision.

---

# 51. Service GAB/DAB

Il gère :

- machines ;
- transactions ;
- cassettes ;
- billets ;
- cash ;
- dépôt ;
- retrait ;
- maintenance ;
- alarmes ;
- versions ;
- sécurité ;
- rapprochement.

---

# 52. Service Fraude

Il gère :

- règles ;
- scores ;
- signaux ;
- alertes ;
- cas ;
- décisions ;
- blocages ;
- appareils ;
- listes ;
- investigations.

---

# 53. Risk Engine

Le Risk Engine peut analyser :

- montant ;
- fréquence ;
- utilisateur ;
- appareil ;
- localisation ;
- commerçant ;
- carte ;
- Agent ;
- pays ;
- heure ;
- comportement ;
- historique.

---

# 54. Décisions du Risk Engine

- ALLOW ;
- ALLOW_WITH_MONITORING ;
- REQUIRE_ADDITIONAL_AUTH ;
- REVIEW ;
- DECLINE ;
- BLOCK ;
- FREEZE.

---

# 55. Service Notifications

Il gère :

- push ;
- SMS ;
- e-mail ;
- WhatsApp si activé ;
- modèles ;
- langues ;
- préférences ;
- retries ;
- statut ;
- coûts.

---

# 56. Service Support

Il gère :

- tickets ;
- conversations ;
- catégories ;
- SLA ;
- escalades ;
- pièces ;
- litiges ;
- remboursements ;
- satisfaction.

---

# 57. Service Configuration

Il centralise :

- pays ;
- devises ;
- frais ;
- commissions ;
- plafonds ;
- produits ;
- langues ;
- feature flags ;
- partenaires ;
- versions ;
- workflows ;
- règles.

---

# 58. Feature Flags

Les feature flags doivent cibler :

- pays ;
- ville ;
- utilisateur ;
- organisation ;
- segment ;
- appareil ;
- version ;
- partenaire ;
- environnement ;
- pourcentage.

---

# 59. Service Documents

Il gère :

- justificatifs ;
- contrats ;
- reçus ;
- relevés ;
- preuves ;
- fichiers ;
- métadonnées ;
- rétention ;
- accès ;
- chiffrement.

---

# 60. PostgreSQL

PostgreSQL peut constituer la base transactionnelle principale.

Il peut héberger :

- utilisateurs ;
- wallets ;
- ledger ;
- paiements ;
- transferts ;
- Agents ;
- commerçants ;
- cartes ;
- KYC ;
- support ;
- configuration ;
- audits.

---

# 61. Stratégie de bases

Chaque service critique peut disposer :

- de sa propre base ;
- de son propre schéma ;
- de ses migrations ;
- de ses droits ;
- de ses sauvegardes ;
- de sa rétention.

---

# 62. Database per Service

Le principe recommandé :

```text
Service
→ base ou schéma dédié
→ accès limité au service propriétaire
```

---

# 63. Interdiction d’accès direct interservice

Un service ne doit pas modifier directement les tables d’un autre service.

Il doit utiliser :

- API ;
- événement ;
- commande ;
- vue autorisée ;
- réplication analytique.

---

# 64. Redis

Redis peut être utilisé pour :

- cache ;
- sessions ;
- rate limiting ;
- verrous distribués ;
- compteurs ;
- feature flags ;
- données temporaires ;
- queues légères.

---

# 65. Cache

Les données pouvant être mises en cache :

- configuration ;
- catalogue ;
- traductions ;
- permissions ;
- statuts publics ;
- références ;
- données non financières.

---

# 66. Données à ne pas mettre en cache sans contrôle

- PIN ;
- secrets ;
- clés ;
- données biométriques ;
- données carte sensibles ;
- soldes critiques non versionnés ;
- écritures non finalisées.

---

# 67. Verrou distribué

Un verrou peut être utilisé pour :

- clôture ;
- traitement unique ;
- génération de règlement ;
- migration ;
- job ;
- réconciliation ;
- mise à jour globale.

---

# 68. Stockage objet

Le stockage objet doit gérer :

- documents KYC ;
- contrats ;
- images ;
- reçus ;
- rapports ;
- exports ;
- vidéos ;
- preuves ;
- sauvegardes ;
- médias.

---

# 69. Sécurité du stockage objet

Il doit appliquer :

- chiffrement ;
- contrôle d’accès ;
- URL temporaires ;
- antivirus ;
- rétention ;
- versionnement ;
- journaux ;
- pays ;
- classification.

---

# 70. Moteur de recherche

Il peut utiliser :

- OpenSearch ;
- Elasticsearch ;
- moteur équivalent.

Il peut indexer :

- transactions ;
- utilisateurs ;
- Agents ;
- commerçants ;
- tickets ;
- documents ;
- logs ;
- base de connaissances.

---

# 71. Indexation sécurisée

L’index ne doit pas contenir inutilement :

- secrets ;
- PIN ;
- CVV ;
- biométrie ;
- données carte complètes ;
- documents bruts non nécessaires.

---

# 72. Data Platform

La Data Platform doit gérer :

- ingestion ;
- transformation ;
- qualité ;
- stockage ;
- anonymisation ;
- modèles ;
- reporting ;
- gouvernance ;
- lineage ;
- accès.

---

# 73. Data Lake

Le Data Lake peut stocker :

- événements ;
- historiques ;
- données brutes ;
- fichiers ;
- logs ;
- données partenaires ;
- données analytiques.

---

# 74. Data Warehouse

Le Data Warehouse peut héberger :

- KPI ;
- agrégats ;
- rapports ;
- Finance ;
- produit ;
- fraude ;
- partenaires ;
- opérations ;
- pays.

---

# 75. ETL et ELT

Les pipelines doivent gérer :

- extraction ;
- validation ;
- nettoyage ;
- transformation ;
- enrichissement ;
- chargement ;
- contrôle ;
- alerte ;
- reprise.

---

# 76. Qualité des données

Contrôles :

- complétude ;
- unicité ;
- validité ;
- cohérence ;
- fraîcheur ;
- conformité ;
- doublons ;
- lineage ;
- anomalies.

---

# 77. Data Lineage

Chaque donnée analytique doit pouvoir être reliée à :

- source ;
- transformation ;
- propriétaire ;
- destination ;
- date ;
- version ;
- rapport.

---

# 78. Sécurité globale

L’architecture doit appliquer une approche Zero Trust.

Chaque accès doit vérifier :

- identité ;
- appareil ;
- rôle ;
- permission ;
- contexte ;
- risque ;
- environnement ;
- ressource ;
- pays.

---

# 79. Chiffrement en transit

Toutes les communications doivent utiliser :

- TLS ;
- certificats valides ;
- suites cryptographiques approuvées ;
- mTLS si nécessaire ;
- rotation ;
- contrôle de domaine.

---

# 80. Chiffrement au repos

Doivent être chiffrés :

- bases ;
- volumes ;
- stockage objet ;
- sauvegardes ;
- appareils ;
- secrets ;
- exports ;
- fichiers sensibles.

---

# 81. HSM

Le HSM doit protéger :

- clés cartes ;
- clés PIN ;
- clés de signature ;
- clés de chiffrement ;
- certificats critiques ;
- clés TPE ;
- clés GAB/DAB ;
- opérations réseau cartes.

---

# 82. Gestion des secrets

Les secrets doivent être stockés dans un coffre centralisé.

Exemples :

- Vault ;
- cloud secrets manager ;
- KMS ;
- HSM.

---

# 83. Interdiction des secrets dans Git

Aucun secret ne doit être stocké dans :

- dépôt Git ;
- code source ;
- image Docker ;
- fichier public ;
- logs ;
- documentation ;
- capture.

---

# 84. Rotation des secrets

La rotation peut être :

- automatique ;
- programmée ;
- manuelle contrôlée ;
- déclenchée après incident ;
- liée à une expiration ;
- auditée.

---

# 85. Segmentation réseau

Zones possibles :

- publique ;
- API ;
- services ;
- données ;
- paiement ;
- administration ;
- partenaires ;
- TPE ;
- GAB/DAB ;
- sécurité ;
- sauvegarde.

---

# 86. WAF

Le WAF doit protéger contre :

- attaques web ;
- injection ;
- bots ;
- abus ;
- scans ;
- trafic malveillant ;
- signatures connues ;
- règles personnalisées.

---

# 87. Protection DDoS

La protection doit inclure :

- filtrage ;
- CDN ;
- limitation ;
- détection ;
- mitigation ;
- redondance ;
- alertes ;
- runbook.

---

# 88. Pare-feu

Les règles réseau doivent être :

- minimales ;
- documentées ;
- versionnées ;
- approuvées ;
- testées ;
- auditées ;
- révisées.

---

# 89. Bastion

L’accès administratif peut passer par :

- bastion ;
- VPN ;
- Zero Trust Access ;
- MFA ;
- appareil géré ;
- journal de session ;
- accès temporaire.

---

# 90. Accès Production

L’accès Production doit être :

- limité ;
- temporaire si possible ;
- approuvé ;
- journalisé ;
- soumis à MFA ;
- lié à un motif ;
- révocable ;
- audité.

---

# 91. Infrastructure as Code

L’infrastructure doit être décrite avec :

- Terraform ;
- Pulumi ;
- CloudFormation ;
- outil équivalent.

---

# 92. Avantages de l’IaC

- reproductibilité ;
- versionnement ;
- revue ;
- audit ;
- déploiement ;
- restauration ;
- multi-région ;
- multi-pays ;
- contrôle des changements.

---

# 93. Conteneurs

Les services peuvent être empaquetés en conteneurs.

Chaque image doit être :

- minimale ;
- versionnée ;
- signée ;
- scannée ;
- immuable ;
- non root ;
- traçable ;
- testée.

---

# 94. Registre d’images

Le registre doit gérer :

- images ;
- versions ;
- signatures ;
- scans ;
- rétention ;
- accès ;
- promotion entre environnements ;
- suppression.

---

# 95. Orchestration Kubernetes

Kubernetes peut gérer :

- déploiement ;
- autoscaling ;
- réseau ;
- secrets ;
- health checks ;
- redémarrage ;
- disponibilité ;
- rollouts ;
- rollback.

---

# 96. Namespaces

Exemples :

- development ;
- test ;
- demo ;
- recette ;
- preproduction ;
- production ;
- observability ;
- security ;
- data.

---

# 97. Health Checks

Chaque service doit exposer :

- liveness ;
- readiness ;
- startup ;
- dépendances critiques ;
- version ;
- statut.

---

# 98. Autoscaling

L’autoscaling peut utiliser :

- CPU ;
- mémoire ;
- nombre de requêtes ;
- latence ;
- taille de queue ;
- événements ;
- horaires ;
- charge pays.

---

# 99. Resource Limits

Chaque service doit définir :

- CPU minimal ;
- CPU maximal ;
- mémoire minimale ;
- mémoire maximale ;
- stockage ;
- priorité ;
- politique de redémarrage.

---

# 100. Service Mesh

Un service mesh peut fournir :

- mTLS ;
- observabilité ;
- retries ;
- circuit breaker ;
- routage ;
- politique ;
- contrôle de trafic.

---

# 101. Circuit Breaker

Chaque intégration doit gérer :

- seuil d’erreurs ;
- ouverture ;
- période ;
- tentative ;
- fermeture ;
- fallback ;
- alerte.

---

# 102. Timeout

Chaque appel doit avoir un timeout explicite.

Les appels financiers doivent ensuite :

- vérifier le statut ;
- éviter le doublon ;
- déclencher un reversal si nécessaire ;
- rapprocher.

---

# 103. Bulkhead

Les ressources doivent être isolées afin qu’une panne partenaire ne bloque pas tout le système.

---

# 104. Environnements

Environnements officiels :

- LOCAL ;
- DEVELOPMENT ;
- TEST ;
- DEMO ;
- RECETTE ;
- SANDBOX ;
- PREPRODUCTION ;
- PRODUCTION ;
- PERFORMANCE ;
- SECURITY ;
- DISASTER_RECOVERY.

---

# 105. Séparation des environnements

Chaque environnement doit avoir :

- bases séparées ;
- secrets séparés ;
- certificats séparés ;
- partenaires séparés ;
- clés séparées ;
- accès séparés ;
- logs séparés ;
- coûts séparés.

---

# 106. Données de test

Les environnements non Production doivent utiliser :

- données fictives ;
- données anonymisées ;
- données synthétiques ;
- comptes de test ;
- cartes de test ;
- partenaires Sandbox.

---

# 107. CI

La CI doit automatiser :

- installation ;
- lint ;
- compilation ;
- type checking ;
- validation Prisma ;
- génération ;
- tests ;
- scans ;
- artefacts ;
- rapports.

---

# 108. CD

La CD doit automatiser :

- déploiement ;
- migrations ;
- smoke tests ;
- validation ;
- promotion ;
- rollback ;
- notification ;
- audit.

---

# 109. Quality Gates

Le pipeline doit bloquer en cas de :

- build échoué ;
- tests critiques échoués ;
- secret détecté ;
- vulnérabilité critique ;
- migration invalide ;
- qualité insuffisante ;
- image non signée ;
- absence d’approbation.

---

# 110. SAST

Le SAST doit analyser :

- code ;
- dépendances ;
- injections ;
- secrets ;
- mauvaises pratiques ;
- vulnérabilités ;
- règles internes.

---

# 111. DAST

Le DAST doit tester :

- API ;
- web ;
- authentification ;
- injection ;
- sessions ;
- erreurs ;
- permissions ;
- exposition.

---

# 112. Scan des dépendances

Le scan doit détecter :

- vulnérabilités ;
- licences ;
- packages obsolètes ;
- packages compromis ;
- dépendances indirectes ;
- conflits.

---

# 113. SBOM

Chaque release peut produire une Software Bill of Materials contenant :

- composants ;
- versions ;
- licences ;
- dépendances ;
- hash ;
- provenance.

---

# 114. Signature des artefacts

Doivent être signés lorsque possible :

- images ;
- packages ;
- applications ;
- firmwares ;
- SDK ;
- fichiers de release ;
- artefacts critiques.

---

# 115. Migrations de base

Les migrations doivent être :

- versionnées ;
- testées ;
- réversibles lorsque possible ;
- compatibles ;
- sauvegardées ;
- observées ;
- approuvées.

---

# 116. Migration sans interruption

Les changements doivent privilégier :

- ajout avant suppression ;
- colonnes compatibles ;
- double lecture temporaire ;
- double écriture contrôlée ;
- migration progressive ;
- nettoyage ultérieur.

---

# 117. Observabilité

Chaque service doit produire :

- logs ;
- métriques ;
- traces ;
- événements ;
- health checks ;
- alertes ;
- SLI ;
- SLO.

---

# 118. Logs

Les logs doivent inclure :

- service ;
- version ;
- environnement ;
- correlationId ;
- requestId ;
- statut ;
- durée ;
- erreur ;
- pays ;
- partenaire ;
- ressource.

---

# 119. Logs interdits

Ne pas enregistrer :

- PIN ;
- CVV ;
- PAN complet ;
- mot de passe ;
- OTP complet ;
- clé ;
- secret ;
- biométrie brute ;
- document complet.

---

# 120. Métriques

Exemples :

- requêtes ;
- erreurs ;
- latence ;
- transactions ;
- paiements ;
- transferts ;
- files ;
- CPU ;
- mémoire ;
- stockage ;
- connexions ;
- retries ;
- timeouts.

---

# 121. Traces distribuées

Une transaction doit pouvoir être suivie à travers :

```text
Application
→ Gateway
→ Payment Service
→ Risk Engine
→ Ledger
→ Partenaire
→ Notification
```

---

# 122. Stack d’observabilité

Technologies possibles :

- OpenTelemetry ;
- Prometheus ;
- Grafana ;
- Loki ;
- Tempo ;
- Jaeger ;
- ELK/OpenSearch ;
- outils cloud équivalents.

---

# 123. Dashboards

Dashboards essentiels :

- plateforme ;
- API ;
- ledger ;
- paiements ;
- transferts ;
- cartes ;
- Agents ;
- TPE ;
- GAB/DAB ;
- partenaires ;
- bases ;
- sécurité ;
- coûts.

---

# 124. Alertes

Alertes possibles :

- service indisponible ;
- latence élevée ;
- taux d’erreur ;
- ledger déséquilibré ;
- partenaire indisponible ;
- queue bloquée ;
- réplication en retard ;
- certificat expirant ;
- stockage élevé ;
- fraude ;
- backup échoué.

---

# 125. SLI

Exemples :

- taux de succès ;
- disponibilité ;
- latence ;
- fraîcheur ;
- intégrité ;
- temps de traitement ;
- taux de rapprochement.

---

# 126. SLO

Exemples :

- disponibilité API ;
- temps de réponse ;
- taux de paiement réussi ;
- délai de notification ;
- temps de reprise ;
- taux de traitement événementiel.

---

# 127. Incident Management

Le processus doit couvrir :

- détection ;
- classification ;
- assignation ;
- mitigation ;
- résolution ;
- communication ;
- post-mortem ;
- actions correctives.

---

# 128. Gravité des incidents

- SEV0 ;
- SEV1 ;
- SEV2 ;
- SEV3 ;
- SEV4.

---

# 129. Runbooks

Les runbooks doivent couvrir :

- service indisponible ;
- base indisponible ;
- ledger ;
- partenaire ;
- queue ;
- certificat ;
- fuite de secret ;
- GAB ;
- TPE ;
- sauvegarde ;
- région cloud.

---

# 130. Haute disponibilité

Les services critiques doivent fonctionner avec :

- plusieurs instances ;
- plusieurs zones ;
- load balancing ;
- réplication ;
- stockage redondé ;
- health checks ;
- bascule ;
- autoscaling.

---

# 131. Base haute disponibilité

PostgreSQL doit prévoir :

- primaire ;
- réplica ;
- bascule ;
- sauvegarde ;
- réplication ;
- contrôle de lag ;
- test ;
- monitoring.

---

# 132. Réplication

La réplication peut être :

- synchrone ;
- asynchrone ;
- locale ;
- inter-région ;
- lecture ;
- analytique.

---

# 133. Sauvegardes

Doivent être sauvegardés :

- bases ;
- ledger ;
- documents ;
- configurations ;
- secrets selon politique ;
- certificats ;
- logs critiques ;
- données Data ;
- audits.

---

# 134. Politique de sauvegarde

Elle doit définir :

- fréquence ;
- rétention ;
- emplacement ;
- chiffrement ;
- copie hors région ;
- propriétaire ;
- test ;
- restauration ;
- audit.

---

# 135. Point-in-Time Recovery

Les bases critiques doivent permettre une restauration à un instant précis.

---

# 136. Tests de restauration

Les sauvegardes doivent être restaurées régulièrement dans un environnement contrôlé.

Une sauvegarde non testée ne doit pas être considérée comme fiable.

---

# 137. PRA

Le Plan de Reprise d’Activité doit préciser :

- services critiques ;
- ordre de reprise ;
- dépendances ;
- RTO ;
- RPO ;
- responsables ;
- régions ;
- procédures ;
- communication ;
- tests.

---

# 138. RTO

Le RTO correspond au délai maximal acceptable avant reprise.

Il doit être défini par service.

---

# 139. RPO

Le RPO correspond à la perte maximale de données acceptable.

Le ledger et les paiements doivent avoir un RPO très faible.

---

# 140. Multi-région

L’architecture doit pouvoir utiliser :

- région principale ;
- région secondaire ;
- réplication ;
- DNS ;
- bascule ;
- failback ;
- sauvegarde ;
- isolation ;
- tests.

---

# 141. Active-Passive

Dans un modèle Active-Passive :

- une région traite ;
- une région attend ;
- les données sont répliquées ;
- la bascule est contrôlée ;
- le retour est planifié.

---

# 142. Active-Active

Le modèle Active-Active peut être envisagé pour certains services non financiers ou fortement distribués.

Le ledger exige une conception très stricte avant tout Active-Active.

---

# 143. Multi-pays

Chaque pays doit pouvoir avoir :

- configuration ;
- devise ;
- langues ;
- partenaires ;
- frais ;
- limites ;
- KYC ;
- KYB ;
- stockage ;
- reporting ;
- support ;
- règles ;
- feature flags.

---

# 144. Isolation pays

L’isolation peut être :

- logique ;
- par schéma ;
- par base ;
- par région ;
- par compte cloud ;
- par environnement ;
- par chiffrement.

---

# 145. Localisation des données

La localisation doit respecter :

- réglementation ;
- contrat ;
- pays ;
- sensibilité ;
- rétention ;
- transfert ;
- sécurité ;
- audit.

---

# 146. Administration centrale

Le Super Admin doit pouvoir gérer :

- services ;
- environnements ;
- pays ;
- partenaires ;
- configurations ;
- versions ;
- feature flags ;
- bases ;
- files ;
- événements ;
- secrets ;
- certificats ;
- déploiements ;
- incidents ;
- coûts ;
- audits.

---

# 147. Rôles techniques

Exemples :

```text
PLATFORM_ADMIN
CLOUD_ADMIN
SECURITY_ADMIN
DATABASE_ADMIN
SRE
DEVOPS_ENGINEER
RELEASE_MANAGER
NETWORK_ADMIN
DATA_ENGINEER
LEDGER_OPERATOR
INCIDENT_MANAGER
AUDITOR
VIEWER
```

---

# 148. Permissions

Exemples :

```text
platform.read
platform.manage
deployment.create
deployment.approve
database.read
database.manage
secret.rotate
certificate.rotate
feature_flag.manage
incident.manage
backup.restore
dr.activate
audit.read
```

---

# 149. Approbations

Peuvent nécessiter une approbation :

- déploiement Production ;
- migration base ;
- rotation HSM ;
- restauration ;
- bascule région ;
- modification réseau ;
- changement ledger ;
- changement de secret critique ;
- activation pays ;
- suppression infrastructure.

---

# 150. Critères d’acceptation finaux

L’Architecture technique finale Mansa est validée lorsque :

- les applications sont cartographiées ;
- l’API Gateway est définie ;
- les services sont séparés ;
- les API internes sont définies ;
- REST et gRPC sont encadrés ;
- l’Event Bus est défini ;
- Kafka et RabbitMQ sont évalués ;
- les événements sont versionnés ;
- un Schema Registry est prévu ;
- les DLQ sont prévues ;
- les retries sont contrôlés ;
- l’idempotence est appliquée ;
- les identifiants de corrélation sont généralisés ;
- le service d’identité est défini ;
- JWT, OAuth et mTLS sont supportables ;
- RBAC et ABAC sont appliqués ;
- le KYC est séparé ;
- le KYB est séparé ;
- le Wallet est séparé ;
- le ledger est la source de vérité ;
- la double entrée est appliquée ;
- les écritures sont immuables ;
- les réservations sont gérées ;
- le Payment Orchestrator est défini ;
- le routage intelligent est supportable ;
- les transferts sont séparés ;
- les cartes sont séparées ;
- les Agents sont séparés ;
- les commerçants sont séparés ;
- les TPE sont séparés ;
- les GAB/DAB sont séparés ;
- la fraude est intégrée ;
- le Risk Engine est défini ;
- les notifications sont séparées ;
- le support est séparé ;
- la configuration est centralisée ;
- les feature flags sont disponibles ;
- les documents sont gérés ;
- PostgreSQL est défini ;
- les bases sont isolées ;
- les accès directs interservices sont interdits ;
- Redis est défini ;
- le cache est contrôlé ;
- les verrous distribués sont encadrés ;
- le stockage objet est sécurisé ;
- le moteur de recherche est sécurisé ;
- la Data Platform est définie ;
- le Data Lake est prévu ;
- le Data Warehouse est prévu ;
- la qualité des données est contrôlée ;
- le lineage est disponible ;
- le Zero Trust est appliqué ;
- le chiffrement en transit est appliqué ;
- le chiffrement au repos est appliqué ;
- le HSM est intégré ;
- les secrets sont centralisés ;
- les secrets sont interdits dans Git ;
- la rotation des secrets est définie ;
- les réseaux sont segmentés ;
- le WAF est prévu ;
- l’anti-DDoS est prévu ;
- les pare-feux sont versionnés ;
- les accès Production sont limités ;
- l’infrastructure as code est utilisée ;
- les images sont signées ;
- Kubernetes est supportable ;
- les health checks sont définis ;
- l’autoscaling est prévu ;
- les limites de ressources sont définies ;
- le circuit breaker est intégré ;
- les timeouts sont explicites ;
- les environnements sont séparés ;
- les données de test sont fictives ;
- la CI est définie ;
- la CD est définie ;
- les Quality Gates sont définis ;
- le SAST est intégré ;
- le DAST est intégré ;
- les dépendances sont scannées ;
- une SBOM est générable ;
- les artefacts sont signés ;
- les migrations sont versionnées ;
- l’observabilité est complète ;
- les logs sont structurés ;
- les données sensibles sont exclues des logs ;
- les métriques sont définies ;
- les traces distribuées sont disponibles ;
- les dashboards sont disponibles ;
- les alertes sont configurées ;
- les SLI et SLO sont définis ;
- la gestion d’incident est définie ;
- les runbooks sont disponibles ;
- la haute disponibilité est prévue ;
- PostgreSQL est répliqué ;
- les sauvegardes sont chiffrées ;
- le Point-in-Time Recovery est prévu ;
- les restaurations sont testées ;
- le PRA est défini ;
- les RTO et RPO sont définis ;
- le multi-région est prévu ;
- le multi-pays est supporté ;
- l’isolation pays est définie ;
- la localisation des données est contrôlée ;
- l’administration centrale est complète ;
- les rôles techniques sont définis ;
- les permissions sont appliquées ;
- les approbations critiques sont protégées ;
- les audits sont immuables.
