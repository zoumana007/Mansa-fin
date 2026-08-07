# 102 — Open Banking et agrégation de comptes Mansa : consentements, connexions bancaires, agrégation, initiation de paiement, sécurité, administration et reporting

## 1. Objet du document

Ce document définit le cahier des charges complet du module **Open Banking et agrégation de comptes Mansa**.

Le module doit permettre de connecter des comptes financiers externes, agréger leurs données et, lorsque le cadre réglementaire et les partenaires le permettent, initier des paiements depuis ces comptes via des prestataires autorisés.

Mansa ne doit jamais se présenter comme banque teneuse de compte, prestataire d’information sur compte ou prestataire d’initiation de paiement lorsque ces rôles exigent un agrément qu’elle ne détient pas.

---

## 2. Principe général

```text
Choix d’un établissement
→ Consentement explicite
→ Redirection ou authentification sécurisée
→ Connexion partenaire
→ Récupération des comptes autorisés
→ Synchronisation des soldes et transactions
→ Catégorisation et usages Mansa
→ Renouvellement ou révocation du consentement
```

Pour l’initiation de paiement :

```text
Création de l’ordre
→ Vérification du bénéficiaire et du montant
→ Authentification forte si requise
→ Transmission au partenaire
→ Suivi du statut
→ Confirmation finale
→ Réconciliation
```

---

## 3. Positionnement dans Mansa

Intégrations : Identity, KYC/KYB, Wallet, Ledger, Paiements, Budget, Trésorerie, Jini, Notifications, RBAC, Audit, Reporting, Feature Flags et partenaires bancaires/Open Banking.

---

## 4. Utilisateurs cibles

- particuliers ;
- commerçants ;
- indépendants ;
- PME ;
- grandes entreprises ;
- organisations autorisées.

---

## 5. Cas d’usage

- vue consolidée de plusieurs comptes ;
- analyse de dépenses ;
- budget automatique ;
- détection de revenus ;
- rapprochement de trésorerie ;
- préparation de paiements ;
- vérification de compte ;
- preuve de solde lorsque juridiquement autorisée ;
- scoring uniquement sous base légale distincte ;
- initiation de paiement via partenaire autorisé.

---

## 6. Entité FinancialInstitution

Champs : identifiant, nom, pays, logo, statut, capacités, méthodes d’authentification, devises, horaires, SLA, environnement et partenaire technique.

---

## 7. Capacités d’un établissement

```text
ACCOUNT_INFORMATION
BALANCES
TRANSACTIONS
BENEFICIARIES
PAYMENT_INITIATION
ACCOUNT_VERIFICATION
STATEMENTS
```

---

## 8. Entité Connection

Une connexion doit contenir utilisateur/organisation, établissement, partenaire, scopes, dates, statut, consentement associé, dernière synchronisation et références techniques non sensibles.

---

## 9. Statuts de connexion

```text
PENDING
ACTIVE
ACTION_REQUIRED
EXPIRED
REVOKED
ERROR
SUSPENDED
DELETED
```

---

## 10. Consentement

Chaque connexion exige un consentement explicite précisant finalité, comptes concernés, données accessibles, durée, partenaire, révocation et version du texte.

---

## 11. Scopes

Exemples : comptes, soldes, transactions, identité de compte, bénéficiaires, initiation de paiement. Le système doit demander uniquement les scopes nécessaires.

---

## 12. Consentement granulaire

L’utilisateur doit pouvoir sélectionner les comptes et usages autorisés lorsqu’un partenaire le permet.

---

## 13. Durée du consentement

Elle doit être fournie par le partenaire et la réglementation. Toute expiration nécessite renouvellement ou reconnexion.

---

## 14. Révocation

Une révocation utilisateur doit désactiver immédiatement les synchronisations futures et supprimer ou invalider les jetons partenaires associés.

---

## 15. Authentification bancaire

Mansa ne doit jamais collecter directement les identifiants bancaires lorsqu’un flux OAuth, redirect, decoupled ou équivalent est disponible.

---

## 16. Secrets et jetons

Les jetons partenaires doivent être chiffrés, stockés dans un gestionnaire de secrets ou coffre applicatif sécurisé et jamais journalisés en clair.

---

## 17. MFA et SCA

Les authentifications fortes imposées par la banque ou la réglementation doivent être respectées sans tentative de contournement.

---

## 18. Comptes externes

Chaque compte externe doit avoir identifiant interne Mansa, identifiant partenaire, établissement, type, devise, nom masqué, propriétaire et statut.

---

## 19. Types de comptes

- compte courant ;
- épargne ;
- compte professionnel ;
- carte de paiement exposée via API ;
- compte de paiement ;
- compte partenaire personnalisé.

---

## 20. Solde

Le module doit distinguer solde comptable, solde disponible, solde réservé et date/heure de fraîcheur lorsque ces données existent.

---

## 21. Fraîcheur des données

Toute donnée externe doit afficher ou stocker son timestamp de récupération et son niveau de fraîcheur.

---

## 22. Transactions

Champs minimum : identifiant externe, compte, date de valeur, date d’opération, montant, devise, sens, libellé, statut et référence.

---

## 23. Transactions pending

Les opérations en attente doivent être distinguées des opérations comptabilisées afin d’éviter le double comptage.

---

## 24. Déduplication

Les transactions doivent être dédupliquées par identifiants partenaires, références, montants, dates et règles adaptatives.

---

## 25. Mise à jour d’une transaction

Une transaction pending peut devenir booked sans être créée une seconde fois.

---

## 26. Suppression ou correction partenaire

Toute correction reçue doit être historisée et ne jamais modifier silencieusement l’historique local utilisé par un audit.

---

## 27. Synchronisation

Le moteur doit supporter synchronisation initiale, incrémentale, manuelle, périodique et événementielle.

---

## 28. Pagination

Les adaptateurs doivent gérer pagination, curseurs, fenêtres de dates et limites partenaires sans perte de données.

---

## 29. Rate limits

Chaque connecteur doit respecter les quotas partenaires et utiliser backoff, cache et scheduling adaptés.

---

## 30. Webhooks partenaires

Les webhooks doivent être signés, validés, dédupliqués et traités de manière idempotente.

---

## 31. Offline

L’application peut afficher le dernier état connu avec indication explicite de la date de synchronisation.

---

## 32. Catégorisation

Les transactions externes peuvent alimenter le moteur Budget et Jini sans modifier leur nature comptable d’origine.

---

## 33. Données de budget

Les catégories Mansa sont des métadonnées locales et ne doivent pas modifier les libellés ou données sources externes.

---

## 34. Multi-devises

Les comptes gardent leur devise source. Toute consolidation de reporting utilise des taux horodatés et doit être marquée indicative.

---

## 35. Agrégation personnelle

Un utilisateur peut voir plusieurs établissements dans un même dashboard sans fusionner les soldes juridiquement.

---

## 36. Agrégation entreprise

Une organisation peut connecter plusieurs comptes avec RBAC, entités, centres de coût et délégations.

---

## 37. Initiation de paiement

Elle ne doit être disponible que pour les corridors, établissements, pays et partenaires autorisés.

---

## 38. Entité PaymentInitiation

Champs : compte débité, bénéficiaire, montant, devise, référence, partenaire, statut, consentement, authentification, timestamps et audit.

---

## 39. Statuts de paiement

```text
DRAFT
PENDING_AUTHORIZATION
AUTHORIZED
SUBMITTED
IN_PROGRESS
ACCEPTED
SETTLED
REJECTED
FAILED
CANCELLED
UNKNOWN
```

---

## 40. Idempotence paiement

Chaque ordre doit avoir une clé idempotente stable empêchant toute double soumission.

---

## 41. Beneficiary validation

Le bénéficiaire doit être validé selon les capacités locales : IBAN, numéro de compte, nom, banque, Mobile Money ou autre identifiant.

---

## 42. Point d’irrévocabilité

L’annulation n’est possible que tant que le rail et le partenaire l’autorisent.

---

## 43. Timeout

Un timeout de réponse ne doit jamais être transformé directement en échec final ; le statut doit être vérifié auprès du partenaire.

---

## 44. Ledger

Le Ledger Mansa ne doit enregistrer une écriture financière interne que si des fonds Mansa sont impliqués. Une simple initiation externe est tracée séparément comme instruction externe.

---

## 45. Réconciliation

Comparer ordres Mansa, statuts partenaires, références bancaires, événements et éventuelles écritures internes.

---

## 46. Vérification de propriété de compte

Lorsque disponible, la vérification de nom/compte doit produire résultat, source, date et niveau de confiance.

---

## 47. Jini

Jini peut expliquer les comptes, transactions et tendances, mais ne doit jamais connecter un établissement, renouveler un consentement ou initier un paiement sans action utilisateur requise.

---

## 48. Notifications

Connexion réussie, consentement expirant, reconnexion requise, établissement indisponible, synchronisation échouée, paiement soumis, paiement rejeté et activité inhabituelle.

---

## 49. API

```text
GET /open-banking/institutions
POST /open-banking/connections
GET /open-banking/connections
DELETE /open-banking/connections/:id
GET /open-banking/accounts
GET /open-banking/accounts/:id/transactions
POST /open-banking/payments
GET /open-banking/payments/:id
```

---

## 50. Webhooks Mansa

open_banking.connection.active, open_banking.connection.action_required, account.updated, transaction.created, transaction.updated, payment.updated, consent.expiring.

---

## 51. Adaptateurs partenaires

Chaque partenaire doit implémenter une interface commune pour institutions, comptes, soldes, transactions, consentements et paiements.

---

## 52. Administration

Configurer pays, établissements, partenaires, capacités, scopes, limites, délais de synchronisation, SLA, feature flags et incidents.

---

## 53. RBAC

Open Banking Admin, Operations, Finance, Treasury, Compliance, Support Restricted, Auditor, Organization Admin et Read Only.

---

## 54. Audit

Connexion, consentement, révocation, synchronisation manuelle, changement de compte, initiation de paiement et action admin doivent être audités.

---

## 55. Anti-fraude

Détection de compte compromis, nouvelle connexion inhabituelle, bénéficiaire à risque, paiements répétés, contournement de limites et appareils suspects.

---

## 56. Confidentialité

Les données externes sont minimisées, isolées par tenant, chiffrées et utilisées uniquement pour les finalités autorisées.

---

## 57. Conservation

Les durées doivent respecter consentements, réglementation, obligations comptables éventuelles et politique de suppression Mansa.

---

## 58. Multi-pays

Institutions, protocoles, exigences d’authentification, durées de consentement et droits d’accès doivent être configurables par pays.

---

## 59. Observabilité

Suivre disponibilité partenaires, latence, erreurs d’authentification, taux de reconnexion, retard de synchronisation, doublons et statuts UNKNOWN.

---

## 60. Tests fonctionnels, sécurité, performance et résilience

Tester consentement, connexion, expiration, révocation, synchronisation, pagination, déduplication, transactions pending/booked, paiement, timeout, webhook dupliqué, panne partenaire et reprise.

---

## 61. Règles métier

1. Aucun accès à un compte externe sans consentement valide.
2. Les scopes demandés sont minimisés.
3. Les identifiants bancaires ne sont pas collectés directement lorsque le partenaire fournit un flux sécurisé.
4. Les jetons partenaires ne sont jamais journalisés en clair.
5. Toute donnée externe possède un timestamp de fraîcheur.
6. Les transactions pending et booked sont distinguées.
7. La déduplication est obligatoire.
8. Une correction partenaire conserve un historique local.
9. Les comptes externes ne sont jamais fusionnés juridiquement.
10. Les conversions de reporting sont indicatives.
11. Les initiations de paiement sont idempotentes.
12. Un timeout n’est pas un échec final.
13. L’annulation respecte le point d’irrévocabilité.
14. Le Ledger Mansa n’enregistre que les mouvements internes pertinents.
15. Jini ne donne jamais un consentement à la place de l’utilisateur.
16. Les organisations sont isolées.
17. Les règles sont configurables par pays.
18. Les feature flags sont obligatoires.
19. Les accès et paiements sensibles sont audités.
20. Les audits critiques sont immuables.

---

## 62. Ordre de développement recommandé

```text
P1-OBK-01 — Institutions et capacités
P1-OBK-02 — Consentements et connexions
P1-OBK-03 — Comptes et soldes
P1-OBK-04 — Transactions et déduplication
P1-OBK-05 — Synchronisation et webhooks
P1-OBK-06 — Agrégation personnelle et entreprise
P1-OBK-07 — Initiation de paiement
P1-OBK-08 — Réconciliation et statuts inconnus
P1-OBK-09 — Jini et notifications
P1-OBK-10 — Adaptateurs et API
P1-OBK-11 — Administration, risque et reporting
P1-OBK-12 — Tests de bout en bout
```

---

## 63. Critères d’acceptation finaux

Le module est validé lorsque : les établissements sont configurables ; un consentement granulaire peut être créé et révoqué ; une connexion bancaire peut être établie sans stocker d’identifiants bancaires en clair ; les comptes, soldes et transactions sont synchronisés ; la fraîcheur des données est visible ; les doublons sont évités ; les opérations pending/booked sont réconciliées ; l’agrégation multi-comptes fonctionne ; les connexions entreprise respectent le RBAC ; l’initiation de paiement est idempotente ; les timeouts sont vérifiés avant décision finale ; les webhooks sont signés et dédupliqués ; Jini explique sans agir seul ; les audits sont présents ; les tests fonctionnels, sécurité, performance et résilience réussissent.