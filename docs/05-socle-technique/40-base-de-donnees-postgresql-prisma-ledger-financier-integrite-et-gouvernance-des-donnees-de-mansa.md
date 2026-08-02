# 40 — Base de données, PostgreSQL, Prisma, ledger financier, intégrité et gouvernance des données de Mansa

## 1. Objet du document

Ce document définit l’architecture officielle des bases de données et du ledger financier de Mansa.

Il couvre :

- PostgreSQL ;
- Prisma ;
- les modèles métier ;
- les schémas ;
- les migrations ;
- les transactions ;
- le ledger en double entrée ;
- les comptes comptables ;
- les écritures ;
- les soldes ;
- les réservations ;
- les contre-écritures ;
- les remboursements ;
- les commissions ;
- les règlements ;
- les rapprochements ;
- les devises ;
- les arrondis ;
- l’idempotence ;
- la concurrence ;
- l’historisation ;
- l’archivage ;
- le partitionnement ;
- les index ;
- les performances ;
- les sauvegardes ;
- la restauration ;
- l’audit ;
- le multi-pays ;
- le multi-tenant ;
- la sécurité ;
- les tests.

L’objectif est de garantir que les données de Mansa soient :

- cohérentes ;
- exactes ;
- traçables ;
- sécurisées ;
- disponibles ;
- restaurables ;
- performantes ;
- compatibles avec plusieurs pays ;
- protégées contre les doublons ;
- adaptées aux opérations financières critiques.

---

# 2. Principes fondamentaux

## 2.1 Le ledger est la source financière officielle

Les soldes affichés dans les applications ne doivent pas constituer la source officielle.

La vérité financière doit provenir :

- des comptes ledger ;
- des écritures validées ;
- des réservations ;
- des contre-écritures ;
- des règles de calcul officielles.

---

## 2.2 Une écriture financière validée est immuable

Une écriture validée ne doit jamais être modifiée ou supprimée silencieusement.

Une correction doit utiliser :

- une contre-écriture ;
- une écriture complémentaire ;
- une référence à l’opération d’origine ;
- une justification ;
- une approbation lorsque nécessaire ;
- un audit.

---

## 2.3 Toute opération financière doit être équilibrée

Dans un système en double entrée :

```text
Somme des débits = Somme des crédits
```

Une transaction déséquilibrée doit être refusée.

---

## 2.4 Le solde est une conséquence des écritures

Le solde ne doit pas être modifié directement.

Il doit être calculé à partir :

- des écritures ;
- des réservations ;
- des libérations ;
- des ajustements tracés.

---

## 2.5 La base ne doit pas dépendre de l’interface

Les modèles de données doivent représenter le métier, pas uniquement les écrans actuels.

---

# 3. Architecture des données

Structure possible :

```text
Applications
    │
    ▼
API Gateway
    │
    ▼
Services métier
    │
    ├── Repositories
    ├── Transactions
    ├── Domain Rules
    └── Audit
    │
    ▼
PostgreSQL
    │
    ├── Données métier
    ├── Ledger
    ├── Outbox
    ├── Inbox
    ├── Audit
    └── Configurations
```

---

# 4. PostgreSQL

PostgreSQL doit être utilisé pour :

- utilisateurs ;
- organisations ;
- commerçants ;
- wallets ;
- paiements ;
- transferts ;
- cartes ;
- TPE ;
- KYC ;
- fraude ;
- support ;
- partenaires ;
- configurations ;
- ledger ;
- audit ;
- événements transactionnels.

---

# 5. Prisma

Prisma doit permettre :

- la définition du schéma ;
- la génération du client ;
- les relations ;
- les enums ;
- les migrations ;
- les transactions ;
- la validation ;
- le typage ;
- l’accès contrôlé aux données.

---

# 6. Organisation du schéma Prisma

Structure recommandée :

```text
database/
├── prisma/
│   ├── schema.prisma
│   ├── migrations/
│   ├── seeds/
│   └── extensions/
├── scripts/
├── backups/
└── documentation/
```

Dans un schéma volumineux, Mansa peut utiliser plusieurs fichiers Prisma si la version utilisée le permet.

---

# 7. Domaines de données

Le schéma doit être organisé par domaines :

```text
Identity
Customer
Organization
Compliance
Wallet
Ledger
Payment
Transfer
Card
Merchant
Terminal
Pricing
Fraud
Support
Partner
Notification
Document
PublicService
Audit
Configuration
```

---

# 8. Identifiants

Les identifiants doivent être :

- uniques ;
- non prévisibles ;
- indépendants des données métier ;
- adaptés aux systèmes distribués ;
- non réutilisés.

Formats possibles :

- UUID ;
- ULID ;
- CUID.

---

# 9. Références publiques

Les références affichées aux utilisateurs doivent être distinctes des identifiants internes lorsque nécessaire.

Exemples :

```text
PAY-2026-000001
TRF-2026-000001
SUP-2026-000001
INV-2026-000001
```

---

# 10. Horodatage

Chaque modèle important doit posséder :

```text
createdAt
updatedAt
```

Selon le contexte :

```text
deletedAt
approvedAt
completedAt
failedAt
expiredAt
```

Les dates doivent être stockées dans un format cohérent, généralement UTC.

---

# 11. Fuseaux horaires

Les données doivent distinguer :

- heure de stockage ;
- fuseau utilisateur ;
- fuseau pays ;
- fuseau établissement ;
- fuseau contractuel.

---

# 12. Suppression logique

La suppression logique peut être utilisée pour :

- utilisateurs ;
- commerces ;
- produits ;
- configurations ;
- terminaux ;
- documents non financiers.

Elle ne doit pas remplacer une vraie politique de rétention.

---

# 13. Données financières non supprimables

Les données suivantes ne doivent généralement pas être supprimées directement :

- écritures ledger ;
- transactions validées ;
- remboursements ;
- règlements ;
- rapprochements ;
- audits financiers ;
- preuves d’acceptation ;
- décisions de conformité obligatoires.

---

# 14. Multi-pays

Les modèles concernés doivent pouvoir contenir :

```text
countryId
countryCode
currencyCode
locale
timezone
```

Les règles par pays ne doivent pas être codées directement dans chaque modèle.

---

# 15. Multi-tenant

Les données organisationnelles doivent pouvoir contenir :

```text
tenantId
organizationId
merchantId
institutionId
establishmentId
```

Les requêtes doivent toujours appliquer le bon périmètre.

---

# 16. Isolation des tenants

Options possibles :

- colonne `tenantId` ;
- schéma PostgreSQL séparé ;
- base séparée ;
- cluster séparé.

Le choix dépend :

- du niveau de risque ;
- du volume ;
- du pays ;
- du contrat ;
- de la souveraineté ;
- de la criticité.

---

# 17. Row-Level Security

PostgreSQL Row-Level Security peut renforcer l’isolation.

Elle peut limiter les lignes selon :

- tenant ;
- organisation ;
- pays ;
- rôle ;
- session technique.

Elle ne remplace pas les contrôles applicatifs.

---

# 18. Wallet

Un wallet doit contenir au minimum :

- propriétaire ;
- type ;
- devise ;
- statut ;
- pays ;
- compte ledger associé ;
- niveau de vérification ;
- limites ;
- date de création.

---

# 19. Statuts du wallet

Exemples :

- PENDING ;
- ACTIVE ;
- LIMITED ;
- SUSPENDED ;
- FROZEN ;
- CLOSED.

---

# 20. Ledger

Le ledger doit représenter :

- comptes ;
- journaux ;
- transactions ;
- écritures ;
- réservations ;
- contre-écritures ;
- périodes ;
- devises ;
- références ;
- audits.

---

# 21. Comptes ledger

Types possibles :

- actif ;
- passif ;
- revenu ;
- charge ;
- capitaux propres ;
- suspense ;
- règlement ;
- frais ;
- taxes ;
- réserve ;
- wallet client ;
- wallet commerçant.

---

# 22. Hiérarchie des comptes

Exemple :

```text
Actifs
├── Banque
├── Mobile Money
├── Fonds en règlement
└── Créances

Passifs
├── Wallets clients
├── Wallets commerçants
├── Montants en attente
└── Réserves

Revenus
├── Frais de paiement
├── Commissions
└── Abonnements

Charges
├── Frais partenaires
├── Réseaux cartes
└── Mobile Money
```

---

# 23. Journal comptable

Chaque type d’opération peut être associé à un journal :

- paiements ;
- transferts ;
- cartes ;
- remboursements ;
- frais ;
- règlements ;
- ajustements ;
- services publics ;
- Mobile Money.

---

# 24. Transaction ledger

Une transaction ledger doit contenir :

- identifiant ;
- référence métier ;
- type ;
- statut ;
- devise ;
- pays ;
- date ;
- description ;
- corrélation ;
- idempotency key ;
- écritures ;
- source ;
- auteur ;
- approbateur éventuel.

---

# 25. Écriture ledger

Une écriture doit contenir :

- transaction ledger ;
- compte ;
- direction ;
- montant ;
- devise ;
- date ;
- référence ;
- libellé ;
- séquence ;
- statut.

---

# 26. Débit et crédit

Valeurs possibles :

```text
DEBIT
CREDIT
```

Le moteur doit vérifier l’équilibre avant validation.

---

# 27. Montants

Les montants financiers ne doivent pas être stockés en nombre flottant.

Utiliser :

- entier dans l’unité minimale ;
- type Decimal avec précision contrôlée.

Exemple :

```text
10 000 FCFA = 10000 unités
```

---

# 28. Devise

Chaque montant doit avoir une devise explicite.

Exemples :

```text
XOF
EUR
USD
GBP
```

Aucun calcul entre deux devises ne doit être effectué sans conversion explicite.

---

# 29. Précision monétaire

Chaque devise doit définir :

- nombre de décimales ;
- unité minimale ;
- méthode d’arrondi ;
- montant minimal ;
- montant maximal.

---

# 30. Arrondis

Les règles d’arrondi doivent être centralisées.

Méthodes possibles :

- moitié supérieure ;
- moitié paire ;
- arrondi inférieur ;
- arrondi supérieur ;
- troncature réglementaire.

---

# 31. Réservations de fonds

Une réservation permet de bloquer temporairement un montant.

Cas :

- paiement carte ;
- transfert ;
- retrait ;
- paiement TPE ;
- opération hors ligne ;
- autorisation différée.

---

# 32. Statuts d’une réservation

- CREATED ;
- ACTIVE ;
- CAPTURED ;
- PARTIALLY_CAPTURED ;
- RELEASED ;
- EXPIRED ;
- CANCELLED.

---

# 33. Solde disponible

Exemple conceptuel :

```text
Solde disponible =
Solde comptable
- réservations actives
- restrictions applicables
```

---

# 34. Capture

La capture transforme une réservation en écriture financière finale.

Elle doit vérifier :

- réservation active ;
- montant autorisé ;
- devise ;
- référence partenaire ;
- idempotence ;
- délai ;
- statut.

---

# 35. Libération

Une réservation doit être libérée lorsque :

- paiement refusé ;
- opération annulée ;
- délai expiré ;
- partenaire confirme l’échec ;
- opération compensée.

---

# 36. Contre-écriture

Une contre-écriture doit :

- référencer l’écriture d’origine ;
- inverser les débits et crédits ;
- conserver le même montant ou un montant partiel justifié ;
- contenir un motif ;
- être auditée.

---

# 37. Remboursement

Un remboursement doit créer une nouvelle opération.

Il ne doit pas modifier la transaction d’origine.

Il doit contenir :

- transaction d’origine ;
- montant disponible ;
- montant remboursé ;
- devise ;
- motif ;
- partenaire ;
- écritures ;
- statut ;
- approbation éventuelle.

---

# 38. Remboursement partiel

Le système doit calculer :

```text
Montant encore remboursable =
Montant initial
- remboursements validés
- remboursements en cours
```

---

# 39. Frais

Les frais doivent être enregistrés séparément du principal.

Exemple :

```text
Montant principal : 10 000 XOF
Frais Mansa : 100 XOF
Frais partenaire : 50 XOF
Total débité : 10 150 XOF
```

---

# 40. Commissions

Les commissions peuvent être réparties entre :

- Mansa ;
- banque ;
- opérateur ;
- réseau carte ;
- commerçant ;
- agent ;
- institution ;
- partenaire.

Chaque part doit être traçable.

---

# 41. Taxes

Les taxes doivent être :

- versionnées ;
- rattachées à un pays ;
- rattachées à une date ;
- calculées séparément ;
- affichables ;
- auditables.

---

# 42. Règlements commerçants

Le règlement doit regrouper :

- ventes ;
- remboursements ;
- commissions ;
- frais ;
- taxes ;
- réserves ;
- ajustements ;
- montant net.

---

# 43. Statuts de règlement

- CALCULATED ;
- PENDING ;
- APPROVED ;
- SUBMITTED ;
- PAID ;
- PARTIALLY_PAID ;
- FAILED ;
- RECONCILIATION_REQUIRED ;
- CANCELLED.

---

# 44. Rapprochement

Le rapprochement compare :

- transactions internes ;
- ledger ;
- partenaire ;
- banque ;
- Mobile Money ;
- réseau carte ;
- règlement ;
- fichiers externes.

---

# 45. Divergences

Types possibles :

- opération manquante ;
- doublon ;
- montant différent ;
- statut différent ;
- frais différents ;
- devise différente ;
- date différente ;
- référence inconnue.

---

# 46. Comptes de suspense

Une divergence peut être placée dans un compte de suspense.

Elle doit être :

- identifiée ;
- assignée ;
- justifiée ;
- résolue ;
- auditable ;
- suivie par ancienneté.

---

# 47. Idempotence en base

Une contrainte unique doit protéger les opérations critiques.

Exemples :

```text
idempotencyKey
partnerReference
externalTransactionId
eventId
webhookId
```

---

# 48. Contraintes uniques

Les contraintes doivent couvrir les invariants réels.

Exemples :

- un téléphone actif unique par pays selon politique ;
- une référence de paiement unique ;
- un événement consommé une seule fois ;
- une carte liée à un identifiant processeur unique ;
- un TPE avec un numéro de série unique.

---

# 49. Contraintes de clé étrangère

Les relations critiques doivent utiliser des clés étrangères lorsque possible.

Elles protègent contre :

- données orphelines ;
- incohérences ;
- suppressions accidentelles ;
- références invalides.

---

# 50. Transactions PostgreSQL

Une transaction doit être utilisée lorsque plusieurs écritures doivent réussir ou échouer ensemble.

Exemples :

- création transaction ledger + écritures ;
- paiement + réservation ;
- événement Outbox + opération métier ;
- remboursement + contre-écriture ;
- règlement + lignes associées.

---

# 51. Isolation transactionnelle

Les niveaux possibles doivent être choisis selon le risque :

- Read Committed ;
- Repeatable Read ;
- Serializable.

Les opérations financières critiques peuvent nécessiter un niveau renforcé.

---

# 52. Concurrence

Le système doit gérer :

- deux paiements simultanés ;
- deux remboursements ;
- deux mises à jour ;
- deux captures ;
- deux workers ;
- deux webhooks ;
- deux règlements.

---

# 53. Verrouillage pessimiste

Peut être utilisé lorsque :

- la ressource doit être bloquée ;
- le conflit est probable ;
- l’opération est courte ;
- le risque financier est élevé.

---

# 54. Verrouillage optimiste

Peut utiliser :

```text
version
updatedAt
```

Une mise à jour échoue si la version a changé.

---

# 55. Séquences et numérotation

Les références métier doivent être générées de manière sûre.

Elles ne doivent pas dépendre uniquement d’un compteur local non synchronisé.

---

# 56. Index

Les index doivent être conçus selon les requêtes réelles.

Exemples :

- utilisateur + statut ;
- transaction + date ;
- marchand + date ;
- pays + statut ;
- tenant + ressource ;
- partenaire + référence ;
- corrélation ;
- idempotency key.

---

# 57. Index composites

Un index composite doit respecter l’ordre des filtres les plus fréquents.

Exemple :

```text
tenantId, countryId, status, createdAt
```

---

# 58. Index partiels

PostgreSQL peut utiliser des index partiels.

Exemple :

- uniquement les transactions `PENDING` ;
- uniquement les comptes actifs ;
- uniquement les tickets ouverts ;
- uniquement les réservations actives.

---

# 59. Index inutiles

Les index inutiles augmentent :

- le stockage ;
- le coût d’écriture ;
- le temps de migration ;
- la maintenance.

Ils doivent être suivis et supprimés avec prudence.

---

# 60. Pagination

Pour les gros volumes, utiliser :

- curseur ;
- keyset pagination ;
- identifiant stable ;
- ordre déterministe.

Éviter les offsets très élevés.

---

# 61. Partitionnement

Les grandes tables peuvent être partitionnées par :

- date ;
- pays ;
- tenant ;
- type ;
- environnement.

Tables possibles :

- transactions ;
- écritures ledger ;
- événements ;
- audits ;
- logs métier ;
- notifications.

---

# 62. Partitionnement temporel

Exemples :

- mensuel ;
- trimestriel ;
- annuel.

La stratégie dépend du volume et des requêtes.

---

# 63. Archivage

Les données anciennes peuvent être déplacées vers :

- partitions froides ;
- base d’archive ;
- stockage objet ;
- entrepôt analytique.

L’archive doit rester consultable selon les permissions.

---

# 64. Réplication

PostgreSQL peut utiliser :

- réplication synchrone ;
- réplication asynchrone ;
- standby ;
- read replicas ;
- réplication interrégionale.

---

# 65. Lectures sur réplicas

Les lectures non critiques peuvent utiliser des réplicas.

Exemples :

- rapports ;
- analytics ;
- historique ;
- exports ;
- recherches.

Les soldes critiques doivent éviter une lecture obsolète.

---

# 66. Pool de connexions

Le pool doit limiter les connexions à PostgreSQL.

Il doit gérer :

- maximum ;
- minimum ;
- timeout ;
- file d’attente ;
- environnement ;
- service ;
- monitoring.

---

# 67. Requêtes lentes

Les requêtes lentes doivent être :

- détectées ;
- mesurées ;
- expliquées ;
- optimisées ;
- testées ;
- suivies après correction.

---

# 68. Plans d’exécution

Utiliser :

```sql
EXPLAIN
EXPLAIN ANALYZE
```

pour comprendre :

- index utilisés ;
- scans ;
- jointures ;
- tri ;
- coût ;
- temps réel.

---

# 69. N+1 Queries

Les services doivent éviter les requêtes N+1.

Solutions :

- include contrôlé ;
- jointures ;
- batch ;
- DataLoader ;
- préchargement ciblé.

---

# 70. Sélection des colonnes

Les requêtes ne doivent sélectionner que les données nécessaires.

Éviter de charger :

- documents ;
- secrets ;
- payloads volumineux ;
- relations inutiles ;
- données sensibles.

---

# 71. JSONB

JSONB peut être utilisé pour :

- métadonnées ;
- payloads partenaires ;
- configurations flexibles ;
- réponses brutes contrôlées ;
- audit technique.

Il ne doit pas remplacer systématiquement un modèle relationnel.

---

# 72. Données partenaires brutes

Les réponses brutes peuvent être conservées temporairement pour :

- audit ;
- litige ;
- rapprochement ;
- investigation.

Elles doivent être :

- chiffrées ;
- limitées ;
- masquées ;
- soumises à rétention.

---

# 73. Outbox

La table Outbox doit contenir :

- événement ;
- type ;
- version ;
- payload ;
- statut ;
- tentative ;
- prochaine exécution ;
- corrélation ;
- date de publication.

---

# 74. Inbox

La table Inbox doit enregistrer :

- eventId ;
- consommateur ;
- date ;
- statut ;
- résultat ;
- erreur ;
- corrélation.

---

# 75. Audit

L’audit doit enregistrer :

- acteur ;
- action ;
- ressource ;
- ancienne valeur ;
- nouvelle valeur ;
- motif ;
- date ;
- pays ;
- tenant ;
- environnement ;
- corrélation.

---

# 76. Audit financier

L’audit financier doit inclure :

- transaction ;
- écritures ;
- comptes ;
- montant ;
- devise ;
- approbateur ;
- partenaire ;
- référence ;
- correction ;
- rapprochement.

---

# 77. Sécurité de la base

La base doit appliquer :

- chiffrement ;
- réseau privé ;
- accès minimal ;
- comptes séparés ;
- rotation ;
- audit ;
- sauvegarde ;
- monitoring ;
- restrictions par environnement.

---

# 78. Comptes PostgreSQL

Comptes possibles :

- migration ;
- application lecture-écriture ;
- application lecture seule ;
- analytics ;
- sauvegarde ;
- audit ;
- administration d’urgence.

---

# 79. Permissions minimales

Chaque service ne doit accéder qu’aux tables nécessaires.

Un service ne doit pas disposer automatiquement de droits sur tout le schéma.

---

# 80. Secrets de connexion

Les chaînes de connexion doivent être stockées dans :

- gestionnaire de secrets ;
- variables sécurisées ;
- identités temporaires lorsque possible.

Elles ne doivent pas être committées.

---

# 81. Chiffrement au repos

Le stockage de la base doit être chiffré.

Les sauvegardes et réplicas doivent également être chiffrés.

---

# 82. Chiffrement applicatif

Certaines données peuvent nécessiter un chiffrement supplémentaire :

- documents ;
- identifiants sensibles ;
- secrets partenaires ;
- données biométriques ;
- informations réglementaires.

---

# 83. Masquage

Les environnements et rôles doivent masquer :

- téléphone ;
- e-mail ;
- carte ;
- document ;
- adresse ;
- données sensibles.

---

# 84. Environnements non production

Ils doivent utiliser :

- données fictives ;
- seeds ;
- données synthétiques ;
- données anonymisées ;
- bases séparées ;
- accès séparés.

---

# 85. Migrations

Chaque modification du schéma doit passer par une migration versionnée.

Elle doit être :

- relue ;
- testée ;
- reproductible ;
- compatible ;
- auditable ;
- liée à un commit.

---

# 86. Migrations destructives

Exemples :

- suppression de colonne ;
- changement de type ;
- suppression de table ;
- ajout de contrainte sur données existantes ;
- renommage risqué.

Elles doivent exiger :

- analyse ;
- backup ;
- test ;
- plan de retour ;
- déploiement progressif ;
- approbation.

---

# 87. Expand and Contract

Stratégie recommandée :

1. ajouter la nouvelle structure ;
2. rendre le code compatible ;
3. migrer les données ;
4. basculer les lectures ;
5. supprimer l’ancienne structure plus tard.

---

# 88. Backfill

Un backfill doit être :

- batché ;
- reprenable ;
- idempotent ;
- mesuré ;
- limité ;
- audité ;
- compatible avec la production.

---

# 89. Drift

Le système doit détecter les différences entre :

- schéma Prisma ;
- migrations ;
- base réelle ;
- environnement ;
- client généré.

---

# 90. Seeds

Les seeds doivent fournir :

- pays ;
- devises ;
- rôles ;
- permissions ;
- statuts ;
- configurations ;
- données de démonstration.

Les seeds production doivent être contrôlés.

---

# 91. Sauvegardes

La base doit disposer de :

- sauvegardes automatiques ;
- snapshots ;
- journaux WAL ;
- PITR ;
- copies secondaires ;
- tests de restauration ;
- rétention.

---

# 92. Restauration

Après restauration, vérifier :

- schéma ;
- migrations ;
- utilisateurs ;
- transactions ;
- ledger ;
- soldes ;
- réservations ;
- Outbox ;
- Inbox ;
- audits ;
- rapprochements.

---

# 93. Reconstruction des soldes

Le système doit pouvoir recalculer :

- solde comptable ;
- solde disponible ;
- réservations ;
- agrégats ;
- positions partenaires.

---

# 94. Contrôle d’intégrité

Contrôles réguliers :

- équilibre des écritures ;
- comptes inexistants ;
- doublons ;
- montants négatifs interdits ;
- réservations expirées ;
- transactions sans ledger ;
- ledger sans transaction métier ;
- règlements incohérents.

---

# 95. Jobs de contrôle

Exemples :

```text
ledger_balance_check
ledger_orphan_check
payment_ledger_consistency_check
reservation_expiration_check
settlement_consistency_check
partner_reconciliation_check
```

---

# 96. Alertes

Une alerte doit être créée en cas de :

- ledger déséquilibré ;
- solde négatif interdit ;
- doublon ;
- migration échouée ;
- réplication en retard ;
- espace faible ;
- requête lente ;
- sauvegarde échouée ;
- restauration impossible ;
- rapprochement incohérent.

---

# 97. Administration

Le portail Admin technique peut afficher :

- état des bases ;
- migrations ;
- réplication ;
- sauvegardes ;
- requêtes lentes ;
- partitions ;
- index ;
- contrôles ledger ;
- divergences ;
- comptes de suspense ;
- capacité ;
- alertes.

Il ne doit pas permettre de modifier directement les écritures financières.

---

# 98. Permissions

Exemples :

```text
database.health.read
database.schema.read
database.migration.read
database.migration.approve
database.replication.read
database.backup.read
database.restore.request
ledger.account.read
ledger.transaction.read
ledger.entry.read
ledger.reconciliation.read
ledger.adjustment.request
ledger.audit.read
```

---

# 99. Actions critiques

Doivent être protégées :

- migration production ;
- restauration ;
- modification de schéma ;
- ajustement ledger ;
- création d’un compte comptable ;
- clôture de période ;
- suppression de partition ;
- changement de rétention ;
- modification des règles d’arrondi ;
- accès administratif direct.

---

# 100. Double validation

Peut être exigée pour :

- migration destructive ;
- restauration production ;
- ajustement financier ;
- clôture ;
- suppression d’archive ;
- changement de devise ;
- changement de plan comptable ;
- modification du moteur de solde ;
- correction massive.

---

# 101. Modèles

- DatabaseInstance
- DatabaseSchema
- DatabaseMigration
- DatabaseBackup
- DatabaseRestore
- DatabaseReplica
- DatabasePartition
- DatabaseIndex
- DatabaseQueryMetric
- Wallet
- LedgerAccount
- LedgerJournal
- LedgerTransaction
- LedgerEntry
- LedgerReservation
- LedgerReversal
- LedgerPeriod
- LedgerBalanceSnapshot
- Settlement
- SettlementLine
- Reconciliation
- ReconciliationItem
- SuspenseAccountItem
- FinancialAdjustment
- DatabaseAudit

---

# 102. Règles métier

1. PostgreSQL est la base principale des données métier.
2. Prisma définit le schéma applicatif.
3. Toute modification passe par une migration.
4. Le ledger est la source financière officielle.
5. Les écritures validées sont immuables.
6. Toute correction utilise une contre-écriture.
7. Les débits égalent les crédits.
8. Les montants ne sont pas stockés en flottants.
9. Toute valeur financière possède une devise.
10. Les règles d’arrondi sont centralisées.
11. Le solde n’est jamais modifié directement.
12. Les réservations sont séparées des écritures finales.
13. Les remboursements référencent l’opération d’origine.
14. Les frais sont séparés du principal.
15. Les opérations critiques sont idempotentes.
16. Les contraintes uniques protègent contre les doublons.
17. Les transactions critiques utilisent une isolation adaptée.
18. Les tenants sont isolés.
19. Les requêtes appliquent les permissions.
20. Les index sont liés aux usages réels.
21. Les tables volumineuses peuvent être partitionnées.
22. Les sauvegardes sont testées.
23. Les soldes peuvent être reconstruits.
24. Les contrôles d’intégrité sont automatisés.
25. Les actions critiques sont auditées.

---

# 103. Analytics

Événements possibles :

```text
database_migration_started
database_migration_completed
database_migration_failed
database_replication_lag_detected
database_backup_completed
database_restore_started
database_restore_completed
database_slow_query_detected
ledger_transaction_created
ledger_transaction_posted
ledger_transaction_reversed
ledger_reservation_created
ledger_reservation_released
ledger_balance_mismatch_detected
ledger_reconciliation_completed
ledger_suspense_item_created
ledger_adjustment_approved
```

---

# 104. Tests

- tests Prisma ;
- tests de relations ;
- tests de contraintes ;
- tests de migrations ;
- tests de drift ;
- tests de transactions ;
- tests de concurrence ;
- tests d’idempotence ;
- tests du ledger ;
- tests de double entrée ;
- tests d’arrondi ;
- tests multi-devise ;
- tests de réservation ;
- tests de capture ;
- tests de libération ;
- tests de remboursement ;
- tests de contre-écriture ;
- tests de règlement ;
- tests de rapprochement ;
- tests de suspense ;
- tests multi-pays ;
- tests multi-tenant ;
- tests d’index ;
- tests de partitionnement ;
- tests de sauvegarde ;
- tests de restauration ;
- tests de reconstruction de solde ;
- tests de permissions ;
- tests d’audit.

---

# 105. Critères d’acceptation

L’architecture de données et du ledger est validée lorsque :

- PostgreSQL est configuré ;
- Prisma valide le schéma ;
- les domaines sont correctement modélisés ;
- les migrations sont versionnées ;
- les contraintes protègent les invariants ;
- les tenants sont isolés ;
- les montants utilisent une précision sûre ;
- les devises sont explicites ;
- le ledger utilise la double entrée ;
- les écritures sont immuables ;
- les contre-écritures sont disponibles ;
- les réservations sont gérées ;
- les remboursements sont traçables ;
- les frais et commissions sont séparés ;
- les opérations sont idempotentes ;
- la concurrence est maîtrisée ;
- les index sont adaptés ;
- les grandes tables peuvent être partitionnées ;
- les sauvegardes sont testées ;
- les soldes peuvent être reconstruits ;
- les contrôles d’intégrité sont automatisés ;
- les actions critiques sont protégées ;
- les tests couvrent les scénarios financiers principaux.
