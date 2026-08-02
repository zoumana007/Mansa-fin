# 25 — Architecture des intégrations partenaires, banques, Mobile Money, réseaux cartes et services externes de Mansa

## 1. Objet du document

Ce document définit l'architecture officielle des intégrations externes de Mansa.

Il couvre :

- les banques ;
- les établissements de monnaie électronique ;
- les opérateurs Mobile Money ;
- Visa ;
- Mastercard ;
- les processeurs de paiement ;
- les prestataires KYC/KYB ;
- les fournisseurs AML ;
- les services SMS ;
- les services e-mail ;
- les notifications Push ;
- les fournisseurs de taux de change ;
- les services gouvernementaux ;
- les APIs partenaires ;
- les webhooks ;
- les certificats ;
- les environnements ;
- les stratégies de reprise ;
- les contrats d'intégration.

L'objectif est de construire une plateforme capable d'intégrer facilement de nouveaux partenaires sans modifier le cœur métier.

---

# 2. Principes fondamentaux

## 2.1 Architecture découplée

Le code métier ne doit jamais dépendre directement d'un partenaire spécifique.

Toutes les intégrations passent par une couche d'abstraction.

---

## 2.2 Chaque partenaire est interchangeable

Le remplacement d'un partenaire doit nécessiter le moins de modifications possible.

Exemples :

- changement de fournisseur SMS ;
- changement de banque ;
- ajout d'un nouvel opérateur Mobile Money ;
- ajout d'un nouveau fournisseur KYC.

---

## 2.3 Aucun partenaire n'est une source de vérité unique

Les données critiques restent contrôlées par Mansa.

Exemples :

- ledger ;
- utilisateurs ;
- historique ;
- audit ;
- permissions.

---

## 2.4 Isolation des erreurs

Une panne chez un partenaire ne doit pas bloquer toute la plateforme.

Les intégrations utilisent :

- retries ;
- circuit breaker ;
- timeout ;
- fallback ;
- statut UNKNOWN ;
- files d'attente.

---

# 3. Architecture générale

```text
Applications
        │
 API Gateway
        │
Integration Service
        │
──────────────────────────────────────
│
├── Banking Connector
├── Mobile Money Connector
├── Card Network Connector
├── KYC Connector
├── AML Connector
├── FX Connector
├── SMS Connector
├── Email Connector
├── Push Connector
├── Government Connector
├── Merchant Connector
└── Generic REST Connector
```

---

# 4. Couche d'abstraction

Chaque connecteur expose une interface métier standardisée.

Exemple :

```text
authorizePayment()

capturePayment()

refundPayment()

checkStatus()

cancelPayment()
```

Le reste du backend ignore l'API spécifique du partenaire.

---

# 5. Types de partenaires

Catégories :

- banques ;
- Mobile Money ;
- réseaux cartes ;
- KYC ;
- KYB ;
- AML ;
- SMS ;
- e-mail ;
- Push ;
- signature électronique ;
- taux de change ;
- stockage documentaire ;
- services publics ;
- assurances ;
- partenaires commerciaux.

---

# 6. Environnements

Chaque partenaire peut disposer de plusieurs environnements :

- Sandbox ;
- Test ;
- Préproduction ;
- Production.

Les identifiants et certificats sont séparés par environnement.

---

# 7. Gestion des identifiants

Chaque intégration possède :

- Partner ID ;
- Client ID ;
- Secret ;
- Certificat ;
- Clé API ;
- Version ;
- Date d'expiration.

Les secrets sont stockés dans un gestionnaire sécurisé.

---

# 8. Authentification partenaire

Méthodes possibles :

- OAuth2 ;
- API Key ;
- JWT signé ;
- HMAC ;
- mTLS ;
- certificat client.

---

# 9. Rotation des secrets

Le système doit permettre :

- rotation automatique ;
- coexistence ancienne/nouvelle clé ;
- révocation ;
- audit ;
- alerte avant expiration.

---

# 10. Version des APIs partenaires

Chaque partenaire possède :

- version supportée ;
- version cible ;
- date de retrait ;
- historique.

Une migration doit être planifiée avant la fin de support.

---

# 11. Banking Connector

Fonctions possibles :

- ouverture de compte ;
- consultation ;
- virement ;
- règlement ;
- confirmation ;
- rapprochement ;
- rejet ;
- annulation.

---

# 12. Mobile Money Connector

Fonctions :

- paiement ;
- cash-in ;
- cash-out ;
- transfert ;
- confirmation ;
- vérification ;
- annulation ;
- rapprochement.

---

# 13. Card Network Connector

Fonctions :

- autorisation ;
- capture ;
- annulation ;
- remboursement ;
- tokenisation ;
- provisioning wallet ;
- consultation.

---

# 14. KYC Connector

Fonctions :

- vérification document ;
- OCR ;
- selfie ;
- preuve de vie ;
- contrôle fraude documentaire ;
- vérification identité.

---

# 15. AML Connector

Fonctions :

- sanctions ;
- PEP ;
- adverse media ;
- scoring ;
- surveillance continue.

---

# 16. Notification Connectors

SMS :

- OTP ;
- alertes ;
- notifications.

Email :

- reçus ;
- support ;
- sécurité.

Push :

- paiement ;
- promotions ;
- sécurité.

---

# 17. FX Connector

Fonctions :

- récupération des taux ;
- historique ;
- validation ;
- fournisseur ;
- date de validité.

---

# 18. Government Connector

Exemples :

- paiement d'amendes ;
- bourses ;
- taxes ;
- cartes étudiantes ;
- services administratifs.

---

# 19. Timeouts

Chaque partenaire possède :

- timeout connexion ;
- timeout lecture ;
- timeout global.

Les valeurs sont configurables.

---

# 20. Retry

Politique configurable :

- nombre maximal ;
- backoff exponentiel ;
- jitter ;
- erreurs réessayables.

---

# 21. Circuit Breaker

Le Circuit Breaker protège contre :

- partenaire indisponible ;
- latence excessive ;
- erreurs répétées.

États :

- Closed ;
- Open ;
- Half-Open.

---

# 22. Rate Limiting

Chaque partenaire peut avoir :

- limite par minute ;
- limite par heure ;
- limite journalière.

Le système adapte son débit.

---

# 23. Idempotence

Les appels critiques utilisent :

- idempotency key ;
- external reference ;
- correlation ID.

---

# 24. Journalisation

Chaque appel enregistre :

- partenaire ;
- endpoint ;
- requête (masquée si sensible) ;
- réponse ;
- durée ;
- statut ;
- erreur ;
- corrélation.

---

# 25. Webhooks

Les partenaires peuvent envoyer :

- confirmations ;
- annulations ;
- remboursements ;
- changements de statut.

Les webhooks doivent être :

- signés ;
- validés ;
- idempotents ;
- journalisés.

---

# 26. Réconciliation

Le rapprochement compare :

- ledger ;
- partenaire ;
- banque ;
- Mobile Money ;
- réseau carte.

Toute divergence crée une alerte.

---

# 27. Modèles

- Partner
- PartnerEnvironment
- PartnerCredential
- PartnerEndpoint
- PartnerCertificate
- PartnerCapability
- PartnerRequest
- PartnerResponse
- PartnerWebhook
- PartnerReconciliation
- PartnerIncident
- ExchangeRate
- PartnerAudit

---

# 28. Permissions

```text
partner.read
partner.manage
partner.credentials.rotate
partner.webhook.manage
partner.reconciliation.run
partner.audit.read
partner.incident.manage
```

---

# 29. API internes

```http
GET    /partners
GET    /partners/{id}

GET    /partners/{id}/health
GET    /partners/{id}/metrics

POST   /partners/{id}/rotate-secret
POST   /partners/{id}/test

GET    /partners/reconciliation
POST   /partners/reconciliation/run
```

---

# 30. Règles métier

1. Toutes les intégrations passent par l'Integration Service.
2. Aucun partenaire n'est directement appelé par les applications.
3. Les secrets sont stockés hors du code.
4. Les partenaires sont versionnés.
5. Les appels critiques sont idempotents.
6. Les retries sont limités.
7. Les Circuit Breakers protègent les partenaires.
8. Les webhooks sont signés.
9. Les rapprochements sont obligatoires pour les opérations financières.
10. Les environnements sont totalement séparés.
11. Les erreurs partenaires sont journalisées.
12. Les certificats sont surveillés.
13. Les taux de change sont datés.
14. Les intégrations sont testables individuellement.
15. Les permissions administratives sont contrôlées.

---

# 31. Analytics

```text
partner_request_started
partner_request_completed
partner_request_failed
partner_timeout
partner_retry
partner_circuit_open
partner_circuit_closed
partner_webhook_received
partner_reconciliation_completed
partner_secret_rotated
```

---

# 32. Tests

- tests Sandbox ;
- tests d'authentification ;
- tests OAuth ;
- tests mTLS ;
- tests timeout ;
- tests retry ;
- tests circuit breaker ;
- tests webhook ;
- tests rapprochement ;
- tests Mobile Money ;
- tests banques ;
- tests cartes ;
- tests FX ;
- tests KYC ;
- tests AML ;
- tests charge.

---

# 33. Critères d'acceptation

L'architecture des intégrations est validée lorsque :

- les partenaires sont isolés ;
- les secrets sont sécurisés ;
- les retries fonctionnent ;
- les Circuit Breakers sont actifs ;
- les webhooks sont validés ;
- les rapprochements fonctionnent ;
- les APIs partenaires sont versionnées ;
- les environnements sont séparés ;
- les métriques sont disponibles ;
- les tests sont validés.
