# 23 — Architecture des bases de données, Prisma et migrations de Mansa

## 1. Objet du document

Ce document définit l’architecture officielle des données de Mansa.

Il couvre :

- PostgreSQL ;
- Prisma ;
- les schémas de données ;
- les migrations ;
- les transactions ;
- les contraintes ;
- les index ;
- les relations ;
- les données financières ;
- les données utilisateurs ;
- les données commerçants ;
- les données TPE ;
- les données administratives ;
- les données partenaires ;
- les données publiques ;
- les données analytiques ;
- les sauvegardes ;
- l’archivage ;
- la rétention ;
- la sécurité ;
- la performance ;
- la haute disponibilité ;
- le multi-pays ;
- le multi-devise ;
- les environnements ;
- les données locales SQLite des applications lorsque nécessaires.

L’objectif est de garantir que les données de Mansa soient :

- cohérentes ;
- sécurisées ;
- traçables ;
- performantes ;
- évolutives ;
- récupérables ;
- correctement versionnées ;
- séparées selon leur niveau de sensibilité ;
- protégées contre la perte et la corruption.

---

# 2. Principes fondamentaux

## 2.1 PostgreSQL comme base principale

La base de données transactionnelle principale de Mansa doit utiliser PostgreSQL.

PostgreSQL doit stocker notamment :

- utilisateurs ;
- identités ;
- KYC ;
- KYB ;
- organisations ;
- commerçants ;
- établissements ;
- employés ;
- comptes ;
- wallets ;
- transactions ;
- ledger ;
- cartes ;
- paiements ;
- transferts ;
- TPE ;
- commandes ;
- stocks ;
- promotions ;
- notifications ;
- support ;
- audits ;
- configurations ;
- partenaires ;
- services publics.

---

## 2.2 Prisma comme ORM principal

Prisma doit être utilisé pour :

- définir le schéma ;
- générer le client ;
- gérer les migrations ;
- appliquer les relations ;
- assurer le typage ;
- faciliter les requêtes ;
- documenter les modèles ;
- standardiser l’accès aux données.

Prisma ne doit pas être utilisé pour contourner les règles métier du domaine.

---

## 2.3 Le schéma est une source de vérité technique

Le schéma Prisma doit refléter :

- les entités officielles ;
- les relations ;
- les contraintes ;
- les enums ;
- les règles d’intégrité ;
- les index ;
- les identifiants ;
- les historiques nécessaires.

Une modification du schéma doit être accompagnée de :

- migration ;
- revue ;
- test ;
- documentation ;
- plan de rollback ;
- analyse de compatibilité.

---

## 2.4 Aucune donnée financière critique sans contrainte

Les données financières doivent utiliser :

- transactions atomiques ;
- contraintes de cohérence ;
- références uniques ;
- identifiants idempotents ;
- historique ;
- audit ;
- version ;
- statut explicite.

---

## 2.5 Pas de suppression silencieuse

Les données importantes ne doivent pas être supprimées sans trace.

Selon le domaine, utiliser :

- suppression logique ;
- archivage ;
- anonymisation ;
- révocation ;
- expiration ;
- contre-écriture ;
- versionnement.

---

# 3. Organisation générale

Structure recommandée :

```text
database/
├── prisma/
│   ├── schema.prisma
│   ├── models/
│   ├── enums/
│   ├── extensions/
│   └── generated/
│
├── migrations/
│   ├── 2026xxxx_init/
│   ├── 2026xxxx_add_wallets/
│   └── 2026xxxx_add_indexes/
│
├── seeds/
│   ├── development/
│   ├── test/
│   ├── demo/
│   └── reference/
│
├── scripts/
│   ├── validate/
│   ├── migrate/
│   ├── rollback/
│   ├── anonymize/
│   ├── repair/
│   └── export/
│
└── README.md
```

---

# 4. Domaines de données

## 4.1 Identité et accès

Modèles possibles :

- User
- UserProfile
- UserIdentity
- UserContact
- UserAddress
- UserDevice
- UserSession
- AuthenticationMethod
- PasskeyCredential
- RecoveryMethod
- Consent
- Role
- Permission
- RoleAssignment
- TemporaryAccess
- Delegation

---

## 4.2 KYC et conformité

Modèles possibles :

- KycCase
- KycLevel
- KycDocument
- KycVerification
- KycDecision
- KycRiskAssessment
- KycReview
- KycProviderRequest
- SanctionScreening
- PepScreening
- ComplianceAlert
- ComplianceCase

---

## 4.3 Commerce et KYB

Modèles possibles :

- Organization
- Merchant
- MerchantProfile
- MerchantEstablishment
- MerchantEmployee
- MerchantRole
- MerchantPermission
- KybCase
- BeneficialOwner
- BusinessDocument
- SettlementAccount
- MerchantSubscription
- MerchantPlan
- MerchantConfiguration

---

## 4.4 Comptes et wallets

Modèles possibles :

- Wallet
- WalletAccount
- WalletBalance
- WalletLimit
- WalletHold
- WalletBeneficiary
- WalletStatement
- WalletOwnership
- WalletStatusHistory

Un utilisateur ou une organisation peut posséder plusieurs comptes.

---

## 4.5 Ledger

Modèles possibles :

- LedgerAccount
- LedgerTransaction
- LedgerEntry
- LedgerPosting
- LedgerBalanceSnapshot
- LedgerHold
- LedgerAdjustment
- LedgerReversal
- LedgerReconciliation
- LedgerPeriod
- LedgerAuditRecord

Le ledger doit être conçu en double entrée.

---

## 4.6 Paiements et transferts

Modèles possibles :

- Payment
- PaymentAttempt
- PaymentMethod
- PaymentAuthorization
- PaymentCapture
- PaymentCancellation
- PaymentRefund
- PaymentDispute
- PaymentFee
- PaymentCommission
- Transfer
- TransferParticipant
- TransferSchedule
- TransferRecurringRule
- TransferBeneficiary
- PaymentIdempotencyRecord

---

## 4.7 Cartes

Modèles possibles :

- Card
- CardProduct
- CardDesign
- CardToken
- CardAuthorization
- CardTransaction
- CardLimit
- CardRestriction
- CardPinEvent
- CardDelivery
- CardReplacement
- CardWalletProvisioning
- CardLifecycleEvent

Les données sensibles de carte doivent être tokenisées et minimisées.

---

## 4.8 TPE

Modèles possibles :

- Terminal
- TerminalModel
- TerminalAssignment
- TerminalCertificate
- TerminalSession
- TerminalEmployee
- TerminalTransaction
- TerminalConfiguration
- TerminalSoftwareVersion
- TerminalUpdate
- TerminalHealth
- TerminalSyncJob
- TerminalOfflineOperation

---

## 4.9 Catalogue, vente et stock

Modèles possibles :

- Product
- ProductVariant
- ProductCategory
- ProductImage
- ProductBarcode
- ServiceItem
- Inventory
- InventoryMovement
- StockAdjustment
- Supplier
- PurchaseOrder
- Sale
- SaleItem
- Receipt
- Invoice
- Return
- Exchange
- Discount
- TaxRule

---

## 4.10 Annuaire et Hub

Modèles possibles :

- DirectoryProfile
- DirectoryCategory
- DirectoryLocation
- DirectoryOpeningHour
- DirectoryMedia
- DirectoryPromotion
- DirectoryReview
- DirectoryFavorite
- DirectoryReservation
- DirectoryAppointment
- DirectorySubscription
- DirectoryVisibilityPlan
- DirectoryModerationCase

---

## 4.11 Notifications

Modèles possibles :

- Notification
- NotificationTemplate
- NotificationTemplateVersion
- NotificationRecipient
- NotificationDelivery
- NotificationAttempt
- NotificationPreference
- NotificationConsent
- NotificationCampaign
- NotificationSegment
- PushDeviceToken

---

## 4.12 Support et litiges

Modèles possibles :

- SupportTicket
- SupportMessage
- SupportAttachment
- SupportCategory
- SupportPriority
- SupportEscalation
- SupportSla
- Complaint
- Dispute
- MediationCase
- Compensation
- Resolution

---

## 4.13 Administration

Modèles possibles :

- AdminUser
- AdminRole
- AdminPermission
- AdminSession
- AdminAction
- ApprovalWorkflow
- ApprovalRequest
- ApprovalDecision
- Configuration
- FeatureFlag
- AuditEvent
- ExportRequest
- ImportJob

---

## 4.14 Partenaires

Modèles possibles :

- Partner
- PartnerContract
- PartnerEnvironment
- PartnerCredentialReference
- PartnerEndpoint
- PartnerCapability
- PartnerCountry
- PartnerCurrency
- PartnerWebhook
- PartnerRequest
- PartnerResponse
- PartnerReconciliation
- PartnerIncident

---

## 4.15 Services publics

Modèles possibles :

- PublicInstitution
- PublicAgent
- PublicService
- PublicServiceCase
- PublicPayment
- Fine
- Tax
- Scholarship
- StudentCard
- PublicDocument
- PublicApproval
- PublicAuditEvent

---

# 5. Identifiants

## 5.1 Identifiants internes

Chaque entité doit utiliser un identifiant unique.

Format recommandé :

- UUID ;
- ULID ;
- CUID2 ;
- identifiant opaque équivalent.

Les identifiants séquentiels exposés publiquement doivent être évités lorsqu’ils facilitent l’énumération.

---

## 5.2 Références lisibles

Certaines entités doivent aussi avoir une référence métier.

Exemples :

```text
PAY-2026-000123
TRF-2026-000456
TKT-2026-000789
KYC-2026-000654
```

La référence métier ne remplace pas l’identifiant interne.

---

## 5.3 Identifiants externes

Chaque intégration partenaire doit pouvoir stocker :

- identifiant interne ;
- identifiant externe ;
- type de partenaire ;
- environnement ;
- date ;
- corrélation.

---

# 6. Conventions de nommage

## 6.1 Modèles Prisma

Utiliser le singulier et le PascalCase.

Exemples :

```text
User
Merchant
Payment
LedgerEntry
```

## 6.2 Tables SQL

Convention recommandée :

```text
snake_case
```

Exemples :

```text
users
merchant_establishments
ledger_entries
payment_attempts
```

## 6.3 Colonnes

Convention recommandée :

```text
snake_case
```

Exemples :

```text
created_at
updated_at
country_code
external_reference
```

---

# 7. Champs communs

Les modèles importants doivent contenir lorsque pertinent :

- id ;
- status ;
- createdAt ;
- updatedAt ;
- deletedAt ;
- createdBy ;
- updatedBy ;
- countryCode ;
- environment ;
- version ;
- correlationId ;
- metadata ;
- source ;
- externalReference.

Tous les modèles n’ont pas besoin de tous ces champs.

---

# 8. Dates et heures

Toutes les dates techniques doivent être enregistrées en UTC.

Les interfaces affichent ensuite les dates selon :

- fuseau utilisateur ;
- pays ;
- locale ;
- préférence.

Les champs doivent distinguer :

- date ;
- heure ;
- timestamp ;
- durée ;
- date d’effet ;
- date d’expiration.

---

# 9. Montants financiers

## 9.1 Pas de flottants binaires

Les montants financiers ne doivent pas utiliser un type flottant classique.

Utiliser :

- Decimal ;
- entier dans la plus petite unité ;
- type monétaire contrôlé.

---

## 9.2 Devise obligatoire

Chaque montant doit être associé à une devise.

Exemples :

```text
amountMinor = 125000
currency = XOF
```

ou :

```text
amount = 1250.50
currency = EUR
```

La stratégie doit être uniforme par domaine.

---

## 9.3 Précision

La précision dépend de la devise.

Le système doit gérer :

- devises sans décimales ;
- devises à deux décimales ;
- autres précisions autorisées.

---

# 10. Enums

Les enums doivent être utilisés pour les valeurs stables.

Exemples :

- UserStatus
- PaymentStatus
- CardStatus
- KycStatus
- MerchantStatus
- TerminalStatus
- AuditSeverity
- Environment
- CurrencyCode
- CountryCode

Les enums appelés à évoluer fréquemment peuvent être remplacés par des tables de référence.

---

# 11. Statuts

Chaque processus important doit avoir des statuts explicites.

Exemple paiement :

```text
CREATED
PENDING
PROCESSING
AUTHORIZED
CAPTURED
COMPLETED
FAILED
DECLINED
CANCELLED
REFUNDED
PARTIALLY_REFUNDED
UNKNOWN
```

Un statut ne doit jamais être déduit uniquement de l’absence d’une valeur.

---

# 12. Historique des statuts

Les entités critiques doivent conserver un historique.

Exemples :

- PaymentStatusHistory
- CardStatusHistory
- KycStatusHistory
- MerchantStatusHistory
- TerminalStatusHistory

Chaque changement doit contenir :

- ancien statut ;
- nouveau statut ;
- auteur ;
- motif ;
- date ;
- corrélation.

---

# 13. Relations

Les relations doivent être explicites.

Exemples :

- un utilisateur peut avoir plusieurs wallets ;
- un wallet peut avoir plusieurs comptes ;
- une organisation peut avoir plusieurs établissements ;
- un établissement peut avoir plusieurs TPE ;
- un paiement peut avoir plusieurs tentatives ;
- un remboursement appartient à un paiement ;
- une transaction ledger contient plusieurs écritures.

---

# 14. Contraintes d’intégrité

Exemples :

- e-mail unique selon les règles ;
- téléphone normalisé ;
- référence de paiement unique ;
- clé d’idempotence unique par périmètre ;
- identifiant partenaire unique par environnement ;
- une écriture ledger doit appartenir à une transaction ;
- un remboursement ne doit pas dépasser le montant disponible ;
- un terminal ne peut appartenir qu’à un établissement actif à un instant donné.

---

# 15. Unicité

Les contraintes uniques peuvent être simples ou composites.

Exemples :

```text
@@unique([countryCode, phoneNumber])
@@unique([partnerId, externalReference, environment])
@@unique([merchantId, productSku])
@@unique([userId, deviceFingerprint])
```

Les contraintes doivent refléter les règles métier.

---

# 16. Index

Créer des index pour :

- identifiants externes ;
- références ;
- statuts ;
- dates ;
- pays ;
- commerçants ;
- utilisateurs ;
- transactions ;
- corrélations ;
- clés d’idempotence ;
- recherches ;
- tri fréquent ;
- rapprochement.

Un index inutile augmente le coût des écritures.

---

# 17. Index composites

Exemples :

```text
@@index([merchantId, createdAt])
@@index([userId, status, createdAt])
@@index([partnerId, environment, status])
@@index([countryCode, currencyCode, createdAt])
```

---

# 18. Recherche textuelle

Pour certaines fonctions, utiliser :

- PostgreSQL Full Text Search ;
- trigrammes ;
- index spécialisés ;
- moteur externe lorsque nécessaire.

Exemples :

- annuaire ;
- produits ;
- utilisateurs admin ;
- tickets support ;
- documents ;
- commerces.

---

# 19. Géolocalisation

Pour l’annuaire et les services proches, utiliser lorsque nécessaire :

- latitude ;
- longitude ;
- géohash ;
- PostGIS ;
- index spatial.

Les données de localisation doivent être protégées selon leur sensibilité.

---

# 20. JSON

Les champs JSON peuvent être utilisés pour :

- métadonnées ;
- configuration ;
- réponses partenaires ;
- contexte d’audit ;
- propriétés extensibles.

Ils ne doivent pas remplacer abusivement des colonnes structurées.

---

# 21. Transactions de base de données

Utiliser des transactions atomiques pour :

- paiements ;
- écritures ledger ;
- remboursements ;
- réservations ;
- modifications de solde ;
- créations liées ;
- workflows critiques.

Exemple conceptuel :

```typescript
await prisma.$transaction(async (tx) => {
  // créer la transaction métier
  // créer les écritures ledger
  // mettre à jour les statuts
  // enregistrer l’audit
})
```

---

# 22. Niveau d’isolation

Le niveau d’isolation doit être choisi selon le risque.

Exemples :

- Read Committed pour les opérations courantes ;
- Repeatable Read pour certains calculs ;
- Serializable pour certaines opérations critiques.

L’usage de niveaux élevés doit être maîtrisé pour éviter les blocages.

---

# 23. Verrouillage

Des verrous peuvent être nécessaires pour :

- solde ;
- inventaire ;
- réservation ;
- remboursement ;
- règlement ;
- clôture ;
- rapprochement.

Utiliser avec prudence :

- verrouillage pessimiste ;
- verrouillage optimiste ;
- version de ligne ;
- advisory locks.

---

# 24. Concurrence optimiste

Les modèles sensibles peuvent contenir un champ `version`.

Exemple :

```text
version Int @default(1)
```

Une mise à jour doit échouer si la version attendue a changé.

---

# 25. Idempotence

Une table dédiée peut contenir :

- clé ;
- utilisateur ;
- endpoint ;
- empreinte ;
- réponse ;
- statut ;
- date ;
- expiration.

La même clé avec un contenu différent doit être rejetée.

---

# 26. Ledger et immutabilité

Les écritures comptables validées ne doivent pas être modifiées.

Une correction doit créer :

- contre-écriture ;
- nouvelle transaction ;
- référence à l’original ;
- motif ;
- approbation ;
- audit.

---

# 27. Soldes

Les soldes peuvent être :

- calculés depuis le ledger ;
- matérialisés pour la performance ;
- reconstruisibles ;
- contrôlés par réconciliation.

Le solde matérialisé ne doit pas être la seule source de vérité.

---

# 28. Snapshots

Des snapshots peuvent être utilisés pour :

- soldes ;
- périodes ;
- rapports ;
- performances ;
- clôtures.

Chaque snapshot doit contenir :

- date ;
- version ;
- source ;
- périmètre ;
- empreinte ;
- statut.

---

# 29. Suppression logique

Les entités nécessitant une suppression logique peuvent utiliser :

```text
deletedAt
deletedBy
deletionReason
```

Une entité supprimée logiquement doit être exclue par défaut des requêtes courantes.

---

# 30. Archivage

Les données anciennes peuvent être archivées.

Exemples :

- notifications ;
- logs ;
- événements ;
- transactions anciennes ;
- pièces jointes ;
- exports ;
- audits.

L’archivage doit préserver :

- recherche ;
- intégrité ;
- sécurité ;
- obligations de conservation.

---

# 31. Anonymisation

L’anonymisation doit pouvoir remplacer :

- nom ;
- téléphone ;
- e-mail ;
- adresse ;
- identifiants directs.

Les relations nécessaires à la conformité ou à la comptabilité peuvent être conservées sous forme pseudonymisée.

---

# 32. Données sensibles

Données hautement sensibles :

- mots de passe ;
- PIN ;
- OTP ;
- CVV ;
- secrets ;
- clés privées ;
- documents d’identité ;
- données bancaires ;
- données de fraude.

Elles doivent être :

- chiffrées ;
- masquées ;
- limitées ;
- auditables ;
- absentes des logs.

---

# 33. Chiffrement

Le chiffrement peut être appliqué :

- au disque ;
- aux sauvegardes ;
- à certaines colonnes ;
- aux documents ;
- aux exports ;
- aux liens temporaires.

Les clés doivent être gérées hors de la base.

---

# 34. Séparation des secrets

La base ne stocke pas les secrets en clair.

Elle stocke uniquement :

- référence de secret ;
- identifiant de clé ;
- version ;
- date de rotation ;
- statut.

---

# 35. Multi-pays

Chaque donnée concernée doit pouvoir être rattachée à :

- pays ;
- région ;
- réglementation ;
- environnement ;
- devise ;
- entité légale.

Les données d’un pays ne doivent pas être mélangées sans règle explicite.

---

# 36. Multi-devise

Les modèles financiers doivent toujours distinguer :

- montant d’origine ;
- devise d’origine ;
- montant converti ;
- devise cible ;
- taux ;
- frais ;
- date du taux ;
- fournisseur du taux ;
- règle d’arrondi.

---

# 37. Multi-tenant

Mansa peut gérer plusieurs organisations dans la même plateforme.

Chaque donnée professionnelle doit être rattachée à :

- organisation ;
- commerçant ;
- établissement ;
- tenant logique.

Toutes les requêtes doivent appliquer le périmètre tenant.

---

# 38. Isolation des tenants

Options possibles :

- colonne tenantId ;
- schéma PostgreSQL par tenant ;
- base séparée pour certains partenaires ;
- instance dédiée pour certaines institutions.

Le choix dépend de :

- volume ;
- réglementation ;
- contrat ;
- sécurité ;
- coût ;
- souveraineté des données.

---

# 39. Environnements

Les bases doivent être séparées entre :

- développement ;
- test ;
- démonstration ;
- recette ;
- préproduction ;
- production.

Les données de production ne doivent pas être copiées librement dans les autres environnements.

---

# 40. Base SQLite locale

Certaines applications peuvent utiliser SQLite localement.

Cas possibles :

- cache ;
- mode hors ligne limité ;
- catalogue ;
- panier ;
- brouillons ;
- synchronisation ;
- données de démonstration ;
- file d’actions locales.

SQLite ne doit pas devenir l’autorité pour :

- solde réel ;
- statut financier définitif ;
- permissions ;
- frais ;
- limite ;
- décision de fraude ;
- confirmation de paiement.

---

# 41. Structure SQLite

La base locale peut contenir :

- CachedConfiguration
- CachedFeatureFlag
- CachedProfile
- CachedCatalog
- CachedTransaction
- DraftOperation
- PendingSync
- LocalEvent
- SyncCheckpoint
- LocalMigration

---

# 42. Synchronisation locale

Chaque donnée synchronisable doit contenir :

- identifiant local ;
- identifiant serveur ;
- version ;
- date locale ;
- date serveur ;
- statut ;
- tentative ;
- conflit ;
- erreur ;
- dernier checkpoint.

---

# 43. Résolution des conflits

Stratégies possibles :

- serveur prioritaire ;
- dernier changement valide ;
- fusion contrôlée ;
- revue manuelle ;
- refus et reprise ;
- version optimiste.

Les opérations financières ne doivent pas utiliser une fusion automatique risquée.

---

# 44. Migrations Prisma

Chaque migration doit contenir :

- nom explicite ;
- SQL généré ;
- objectif ;
- risque ;
- durée estimée ;
- compatibilité ;
- rollback ;
- validation ;
- ticket ;
- auteur ;
- date.

---

# 45. Convention de nommage des migrations

Exemples :

```text
20260802090000_init_core_schema
20260802103000_add_wallet_limits
20260802123000_add_payment_idempotency
20260802150000_add_ledger_indexes
```

---

# 46. Types de migrations

Une migration peut être :

- additive ;
- compatible ;
- corrective ;
- de données ;
- de performance ;
- potentiellement destructive ;
- destructive ;
- urgente.

---

# 47. Migration additive

Exemples :

- ajout de table ;
- ajout de colonne nullable ;
- ajout d’index ;
- ajout d’enum compatible ;
- ajout de relation optionnelle.

C’est la forme privilégiée.

---

# 48. Migration destructive

Exemples :

- suppression de colonne ;
- changement de type ;
- suppression de table ;
- réduction de longueur ;
- ajout d’une contrainte sur des données invalides.

Elle doit exiger une procédure renforcée.

---

# 49. Expand and Contract

Pour les changements complexes :

## 49.1 Expand

Ajouter la nouvelle structure.

## 49.2 Migrate

Copier ou transformer les données.

## 49.3 Switch

Faire utiliser la nouvelle structure par le code.

## 49.4 Contract

Supprimer l’ancienne structure plus tard.

---

# 50. Migration de données

Une migration de données doit être :

- reprise possible ;
- idempotente ;
- mesurable ;
- journalisée ;
- testée sur un volume réaliste ;
- interrompable ;
- validée.

---

# 51. Déploiement des migrations

Ordre recommandé :

1. sauvegarde ;
2. validation du schéma ;
3. vérification de compatibilité ;
4. déploiement du code compatible ;
5. migration ;
6. vérification ;
7. activation ;
8. monitoring ;
9. nettoyage ultérieur.

---

# 52. Rollback

Toute migration critique doit avoir un plan de retour.

Le rollback peut consister à :

- restaurer un snapshot ;
- réactiver l’ancien champ ;
- revenir au code précédent ;
- exécuter une migration inverse ;
- restaurer une sauvegarde ;
- désactiver la fonctionnalité.

---

# 53. Prisma Validate

La CI doit exécuter :

```bash
prisma validate
```

Elle doit échouer si le schéma est invalide.

---

# 54. Prisma Generate

La CI doit exécuter :

```bash
prisma generate
```

Le client généré doit correspondre au schéma utilisé.

---

# 55. Prisma Migrate

En environnement de développement :

```bash
prisma migrate dev
```

En environnement contrôlé :

```bash
prisma migrate deploy
```

Les commandes destructives improvisées sont interdites en production.

---

# 56. Prisma DB Push

`prisma db push` ne doit pas être utilisé comme méthode normale de production.

Il peut être limité à :

- prototypes ;
- environnements locaux ;
- démonstrations contrôlées ;
- tests temporaires.

---

# 57. Seeds

Les seeds doivent être séparés selon l’environnement.

## 57.1 Références

Exemples :

- pays ;
- devises ;
- langues ;
- catégories ;
- permissions ;
- rôles ;
- statuts ;
- types de documents.

## 57.2 Démo

Exemples :

- faux utilisateurs ;
- faux commerces ;
- fausses transactions ;
- faux TPE ;
- faux partenaires.

## 57.3 Test

Données minimales reproductibles pour les tests.

---

# 58. Données de production dans les seeds

Les seeds ne doivent jamais contenir :

- vraies identités ;
- vrais documents ;
- vrais numéros ;
- vraies cartes ;
- vrais secrets ;
- vrais tokens ;
- vraies données bancaires.

---

# 59. Requêtes

Les requêtes doivent éviter :

- N+1 ;
- chargement excessif ;
- sélection de colonnes inutiles ;
- pagination absente ;
- jointures incontrôlées ;
- recherche sans index ;
- transactions trop longues.

---

# 60. Pagination

Utiliser :

- pagination par curseur pour les grands flux ;
- pagination par page pour certains écrans administratifs ;
- limite maximale ;
- tri stable ;
- filtre explicite.

---

# 61. Sélection de champs

L’API ne doit pas charger automatiquement toutes les colonnes sensibles.

Utiliser :

- `select` ;
- DTO ;
- projections ;
- vues ;
- permissions ;
- masquage.

---

# 62. Batch

Pour les traitements importants :

- lecture par lots ;
- mise à jour par lots ;
- checkpoint ;
- reprise ;
- limite de mémoire ;
- journalisation.

---

# 63. Cache

Certaines données peuvent être mises en cache :

- configuration ;
- feature flags ;
- références ;
- profils publics ;
- catalogues ;
- droits calculés.

Les données critiques doivent toujours avoir une stratégie d’invalidation.

---

# 64. Réplication

PostgreSQL peut utiliser :

- réplication ;
- read replicas ;
- réplication régionale ;
- standby ;
- failover.

Les écritures critiques doivent utiliser l’instance principale.

---

# 65. Lecture depuis des réplicas

Les lectures non critiques peuvent utiliser des réplicas.

Attention à la cohérence différée pour :

- solde ;
- statut de paiement ;
- autorisation ;
- KYC ;
- permissions ;
- ledger.

---

# 66. Sauvegardes

Les sauvegardes doivent être :

- automatiques ;
- chiffrées ;
- versionnées ;
- surveillées ;
- testées ;
- redondantes ;
- protégées contre la suppression accidentelle.

---

# 67. Types de sauvegardes

- sauvegarde complète ;
- sauvegarde incrémentale ;
- sauvegarde logique ;
- snapshot ;
- point-in-time recovery ;
- export de sécurité.

---

# 68. Point-in-Time Recovery

La production doit prévoir, lorsque possible, une restauration à un instant précis.

La politique doit définir :

- fenêtre ;
- fréquence ;
- RPO ;
- RTO ;
- environnement ;
- responsable ;
- test.

---

# 69. Tests de restauration

Une sauvegarde non testée ne doit pas être considérée comme fiable.

Les restaurations doivent être testées régulièrement.

---

# 70. Haute disponibilité

Le système doit prévoir :

- réplication ;
- monitoring ;
- failover ;
- sauvegardes ;
- health checks ;
- procédure d’incident ;
- capacité de reconstruction.

---

# 71. Monitoring de la base

Surveiller :

- connexions ;
- latence ;
- CPU ;
- mémoire ;
- stockage ;
- locks ;
- deadlocks ;
- requêtes lentes ;
- index inutilisés ;
- réplication ;
- sauvegardes ;
- migrations ;
- erreurs ;
- croissance.

---

# 72. Requêtes lentes

Une requête lente doit pouvoir être liée à :

- endpoint ;
- service ;
- utilisateur technique ;
- corrélation ;
- version ;
- environnement ;
- plan d’exécution.

---

# 73. Analyse des plans

Utiliser lorsque nécessaire :

```sql
EXPLAIN
EXPLAIN ANALYZE
```

Les analyses en production doivent être contrôlées.

---

# 74. Partitionnement

Le partitionnement peut être utilisé pour :

- événements ;
- audits ;
- notifications ;
- transactions volumineuses ;
- logs ;
- données historiques.

Clés possibles :

- date ;
- pays ;
- tenant ;
- type.

---

# 75. Vues

Des vues peuvent être utilisées pour :

- rapports ;
- lecture simplifiée ;
- séparation de données ;
- accès contrôlé ;
- agrégations.

---

# 76. Vues matérialisées

Utiles pour :

- reporting ;
- dashboards ;
- analytics ;
- agrégats lourds ;
- soldes historiques.

Elles doivent avoir une stratégie de rafraîchissement.

---

# 77. Procédures et fonctions SQL

Elles peuvent être utilisées pour :

- contraintes complexes ;
- performance ;
- opérations atomiques ;
- maintenance.

Elles doivent être :

- versionnées ;
- testées ;
- documentées ;
- auditées.

---

# 78. Triggers

Les triggers doivent rester limités.

Ils peuvent servir à :

- audit technique ;
- timestamps ;
- intégrité ;
- notifications internes ;
- contrôle spécifique.

Les règles métier principales doivent rester visibles dans le code métier.

---

# 79. Row-Level Security

La sécurité au niveau des lignes peut être utilisée pour :

- tenants ;
- organisations ;
- pays ;
- partenaires ;
- institutions.

Elle ne remplace pas l’autorisation applicative.

---

# 80. Accès direct à la base

L’accès direct à la production doit être limité.

Rôles possibles :

- service applicatif ;
- migration ;
- lecture support limitée ;
- audit ;
- sauvegarde ;
- administration base.

---

# 81. Comptes de base de données

Chaque environnement doit utiliser des comptes séparés.

Chaque service ou rôle doit avoir les permissions minimales.

---

# 82. Audit des accès

Les accès sensibles à la base doivent être tracés.

Exemples :

- connexion ;
- requête administrative ;
- export ;
- modification ;
- migration ;
- création d’utilisateur ;
- changement de permission.

---

# 83. Exports

Les exports doivent :

- être autorisés ;
- être limités ;
- être chiffrés ;
- expirer ;
- être audités ;
- masquer les champs inutiles.

---

# 84. Import

Les imports doivent :

- valider le format ;
- valider le schéma ;
- empêcher les doublons ;
- appliquer l’idempotence ;
- produire un rapport ;
- être réversibles lorsque possible.

---

# 85. Réconciliation

Les données financières doivent être réconciliées avec :

- ledger ;
- partenaires ;
- banques ;
- Mobile Money ;
- réseaux cartes ;
- règlements commerçants ;
- comptes de suspense.

---

# 86. Qualité des données

Contrôles :

- doublons ;
- références orphelines ;
- statut impossible ;
- montant négatif interdit ;
- devise incohérente ;
- date invalide ;
- relation manquante ;
- solde incohérent ;
- document expiré ;
- valeur hors limite.

---

# 87. Réparation

Les scripts de réparation doivent :

- être versionnés ;
- être idempotents ;
- produire un rapport ;
- fonctionner en simulation ;
- être approuvés ;
- être audités ;
- éviter les modifications silencieuses.

---

# 88. Administration

Le portail Admin ne doit pas accéder directement à la base.

Il utilise des API contrôlées.

Les administrateurs peuvent :

- consulter certaines données ;
- rechercher ;
- filtrer ;
- exporter selon permission ;
- lancer certains workflows ;
- demander une correction ;
- consulter un audit.

---

# 89. API d’administration des données

Exemples internes :

```http
GET    /data/health
GET    /data/migrations
GET    /data/schema-version
GET    /data/quality
GET    /data/reconciliation

POST   /data/exports
POST   /data/imports
POST   /data/repair-jobs
POST   /data/anonymization-jobs
```

---

# 90. Modèles techniques

- DatabaseSchemaVersion
- DatabaseMigration
- MigrationExecution
- MigrationApproval
- DataRepairJob
- DataExportJob
- DataImportJob
- DataQualityCheck
- DataQualityIssue
- BackupRecord
- RestoreTest
- DatabaseHealth
- ReplicationStatus
- DataRetentionExecution
- DataAnonymizationJob

---

# 91. Permissions

Exemples :

```text
database.schema.read
database.migration.read
database.migration.approve
database.migration.deploy
database.backup.read
database.restore.execute
database.export.create
database.import.create
database.repair.request
database.repair.approve
database.quality.read
database.production.access
```

---

# 92. Actions critiques

Doivent être protégées :

- migration production ;
- suppression de colonne ;
- suppression de table ;
- restauration ;
- export massif ;
- réparation financière ;
- modification d’écriture ledger ;
- désactivation d’une contrainte ;
- changement de permission base ;
- accès direct production.

---

# 93. Double validation

La double validation est recommandée pour :

- migration destructive ;
- restauration ;
- export sensible ;
- correction ledger ;
- suppression massive ;
- changement de schéma financier ;
- modification d’un tenant institutionnel ;
- accès d’urgence.

---

# 94. Audit

Chaque opération critique doit enregistrer :

- auteur ;
- approbateur ;
- environnement ;
- base ;
- schéma ;
- version ;
- migration ;
- résultat ;
- durée ;
- erreur ;
- rollback ;
- ticket ;
- date.

---

# 95. Alertes

Déclencher une alerte si :

- migration échoue ;
- sauvegarde échoue ;
- réplication est en retard ;
- espace disque est faible ;
- deadlock augmente ;
- requête lente augmente ;
- intégrité ledger échoue ;
- export massif est lancé ;
- restauration est demandée ;
- checksum est invalide ;
- schéma diverge ;
- données orphelines apparaissent.

---

# 96. Analytics

Événements possibles :

```text
database_migration_started
database_migration_completed
database_migration_failed
database_backup_started
database_backup_completed
database_backup_failed
database_restore_test_started
database_restore_test_completed
database_quality_issue_detected
database_repair_started
database_repair_completed
database_replication_lag_detected
database_slow_query_detected
database_export_created
database_schema_drift_detected
```

---

# 97. Tests

- tests du schéma Prisma ;
- tests de migration ;
- tests de rollback ;
- tests de contraintes ;
- tests d’unicité ;
- tests de concurrence ;
- tests de transaction ;
- tests ledger ;
- tests d’idempotence ;
- tests multi-pays ;
- tests multi-devises ;
- tests multi-tenant ;
- tests de sauvegarde ;
- tests de restauration ;
- tests d’anonymisation ;
- tests d’export ;
- tests d’import ;
- tests de charge ;
- tests de réplication ;
- tests SQLite ;
- tests de synchronisation ;
- tests de conflit ;
- tests de sécurité.

---

# 98. Règles métier

1. PostgreSQL est la base transactionnelle principale.
2. Prisma définit le schéma applicatif officiel.
3. Toute modification du schéma passe par une migration.
4. Les migrations production sont contrôlées.
5. Les montants n’utilisent pas de flottants binaires.
6. Toute valeur financière possède une devise.
7. Le ledger reste immuable après validation.
8. Les corrections financières utilisent des contre-écritures.
9. Les transactions critiques sont atomiques.
10. Les opérations critiques sont idempotentes.
11. Les contraintes d’intégrité sont appliquées en base lorsque pertinent.
12. Les identifiants publics sont opaques.
13. Les données sensibles sont chiffrées ou tokenisées.
14. Les secrets ne sont pas stockés en clair.
15. Les environnements sont séparés.
16. Les données production ne sont pas copiées librement.
17. SQLite n’est pas l’autorité financière.
18. Les synchronisations locales sont versionnées.
19. Les conflits financiers ne sont pas fusionnés automatiquement.
20. Les sauvegardes sont testées.
21. Les restaurations sont documentées.
22. Les requêtes importantes sont indexées.
23. Les accès directs sont limités.
24. Les exports sensibles sont audités.
25. Les migrations destructives nécessitent une approbation renforcée.
26. Les données expirées sont archivées, anonymisées ou supprimées selon la politique.
27. Les tenants sont isolés.
28. Les pays et devises sont explicites.
29. Les réparations sont traçables.
30. La qualité des données est surveillée.

---

# 99. Critères d’acceptation

L’architecture des bases de données est validée lorsque :

- PostgreSQL est configuré comme base principale ;
- le schéma Prisma est valide ;
- les domaines sont clairement modélisés ;
- les relations sont explicites ;
- les contraintes d’intégrité existent ;
- les migrations sont versionnées ;
- les migrations destructives sont protégées ;
- les données financières sont correctement typées ;
- le ledger est immuable ;
- les opérations critiques sont transactionnelles ;
- l’idempotence est prise en charge ;
- les index couvrent les recherches principales ;
- le multi-pays et le multi-devise sont supportés ;
- les tenants sont isolés ;
- SQLite est limité aux usages locaux ;
- la synchronisation locale est contrôlée ;
- les sauvegardes sont automatisées ;
- les restaurations sont testées ;
- les accès sont limités ;
- les exports sont sécurisés ;
- le monitoring de la base fonctionne ;
- les tests couvrent les scénarios critiques.
