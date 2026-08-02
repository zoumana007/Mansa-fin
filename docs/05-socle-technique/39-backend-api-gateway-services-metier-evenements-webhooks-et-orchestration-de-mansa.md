# 39 — Backend, API Gateway, services métier, événements, webhooks et orchestration de Mansa

## 1. Objet du document

Ce document définit l’architecture officielle du backend de Mansa.

Il couvre :

- l’API Gateway ;
- les services métier ;
- les modules backend ;
- les APIs internes ;
- les APIs publiques ;
- l’authentification ;
- l’autorisation ;
- les événements ;
- les files de messages ;
- les workers ;
- les webhooks ;
- les sagas ;
- les transactions distribuées ;
- l’idempotence ;
- les retries ;
- les timeouts ;
- les erreurs ;
- les contrats ;
- le versionnement ;
- les modèles de données ;
- les dépendances ;
- les tests ;
- l’observabilité ;
- la résilience ;
- la sécurité ;
- le multi-pays ;
- le multi-tenant.

L’objectif est de fournir un backend :

- modulaire ;
- sécurisé ;
- évolutif ;
- testable ;
- observable ;
- résilient ;
- compatible avec plusieurs applications ;
- indépendant des fournisseurs externes ;
- capable de traiter des opérations financières critiques ;
- prêt pour plusieurs millions d’utilisateurs.

---

# 2. Principes fondamentaux

## 2.1 Le backend porte la logique métier officielle

Les applications clientes ne doivent pas décider seules :

- des frais ;
- des plafonds ;
- des statuts financiers ;
- des permissions ;
- des remboursements ;
- des validations KYC ;
- des règles fraude ;
- des écritures ledger ;
- des règles pays ;
- des règles partenaires.

La logique officielle doit être exécutée côté backend.

---

## 2.2 Architecture par domaines

Le backend doit être structuré par domaines fonctionnels.

Exemples :

```text
auth
identity
customer
wallet
ledger
payments
transfers
cards
merchant
terminal
pricing
compliance
fraud
support
notifications
documents
public-services
analytics
integrations
jini
```

Chaque domaine doit rester aussi autonome que possible.

---

## 2.3 Le backend ne dépend pas directement des applications

Les services métier ne doivent pas contenir de logique spécifique à une seule interface sauf nécessité justifiée.

Ils doivent pouvoir servir :

- l’application Client ;
- l’application Commerce ;
- l’application TPE ;
- l’application Admin Lite ;
- le Hub ;
- le portail Admin ;
- les partenaires API ;
- les institutions.

---

## 2.4 Aucun accès direct à la base par les applications

Toutes les lectures et écritures passent par :

- l’API Gateway ;
- un service métier ;
- des permissions ;
- une validation ;
- un audit ;
- un contrat versionné.

---

## 2.5 Les opérations financières doivent être idempotentes

Un même appel répété ne doit pas créer plusieurs opérations financières identiques.

Chaque opération critique doit utiliser :

- une clé d’idempotence ;
- une référence métier ;
- une corrélation ;
- un statut ;
- un historique.

---

# 3. Organisation du backend

Structure recommandée :

```text
apps/
└── api-gateway/

packages/
├── auth/
├── identity/
├── customer/
├── wallet/
├── ledger/
├── payments/
├── transfers/
├── cards/
├── merchant/
├── terminal/
├── pricing/
├── compliance/
├── fraud/
├── notifications/
├── documents/
├── support/
├── public-services/
├── analytics/
├── integrations/
├── jini/
├── permissions/
├── events/
├── observability/
├── security/
└── shared/
```

---

# 4. API Gateway

L’API Gateway constitue le point d’entrée officiel des clients.

Il doit gérer :

- authentification ;
- vérification des tokens ;
- autorisation ;
- routage ;
- versionnement ;
- validation des requêtes ;
- rate limiting ;
- quotas ;
- corrélation ;
- logs ;
- métriques ;
- protection contre les abus ;
- gestion des erreurs ;
- compatibilité multi-applications.

---

# 5. Types d’APIs

Mansa doit distinguer :

- API Client ;
- API Commerce ;
- API TPE ;
- API Admin Lite ;
- API Admin Web ;
- API Hub ;
- API publique ;
- API partenaire ;
- API institutionnelle ;
- API interne.

---

# 6. Versionnement

Les APIs doivent être versionnées.

Exemple :

```http
/api/v1/payments
/api/v1/cards
/api/v1/merchants
```

Le versionnement doit permettre :

- coexistence temporaire ;
- migration ;
- dépréciation ;
- compatibilité ;
- documentation ;
- suivi des consommateurs.

---

# 7. Contrats d’API

Chaque endpoint doit définir :

- méthode ;
- route ;
- description ;
- authentification ;
- permission ;
- paramètres ;
- corps ;
- réponse ;
- erreurs ;
- idempotence ;
- pagination ;
- limites ;
- version ;
- exemples.

---

# 8. Validation des entrées

Toute entrée doit être validée.

Contrôles possibles :

- type ;
- format ;
- longueur ;
- valeur minimale ;
- valeur maximale ;
- enum ;
- devise ;
- pays ;
- référence ;
- relation ;
- permissions ;
- cohérence métier.

---

# 9. Validation métier

Une requête techniquement valide peut rester interdite.

Exemples :

- remboursement supérieur au montant disponible ;
- transfert au-dessus du plafond ;
- carte bloquée ;
- commerçant suspendu ;
- TPE non autorisé ;
- utilisateur KYC insuffisant ;
- partenaire indisponible ;
- pays non activé.

---

# 10. Authentification

Le backend doit gérer :

- access token ;
- refresh token ;
- sessions ;
- MFA ;
- passkeys ;
- appareils ;
- certificats TPE ;
- comptes de service ;
- clés API ;
- OAuth2 ;
- mTLS.

---

# 11. Autorisation

Chaque requête doit vérifier :

- identité ;
- rôle ;
- permission ;
- tenant ;
- pays ;
- organisation ;
- appareil ;
- niveau de risque ;
- statut de la ressource ;
- montant ;
- contexte.

---

# 12. RBAC

Le RBAC utilise :

- rôles ;
- permissions ;
- groupes ;
- portées ;
- héritage ;
- restrictions.

Exemples :

```text
customer.read
payment.create
payment.refund
merchant.manage
terminal.activate
support.ticket.read
fraud.case.review
```

---

# 13. ABAC

L’ABAC peut utiliser :

- pays ;
- organisation ;
- montant ;
- niveau KYC ;
- heure ;
- appareil ;
- risque ;
- type de transaction ;
- établissement ;
- partenaire ;
- environnement.

---

# 14. Middleware

Le backend peut utiliser des middlewares pour :

- authentification ;
- corrélation ;
- logs ;
- rate limiting ;
- localisation ;
- version ;
- contexte tenant ;
- sécurité ;
- audit ;
- métriques.

---

# 15. Contexte de requête

Chaque requête doit pouvoir transporter :

```text
requestId
correlationId
userId
sessionId
deviceId
tenantId
organizationId
countryId
applicationId
environment
locale
permissions
```

---

# 16. Domain Services

Un service de domaine porte les règles métier.

Exemple :

```text
PaymentService
TransferService
CardService
MerchantService
FraudEvaluationService
```

Il ne doit pas dépendre directement du transport HTTP.

---

# 17. Application Services

Les services applicatifs orchestrent :

- validations ;
- appels de domaine ;
- persistence ;
- événements ;
- partenaires ;
- audit ;
- notifications.

---

# 18. Repositories

Les repositories isolent l’accès aux données.

Ils doivent exposer des méthodes métier.

Exemple :

```text
findPaymentById()
savePayment()
findWalletByOwner()
createLedgerEntry()
```

---

# 19. Adapters

Les adaptateurs connectent le métier aux dépendances externes.

Exemples :

- banque ;
- Mobile Money ;
- réseau carte ;
- fournisseur SMS ;
- fournisseur KYC ;
- stockage ;
- moteur IA.

---

# 20. Ports et adaptateurs

Le cœur métier doit dépendre d’interfaces.

Exemple :

```text
PaymentProvider
NotificationProvider
KycProvider
StorageProvider
ExchangeRateProvider
```

Les implémentations partenaires restent remplaçables.

---

# 21. Communication synchrone

À utiliser lorsque la réponse immédiate est nécessaire.

Exemples :

- connexion ;
- consultation de solde ;
- calcul de frais ;
- vérification de limite ;
- autorisation ;
- lecture de configuration.

---

# 22. Communication asynchrone

À utiliser pour :

- notifications ;
- rapports ;
- rapprochement ;
- documents ;
- traitement KYC ;
- analytics ;
- webhooks ;
- synchronisation ;
- tâches lourdes.

---

# 23. Message Broker

Le broker doit gérer :

- publication ;
- consommation ;
- persistance ;
- retries ;
- dead-letter queue ;
- ordre lorsque nécessaire ;
- duplication ;
- monitoring ;
- sécurité.

---

# 24. Événements

Chaque événement doit contenir :

```json
{
  "eventId": "evt_123",
  "eventType": "payment.completed",
  "eventVersion": 1,
  "occurredAt": "2026-08-02T12:00:00Z",
  "correlationId": "cor_123",
  "countryId": "ML",
  "tenantId": "tenant_123",
  "data": {}
}
```

---

# 25. Versionnement des événements

Les événements doivent être versionnés.

Une nouvelle version ne doit pas casser les consommateurs existants sans période de transition.

---

# 26. Outbox Pattern

Les événements métier doivent être publiés de manière fiable.

Le pattern Outbox permet :

- d’enregistrer l’opération ;
- d’enregistrer l’événement ;
- dans la même transaction ;
- puis de publier l’événement.

---

# 27. Inbox Pattern

Le pattern Inbox permet de détecter les événements déjà consommés.

Il protège contre :

- duplication ;
- rejeu ;
- retries ;
- livraison au moins une fois.

---

# 28. Idempotence

Chaque opération critique doit enregistrer :

- idempotency key ;
- endpoint ;
- utilisateur ;
- résultat ;
- statut ;
- date ;
- expiration ;
- réponse associée.

---

# 29. Timeouts

Chaque appel doit avoir un timeout explicite.

Catégories :

- connexion ;
- lecture ;
- global ;
- partenaire ;
- base ;
- cache ;
- file ;
- IA.

---

# 30. Retry

Le retry doit être limité et contrôlé.

Il doit définir :

- erreurs réessayables ;
- nombre maximal ;
- backoff ;
- jitter ;
- délai ;
- idempotence ;
- abandon ;
- dead-letter queue.

---

# 31. Circuit Breaker

Le Circuit Breaker doit protéger contre :

- panne partenaire ;
- latence ;
- erreurs répétées ;
- saturation ;
- dépendance instable.

États :

- CLOSED ;
- OPEN ;
- HALF_OPEN.

---

# 32. Bulkhead

Le Bulkhead permet d’isoler :

- partenaires ;
- workers ;
- files ;
- pays ;
- services ;
- charges critiques.

Une panne locale ne doit pas épuiser toutes les ressources.

---

# 33. Saga

Une saga orchestre une opération répartie sur plusieurs services.

Exemples :

- ouverture de compte ;
- paiement ;
- remboursement ;
- activation commerçant ;
- émission de carte ;
- règlement ;
- service public.

---

# 34. Étapes d’une saga

Exemple paiement :

```text
1. création de la demande
2. calcul des frais
3. évaluation fraude
4. réservation ledger
5. appel partenaire
6. confirmation
7. finalisation ledger
8. notification
9. rapprochement
```

---

# 35. Compensation

Chaque étape importante doit définir une compensation.

Exemples :

- libérer une réservation ;
- annuler une autorisation ;
- restaurer un statut ;
- créer une contre-écriture ;
- arrêter une livraison ;
- désactiver un terminal.

---

# 36. Statuts de saga

Exemples :

- CREATED ;
- RUNNING ;
- WAITING ;
- COMPLETED ;
- COMPENSATING ;
- COMPENSATED ;
- FAILED ;
- MANUAL_REVIEW_REQUIRED.

---

# 37. Transactions distribuées

Mansa doit éviter les transactions distribuées fortes entre services lorsque possible.

Préférer :

- sagas ;
- événements ;
- idempotence ;
- compensations ;
- rapprochement ;
- cohérence éventuelle contrôlée.

---

# 38. Cohérence forte

À privilégier pour :

- ledger ;
- réservation de fonds ;
- plafonds critiques ;
- permissions ;
- état financier officiel.

---

# 39. Cohérence éventuelle

Acceptable pour :

- analytics ;
- notifications ;
- recherche ;
- rapports ;
- annuaire ;
- dashboards ;
- documents secondaires.

---

# 40. Webhooks entrants

Les webhooks reçus doivent être :

- authentifiés ;
- signés ;
- horodatés ;
- idempotents ;
- validés ;
- journalisés ;
- associés à une corrélation ;
- traités rapidement ;
- mis en file si nécessaire.

---

# 41. Webhooks sortants

Les webhooks envoyés doivent gérer :

- signature ;
- version ;
- idempotence ;
- retry ;
- backoff ;
- statut ;
- logs ;
- désactivation ;
- secret ;
- rotation ;
- dead-letter queue.

---

# 42. Statuts de webhook

Exemples :

- PENDING ;
- SENT ;
- DELIVERED ;
- RETRYING ;
- FAILED ;
- DISABLED ;
- EXPIRED.

---

# 43. Validation de signature

Le système doit vérifier :

- algorithme ;
- secret ;
- certificat ;
- timestamp ;
- nonce ;
- contenu ;
- version.

---

# 44. API publiques

Les APIs publiques doivent avoir :

- documentation ;
- authentification ;
- quotas ;
- scopes ;
- sandbox ;
- version ;
- support ;
- monitoring ;
- conditions d’utilisation ;
- audit.

---

# 45. Comptes de service

Chaque intégration doit utiliser un compte distinct.

Un compte de service doit avoir :

- identifiant ;
- organisation ;
- scopes ;
- environnement ;
- date d’expiration ;
- secret ;
- rotation ;
- statut ;
- audit.

---

# 46. Rate Limiting

Le rate limiting doit pouvoir s’appliquer par :

- IP ;
- utilisateur ;
- appareil ;
- token ;
- compte de service ;
- endpoint ;
- pays ;
- tenant ;
- partenaire.

---

# 47. Quotas

Les quotas peuvent limiter :

- appels par minute ;
- appels par jour ;
- transactions ;
- exports ;
- webhooks ;
- requêtes IA ;
- documents ;
- recherches.

---

# 48. Pagination

Toute liste importante doit utiliser une pagination.

Options :

- offset ;
- cursor ;
- keyset.

Pour les gros volumes, privilégier une pagination stable par curseur.

---

# 49. Tri et filtrage

Les filtres doivent être :

- documentés ;
- limités ;
- validés ;
- indexés ;
- compatibles avec les permissions.

---

# 50. Recherche

Les recherches administratives sensibles doivent :

- appliquer le tenant ;
- appliquer le pays ;
- appliquer les permissions ;
- masquer les données ;
- être auditées.

---

# 51. Gestion des erreurs

Les erreurs doivent être standardisées.

Exemple :

```json
{
  "error": {
    "code": "PAYMENT_LIMIT_EXCEEDED",
    "message": "Le plafond autorisé est dépassé.",
    "requestId": "req_123",
    "details": {}
  }
}
```

---

# 52. Catégories d’erreurs

- validation ;
- authentification ;
- autorisation ;
- ressource absente ;
- conflit ;
- limite ;
- partenaire ;
- timeout ;
- fraude ;
- conformité ;
- interne ;
- indisponibilité.

---

# 53. Codes d’erreur

Les codes doivent être :

- stables ;
- documentés ;
- traduisibles ;
- indépendants du message ;
- compatibles avec les applications.

---

# 54. Messages d’erreur

Les messages utilisateurs ne doivent pas exposer :

- stack trace ;
- secret ;
- structure interne ;
- règle fraude détaillée ;
- donnée sensible ;
- information d’un autre tenant.

---

# 55. Logs

Les logs doivent être :

- structurés ;
- corrélés ;
- horodatés ;
- filtrés ;
- contextualisés ;
- centralisés ;
- protégés.

---

# 56. Données interdites dans les logs

- mot de passe ;
- OTP ;
- PIN ;
- CVV ;
- secret ;
- token complet ;
- numéro complet de carte ;
- document d’identité complet ;
- donnée biométrique brute.

---

# 57. Traces

Les traces doivent permettre de suivre :

- l’API Gateway ;
- le service ;
- la base ;
- la file ;
- le worker ;
- le partenaire ;
- le webhook ;
- le ledger ;
- la notification.

---

# 58. Métriques

Exemples :

```text
api_request_total
api_request_duration
api_error_total
payment_created_total
payment_failed_total
queue_depth
webhook_retry_total
partner_timeout_total
database_query_duration
```

---

# 59. Health Checks

Chaque service doit exposer :

- liveness ;
- readiness ;
- version ;
- dépendances ;
- statut partiel ;
- build ;
- environnement.

---

# 60. Sécurité

Le backend doit appliquer :

- chiffrement TLS ;
- secrets hors code ;
- permissions minimales ;
- validation stricte ;
- protection contre les injections ;
- rate limiting ;
- WAF ;
- mTLS si nécessaire ;
- audit ;
- rotation des clés ;
- segmentation réseau.

---

# 61. Protection contre les injections

Le backend doit se protéger contre :

- SQL Injection ;
- NoSQL Injection ;
- Command Injection ;
- SSRF ;
- Path Traversal ;
- Header Injection ;
- Template Injection ;
- désérialisation dangereuse.

---

# 62. Validation des fichiers

Les fichiers reçus doivent être contrôlés par :

- taille ;
- type ;
- extension ;
- contenu ;
- antivirus ;
- hash ;
- métadonnées ;
- stockage isolé.

---

# 63. Multi-pays

Chaque requête doit pouvoir déterminer :

- pays actif ;
- devise ;
- langue ;
- partenaires ;
- frais ;
- limites ;
- règles KYC ;
- règles réglementaires ;
- fonctionnalités disponibles.

---

# 64. Multi-tenant

Chaque accès doit vérifier :

- tenant ;
- organisation ;
- établissement ;
- utilisateur ;
- rôle ;
- portée ;
- pays.

Aucune requête ne doit retourner des données d’un autre tenant.

---

# 65. Configuration

Les configurations doivent être externalisées.

Elles peuvent varier par :

- pays ;
- environnement ;
- partenaire ;
- application ;
- tenant ;
- version ;
- segment.

---

# 66. Feature Flags

Le backend doit vérifier les feature flags avant d’exécuter une fonctionnalité.

Exemples :

- cartes virtuelles ;
- paiement sans contact ;
- service public ;
- Jini ;
- cash-out ;
- transfert international.

---

# 67. Mode maintenance

Le backend doit pouvoir activer :

- maintenance globale ;
- maintenance par service ;
- maintenance par pays ;
- maintenance par partenaire ;
- lecture seule ;
- blocage des paiements ;
- blocage des inscriptions.

---

# 68. Workers

Les workers doivent traiter :

- événements ;
- notifications ;
- rapports ;
- documents ;
- synchronisations ;
- webhooks ;
- rapprochements ;
- tâches planifiées.

---

# 69. Tâches planifiées

Exemples :

- rapprochement quotidien ;
- expiration de session ;
- re-KYC ;
- renouvellement de certificat ;
- archivage ;
- rétention ;
- relance ;
- vérification partenaire ;
- clôture de période.

---

# 70. Verrouillage

Les tâches critiques doivent utiliser :

- verrou distribué ;
- leader election ;
- idempotence ;
- statut en base ;
- lease ;
- expiration.

---

# 71. Dead-Letter Queue

Une DLQ doit recevoir :

- messages invalides ;
- retries épuisés ;
- erreurs persistantes ;
- événements incompatibles ;
- webhooks non livrés.

---

# 72. Rejeu

Le rejeu doit être :

- autorisé ;
- limité ;
- idempotent ;
- audité ;
- lié à une raison ;
- supervisé.

---

# 73. Administration technique

Le portail Admin doit pouvoir afficher :

- services ;
- versions ;
- santé ;
- erreurs ;
- files ;
- jobs ;
- webhooks ;
- partenaires ;
- retries ;
- DLQ ;
- sagas ;
- incidents ;
- métriques.

---

# 74. Permissions

Exemples :

```text
backend.service.read
backend.health.read
backend.queue.read
backend.queue.replay
backend.webhook.read
backend.webhook.retry
backend.saga.read
backend.saga.resume
backend.job.read
backend.job.run
backend.configuration.read
backend.audit.read
```

---

# 75. Actions critiques

Doivent être protégées :

- rejeu d’un message financier ;
- reprise d’une saga ;
- relance d’un webhook ;
- modification d’une configuration ;
- purge d’une file ;
- arrêt d’un worker ;
- bascule de partenaire ;
- suppression d’une DLQ ;
- changement de permission.

---

# 76. Double validation

Peut être exigée pour :

- rejeu financier massif ;
- reprise de saga critique ;
- purge de file ;
- modification de configuration production ;
- désactivation d’un contrôle ;
- bascule globale ;
- correction manuelle d’un statut financier.

---

# 77. Modèles

- ApiClient
- ApiCredential
- ApiScope
- ApiRequest
- ApiResponse
- ApiError
- IdempotencyRecord
- DomainCommand
- DomainEvent
- EventOutbox
- EventInbox
- MessageQueue
- MessageDelivery
- DeadLetterMessage
- SagaExecution
- SagaStep
- WebhookEndpoint
- WebhookDelivery
- ServiceHealth
- ScheduledJob
- BackendConfiguration
- BackendAudit

---

# 78. Règles métier

1. Toute requête passe par l’API Gateway.
2. Toute entrée est validée.
3. Toute opération critique est idempotente.
4. Toute permission est vérifiée côté backend.
5. Les applications ne décident pas des règles financières.
6. Les domaines sont séparés.
7. Les partenaires passent par des adaptateurs.
8. Les événements sont versionnés.
9. Les événements critiques utilisent l’Outbox.
10. Les consommateurs utilisent l’Inbox lorsque nécessaire.
11. Les retries sont limités.
12. Les timeouts sont explicites.
13. Les Circuit Breakers protègent les dépendances.
14. Les opérations distribuées utilisent des sagas.
15. Les compensations sont documentées.
16. Les webhooks sont signés.
17. Les erreurs sont standardisées.
18. Les logs sont structurés.
19. Les données sensibles ne figurent pas dans les logs.
20. Les files critiques sont surveillées.
21. Les DLQ sont traitables.
22. Les rejouements sont audités.
23. Les configurations sont externalisées.
24. Les tenants sont isolés.
25. Les services sont observables et testables.

---

# 79. Analytics

Événements possibles :

```text
backend_request_received
backend_request_completed
backend_request_failed
backend_idempotency_hit
backend_event_published
backend_event_consumed
backend_event_failed
backend_saga_started
backend_saga_completed
backend_saga_compensated
backend_webhook_received
backend_webhook_delivered
backend_webhook_failed
backend_dlq_message_created
backend_dlq_message_replayed
backend_circuit_opened
backend_partner_switched
```

---

# 80. Tests

- tests de validation ;
- tests d’authentification ;
- tests d’autorisation ;
- tests RBAC ;
- tests ABAC ;
- tests d’idempotence ;
- tests d’événements ;
- tests Outbox ;
- tests Inbox ;
- tests de retry ;
- tests de timeout ;
- tests Circuit Breaker ;
- tests de saga ;
- tests de compensation ;
- tests de webhook ;
- tests de signature ;
- tests de file ;
- tests de DLQ ;
- tests de rejeu ;
- tests multi-pays ;
- tests multi-tenant ;
- tests de sécurité ;
- tests de performance ;
- tests d’observabilité ;
- tests de mode dégradé.

---

# 81. Critères d’acceptation

Le backend est validé lorsque :

- l’API Gateway centralise les entrées ;
- les domaines sont clairement séparés ;
- les contrats d’API sont documentés ;
- les entrées sont validées ;
- les permissions sont vérifiées ;
- les opérations critiques sont idempotentes ;
- les événements sont versionnés ;
- les Outbox et Inbox sont disponibles ;
- les sagas gèrent les opérations distribuées ;
- les compensations sont définies ;
- les partenaires sont encapsulés ;
- les webhooks sont sécurisés ;
- les erreurs sont standardisées ;
- les logs et traces sont disponibles ;
- les données sensibles sont protégées ;
- les files et workers sont surveillés ;
- les DLQ sont administrables ;
- le multi-pays et le multi-tenant sont pris en charge ;
- les actions critiques sont protégées ;
- les tests couvrent les principaux scénarios.
