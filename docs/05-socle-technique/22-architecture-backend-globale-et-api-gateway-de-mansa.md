# 22 — Architecture Backend Globale et API Gateway de Mansa

## 1. Objet du document

Ce document définit l'architecture backend officielle de Mansa.

Il couvre :

- l'API Gateway ;
- les services métier ;
- les microservices ;
- les services partagés ;
- les APIs publiques ;
- les APIs internes ;
- les événements ;
- les workers ;
- les webhooks ;
- les tâches planifiées ;
- les connecteurs partenaires ;
- Jini ;
- les TPE ;
- les applications mobiles ;
- les sites web ;
- les intégrations gouvernementales.

L'objectif est de construire une plateforme :

- modulaire ;
- scalable ;
- hautement disponible ;
- sécurisée ;
- observable ;
- multi-pays ;
- multi-devises ;
- extensible.

---

# 2. Principes fondamentaux

## 2.1 Backend unique

Toutes les applications Mansa utilisent le même backend.

Applications concernées :

- Mansa Client ;
- Mansa Commerce ;
- Mansa TPE ;
- Mansa Admin Lite ;
- Mansa Hub ;
- Site public ;
- Site Professionnels ;
- Portail Admin.

---

## 2.2 API Gateway unique

Toutes les requêtes passent par l'API Gateway.

Elle centralise :

- authentification ;
- autorisation ;
- rate limiting ;
- routing ;
- validation ;
- observabilité ;
- corrélation ;
- audit ;
- versionning ;
- sécurité.

---

# 3. Architecture générale

```text
Applications
      │
API Gateway
      │
──────────────────────────────
│
├── Auth Service
├── User Service
├── Wallet Service
├── Ledger Service
├── Payment Service
├── Card Service
├── Merchant Service
├── TPE Service
├── Directory Service
├── Government Service
├── Notification Service
├── KYC Service
├── Fraud Service
├── Jini Service
├── Analytics Service
├── Support Service
├── Configuration Service
├── Audit Service
└── Integration Service
```

---

# 4. API Gateway

Responsabilités :

- authentification ;
- RBAC ;
- validation ;
- limitation de débit ;
- journalisation ;
- propagation des corrélations ;
- métriques ;
- gestion des versions ;
- gestion des erreurs ;
- routage.

---

# 5. Services métier

Chaque domaine possède son propre service.

Exemples :

- Wallet
- Payment
- Merchant
- Card
- Ledger
- KYC
- Notification
- Fraud
- Support
- Directory
- Government
- Analytics

Chaque service possède :

- API ;
- logique métier ;
- événements ;
- permissions ;
- tests ;
- métriques.

---

# 6. Communication

Communication synchrone :

- REST ;
- gRPC lorsque pertinent.

Communication asynchrone :

- Event Bus ;
- Files ;
- Webhooks.

---

# 7. API publiques

Les API publiques doivent être :

- documentées ;
- versionnées ;
- sécurisées ;
- limitées ;
- surveillées.

---

# 8. API internes

Les APIs internes ne sont accessibles qu'aux services autorisés.

Authentification :

- mTLS ;
- JWT Service ;
- Service Accounts.

---

# 9. Versionnement

Toutes les APIs utilisent :

```text
/api/v1
```

Les changements incompatibles nécessitent une nouvelle version.

---

# 10. Contrats

Les DTO doivent être :

- versionnés ;
- documentés ;
- compatibles ;
- testés.

---

# 11. Validation

Toutes les entrées sont validées :

- types ;
- formats ;
- tailles ;
- permissions ;
- règles métier.

---

# 12. Idempotence

Toutes les opérations critiques utilisent :

- Idempotency-Key ;
- Correlation-ID.

---

# 13. Services partagés

Services transverses :

- Auth
- Configuration
- Feature Flags
- Notifications
- Audit
- Logging
- Storage
- Monitoring

---

# 14. Workers

Les traitements longs utilisent des workers.

Exemples :

- génération PDF ;
- rapprochement ;
- notifications ;
- imports ;
- exports ;
- synchronisation partenaire.

---

# 15. Scheduler

Tâches planifiées :

- rapprochement ;
- purge ;
- sauvegardes ;
- expiration ;
- synchronisation ;
- statistiques.

---

# 16. Webhooks

Tous les webhooks doivent être :

- signés ;
- journalisés ;
- versionnés ;
- rejouables ;
- idempotents.

---

# 17. Intégrations

Connecteurs :

- banques ;
- Visa ;
- Mastercard ;
- Mobile Money ;
- État ;
- KYC ;
- SMS ;
- Email ;
- Push ;
- Change ;
- partenaires.

---

# 18. Gestion des erreurs

Format standard :

```json
{
  "code": "PAYMENT_FAILED",
  "message": "...",
  "correlationId": "...",
  "retryable": false
}
```

---

# 19. Observabilité

Chaque service expose :

- métriques ;
- traces ;
- logs ;
- health checks.

---

# 20. Sécurité

Protection :

- JWT ;
- OAuth2 ;
- RBAC ;
- MFA ;
- TLS ;
- chiffrement ;
- audit.

---

# 21. Résilience

Utiliser :

- Retry ;
- Circuit Breaker ;
- Bulkhead ;
- Timeout ;
- Saga ;
- Compensation.

---

# 22. Scalabilité

Le backend doit supporter :

- montée horizontale ;
- autoscaling ;
- multi-instances ;
- multi-régions.

---

# 23. Déploiement

Chaque service est déployable indépendamment.

---

# 24. Administration

Le portail Admin permet :

- consulter les services ;
- voir leur état ;
- consulter les versions ;
- consulter les métriques ;
- consulter les erreurs.

---

# 25. Permissions

Exemples :

```text
api.read
api.manage
service.deploy
service.restart
service.read.logs
service.health.read
```

---

# 26. API principales

Exemples :

```http
GET /health

GET /services

GET /metrics

GET /status

GET /version

POST /deploy
```

---

# 27. Modèles

- ApiService
- ApiRoute
- GatewayRoute
- ServiceInstance
- ServiceHealth
- ServiceDependency
- ApiVersion
- ApiContract
- Worker
- ScheduledTask
- WebhookEndpoint
- IntegrationConnector

---

# 28. Règles métier

1. Toute requête passe par l'API Gateway.
2. Les services sont indépendants.
3. Les APIs sont versionnées.
4. Les communications critiques sont sécurisées.
5. Les traitements longs utilisent des workers.
6. Les webhooks sont signés.
7. Les services sont observables.
8. Les erreurs sont normalisées.
9. Les opérations critiques sont idempotentes.
10. Les services sont déployables indépendamment.
11. Les intégrations sont isolées.
12. Les permissions sont contrôlées.
13. Les événements sont auditables.
14. Les métriques sont disponibles.
15. Les tests couvrent tous les services.

---

# 29. Analytics

```text
service_started
service_stopped
service_scaled
api_request_received
api_request_failed
worker_started
worker_completed
webhook_received
integration_timeout
gateway_rate_limit
```

---

# 30. Tests

- tests API ;
- tests Gateway ;
- tests services ;
- tests intégrations ;
- tests workers ;
- tests webhooks ;
- tests charge ;
- tests sécurité ;
- tests résilience ;
- tests observabilité.

---

# 31. Critères d'acceptation

Le backend est validé lorsque :

- toutes les applications utilisent l'API Gateway ;
- les services sont indépendants ;
- les APIs sont versionnées ;
- les workers fonctionnent ;
- les webhooks sont sécurisés ;
- les intégrations sont isolées ;
- les métriques sont disponibles ;
- les logs sont corrélés ;
- les tests sont validés ;
- le backend peut évoluer sans interrompre les autres services.
