# 38 — Architecture globale de la plateforme Mansa, domaines, services et flux principaux

## 1. Objet du document

Ce document définit l’architecture fonctionnelle et technique globale de Mansa.

Il couvre :

- les applications ;
- les portails web ;
- les services backend ;
- l’API Gateway ;
- les domaines métier ;
- les bases de données ;
- le ledger ;
- les événements ;
- les files ;
- les partenaires ;
- les environnements ;
- le multi-pays ;
- le multi-tenant ;
- les permissions ;
- les flux principaux ;
- la communication entre les composants ;
- la séparation des responsabilités ;
- la résilience ;
- l’observabilité ;
- la sécurité ;
- les dépendances critiques.

L’objectif est de disposer d’une vue d’ensemble unique permettant de comprendre :

- quels composants existent ;
- quel est leur rôle ;
- comment ils communiquent ;
- où se trouvent les données ;
- quels services sont critiques ;
- comment Mansa évolue vers plusieurs pays et plusieurs partenaires ;
- comment éviter un système centralisé impossible à maintenir.

---

# 2. Principes fondamentaux

## 2.1 Architecture modulaire

Mansa doit être organisée par domaines fonctionnels clairement séparés.

Chaque domaine doit posséder :

- ses responsabilités ;
- ses services ;
- ses règles métier ;
- ses données ;
- ses événements ;
- ses permissions ;
- ses tests ;
- son propriétaire.

---

## 2.2 Séparation entre interface et logique métier

Les applications ne doivent pas contenir la logique financière officielle.

Les applications doivent principalement gérer :

- l’affichage ;
- la navigation ;
- la saisie ;
- les validations locales ;
- le cache ;
- l’expérience utilisateur ;
- les appels API ;
- la synchronisation.

Les règles officielles restent dans le backend.

---

## 2.3 Source de vérité explicite

Chaque type de donnée doit avoir une source officielle.

Exemples :

- soldes : ledger ;
- identité : service identité ;
- KYC : service conformité ;
- transactions : service paiement ;
- cartes : service cartes ;
- rôles : service IAM ;
- catalogue : service commerce ;
- tickets : service support.

---

## 2.4 Aucun accès direct aux bases depuis les applications

Les applications doivent passer par :

- API Gateway ;
- services backend autorisés ;
- endpoints versionnés ;
- contrôles d’authentification ;
- contrôles de permissions.

---

## 2.5 Architecture évolutive

La plateforme doit pouvoir évoluer :

- d’un pays à plusieurs pays ;
- d’un partenaire à plusieurs partenaires ;
- d’une petite base d’utilisateurs à plusieurs millions ;
- d’un monolithe modulaire à des services séparés si nécessaire ;
- d’une infrastructure simple à une architecture distribuée.

---

# 3. Vue générale

```text
Utilisateurs et acteurs
│
├── Application Client
├── Application Commerce
├── Application TPE
├── Application Admin Lite
├── Hub / Annuaire
├── Site public
├── Portail Admin Web
└── Portails partenaires et institutions
        │
        ▼
API Gateway
        │
        ├── Authentification
        ├── Autorisation
        ├── Rate limiting
        ├── Routage
        ├── Versionnement
        ├── Observabilité
        └── Protection
        │
        ▼
Services métier
│
├── Identity & Access
├── Customer
├── KYC / KYB
├── Wallet
├── Ledger
├── Payments
├── Transfers
├── Cards
├── Merchant
├── TPE
├── Fees & Pricing
├── Fraud
├── Compliance
├── Notifications
├── Documents
├── Support
├── Public Services
├── Jini
├── Analytics
└── Partner Integrations
        │
        ▼
Données et infrastructure
│
├── PostgreSQL
├── Ledger Store
├── Redis
├── Message Broker
├── Object Storage
├── Search
├── Logs
├── Metrics
└── Backups
        │
        ▼
Partenaires externes
│
├── Banques
├── Mobile Money
├── Visa / Mastercard
├── KYC / AML
├── SMS / E-mail / Push
├── Services publics
└── Fournisseurs techniques
```

---

# 4. Applications officielles

## 4.1 Application Client

Destinée aux particuliers.

Fonctions principales :

- inscription ;
- KYC ;
- wallet ;
- paiements ;
- transferts ;
- cartes ;
- budget ;
- coffre ;
- reçus ;
- support ;
- Jini ;
- annuaire.

---

## 4.2 Application Commerce

Destinée aux commerçants et organisations.

Fonctions principales :

- profil commerce ;
- établissements ;
- employés ;
- produits ;
- stock ;
- ventes ;
- factures ;
- remboursements ;
- règlements ;
- rapports ;
- promotions ;
- mini-site ;
- TPE associés.

---

## 4.3 Application TPE

Destinée aux terminaux de paiement.

Fonctions principales :

- activation ;
- paiement ;
- remboursement ;
- impression ;
- catalogue ;
- tickets ;
- clôture ;
- synchronisation ;
- mode hors ligne contrôlé ;
- gestion de l’appareil.

---

## 4.4 Application Admin Lite

Destinée aux équipes opérationnelles mobiles.

Fonctions possibles :

- support terrain ;
- commerçants ;
- TPE ;
- validation limitée ;
- contrôle ;
- incident ;
- intervention ;
- consultation sécurisée.

---

## 4.5 Hub / Annuaire

Destiné à la découverte d’activités.

Fonctions principales :

- annuaire ;
- recherche ;
- géolocalisation ;
- filtres ;
- profils ;
- mini-sites ;
- promotions ;
- mise en avant ;
- prise de contact ;
- navigation vers le paiement.

---

## 4.6 Site public

Fonctions principales :

- présentation de Mansa ;
- informations ;
- offres ;
- partenaires ;
- chiffres ;
- actualités ;
- sécurité ;
- recrutement ;
- support ;
- téléchargement des applications.

---

## 4.7 Portail Admin Web

Destiné aux équipes autorisées.

Fonctions principales :

- utilisateurs ;
- commerçants ;
- TPE ;
- paiements ;
- cartes ;
- conformité ;
- fraude ;
- support ;
- partenaires ;
- configuration ;
- audit ;
- analytics ;
- infrastructure ;
- permissions.

---

# 5. API Gateway

L’API Gateway est le point d’entrée officiel.

Il doit gérer :

- authentification ;
- vérification des tokens ;
- autorisation ;
- routage ;
- quotas ;
- limitations ;
- versionnement ;
- validation ;
- corrélation ;
- logs ;
- protection contre les abus ;
- disponibilité.

---

# 6. Services métier principaux

## 6.1 Identity and Access Service

Responsabilités :

- comptes ;
- sessions ;
- MFA ;
- appareils ;
- rôles ;
- permissions ;
- délégations ;
- accès d’urgence ;
- révocation.

---

## 6.2 Customer Service

Responsabilités :

- profil particulier ;
- coordonnées ;
- préférences ;
- statut ;
- pays ;
- langue ;
- relations ;
- clôture.

---

## 6.3 Compliance Service

Responsabilités :

- KYC ;
- KYB ;
- AML ;
- sanctions ;
- PEP ;
- dossiers ;
- alertes ;
- restrictions ;
- reporting.

---

## 6.4 Wallet Service

Responsabilités :

- création de wallet ;
- statut ;
- devise ;
- plafonds ;
- règles d’usage ;
- association utilisateur ;
- consultation contrôlée.

---

## 6.5 Ledger Service

Responsabilités :

- écritures ;
- comptes ;
- soldes ;
- réservations ;
- contre-écritures ;
- clôture ;
- cohérence ;
- audit financier.

---

## 6.6 Payment Service

Responsabilités :

- paiements ;
- autorisations ;
- captures ;
- annulations ;
- statuts ;
- orchestration ;
- idempotence ;
- partenaires.

---

## 6.7 Transfer Service

Responsabilités :

- transferts internes ;
- transferts externes ;
- bénéficiaires ;
- statuts ;
- limites ;
- frais ;
- vérifications ;
- rapprochement.

---

## 6.8 Card Service

Responsabilités :

- cartes physiques ;
- cartes virtuelles ;
- activation ;
- gel ;
- plafonds ;
- PIN ;
- remplacement ;
- tokenisation ;
- provisioning wallet.

---

## 6.9 Merchant Service

Responsabilités :

- commerces ;
- établissements ;
- employés ;
- catalogue ;
- stock ;
- commandes ;
- factures ;
- règlements ;
- promotions.

---

## 6.10 Terminal Service

Responsabilités :

- TPE ;
- activation ;
- affectation ;
- certificats ;
- versions ;
- statut ;
- santé ;
- synchronisation ;
- maintenance.

---

## 6.11 Pricing Service

Responsabilités :

- frais ;
- commissions ;
- taxes ;
- taux ;
- paliers ;
- règles pays ;
- règles partenaires ;
- prévisualisation.

---

## 6.12 Fraud Service

Responsabilités :

- scoring ;
- règles ;
- signaux ;
- alertes ;
- dossiers ;
- blocages ;
- listes ;
- pertes ;
- recouvrements.

---

## 6.13 Notification Service

Responsabilités :

- Push ;
- SMS ;
- e-mail ;
- préférences ;
- templates ;
- fallback ;
- suivi de livraison ;
- campagnes.

---

## 6.14 Document Service

Responsabilités :

- reçus ;
- factures ;
- relevés ;
- contrats ;
- documents KYC ;
- signatures ;
- exports ;
- conservation.

---

## 6.15 Support Service

Responsabilités :

- tickets ;
- messages ;
- pièces jointes ;
- SLA ;
- réclamations ;
- litiges ;
- médiation ;
- remboursements contrôlés.

---

## 6.16 Public Services Service

Responsabilités :

- amendes ;
- taxes ;
- bourses ;
- scolarité ;
- cartes étudiantes ;
- agents publics ;
- institutions ;
- rapprochement ;
- audit anti-corruption.

---

## 6.17 Jini Service

Responsabilités :

- orchestration IA ;
- modèles ;
- prompts ;
- outils ;
- permissions ;
- contexte ;
- coûts ;
- audit ;
- validation humaine.

---

## 6.18 Analytics Service

Responsabilités :

- événements ;
- agrégations ;
- rapports ;
- tableaux de bord ;
- métriques ;
- tendances ;
- données pseudonymisées.

---

## 6.19 Integration Service

Responsabilités :

- banques ;
- Mobile Money ;
- réseaux cartes ;
- KYC ;
- AML ;
- notifications ;
- services publics ;
- partenaires API ;
- webhooks ;
- certificats.

---

# 7. Communication entre services

Les services peuvent communiquer par :

- appels synchrones ;
- événements ;
- commandes asynchrones ;
- webhooks ;
- files ;
- batchs ;
- synchronisations planifiées.

---

# 8. Communication synchrone

À utiliser lorsque :

- la réponse est immédiatement nécessaire ;
- la validation doit bloquer l’action ;
- la latence reste acceptable ;
- l’opération est courte ;
- la cohérence immédiate est obligatoire.

Exemples :

- authentification ;
- vérification de permission ;
- lecture de solde ;
- prévisualisation de frais ;
- contrôle de limite.

---

# 9. Communication asynchrone

À utiliser pour :

- notifications ;
- rapports ;
- rapprochement ;
- documents ;
- analytics ;
- webhooks ;
- traitements longs ;
- synchronisations ;
- vérifications différées.

---

# 10. Événements métier principaux

Exemples :

```text
user.created
user.kyc.approved
wallet.created
payment.initiated
payment.completed
payment.failed
transfer.completed
card.activated
merchant.approved
terminal.assigned
refund.completed
support.ticket.created
```

---

# 11. Flux d’inscription utilisateur

```text
Application Client
    │
    ▼
API Gateway
    │
    ▼
Identity Service
    │
    ├── création du compte
    ├── vérification du téléphone
    └── création de session
    │
    ▼
Customer Service
    │
    ▼
Compliance Service
    │
    ├── KYC
    └── screening
    │
    ▼
Wallet Service
    │
    ▼
Ledger Service
```

---

# 12. Flux de paiement

```text
Application / TPE
    │
    ▼
API Gateway
    │
    ▼
Payment Service
    │
    ├── vérification identité
    ├── vérification permissions
    ├── vérification limites
    ├── calcul des frais
    ├── évaluation fraude
    ├── réservation ledger
    ├── appel partenaire
    ├── confirmation
    ├── écriture finale
    └── notification
```

---

# 13. Flux de remboursement

```text
Application Commerce / Admin
    │
    ▼
Payment Service
    │
    ├── transaction d’origine
    ├── montant disponible
    ├── permissions
    ├── fraude
    ├── approbation éventuelle
    ├── appel partenaire
    ├── contre-écriture ledger
    └── notification
```

---

# 14. Flux TPE

```text
TPE
    │
    ├── authentification terminal
    ├── authentification employé
    ├── demande de paiement
    ├── appel Payment Service
    ├── traitement réseau carte
    ├── confirmation
    ├── reçu
    └── synchronisation
```

---

# 15. Flux Mobile Money

```text
Application Client
    │
    ▼
Transfer / Payment Service
    │
    ▼
Integration Service
    │
    ▼
Opérateur Mobile Money
    │
    ├── réponse synchrone
    ├── webhook
    └── rapprochement
```

---

# 16. Flux service public

```text
Agent public / Citoyen
    │
    ▼
Public Services Service
    │
    ├── vérification agent
    ├── vérification dossier
    ├── calcul montant
    ├── création référence
    ├── paiement
    ├── ledger
    ├── reçu
    ├── rapprochement
    └── audit
```

---

# 17. Multi-pays

L’architecture doit distinguer :

- pays d’inscription ;
- pays de résidence ;
- pays d’activité ;
- pays de transaction ;
- pays du partenaire ;
- pays de conservation.

Chaque pays peut définir :

- devise ;
- langues ;
- limites ;
- frais ;
- règles KYC ;
- partenaires ;
- produits ;
- services publics ;
- conservation ;
- infrastructure.

---

# 18. Multi-tenant

Les organisations doivent être isolées.

Entités possibles :

- merchantId ;
- organizationId ;
- institutionId ;
- establishmentId ;
- countryId ;
- tenantId.

L’accès doit vérifier le périmètre à chaque opération.

---

# 19. Séparation des données

Selon le risque, utiliser :

- isolation logique ;
- schéma séparé ;
- base séparée ;
- cluster séparé ;
- région séparée ;
- compte cloud séparé.

---

# 20. Bases de données

La plateforme peut utiliser :

- PostgreSQL pour les données métier ;
- stockage dédié pour le ledger si nécessaire ;
- Redis pour les données temporaires ;
- stockage objet pour les documents ;
- moteur de recherche pour l’annuaire et l’Admin ;
- entrepôt analytique pour les rapports.

---

# 21. Cohérence du ledger

Le ledger doit rester séparé de :

- l’affichage ;
- l’analytics ;
- le cache ;
- le partenaire ;
- la file ;
- les exports.

Il constitue la source financière officielle.

---

# 22. Cache

Le cache peut accélérer :

- configurations ;
- profils ;
- catalogues ;
- sessions ;
- permissions ;
- taux ;
- annuaire ;
- résultats non critiques.

Il ne doit pas devenir la seule source du solde.

---

# 23. Stockage documentaire

Le stockage objet doit gérer :

- chiffrement ;
- versionnement ;
- rétention ;
- URLs temporaires ;
- permissions ;
- antivirus ;
- audit ;
- archivage.

---

# 24. Recherche

Un moteur de recherche peut être utilisé pour :

- annuaire ;
- commerces ;
- produits ;
- tickets ;
- audits ;
- documents ;
- administration.

Les résultats doivent respecter les permissions.

---

# 25. Observabilité

Chaque service doit exposer :

- logs ;
- métriques ;
- traces ;
- santé ;
- version ;
- erreurs ;
- latence ;
- dépendances ;
- corrélation.

---

# 26. Corrélation globale

Un identifiant de corrélation doit traverser :

- application ;
- API Gateway ;
- service ;
- file ;
- worker ;
- partenaire ;
- webhook ;
- ledger ;
- notification ;
- audit.

---

# 27. Résilience

Chaque service critique doit prévoir :

- timeout ;
- retry ;
- circuit breaker ;
- fallback ;
- idempotence ;
- file ;
- dead-letter queue ;
- mode dégradé ;
- monitoring ;
- reprise.

---

# 28. Dépendances critiques

Les dépendances critiques incluent :

- Identity Service ;
- Ledger Service ;
- PostgreSQL ;
- secrets ;
- DNS ;
- API Gateway ;
- message broker ;
- partenaires financiers ;
- certificats ;
- stockage.

---

# 29. Mode dégradé

Exemples :

- consultation seulement ;
- blocage des paiements ;
- blocage d’un partenaire ;
- désactivation d’un pays ;
- TPE limité ;
- suspension des nouvelles inscriptions ;
- lecture seule du portail Admin.

---

# 30. Sécurité

L’architecture doit intégrer :

- Zero Trust ;
- authentification forte ;
- permissions minimales ;
- chiffrement ;
- rotation des secrets ;
- segmentation ;
- WAF ;
- rate limiting ;
- audit ;
- détection de fraude ;
- surveillance.

---

# 31. Environnements

Environnements officiels :

```text
local
development
test
demo
staging
preproduction
production
```

Chaque environnement doit avoir :

- ses secrets ;
- ses bases ;
- ses partenaires ;
- ses domaines ;
- ses journaux ;
- ses permissions ;
- ses données.

---

# 32. Déploiement

Les services doivent pouvoir être déployés :

- indépendamment ;
- progressivement ;
- par environnement ;
- par pays ;
- avec rollback ;
- avec feature flags ;
- avec smoke tests ;
- avec monitoring.

---

# 33. Feature flags

Les fonctionnalités doivent pouvoir être activées selon :

- pays ;
- application ;
- utilisateur ;
- partenaire ;
- version ;
- organisation ;
- pourcentage ;
- environnement.

---

# 34. Gouvernance des domaines

Chaque domaine doit avoir :

- un propriétaire produit ;
- un propriétaire technique ;
- des règles ;
- des APIs ;
- des modèles ;
- des événements ;
- des métriques ;
- des tests ;
- une documentation.

---

# 35. Dépendances entre domaines

Une dépendance doit être :

- explicite ;
- documentée ;
- versionnée ;
- testée ;
- observable ;
- limitée.

Les appels circulaires doivent être évités.

---

# 36. Monolithe modulaire et microservices

Mansa peut commencer avec un monolithe modulaire bien structuré.

La séparation en microservices devient pertinente lorsque :

- la charge le justifie ;
- l’équipe grandit ;
- les déploiements doivent être indépendants ;
- un domaine possède des contraintes spécifiques ;
- un partenaire exige une isolation ;
- la disponibilité doit être séparée.

---

# 37. Critères d’extraction d’un service

Un module peut devenir un service indépendant s’il possède :

- responsabilité claire ;
- données maîtrisées ;
- API stable ;
- charge distincte ;
- besoin de scaling ;
- besoin de sécurité ;
- cycle de déploiement propre ;
- équipe responsable.

---

# 38. Administration centrale

Le portail Admin doit fournir une vue globale sur :

- applications ;
- services ;
- pays ;
- partenaires ;
- transactions ;
- utilisateurs ;
- incidents ;
- risques ;
- configurations ;
- versions ;
- dépendances ;
- santé ;
- coûts ;
- audits.

---

# 39. Permissions

Exemples :

```text
architecture.read
architecture.service.read
architecture.dependency.read
architecture.environment.read
architecture.country.read
architecture.tenant.read
architecture.configuration.read
architecture.audit.read
```

---

# 40. Modèles

- PlatformApplication
- PlatformService
- PlatformDomain
- ServiceDependency
- ServiceEndpoint
- ServiceEvent
- ServiceOwner
- PlatformEnvironment
- PlatformCountry
- PlatformTenant
- PlatformCapability
- PlatformFlow
- PlatformIntegration
- PlatformDataStore
- PlatformHealth
- PlatformAudit

---

# 41. Règles métier

1. Chaque application passe par l’API Gateway.
2. Les applications n’accèdent pas directement aux bases.
3. Chaque domaine possède une responsabilité claire.
4. Le ledger est la source financière officielle.
5. Les données ont une source de vérité identifiée.
6. Les communications sont versionnées.
7. Les traitements longs sont asynchrones.
8. Les opérations critiques sont idempotentes.
9. Les services critiques sont observables.
10. Les environnements sont séparés.
11. Les pays peuvent avoir des règles différentes.
12. Les tenants sont isolés.
13. Les partenaires sont encapsulés.
14. Les dépendances sont documentées.
15. Les appels circulaires sont évités.
16. Les fonctionnalités peuvent être désactivées.
17. Les services peuvent être déployés indépendamment.
18. Les données sensibles sont minimisées.
19. Les permissions sont vérifiées à chaque niveau.
20. Les flux sont corrélables.
21. Les erreurs partenaires sont isolées.
22. Le mode dégradé est prévu.
23. Les services possèdent un propriétaire.
24. Les modèles sont versionnés.
25. L’architecture peut évoluer progressivement.

---

# 42. Analytics

Événements possibles :

```text
platform_service_started
platform_service_stopped
platform_service_degraded
platform_dependency_failed
platform_flow_started
platform_flow_completed
platform_flow_failed
platform_country_activated
platform_tenant_created
platform_feature_enabled
platform_feature_disabled
platform_service_version_deployed
platform_architecture_change_approved
```

---

# 43. Tests

- tests de communication ;
- tests API Gateway ;
- tests d’authentification ;
- tests de permissions ;
- tests de domaines ;
- tests de flux ;
- tests d’événements ;
- tests de files ;
- tests d’idempotence ;
- tests de partenaires ;
- tests multi-pays ;
- tests multi-tenant ;
- tests de cache ;
- tests ledger ;
- tests de mode dégradé ;
- tests de feature flags ;
- tests de résilience ;
- tests d’observabilité ;
- tests de déploiement ;
- tests de reprise.

---

# 44. Critères d’acceptation

L’architecture globale est validée lorsque :

- toutes les applications sont identifiées ;
- tous les domaines sont identifiés ;
- les responsabilités sont séparées ;
- les sources de vérité sont définies ;
- les flux principaux sont documentés ;
- l’API Gateway centralise les entrées ;
- le ledger est isolé ;
- les communications synchrones et asynchrones sont définies ;
- les partenaires sont encapsulés ;
- les environnements sont séparés ;
- le multi-pays est prévu ;
- le multi-tenant est prévu ;
- les permissions sont intégrées ;
- les dépendances critiques sont identifiées ;
- le mode dégradé est défini ;
- l’observabilité est disponible ;
- le déploiement indépendant est possible ;
- les tests couvrent les principaux flux.
